# Competitor set — Kuwaiti insurance on Instagram

## ILAF's own account

| | |
|---|---|
| Handle | **@ilaf_takaful** |
| Name | ILAF Takaful Insurance Company · إيلاف للتأمين التكافلي |
| Confirmed by | Khaled, Aug 2026 |

## Tracked competitors

| Company | Arabic | Handle | Type | Notes |
|---------|--------|--------|------|-------|
| Warba Insurance & Reinsurance | وربة للتأمين وإعادة التأمين | **@warbakw** | Conventional | Handle confirmed from warba.insure footer — high confidence |
| GIG Kuwait | شركة الخليج للتأمين – الكويت | **@gulfinsurance** | Conventional | Display name on the profile is "GIG-Kuwait" |
| GIG Takaful Kuwait | جي آي جي تكافل | **@gigtakaful** | **Takaful** | Closest like-for-like competitor to ILAF |
| Wethaq Takaful Insurance | وثاق للتأمين التكافلي | **@wethaqkuwait** | **Takaful** | Kuwaiti entity — see Egypt warning below |
| KFH Takaful | بيتك للتأمين التكافلي | **@kfhtakaful** | **Takaful** | KFH's takaful arm |
| Boubyan Takaful Insurance | بوبيان للتأمين التكافلي | **@boubyantakaful** | **Takaful** | |
| Al Ahleia Insurance | الشركة الأهلية للتأمين | **@ahleiainsurance** | Conventional | Handle confirmed from alahleia.com footer — high confidence |

When the deck groups competitors, the **takaful peers** (GIG Takaful, Wethaq, KFH Takaful,
Boubyan Takaful) are the more meaningful comparison for ILAF — same product model, same
faith-conscious audience. The conventional insurers (Warba, GIG Kuwait, Al Ahleia) are useful as
a market-activity benchmark: they're often larger and more active, so they show what's possible
rather than what's expected.

## Two traps that silently corrupt the benchmark

**The three GIGs.** These are separate companies with separate accounts:

- `@gulfinsurance` — GIG Kuwait, the local conventional insurer (gig.com.kw) — **tracked**
- `@gigtakaful` — GIG Takaful Kuwait (gigtakaful.com.kw) — **tracked**
- `@gulfinsgroup` — Gulf Insurance Group KSCP, the regional parent — **not tracked**, wrong scope

Mixing them up produces a comparison against a regional holding company's corporate feed, which
looks like data and isn't.

**Wethaq Egypt.** `@wethaqegypt` and `@wethaq_ins` are different entities. Only `@wethaqkuwait`
is the Kuwaiti company.

If a handle 404s or the profile content clearly doesn't match the company, stop and flag it
rather than substituting the nearest plausible account. Handles do change; a wrong one baked into
a recurring report goes unnoticed for months.

## Verified baseline — captured 10 August 2026

Read directly from each profile in Khaled's logged-in Chrome. Every handle was confirmed against
the bio text on the profile itself, so the whole set is now high-confidence — no more inference
from search results.

| Handle | Company | Followers | Posts (lifetime) |
|--------|---------|-----------|------------------|
| @gulfinsurance | GIG Kuwait | ~46K | 3,045 |
| @kfhtakaful | KFH Takaful | ~40K | 2,810 |
| @boubyantakaful | Boubyan Takaful | ~26K | 1,916 |
| @warbakw | Warba Insurance | ~22K | 3,499 |
| @gigtakaful | GIG Takaful Kuwait | ~15K | 1,112 |
| @ahleiainsurance | Al Ahleia Insurance | ~11K | 2,102 |
| **@ilaf_takaful** | **ILAF Takaful** | **7,371** | **313** |
| @wethaqkuwait | Wethaq Takaful | 1,089 | 353 |

**A precision caveat that matters for month-over-month reporting.** Instagram rounds counts above
about 10,000 in the page metadata — "46K" could be anything from 45,500 to 46,499. So for the
larger accounts you cannot detect real month-to-month movement from this source; a competitor
could gain 400 followers and still read "46K". Report competitor followers as approximate, and
never compute a competitor growth percentage off two rounded figures — that manufactures a trend
out of rounding noise. ILAF's own exact count comes from Insights, so ILAF growth is real.

**What this baseline says about ILAF's position.** ILAF is **7th of 8 by audience size**, ahead
of only Wethaq, and the gap to the leaders is large — GIG Kuwait and KFH Takaful are 5–6× bigger.
ILAF also has by far the smallest content archive: 313 lifetime posts against 1,100–3,500 for
everyone else. The competitors have simply been publishing for much longer.

That reframes what the monthly report is for. ILAF will not win on follower count for years, so a
deck that leads with follower rank tells management something demoralising and unactionable.
Lead instead on the metrics where a small, young account can genuinely win — engagement rate,
growth *rate*, and Google Business actions — and treat follower count as context, not a
scoreboard.

Recapture these each month. If you find yourself about to reuse a follower number from a previous
report, stop — that's how a stale number becomes a trend line nobody can trace back. If you
couldn't capture them, set `data_status: "sample"` on the deck.

## Content theme taxonomy

Classify every captured post into exactly one of these. Consistency month over month is what
makes the trend readable — resist inventing new categories mid-report.

| Theme | What belongs here |
|-------|-------------------|
| **Product promotion** | A specific policy or package being sold — motor, medical, travel, home, marine |
| **Educational / awareness** | Explaining a concept, coverage, or risk without a direct sell — "what does comprehensive cover mean" |
| **Safety tips** | Practical advice — road safety, home fire prevention, travel precautions |
| **Religious occasion** | Ramadan, Eid, Jum'ah greetings, Hijri new year, Islamic messaging |
| **National / civic** | Kuwait National Day, Liberation Day, national achievements |
| **Corporate news** | Results, awards, partnerships, branch openings, leadership announcements |
| **Recruitment** | Hiring posts |
| **Customer service** | Contact info, working hours, branch or app announcements, claim process |
| **Engagement / interactive** | Polls, quizzes, competitions, questions to followers |
| **Other** | Genuinely doesn't fit — keep this bucket small; if it exceeds ~15% of a competitor's posts, the taxonomy needs revisiting and you should say so |

Classify by **intent**, not vocabulary. A post listing motor coverage details under a discount
banner is Product promotion. The same list with no offer and a "did you know" framing is
Educational. The distinction is what makes the strategy read useful — it separates brands that
sell from brands that build.

## What to capture per competitor

```
handle, display_name, followers_at_capture, capture_date
posts_in_window: total, by_format {static, carousel, reel}
themes: {theme_name: count}
posts_per_week, rhythm ("steady" | "bursty" | "sporadic")
standout_posts: [{date, format, theme, engagement, one_line_why}]
stories_in_window: from the story log, with days_covered
availability: "full" | "partial" | "unavailable", with a reason if not full
```

## What is not obtainable, and must never appear

**Reach and impressions for accounts ILAF doesn't own are private.** Instagram does not expose
them. Any competitor "reach" number would be fabricated. Use follower count and visible
engagement (likes + comments), which are public and verifiable.

Saves and shares are also private. Engagement rate for competitors must be computed against
**followers**, not reach — and label it as such, because ILAF's own engagement rate in the same
deck is computed against reach. Two different denominators on one slide without labels is how a
deck gets quietly wrong.
