# Daily tracking — stories and competitor ads

Two things in this report expire and cannot be reconstructed after the fact:

- **Instagram stories** disappear after 24 hours. No archive, no API for other people's accounts.
  If nobody looked on the 8th, what Warba posted on the 8th is gone.
- **Meta Ad Library** shows only ads running at the moment you look. A two-week campaign that
  started and ended between checks is invisible.

So both come from a log built up daily through the month. See `references/ads-tracking.md` for
the ad-specific traps.

---

## Where the log lives — read this before changing anything

**In Google Drive, not on any local filesystem.**

Folder: `ILAF Social Reports / daily-tracking`
(`11ljU9zHv52YkatU5QoGrJ1AtXNBX7i2X`)

One file per day: `tracking-YYYY-MM-DD.json`.

This matters, and an earlier version of this file got it wrong. A scheduled task starts a **fresh
cloud session** whose container is discarded when the run ends. Anything written to `~/` or any
container path is gone minutes later, so a log kept there would be permanently empty while
appearing to work every night. Drive persists and needs no device permission prompt.

**One file per day, never one appended file.** The Drive connector can create and read files but
cannot modify one in place, so "append" would mean read-modify-rewrite — which loses data the
moment two runs overlap or one fails halfway.

Note that `create_file` does **not** overwrite: re-running a day produces a second file with the
same title, not a replacement. That is acceptable and by design — **when reading, take the newest
file per date by `createdTime`** and ignore older ones. Never try to reconcile duplicates by
merging them; the newest run saw the most complete picture.

```json
{
  "date": "2026-08-11",
  "captured_at": "2026-08-11T21:04:00+03:00",
  "stories": [
    {"handle": "@warbakw", "stories_active": 3,
     "themes": ["product_promotion", "safety_tips"],
     "note": "motor insurance offer, 3-frame sequence"},
    {"handle": "@wethaqkuwait", "stories_active": 0, "themes": [], "note": ""},
    {"handle": "@ilaf_takaful", "stories_active": 2,
     "themes": ["religious_occasion"], "note": "Jum'ah greeting"}
  ],
  "ads": [
    {"handle": "@gulfinsurance", "library_id": "1396553961870382",
     "started_on": "2026-08-03", "format": "video",
     "promoted_en": "Motor renewal — 20% off comprehensive",
     "promoted_ar": "تجديد المركبات — خصم 20% على الشامل"}
  ],
  "failures": [
    {"handle": "@kfhtakaful", "reason": "login wall after 3 attempts"}
  ]
}
```

`stories_active` is what was visible at capture time. It undercounts when a competitor posts and
the story expires before the next capture — a real limitation, stated once in the deck rather
than papered over.

**A failed account gets a `failures` entry, not a silent omission.** A missing line reads as
zero. A recorded failure is data.

---

## The run must happen on the user's computer — verified the hard way

**A scheduled cloud task cannot do this capture.** Tested twice on 10 Aug 2026: once on its own
schedule, once fired manually while the user's Mac was confirmed awake with the desktop app open.
Both runs had **no browser tools present at all**. A scheduled run starts a fresh cloud session,
and that session gets no connection to the user's machine — this is not a sleeping-laptop problem
and no amount of retrying fixes it.

The task behaved correctly (wrote the file, logged an honest gap, invented nothing) — it would
simply have written "not captured" every night for a month.

So the capture has to run in a session that has the browser: either a task scheduled **on the
user's computer** through the desktop app, or an interactive session the user starts. If you are
setting this up, do not create a cloud scheduled task for it and assume it works. Confirm a run
actually reached the browser before telling the user it is running.

---

## Detecting stories without watching them

Read the story ring off the profile page; never open the stories.

```js
const hdr = document.querySelector('header');
const cs = [...hdr.querySelectorAll('canvas')].map(c => Math.round(c.getBoundingClientRect().width));
const storyRing = cs.filter(w => w > 120).length;   // avatar ring ~165px, at the top
const highlights = cs.filter(w => w <= 120).length; // highlight rings ~87px, lower down
```

A canvas wider than 120px in the header is the avatar's live-story ring. The ~87px ones are
**highlights** — permanent, and counting them as stories would report activity every single day
for accounts that posted nothing.

