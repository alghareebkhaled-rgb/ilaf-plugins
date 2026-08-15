# Deck structure

Twelve slides, 16:9. The builder script produces these from the data file — this document
explains what each one is *for*, so you gather the right material and write the right commentary.

Management reads this in about four minutes. Slides 2 and 12 are the ones that get read
properly; everything between them is evidence for those two. Write accordingly.

Every slide carries Arabic and English. Arabic sits right-to-left, English left-to-right, and
the builder handles the placement — you supply both strings.

---

| # | Slide | Purpose |
|---|-------|---------|
| 1 | Cover | Month, brand, date generated |
| 2 | Month at a glance | Five KPI tiles with MoM arrows — the executive summary |
| 3 | Audience growth | Follower trend and net growth, churn if available |
| 4 | Reach & engagement | Reach, impressions, engagement rate over the two months |
| 5 | Content output | What ILAF published — volume and format mix |
| 6 | Top performing posts | Best 3 by engagement rate, with the reason |
| 7 | Underperforming posts | Weakest 2–3, with the reason — the honest slide |
| 8 | Google Business Profile | Search discovery, calls, directions, reviews |
| 9 | Competitor activity | The counts table — posts, stories, followers, per competitor |
| 10 | Competitor content strategy | Theme mix across the market, and where ILAF differs |
| 11 | Share of voice | ILAF's share of tracked market posting |
| 12 | Recommendations & coverage | 3–5 actions, plus the data coverage note |

---

## Slide 2 — Month at a glance

Five tiles: followers, reach, engagement rate, Google Business calls, posts published. Each with
the current value, the MoM delta, and an arrow.

Colour the arrows by whether the movement is *good*, not by whether it's *up*. Unfollows rising
is an up arrow and a bad outcome. Getting this backwards on the summary slide is the single most
damaging error in the deck, because it's the slide people remember.

Under the tiles, one sentence in each language stating the month's headline. Write it as a
finding: "Reach grew 18% on 30% fewer posts — the reel format is carrying the account." Not
"This month saw various changes in performance."

## Slides 3–4 — Growth, reach, engagement

Two months side by side. The thing to make visible is the *relationship* between the numbers,
because that's where the insight lives — followers up while engagement rate falls means the
account is growing an audience that doesn't care, which is a real and fixable problem.

If a metric is unavailable, the builder renders "غير متاح · Not available" in the tile. Leave it
that way.

## Slide 5 — Content output

Volume and the static/carousel/reel split, with the previous month behind it for comparison.
Include stories published. This slide sets up slides 9–11: you can't argue about share of voice
without first showing output.

## Slides 6–7 — Top and underperforming posts

Ranked by engagement rate (engagement ÷ reach), so distribution luck doesn't distort the picture.
For each post: date, format, theme, the numbers, and **one line on why**.

The "why" is the entire value of these two slides. Look for the pattern — format, topic, day and
time, hook style, whether it asked anything of the viewer. If three of the top posts are reels
posted on weekend evenings, that's next month's plan writing itself.

Slide 7 is uncomfortable and it is the most useful slide in the deck. Don't soften it into
nothing. "This carousel about marine cargo cover reached 40% below average — the topic is B2B and
the audience here is retail" is useful. "Room for improvement" is not.

## Slide 8 — Google Business Profile

Lead with **calls and direction requests** — these are people trying to reach ILAF, which is
closer to business value than any Instagram metric on the preceding slides. Then the search
split (direct vs discovery), then reviews.

If new reviews arrived, quote the substance of one, good or bad. It's the only qualitative voice
of the actual customer in the whole deck.

## Slide 9 — Competitor activity

A table: one row per competitor, columns for followers, posts in window, format split, stories,
posts/week. ILAF's own row sits at the top, visually distinguished, so the comparison is
immediate.

Group takaful peers above conventional insurers, since the takaful set is the like-for-like
comparison. Mark any competitor whose data is partial or unavailable in the row itself.

## Slide 10 — Competitor content strategy

The theme mix across the market, with ILAF's mix beside it. The question this slide answers is
"what are they doing that we aren't, and does it matter?"

Call out specifically: themes ILAF doesn't touch at all, formats where ILAF is behind the field,
and any competitor running a visible campaign. Name the competitor and the theme — vagueness here
wastes the whole competitive sweep.

## Slide 11 — Share of voice

ILAF's posts as a percentage of all tracked posts in the window. One number, one chart.

**"Share of voice" is a term of art, so the slide defines itself.** The builder writes a plain
sentence under the title — "ILAF published 14 of the 113 posts put out by the 7 tracked Kuwaiti
insurers" — because most of this audience reads the phrase cold. Leaving it undefined produces
two failure modes: people quietly misread it as share of *audience* or *reach*, or they quote the
percentage in another meeting without the denominator attached.

Two honest limits to keep in mind when writing the commentary:

- It measures **volume, not attention**. Posting more low-quality content raises share of voice.
  Never present a rising share as a win on its own — pair it with the engagement figures.
- It depends entirely on **who is counted**. A different competitor list gives a different
  number, which is why the denominator belongs on the slide, not in a footnote.

## Slide 12 — Recommendations & data coverage

Three to five recommendations, each tied to a specific finding earlier in the deck. Order them by
expected impact, not by how easy they are.

Then the coverage note: which sources were captured in full, which were partial, which failed,
and how many days the story log covered. Putting this on the final slide rather than a footnote
is deliberate — it means nobody can read the deck without seeing what it does and doesn't know.

---

## Writing the bilingual copy

Write the Arabic first when the finding is nuanced. Arabic written as a translation of English
insight reads stiff; Arabic written directly reads like a colleague talking. The tone guidance in
`ilaf-social-design/references/brand-facts.md` applies — warm, professional, light Kuwaiti
register, not stiff MSA.

Numbers stay in Western numerals in both languages — that's the norm in Kuwaiti business
documents and it keeps the two columns visually aligned.

Keep slide text short. A management deck fails by being too full far more often than by being too
sparse. If a finding needs a paragraph, it belongs in the summary you write in chat, not on the
slide.

---

## Slide — Enquiries & Direct Contact

WhatsApp messages received as the headline, beside Google's phone calls, direction requests and
website clicks, plus a computed "total conversations started" (WhatsApp + Google calls).

This is the only slide in the deck measuring people rather than attention. Put it directly after
Google Business Profile so the two read together.

`ilaf.whatsapp.current.messages_received` is the one required field; `new_contacts`, `replied`
and `by_topic` are optional and render only when supplied. The total is shown only when every
component is present — a partial sum reads as a real one and understates the month.

Source: Khaled, from WhatsApp Business → Settings → Business tools → Messaging statistics. There
is no connector for this; ask for it up front.

---

## Slide — Competitor Advertising

Which competitors paid to promote posts this month, and what they promoted. One row per
advertiser: name, ads seen, first seen, what they pushed (bilingual).

The `insight` line is the payload — a product nobody is advertising, an offer mechanic everyone
is using, a campaign cluster around renewal season. Counts alone are inventory.

Data comes from the daily ad log; see `references/ads-tracking.md`. The footer always states how
many days were captured, because Meta's Ad Library only shows currently-running ads and short
campaigns between checks are invisible.

Never show ad spend — Meta doesn't publish it for commercial ads, so any figure would be invented.
