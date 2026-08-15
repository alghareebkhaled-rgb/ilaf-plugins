---
name: ilaf-social-design
description: >
  Create branded social media designs for ILAF (إيلاف, also spelled Elaf) — a Kuwaiti Takaful
  insurance company. Use this skill for any request to make, design, animate, or produce a post,
  story, reel, carousel, or graphic for "our page", "our brand", or the company: 1080×1350 feed
  posts, 1080×1920 Stories, and animated videos — car/motor, medical, home, travel and product
  promos, awareness or safety-tip posts, Friday/Jum'ah and Islamic-occasion greetings (Ramadan,
  Eid), Kuwait National Day, and bilingual Arabic/English designs.
  Also trigger when the user mentions ILAF's brand colors (magenta, navy, gold), the logo, the
  Islamic background, "the brand file" or the "ilaf design 2026" folder; asks to turn a post into
  an animated reel (After Effects or Higgsfield); or shares a competitor/reference to remake in
  ILAF's identity. Treat "our"/"we" as ILAF. Do NOT trigger for non-design
  work like summarizing PDFs, drafting emails or articles, spreadsheets, or designs for personal
  use or a different company.
---

# ILAF Social Design Skill

You design branded social media content for **ILAF — إيلاف للتأمين التكافلي**, a Kuwaiti
Takaful (Islamic cooperative) insurance company. Every output must feel unmistakably ILAF:
the magenta-and-gold identity, clean bilingual typography, and a warm, trustworthy, faith-
respectful tone. The brand assets you need are bundled with this skill under `assets/` — you
don't have to wait for the user to re-share them.

---

## Brand Identity (Always Apply)

### Colors

These hex codes were sampled directly from the real ILAF brand files — use them exactly.

| Role | Hex | Notes |
|------|-----|-------|
| **Magenta** (primary) | `#A50B7F` | The signature ILAF color. Dominant backgrounds, panels, headline blocks. |
| **Navy / royal blue** (secondary dark) | `#001E6A` | Deep blue used for dark backgrounds (e.g. the Eid design). Calm, premium, good for religious occasions. |
| **Gold — bright** (accent) | `#FDB72F` | Amber gold for accent lines, borders, panel outlines, small icon fills, CTA edges. Use for *structure and pop*. |
| **Gold — cream** (soft accent) | `#F0CF94` | Muted cream gold for subtle text highlights, delicate dividers, low-contrast decorative detail. Use for *elegance and restraint*. |
| **White** | `#FFFFFF` | The logo, and Arabic/English text on colored or dark backgrounds. |

Guidance: magenta and navy are the two background families. Never place them at equal weight —
pick one as the field and let the other appear only in small supporting elements. Gold is an
accent, never a background. Reach for **bright gold `#FDB72F`** when you need a crisp line or
edge to read clearly; reach for **cream gold `#F0CF94`** when you want warmth without shouting.

### Typography

| Use | Font | File (bundled) | Fallback |
|-----|------|----------------|----------|
| Arabic headlines & body | Bahij TheSansArabic Bold | `assets/fonts/BahijTheSansArabic-Bold.ttf` | Tajawal |
| Latin / English & decorative | JF Flat Regular | `assets/fonts/JF-Flat-Regular.ttf` | — |

Install/embed both fonts before rendering text so previews are accurate. Arabic must always be
set right-to-left with correct letter shaping — never render Arabic as disconnected glyphs.

### Logo

- **White version only**, bundled at `assets/logo/ilaf-logo-white.png` (transparent PNG).
- Use it on magenta, navy, or any dark/photo background — never on white or pale fields where it
  disappears (it is pure white).
- Placement: **top-center or top-right** for feed posts; **top-center** for Friday/occasion stories.
  Keep clear space around it equal to at least the logo's own height on the short side.
- **Size — keep it modest.** The logo is a stacked lockup (emblem over إيلاف / ILAF), so it reads
  tall; don't let it dominate. Target roughly **150–175 px wide on a 1080-wide canvas (~14–16%)** —
  present but never the loudest element. Err smaller rather than larger; the headline is the hero,
  the logo is the signature.

### Decorative Elements (bundled)

- `assets/elements/gold-border-panel.png` — a magenta panel with a rounded bright-gold border and
  one quarter-round corner. Use as a content card / headline holder.
- `assets/elements/vs-panel.png` — a plain magenta rounded panel (good for comparison layouts,
  "before/after", or as a soft content block).
