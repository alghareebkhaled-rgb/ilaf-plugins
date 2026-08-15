---
name: ilaf-monthly-social-report
description: Produce ILAF Takaful's (إيلاف) monthly social media performance report — a bilingual Arabic/English deck covering ILAF's Instagram and Google Business Profile results, plus a competitor benchmark against other Kuwaiti insurers. Use whenever the user asks for the monthly report, "the social report", "last month's numbers", "our Instagram performance", a competitor comparison on social, a Google Business or Maps review, or how "our page" did over a month — even when they never say "report". Trigger on casual phrasings like "how did we do in June", "what are Warba and Wethaq posting", "make the deck for management", "share of voice", "did we grow". ALSO trigger on the daily capture command — "track today", "رصد اليوم", "today's tracking", "log today" — which records competitor stories, ads and follower counts to Drive; and on requests to set up or catch up that log. Do NOT trigger for designing posts or stories (use ilaf-social-design), AI-news content, the Qur'an/Hadith series, or another company.
---

# ILAF Monthly Social Performance Report

You produce the monthly report that ILAF's management reads to understand how the brand is
performing on social media and how it sits against the rest of the Kuwaiti insurance market.

The deliverable is a **bilingual Arabic/English deck, delivered as Google Slides in Khaled's
Google Drive**. The audience is management, not analysts — so the deck has to answer "are we
winning, where are we losing, and what do we do next month" on the first read, with the raw
numbers available but never in the way.

This report is only as good as its honesty. Numbers you couldn't obtain must be shown as
unavailable, not estimated into a confident-looking chart. A management deck that quietly
invents a competitor's reach destroys trust in every other figure on the page the moment
someone checks it.

---

## The shape of the work

1. **Fix the reporting period** — which month, and the exact date range.
2. **Pull ILAF's own numbers** — Instagram + Google Business Profile, current month and the one
   before it (you need the prior month to show growth).
3. **Sweep the competitors** on Instagram — counts, formats, themes.
4. **Merge in the story log** — the daily capture file, because stories expire.
5. **Analyze** — growth, best and worst content, what competitors are doing that ILAF isn't.
6. **Build the deck** with the bundled script.
7. **Upload to Drive** as Google Slides and hand over the link.

Work through these in order, but don't treat step 2 failing as fatal — see *When data is
missing* below. Partial reports delivered on time beat perfect reports delivered never.

---

## Step 1 — Fix the reporting period

If the user names a month, use it. If they say "last month" or just ask for "the report", assume
the **most recently completed calendar month** and say which one you assumed in your first reply
— that single sentence prevents a whole wasted run.

Record the range as full calendar days (e.g. 2026-07-01 → 2026-07-31). Every count in the deck
must use this same window, or the comparisons stop meaning anything.

You also need the **preceding month's** figures for ILAF to show growth. If a previous report
exists in Drive, read its numbers rather than re-pulling — it's faster and it guarantees this
month's "previous" matches last month's "current", so the trend line doesn't contradict itself.

---

## Step 2 — Pull ILAF's own numbers

Primary source is the **Supermetrics** connector (`data_query`), which reaches Instagram and
Google Business Profile. `references/metrics.md` lists the exact metrics to request, the
discovery calls to make first, and the manual-export fallback. Read it before querying.

The short version: use `data_source_discovery` and `accounts_discovery` to find the ILAF
Instagram and Google Business accounts, `field_discovery` to confirm current field names (they
change), then `data_query` for the month and the month before.

If Supermetrics isn't connected or returns nothing, don't stall. Tell the user what's missing
and offer the fallback: they export from Meta Business Suite and Google Business Profile and
attach the files. `references/metrics.md` says exactly which screens and date ranges to grab so
the manual path produces the same fields as the API path.

---

## Step 3 — Sweep the competitors on Instagram

The competitor list, handles, and the traps in it live in `references/competitors.md`. Read it
— there are three separate "GIG" companies and picking the wrong one silently corrupts the
benchmark.

Gather this per competitor, using the Chrome browser tools against their public profiles:

