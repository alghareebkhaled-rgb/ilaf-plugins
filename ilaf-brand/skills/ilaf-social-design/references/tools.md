# ILAF Design — Tool Workflows

Detailed build instructions for each production tool. Read the section for the tool chosen in the
design brief. In every case, the brand system from `SKILL.md` is non-negotiable: magenta `#A50B7F`,
navy `#001E6A`, gold `#FDB72F` (bright) / `#F0CF94` (cream), white; Bahij TheSansArabic Bold for
Arabic, JF Flat Regular for Latin; white logo from `assets/logo/ilaf-logo-white.png`.

## Contents
1. Canva (via MCP) — fast templated statics
2. Adobe Express (via MCP) — alternative templated statics
3. Photoshop — pixel-precise statics & photo compositing
4. After Effects — timeline motion
5. Higgsfield — AI-generated motion from a still

---

## 1 · Canva (via MCP)

Best for: quick, clean posts and stories when a template gets you 80% there.

1. Search for a template matching the format (1080×1350 or 1080×1920) and theme, or start blank.
2. Set the canvas to the exact deliverable size.
3. Apply the brand system: magenta/navy background, upload the white logo, set brand fonts, add
   gold accents. Upload `assets/elements/*` panels if the layout uses a content card.
4. For bilingual output, build the Arabic version, then **duplicate the design and swap the text**
   to English (and vice-versa) so layout stays identical.
5. Confirm Arabic shapes correctly (RTL, connected letters). If Bahij isn't available in the Canva
   brand kit, upload the bundled TTF first.
6. Export **PNG at full resolution** (one file per language).

---

## 2 · Adobe Express (via MCP)

Alternative to Canva with the same logic.

1. Use `search_design` to find a matching template, or build from scratch at the target size.
2. Apply the full brand identity (colors, fonts, white logo, gold accents, bundled panels).
3. For bilingual: duplicate the design, swap the text to the other language.
4. Export PNG.

---

## 3 · Photoshop

Best for: pixel-level control, photo compositing (using the `Images/` library), and precise,
repeatable brand layouts. Photoshop work here is script-driven so it's consistent every time.

### Approach
Produce a **layered PSD spec + an actionable build**, not a vague description. Two paths:

**A) You have image-editing / scripting access (preferred):**
- Set up an RGB document at the exact size (1080×1350 or 1080×1920), 72–150 ppi, sRGB.
- Layer order (bottom → top):
  1. Background fill — magenta `#A50B7F` or navy `#001E6A` (or Islamic pattern when supplied).
  2. Optional photo from `Images/`, color-graded and masked; add a magenta/navy overlay at
     ~15–35% if text sits over it, for legibility.
  3. Decorative panels from `assets/elements/` and/or gold rule lines (`#FDB72F`).
  4. White logo (`assets/logo/ilaf-logo-white.png`), placed per format (top for feed, bottom for story).
  5. Text layers — Arabic in Bahij TheSansArabic Bold (RTL, right-aligned), Latin in JF Flat Regular.
- Install the bundled fonts before rendering so text is accurate.
- Export **PNG** (and keep the layered PSD if the user wants to edit). Provide one file per language.

**B) You're handing the user a Photoshop recipe:**
Give a precise, reproducible spec: document size, exact hex fills per layer, font + size + tracking
for each text block, logo placement coordinates/margins, which bundled asset goes on which layer,
and export settings. The user should be able to rebuild it without guessing.

### Bilingual in Photoshop
Duplicate the text group, swap contents to the other language, keep every other layer identical.
Save two exports: `..._AR.png` and `..._EN.png`.

### Arabic text note
Photoshop needs Middle Eastern text features enabled (World-Ready composer) for Arabic to shape and
run right-to-left correctly. Always verify the Arabic connects properly before exporting.

---

## 4 · After Effects

Best for: full timeline control — text entrances, logo reveals, background transitions.

Produce a **detailed, executable After Effects project spec**:

- **Composition**: exact size (1080×1350 or 1080×1920), 25 fps, duration (typically 5–10 s for a loop
  or 10–20 s for a message), sRGB.
- **Layer structure** mirroring the static layout (background → photo/pattern → panels/gold accents →
  logo → text), each as its own layer for independent animation.
- **Keyframes**: describe entrance/exit for each element — e.g. background fade or gradient sweep,
  headline slide+fade up (Arabic from the right, honoring RTL feel), logo scale/opacity reveal, gold
  line wipe. Give timing (in/out frames) and easing (ease-in-out for elegance).
- **Brand**: exact hex codes and bundled fonts/logo referenced by name.
- **Export**: H.264 MP4, 1080×1350 or 1080×1920, 25 fps, high bitrate.

Offer to produce the **static key-frame first** (as a Photoshop/Canva still) for approval before
animating, so the user signs off on look before motion.

---

## 5 · Higgsfield (app / website)

Best for: quickly turning a finished ILAF still into a short animated video using AI motion — camera
moves, subtle parallax, ambient motion — when you don't need frame-precise control.

Higgsfield is an external app/website, so your job is to prepare the input and hand the user a
clear, ready-to-run recipe:

1. **Create the still first** (Canva or Photoshop) — a finished, on-brand 1080×1350 or 1080×1920
   ILAF design. Higgsfield animates *this*, so it must already be correct: right colors, logo, fonts,
   Arabic shaped properly.
2. **Deliver the still** to the user to upload into Higgsfield.
3. **Provide a Higgsfield prompt + settings**:
   - **Motion prompt** — describe the desired movement in Higgsfield's terms, e.g. *"slow cinematic
     push-in on the center, gentle gold-particle sparkle drifting upward, soft light shimmer across
     the background, logo stays crisp and static, elegant and calm."* Keep motion subtle — this is a
     premium insurance brand, not a hype reel.
   - **Aspect ratio**: 4:5 for feed (1080×1350) or 9:16 for story (1080×1920).
   - **Duration**: typically 3–6 seconds; loopable if possible.
   - **Guidance**: keep the logo and Arabic text stable (avoid warping); motion should sit in the
     background/accents, never distort legible text.
4. **Warn about text/logo integrity**: AI motion can distort type. If Higgsfield warps the logo or
   Arabic, advise animating only the background in Higgsfield and compositing the crisp logo/text
   back on top (in Canva/Photoshop/After Effects), or switch to After Effects for that piece.
5. **On return**, review the exported video against the brand checklist before final delivery.

Because Higgsfield runs outside this environment, always tell the user exactly what to upload, the
prompt to paste, and the settings to pick — so they can execute it in one pass.
