# Pulling ILAF's own numbers

Two sources: **Instagram** (ILAF's own account, so private metrics like reach are available) and
**Google Business Profile** (how ILAF shows up in Search and Maps). Both come through the
Supermetrics connector, with a manual export fallback.

Always pull **two months**: the reporting month and the one before it. Growth is the point of the
report, and a single month of data can't show it.

---

## Instagram — metrics to request

### Audience
| Metric | Why it's in the deck |
|--------|---------------------|
| `followers` (end of period) | The headline number management looks for first |
| `follower_growth` (net gained) | Direction of travel |
| `follows` / `unfollows` if available | Net growth hides churn — a month with 200 gained and 180 lost is a very different story from 20 gained and 0 lost |

### Reach & impressions
| Metric | Why |
|--------|-----|
| `reach` | Unique accounts that saw content — the true audience size |
| `impressions` | Total views; impressions ÷ reach shows repeat exposure |
| `profile_views` | Interest strong enough to click through to the profile |
| `website_clicks` | The closest thing to intent on the platform |

### Engagement
| Metric | Why |
|--------|-----|
| `likes`, `comments`, `saves`, `shares` | The components — saves and shares matter more than likes for reach |
| `total_engagement` | Sum, for the headline |
| **engagement rate** | Computed: `total_engagement ÷ reach`. Compute it yourself; don't trust a platform-supplied "engagement rate" without knowing its denominator |

### Content
| Metric | Why |
|--------|-----|
| Posts published, split static / carousel / reel | Output volume and mix |
| Stories published | ILAF's own stories are in Insights (unlike competitors') |
| Per-post: date, format, caption or topic, reach, engagement | Needed for the top/worst ranking |

---

## Google Business Profile — metrics to request

This is how people find ILAF's office when they're actively looking — high-intent traffic, and
usually under-reported. Management rarely sees it, which makes it one of the more interesting
slides.

Source is the **`GMB`** (Google My Business) connector. Confirmed working field IDs, report type
`Performance`:

| Field ID | Why |
|----------|-----|
| `views_total`, `views_search`, `views_maps` | Visibility, split by surface |
| `actions_total` | All interactions with the profile |
| `actions_phone` | The strongest intent signal in the whole report |
| `actions_driving_directions` | People physically heading to Ahmad Tower |
| `actions_website` | |
| `total_review_count`, `total_review_star_rating` | Lifetime totals (report type `ReviewsTotals`) |
| `review_star_rating`, `review_comment`, `review_create_date` | Individual reviews (report type `Reviews`) |

**Direct vs discovery vs branded searches no longer exist.** Google retired that split in the
newer Business Profile performance API, and the connector has no field for it. Don't go looking
for it and don't approximate it — the deck renders those rows as unavailable, which is correct.

Review text often comes back empty even when a rating exists, because most reviewers leave stars
without writing anything. An empty `review_comment` is normal, not a query error.

Two oddities to expect rather than chase: `actions_total` can slightly exceed `views_total`
(Google counts them over different windows), and monthly views can fall while actions rise. Both
are real, and the second is worth reporting — it means the profile is converting better even
while being seen less.

Review text matters more than the count. If new reviews came in, read them — a single specific
complaint about claims handling is worth more to management than the rating moving 0.1.

---

## Supermetrics — how to query

Discovery first, then query. The connector's field names change, and a query built on remembered
field names fails in ways that look like "no data" rather than an error.

1. **`data_source_discovery`** — confirm Instagram and Google Business Profile are available on
   this account.
2. **`accounts_discovery`** — find ILAF's Instagram account ID and the Google Business Profile
   location ID. Verify you have ILAF's account and not another one on the same login.
3. **`field_discovery`** — get the current metric and dimension names for each source. Map the
   tables above onto whatever names come back; don't assume.
4. **`data_query`** — one query per source per month. Use the exact date range from Step 1 of the
   skill. For per-post data, include the post/media dimension so each row is a post.
5. If a query returns an async handle, poll with **`get_async_query_results`**.

Sanity-check what comes back before building on it. Reach greater than impressions is impossible.
Followers dropping by 40% in a month is a data error, not a crisis. Engagement rates above ~15%
on a business account of this size usually mean the denominator isn't what you think. Catching
this at the query stage costs a minute; catching it after the deck is in front of management
costs the report's credibility.

---

## Manual fallback

When Supermetrics isn't connected or fails, ask for these exports. Be specific — a vague ask
produces the wrong export and a second round trip.

**Instagram — Meta Business Suite → Insights:**
- Set the date range to the full reporting month
- Export or screenshot: *Overview* (reach, engagement, followers), *Audience* (growth, net
  follows), and *Content* (the per-post table — make sure reach and engagement columns are
  visible before exporting)
- Repeat for the previous month, or screenshot the built-in comparison view

**Google Business Profile → Performance:**
- Set the date range to the month
- Export the performance data: searches breakdown, views, calls, direction requests, website
  clicks
- Note the current review count and average rating from the Reviews tab

CSV exports are much better than screenshots — they carry per-post rows you can rank, where a
screenshot only gives totals. Say so when asking; most people will export if they know why it
matters.

If only screenshots arrive, read the figures off them and proceed, but skip the top/worst post
ranking rather than guessing at per-post numbers, and note in the deck why that section is
lighter this month.