- **Follower count** at time of capture
- **Feed posts published in the window** — count, split by format (static / carousel / reel)
- **Content themes** — classify each post into the taxonomy in `references/competitors.md`
- **Posting rhythm** — posts per week, and whether it's steady or bursty
- **Standouts** — the 2–3 posts with visibly high engagement, and what they were about

Practical notes that save time and mistakes:

- Instagram shows posts newest-first with dates on each. Scroll until you pass the start of your
  window, then stop — you don't need their whole history.
- Engagement counts are visible on posts but reach is not. Reach is private data for accounts you
  don't own. Never present a competitor "reach" figure; use engagement and follower count, which
  are public and honest.
- Instagram throttles rapid scrolling and will sometimes show a login wall. If a profile won't
  load after two or three attempts, record it as unavailable for this month and move on rather
  than burning the run on it. One missing competitor is a footnote; a failed report is not.
- Classify themes from what the post is actually *for*, not just its words. A photo of a car with
  a discount is promotional, not educational, even if it lists coverage facts.

---

## Step 4 — Merge in the story log

Stories vanish after 24 hours, so monthly story counts cannot be reconstructed at month end.
They come from the daily capture log in Google Drive: **ILAF Social Reports / daily-tracking**,
one `tracking-YYYY-MM-DD.json` file per day. It is in Drive rather than on disk because each
scheduled run gets a fresh container that is discarded afterwards — a local path would silently
stay empty forever.

Read `references/story-tracking.md` for the log format, how to set up the daily scheduled task
if it doesn't exist yet, and how to report honestly when the log has gaps.

The rule that matters: if the log covers 22 of 31 days, the deck says "22 of 31 days captured"
next to the story figures. Scaling 22 days up to a 31-day estimate produces a number that looks
authoritative and isn't. Management will make decisions on it.

The same daily file also captures **competitor sponsored ads**, under an `ads` key. Read
`references/ads-tracking.md` before building that slide — Meta's Ad Library has the same expiry
problem as stories, and a keyword search silently returns the wrong companies.

---

## Step 4b — Ask for the WhatsApp number

WhatsApp enquiries don't come from any connector — Khaled reads them from WhatsApp Business
(**Settings → Business tools → Messaging statistics**) and gives you the figure.

Ask for it explicitly at the start of the run, in the same message where you confirm the
reporting month. Don't wait until the deck is otherwise finished; that turns a five-second
question into a rebuild.

Only **messages received** is required. `new_contacts`, `replied` and a `by_topic` breakdown are
supported by the builder and render when present, but the slide stands on the single number.

This figure matters more than its size suggests. Every other slide measures attention — reach,
views, likes. WhatsApp messages and Google calls are the only numbers in the report that
represent a human deciding to make contact, which is the closest thing to a lead the deck has.
If it's unavailable, mark it unavailable; never infer it from message volume elsewhere.

---

## The daily capture, on request

Khaled triggers this by saying **"track today"** (or "رصد اليوم"). It is a two-minute job, not a
report. Do it immediately, confirm what was found in two or three lines, and stop — no deck, no
analysis, no summary of the month.

This runs in whatever session he's in, so the browser is available. That is the whole reason this
command exists: scheduled cloud runs have no browser, and scheduling on his Mac proved fiddly. A
command he controls beats an automation he has to keep verifying.

**Timing does not matter.** Stories live 24 hours, so any one capture per day sees everything.
Morning is as good as evening. What matters is roughly once a day, not the hour.

Steps:

1. Check Drive folder `11ljU9zHv52YkatU5QoGrJ1AtXNBX7i2X` for `tracking-<today>.json`. If a file
   already exists for today with real follower numbers, say so and ask whether to re-run rather
   than silently creating a duplicate.
2. For each of the eight handles, open `https://www.instagram.com/<handle>/` and run the header
   read described in `references/story-tracking.md` — story ring, highlights, followers, posts.
   Take the exact follower integer from the `title` attribute, not the abbreviated "45.7K".
