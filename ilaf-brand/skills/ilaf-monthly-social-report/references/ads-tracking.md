# Tracking competitor sponsored ads

Organic posts show what a competitor wants to say. Ads show where they are willing to spend
money, which is a much stronger signal of what they believe is working. This is often the most
useful page in the whole report.

The source is **Meta's Ad Library** — public, free, no login, and it covers Instagram as well as
Facebook because both run through Meta's ad system:

```
https://www.facebook.com/ads/library/
```

---

## The constraint that shapes everything

**The Ad Library only shows ads that are running at the moment you look.** For ordinary
commercial ads there is no history. A competitor who ran a two-week motor campaign in the middle
of the month and stopped is completely invisible by month end.

This is exactly the same problem as Instagram stories, and it has the same answer: **capture as
you go**. A report-time check is not a substitute — it tells you who happens to be advertising
today, not who advertised this month.

One partial mercy: each active ad shows **"Started running on <date>"**. So a check today does
reveal ads that began weeks ago and are still live. That means occasional checks are worth
something — they just systematically miss short campaigns, which are often the most interesting
ones because they signal a push.

Never present the ad list as complete. The deck footer states how many days were captured.

---

## Search by advertiser, never by keyword

This is the trap that will silently corrupt the data.

Keyword search on Arabic insurance terms returns the wrong companies. A search for
`الخليج للتأمين` with `country=KW` returns **GIG Bahrain, GIG Oman and GIG Jordan** — regional
sister companies that advertise into Kuwait or simply match the words. Searching `تأمين` alone
returns roughly 620 results, mostly car rental, travel agencies and unrelated businesses.

Verified on 10 Aug 2026. Do not use keyword search for the competitor table.

Instead, filter by the advertiser's Facebook Page:

```
https://www.facebook.com/ads/library/?active_status=all&ad_type=all&country=KW&view_all_page_id=<PAGE_ID>
```

**Page IDs need to be captured once**, then reused every month. To find one: open the
competitor's Facebook Page → About → Page transparency, or search their exact page name in the
Ad Library and use the advertiser result rather than a keyword result. Record them in
`references/competitors.md` beside each handle, so this is a one-time cost.

Until the Page IDs are recorded, say so in the report rather than substituting keyword results.

---

## What to capture per check

For each competitor, per ad:

| Field | Notes |
|-------|-------|
| `library_id` | The "Library ID" shown on the ad — the stable identifier for deduplication |
| `started_on` | From "Started running on" |
| `first_seen` | Date of *your* check that first saw it |
| `promoted` | One line on what the ad is selling — product and offer |
| `format` | Image / video / carousel |
| `platforms` | Facebook, Instagram, Messenger, Audience Network |

Deduplicate on `library_id`. The same ad appearing across ten daily checks is one ad, not ten.
Counting impressions of your own checks as "ads" inflates a competitor's activity several-fold
and is the easiest mistake to make here.

Ads go under the `ads` key of the same daily Drive file as the stories — see
`references/story-tracking.md` for the file, the folder ID, and why it lives in Drive rather than
on disk. One entry per ad:

```json
{"handle":"@gulfinsurance","page_id":"1234567890",
 "library_id":"1396553961870382","started_on":"2026-08-03","format":"video",
 "platforms":["facebook","instagram"],
 "promoted_en":"Motor renewal — 20% off comprehensive",
 "promoted_ar":"تجديد المركبات — خصم 20% على الشامل"}
```

A day that finds no ads still gets a file with an empty `ads` array. Otherwise a quiet month is
indistinguishable from a month nobody checked.

---

## Rolling it up for the deck

At report time, read the log, filter to the reporting window, deduplicate on `library_id`, and
group by advertiser into `competitor_ads.advertisers[]`. Set `capture_days` to the number of
distinct `checked_on` dates inside the window, and `capture_total_days` to the days in the month.

The `insight` line is the point of the slide. Counts alone are inventory. Look for:

- **A product nobody is advertising.** If six competitors push motor and nobody touches home
  cover, that is either an opening or a reason nobody bothers — worth ILAF asking which.
- **Offer mechanics.** Percentage discounts, free first-year add-ons, instant-quote hooks. If
  every competitor advertises on price, ILAF competing on brand warmth is a deliberate choice
  and should be a conscious one.
- **Timing.** Campaign clusters around renewal season, Ramadan, or back-to-school.
- **Format.** Who is spending on video versus static.

---

## Honesty rules

- Never estimate spend. Meta does not publish spend for commercial ads (only for political and
  social-issue ads, which insurers do not run). Any spend figure in this report would be invented.
- Never state that a competitor "did not advertise" — only that no ads were seen on the days
  checked. The difference matters and the wording should carry it.
- If Page IDs are missing for some competitors, list those competitors as not covered rather
  than leaving them out of the table silently. An absent row reads as "no ads".