**Do not open competitor stories to count frames.** Watching places ILAF in that competitor's
viewer list, every day, indefinitely. Presence is the honest and sufficient signal: "Boubyan
posted stories on 19 of 31 days" is the number the deck actually uses. Record `has_story` as a
boolean and leave `stories_active` null.

Verified 10 Aug 2026 across all eight accounts: three showed a live ring, five did not, and the
ring count tracked highlights correctly on every profile.

---

## Capture follower and post counts too

The same page read gives public follower and post totals, at no extra cost. Record them nightly
for every account, ILAF included.

This quietly solves a gap the report could not otherwise close: Instagram exposes new-follower
data only for the last 30 days, so July's growth was unrecoverable. A nightly public read gives
true month-end figures from now on — and competitor growth curves, which no API provides at all.

**Read the exact count, not the abbreviation.** Instagram displays "45.7K" but carries the true
integer in the follower span's `title` attribute — 45,716. Month-on-month growth computed from
rounded thousands is meaningless; a competitor could gain 400 followers and show no change at
all. Always take the title attribute where it exists and fall back to the visible text only when
it doesn't.

Confirmed working 11 Aug 2026: all eight accounts on the first attempt, exact counts for the six
that Instagram abbreviates.

---

## What the daily run requires

The capture runs through **the user's Chrome on their Mac**, and there is no cloud-only
alternative:

- Instagram stories need a logged-in session. There is no public view.
- The Ad Library refuses automated fetching — a direct fetch from the cloud environment returns
  `ROBOTS_DISALLOWED` (verified 10 Aug 2026). It has to be a real browser.

So the run needs, at the scheduled moment: the Mac **awake** (not asleep, not shut), the **Claude
desktop app open**, and Chrome **logged into Instagram**.

If the Mac is asleep the run cannot reach the browser. In that case still write the day's file
with empty `stories`/`ads` and a `failures` entry explaining why — the month's coverage count
then reflects reality instead of silently dropping a day.

Tell the user this plainly when setting it up. A tracking system that quietly depends on their
laptop being awake, without saying so, produces a confident report built on a third of the data.

---

## How the daily capture is triggered

**By Khaled saying "track today"** (or "رصد اليوم"). Not by a scheduled task.

That is a deliberate choice, arrived at after both alternatives failed:

- A **cloud scheduled task** has no browser at all. Tested twice on 10 Aug 2026 — once on
  schedule, once forced while the Mac was confirmed awake with the app open. Neither run had the
  Chrome tools. It would have logged a gap every night.
- A **task scheduled on the Mac** should work in principle and did work when run by hand, but the
  recurring schedule proved hard to confirm, and a capture nobody can verify is worse than one
  someone controls.

So the capture is a command. It runs in whatever session he is already in, which is exactly the
session that has the browser. The full procedure is in SKILL.md under *The daily capture, on
request*.

**Timing does not matter.** Stories live 24 hours, so any single capture in a day sees everything
that was posted. Morning is as good as night. What matters is roughly once a day, never that it
lands at a particular hour — do not tell him otherwise, and do not treat an afternoon capture as
inferior to an evening one.

A cloud task at 21:30 Kuwait checks whether the day has a file and notifies him only when it
doesn't. That one has no browser and needs none — it only reads Drive.

---

## Reporting from the log

At month end, list the files in the `daily-tracking` folder, read those inside the window, and
count the distinct dates present.

- **Days covered / days in month** goes next to every story and ad figure, and in the coverage
  slide.
- Report the **observed total** — the sum of what was actually captured. Never scale it to a
  full-month estimate. A scaled figure looks like a measurement and isn't one, and it will be
  compared against next month's differently-scaled figure.
- Deduplicate ads on `library_id` before counting. The same ad seen on ten nights is one ad;
  counting sightings inflates a competitor's activity several-fold.
- If coverage is below about two-thirds of the month, say plainly that story and ad counts are
  indicative rather than comparative, and lean the competitive analysis on feed posts instead.

If no log exists for the reporting month, the deck reports these as "غير متاح · Not available"
and you offer to start tracking. An honest first report and a complete second one beats a
fabricated first one.