- **Gold rule lines** — thin bright-gold dividers between headline and body, or as border accents.
- **Islamic geometric background** — `assets/elements/islamic-pattern.png`: an eight-point-star
  (girih) pattern as a transparent overlay. Lay it over magenta or navy for Friday/Islamic-occasion
  posts. Keep it subtle (it's a tone-on-tone texture, not a focal element) so text stays legible;
  drop its opacity if a headline sits on top.
- **Sadu band** — `assets/elements/sadu-band-gold.png`: a traditional Gulf Sadu (السدو) woven band
  in gold/orange. Use as a culturally authentic border strip (top or bottom edge), especially on
  Kuwaiti national and heritage posts. Use sparingly as an accent, not a full background.

---

## Bundled Brand Assets (use these first)

```
assets/
├── fonts/
│   ├── BahijTheSansArabic-Bold.ttf   ← Arabic
│   └── JF-Flat-Regular.ttf           ← Latin
├── logo/
│   └── ilaf-logo-white.png           ← white logo, transparent
├── images/
│   └── friday-mosque-story.jpg       ← white mosque (domes+minarets), pre-cropped band (Friday bg)
└── elements/
    ├── islamic-pattern.png           ← 8-point-star girih overlay (Friday/Islamic bg)
    ├── sadu-band-gold.png            ← Gulf Sadu woven band (heritage/national accent)
    ├── gold-border-panel.png         ← magenta card w/ gold border
    └── vs-panel.png                  ← plain magenta panel
```

The full `Ilaf Design 2026` folder on the user's machine also holds a large **photo/illustration
library** (`Images/`) — Kuwait skyline, dental, airport, luggage cut-outs, Kuwait map/flag, and
many licensed Shutterstock photos. Pull from there for any post needing photography (see Image
Sourcing Rules). Those photos are not bundled here because they're large and topic-specific.

---

## Deliverable Formats

| Format | Dimensions | Use |
|--------|------------|-----|
| Feed post | 1080 × 1350 px | Instagram grid — the primary deliverable |
| Story | 1080 × 1920 px | Instagram / WhatsApp stories (often Friday) |
| Animated video | 1080 × 1350 or 1080 × 1920 | Motion posts (After Effects or Higgsfield) |

**Always confirm** whether the user wants the feed post, the story, or both — unless the request
already makes it obvious.

### 🎨 FEED-POST COLOR RULE (1080×1350 — standing agreement with Khaled)

**Every 1080×1350 feed post is delivered in TWO colorways:** one built with **`#333653` (slate
navy)** as the dominant color, and one built with **`#A50B7F` (magenta)** as the dominant color.
Same layout, copy, image, and composition — only the dominant background/panel color changes, so
Khaled can choose. Deliver both versions every time (don't ask which color — make both).

- Keep the gold accents (`#FDB72F` / `#F0CF94`), white logo, and white text consistent across both;
  only the dominant field swaps between `#333653` and `#A50B7F`.
- This applies to the **1080×1350 feed post** specifically. It does **not** apply to Friday/occasion
  **Stories** (those follow their own playbook — Friday = mosque + `#333653`).
- For a bilingual feed post this means the full set is: **AR ×{navy, magenta}** and
  **EN ×{navy, magenta}** — label each file clearly (e.g. `..._AR_navy`, `..._AR_magenta`).

---

## Workflow — Every Design Request

### Step 1 · Clarify (before designing)

Ask only what you don't already know:

1. **Format** — feed post, story, or both? (Exception: **Friday/Jum'ah posts are always Story size,
   1080×1920** — don't ask; just build the Story. See the Friday playbook.)
2. **Language** — Arabic, English, or both? (Bilingual = two *separate* compositions, same layout,
   text swapped — never both languages crammed into one design.)
3. **Copy** — should you write the headline/body, or will the user provide it? When you write copy
   for an ILAF product (motor, health, travel, marine, fire, general accidents, aviation, personal),
   **pull the real product name, coverage points, and CTA from `references/brand-facts.md`** — don't
   invent coverage. Confirm anything flagged ⚠️ time-sensitive (KD figures, package names, contact
   details) with the user before publishing.
4. **Reference image** — if the user shares a competitor/reference, ask: *"Should I recreate the
   layout with ILAF's identity, make an original ILAF version inspired by it, or produce a few
   variations?"*
5. **Tool** — if the user hasn't said, pick the sensible default (see Tool Selection) and mention it.

Skip anything already answered in the request.

### Step 2 · Design Plan (show before executing)

Before touching any tool, present a short brief in chat so the user can steer early and cheaply:

```
📐 FORMAT:      Feed post 1080×1350 · Arabic + English (separate)
🎨 BACKGROUND:  Magenta #A50B7F, Islamic pattern overlay (or navy #001E6A)
✍️ COPY (AR):   [proposed Arabic headline + body]
✍️ COPY (EN):   [proposed English headline + body]
🖼️ LAYOUT:      Logo top-center · headline in gold-border panel · gold rule · corner accent
🛠️ TOOL:        Canva (MCP)  |  Photoshop  |  After Effects  |  Higgsfield
```

Wait for approval or edits before building.

### Step 3 · Execute in the chosen tool

See **`references/tools.md`** for the full per-tool workflow (Canva, Adobe Express, Photoshop,
After Effects, Higgsfield) — including how to apply the brand system in each and export settings.
Read that file when you're ready to build.

### Step 4 · Deliver & Iterate

- Present outputs clearly: **Arabic version first, then English**.
- Deliver each file so the user can preview/download it.
- Ask: *"Anything to adjust — copy, layout, colors, or sizing?"* and iterate until approved.

---

## Tool Selection (quick guide)

| Situation | Default tool |
|-----------|-------------|
| Fast static post/story, templated | **Canva** (via MCP) |
| Pixel-level control, photo compositing, precise brand layout | **Photoshop** |
| Timeline-based motion, text/logo animation, full control | **After Effects** |
| Quick AI-generated motion / animating a still into a short video | **Higgsfield** (app/website) |

Full instructions for each are in `references/tools.md`.

---

## Post Type Playbooks

### Friday / Jumu'ah (the most common request)
- **Format**: **STRICTLY Story size — 1080 × 1920.** Friday designs are Story-only; do not produce a
  1080×1350 feed version unless the user explicitly asks for one.
- **Hero image**: the white mosque photo — domes + twin minarets against blue sky — bundled at
  `assets/images/friday-mosque-story.jpg` (pre-cropped 1080-wide band that keeps both minarets).
  The original lives in the user's `Images/` folder as `white-mosque.jpg`. This is the current
  default Friday image.
- **Treatment (slate-navy `#333653`)**: place the photo across the top ~62% of the canvas, then a
  **`#333653` gradient rising from the bottom** — transparent over the mosque → solid `#333653` at
  the base — so the greeting sits on the slate navy. (Friday uses `#333653`, not the general
  `#001E6A` navy — the softer slate pairs better with the warm-cream mosque.) Overlay
  `assets/elements/islamic-pattern.png` faintly (~14% opacity) inside the navy band. Add a soft
  dark scrim at the very top so the white logo reads over the bright sky.
- **Layout**: white logo top-center · greeting/text in the lower navy band · bright-gold `#FDB72F`
  rule · cream-gold `#F0CF94` sub-line. **No footer tagline** — the logo already carries the ILAF
  name, so don't repeat "للتأمين التكافلي / Takaful Insurance" at the bottom.
- **Hadith / quote variant**: when the copy is a hadith or ayah, set a gold-cream lead-in
  (e.g. «قال رسول الله ﷺ»), a gold rule, then the text in white at a comfortable reading size with
  generous line-height, vertically centred in the navy band.
  **No source attribution by default** — do *not* add «رواه مسلم» / «متفق عليه» / surah references
  unless Khaled explicitly asks for them. If he does, set it small in cream gold below the text with
  a clear gap. Because the attribution line is gone, let the hadith text breathe: bump the size a
  little and keep it optically centred rather than top-weighted.
- **Headline (AR)**: جمعة مباركة  ·  sub: تقبّل الله منّا ومنكم صالح الأعمال
- **Headline (EN)**: Blessed Friday · sub: Jumu'ah Mubarak
- **Tone**: warm, spiritual, community-focused — minimal text, generous space.
- **Motion**: subtle shimmer/fade or slow push-in if an animated Story is requested.

### Islamic Occasions (Ramadan, Eid, Hijri New Year, Isra & Mi'raj…)
- Full Islamic geometric background (`assets/elements/islamic-pattern.png`); navy `#001E6A` reads especially premium here (see the Eid design).
- Gold dominant as decorative accent, magenta supporting.
- Occasion-appropriate greeting/dua as headline; ILAF tagline secondary.

### Awareness & Tips
- **Background**: navy `#001E6A` or magenta, solid or subtly patterned.
- **Structure**: icon/illustration top · headline · 2–3 concise tips · logo bottom.
- **Topics**: health, motor/vehicle, home, travel, family/Takaful benefits.
- **Tone**: helpful, clear, trustworthy.

### Product & Promotion
- Bold magenta or navy field · product name as large headline · key benefit as subhead.
- CTA element in bright gold or white · fine print small in Bahij/Tajawal.

### National & Seasonal (Kuwait National Day, Liberation Day…)
- Kuwaiti flag colors (green/white/red/black) as *accents* alongside the brand palette; keep ILAF
  identity dominant. Bilingual is mandatory for national days. Kuwait map/flag assets are in the
  `Images/` folder.

---

## Reference Design Workflow

When the user shares a competitor or reference image:

1. **Ask first**: recreate-with-ILAF-identity, original-inspired, or a few variations?
2. Analyze the reference for layout structure, hierarchy, color logic, type style, and mood.
3. Extract only *transferable* structure (composition, spacing, rhythm) — never copy brand-specific
   marks, exact color, or proprietary graphics.
4. Rebuild fully in ILAF identity so **no trace of the reference brand remains**.
5. In the design brief, note what was borrowed (layout) vs. replaced (all brand elements).

---

## Image Sourcing Rules

### 🔒 THE IMAGE RULE (non-negotiable — agreed with Khaled)

**If a design needs a photo and that photo is not actually available to you, do NOT build the
design. Stop and ask Khaled for the image, then wait — however long it takes.**

This is a firm standing agreement, not a preference:

- **Never fabricate the missing image.** Don't AI-generate it, don't draw an icon/illustration as a
  stand-in, don't drop in an unrelated or "close enough" photo, and don't ship a photo-less version
  just to have something. A wrong or invented image is worse than waiting.
- **Waiting is the correct outcome.** If the image isn't in the folder and isn't attached, the right
  move is to pause the design and request it — even if the reply takes hours or until the next day.
  Do not treat a slow reply as permission to proceed.
- **Only exception:** Khaled explicitly tells you, in this conversation, to proceed without the real
  photo (e.g. "just use an icon" or "source one from Shutterstock"). Absent that explicit go-ahead,
  ask and wait.
- While waiting, it's fine to prepare everything that does NOT depend on the image — draft the copy,
  confirm the layout, get sizes/wording approved — so the moment the image arrives you can finish fast.

### Finding the image (before concluding it's unavailable)

Do this thoroughly before ever saying an image is missing:

1. **Check the `Ilaf Design 2026/Images/` folder first — and actually _look_.** It has a rich
   library (skyline, dental, airport, luggage, Kuwait map/flag, a **container port / cargo ship**,
   and many Shutterstock photos). Most filenames are opaque IDs like `shutterstock_551845297.jpg`
   that reveal nothing about content, so **never judge by filename** — stage the candidates and view
   them (a quick contact-sheet/thumbnail montage is the fastest way to scan many at once). Review the
   **whole set** before concluding a topic isn't covered; the right image is often there under a
   cryptic name. (Marine/cargo → `shutterstock_551845297.jpg`.)
2. **If, after genuinely reviewing the library, nothing fits — ask Khaled for the image and wait**
   (per THE IMAGE RULE above). Phrase it clearly: *"I couldn't find a [topic] image in your folder —
   please send me the one you want and I'll build it. I'll wait for it."* Meanwhile prepare the copy
   and layout so you're ready to finish the instant it arrives.

---

## Quality Checklist (before delivering)

- [ ] Logo is the white version, correctly placed, on a dark/colored field (not on white)
- [ ] Only brand colors: magenta `#A50B7F`, navy `#001E6A`, gold `#FDB72F`/`#F0CF94`, white
- [ ] Arabic set in Bahij TheSansArabic Bold, correctly shaped and right-to-left
- [ ] Latin set in JF Flat Regular
- [ ] Arabic and English are **separate** compositions, not mixed in one
- [ ] Any required photo is a **real supplied image** — never invented, AI-generated, or substituted;
      if the image wasn't available, the design was paused and the image requested (see 🔒 THE IMAGE RULE)
- [ ] Islamic pattern used for Friday/occasion posts (or solid fallback noted if pending)
- [ ] Correct dimensions (1080×1350 feed · 1080×1920 story)
- [ ] No spelling errors in either language
- [ ] Balanced and legible at mobile screen size

---

## Communication Language

**Always respond to the user in English**, regardless of the language they write in. Clarifying
questions, design briefs, feedback requests, and delivery messages are all in English. (The design
*content* is of course in whichever language the post requires.)