3. Never open a story. Presence only. The reason is in `references/story-tracking.md`.
4. Ads: only if Page IDs are recorded in `references/competitors.md`. Otherwise record a
   `failures` entry saying they are missing. Never fall back to keyword search.
5. Write `tracking-<today>.json` to the folder, one entry per handle including the empty ones.
6. Report back in two or three lines: how many accounts loaded, which had stories, any failures.
   Mention anything notable — a competitor whose post count jumped, an unusual follower move.

If an account won't load after two or three tries, record the failure and move on. One missing
account is a footnote; a stalled run loses the night.

---

## Step 5 — Analyze

This is where the report earns its place. Anyone can put counts on a slide. What the deck needs
to surface:

**Growth vs last month.** Direction and magnitude for followers, reach, engagement rate, profile
visits, and the Google Business metrics. An engagement *rate* falling while follower count rises
is the single most common story in this data and the most commonly missed — always compute rate,
not just totals.

**Top and worst posts.** Rank ILAF's own posts by engagement rate (engagement ÷ reach), not raw
engagement, so a post that got lucky with distribution doesn't crowd out one that genuinely
resonated. For each, say *why* in one line — format, topic, timing, hook. "Reel, motor insurance,
posted Sunday evening" is a usable insight; "performed well" is not.

**Competitor content strategy.** The counts are the setup; the insight is the pattern. What
themes do they lean on that ILAF doesn't touch? Who is posting reels while ILAF posts statics?
Is anyone running a campaign — a burst of related posts over a short window? Where is ILAF's
posting volume relative to the field: leading, mid-pack, or invisible?

**Share of voice.** ILAF's posts as a share of all tracked posts that month. Simple, and it
lands with management better than any other single number.

**Recommendations.** Three to five, each traceable to something specific in this month's data.
"Post more reels" is filler. "Reels were 3 of your 4 highest-engagement posts this month while
only 20% of output — shift the mix toward reels next month" is a recommendation someone can act
on. If the data doesn't support a recommendation, write fewer of them rather than padding.

Write the commentary in **both Arabic and English**. Arabic should read as natural Kuwaiti
business Arabic, not translated English — the tone guidance in the `ilaf-social-design` skill's
`references/brand-facts.md` applies here too.

---

## Step 6 — Build the deck

Assemble the findings into a data file, then run the bundled builder:

```bash
python3 scripts/build_report_deck.py report_data.json -o "ILAF_Social_Report_2026-07.pptx"
```

`scripts/report_data.template.json` is a filled-in example showing every field — copy it and
replace the values. The script handles the brand styling, the bilingual layout, the RTL Arabic
text, and the charts, so you never have to hand-build slides or reinvent the palette.

The full slide-by-slide structure, and what belongs on each slide, is in
`references/deck-spec.md`. Read it before filling the data file so you gather the right things.

Any field you leave out is rendered as "غير متاح · Not available" rather than a zero — that
distinction is deliberate. Zero means they posted nothing; unavailable means we couldn't see.
Don't collapse the two.

**Set `data_status` honestly.** It's `"verified"` only when every headline figure came from a
source you actually read this month — a Supermetrics query you ran, an export the user attached,
a profile you opened. Anything else — example data, numbers carried over from a previous month,
figures you inferred — stays `"sample"`, which stamps a red banner across every slide.

This matters more than it looks. A deck built from placeholder numbers is visually identical to a
real one, and decks get forwarded to people who never saw the conversation around them. A caveat
in your message doesn't travel with the file; a stamp on the slide does. When in doubt, stamp it
— an obviously-provisional deck costs a follow-up question, an unmarked one costs the report's
credibility.

If the user wants something the builder doesn't cover — an extra slide, a different chart — edit
the script rather than abandoning it for hand-built slides. The script exists so that next
month's report costs minutes instead of hours; keeping it current is what preserves that.

### Post images on the top / weak post cards

Set `image` on a post to a local file path and the card shows the actual post, cropped to 4:5
rather than squashed. Management recognises the picture long before they read the caption, so
this is worth the few minutes it takes. Cards fall back to the text-only layout when `image` is
absent, so a missing file never breaks a slide.

Getting the files needs a specific route, because two obvious ones don't work:

- **This container cannot reach Instagram's CDN** (`scontent-*.cdninstagram.com` returns 403).
  Don't retry it with curl, requests or a proxy.
- **Never copy image bytes through the conversation as base64.** It looks like it works — the
  JPEG still opens — but a third of the data goes missing and the picture is quietly mangled.
  Verified: a 5,488-character image came back as 3,536.

What does work, using the connected desktop:

1. Query Supermetrics for `media_url` and `media_thumbnail_url` alongside the post metrics
   (report type `AccountMedia`). Reels have an empty `media_url` for stills — use
   `media_thumbnail_url` for those, since `media_url` is the video.
2. Ask for access to `~/Downloads` via `device_request_folder_access`, once.
3. For each image: `open_url` straight to the image, then run
   `fetch(location.href) → blob → <a download>` in that tab. **One image per page load** —
   Chrome blocks a page that fires several downloads, and the extra ones vanish silently with
   no error. Navigating first also sidesteps CORS, since the fetch is then same-origin.
4. `device_stage_files` the saved files into the container and point `image` at them.

The builder downsamples to about 200dpi of the printed size, so full-resolution exports don't
bloat the deck — six images add roughly 90KB, not 700KB.

---

## Step 7 — Deliver

Send the `.pptx` to the user with `SendUserFile`, and tell them dropping it into Drive opens it
as Google Slides.

**On uploading to Drive automatically.** The Google Drive connector's `create_file` only accepts
file content inline as base64 — there's no way to point it at a local path. A finished deck is
70–120 KB, which is roughly 100–160 thousand base64 characters that would have to be reproduced
character-perfect in a single tool call. One wrong character produces a corrupt file that looks
fine until someone opens it. So don't attempt it for a full deck.

What works instead: keep a `ILAF Social Reports` folder in the user's Drive, send them the file,
and let them drop it in — a two-second drag that avoids a silent-corruption risk entirely. If
they'd rather it be automatic, the honest options are a Drive desktop-sync folder, or
`device_commit_files` to write it straight to their machine when a device is connected.

Name the file `ILAF Social Report — YYYY-MM` either way. Consistent naming is what makes next
month's "read last month's numbers" step work.

Then give the user: the Drive link, a three-to-five line summary of the month's story in plain
language, and an explicit list of anything that was unavailable or estimated. Lead with the
finding, not the file — they asked for a report because they want to know how the month went.

If Google Drive isn't connected, send the `.pptx` directly with `SendUserFile` and tell them
that dropping it into Drive opens it as Slides. Never let a missing connector block delivery.

---

## When data is missing

This will happen most months in some form — a connector down, a profile behind a login wall, a
gap in the story log. The report is still worth producing. What matters is that the deck is
transparent about its own coverage.

- Mark unavailable figures as **"غير متاح · Not available"** on the slide itself, not only in a
  footnote someone won't read.
- Add a short **data coverage note** on the closing slide: what was captured, what wasn't, and
  why.
- Never interpolate, extrapolate, or fill a gap with a plausible-looking number. If a chart would
  mislead with a gap in it, use a table instead.
- Tell the user in conversation what's missing and what would fix it for next month. That's how
  the gaps actually close.

---

## Bundled resources

| Path | Read it when |
|------|--------------|
| `references/competitors.md` | Before the competitor sweep — handles, the GIG trap, theme taxonomy |
| `references/metrics.md` | Before pulling ILAF's numbers — exact metrics, Supermetrics calls, manual fallback |
| `references/deck-spec.md` | Before filling the data file — slide-by-slide structure |
| `references/story-tracking.md` | When setting up, checking, or reporting on the story log |
| `references/ads-tracking.md` | Step 4 — competitor sponsored ads, and the Ad Library's traps |
| `scripts/build_report_deck.py` | Step 6 — builds the branded bilingual deck |
| `scripts/report_data.template.json` | Copy as the starting point for the data file |
| `assets/` | Logo, brand fonts, and the Sadu band, used automatically by the builder |
