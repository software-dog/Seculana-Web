# Visual Collaboration

This document defines how authentic Seculana visuals are requested, captured, integrated and replaced.

The rule is simple:

> **If the visual claims to show Seculana, it must come from Seculana.**

The website may use generated diagrams, CSS/SVG illustrations and typographic graphics to explain ideas, but it must not fabricate product screenshots or simulated Seculana output and present them as real.

## 1. Three kinds of visuals

### A. Native website visuals

Built directly in Seculana-Web with HTML/CSS/SVG/Canvas as appropriate.

Examples:

- dependency arrows;
- account/flow diagrams;
- the source → AST → binder → evaluator pipeline;
- a conceptual comparison between spreadsheet cells and a financial model;
- roadmap/status graphics;
- code-to-concept animations;
- decorative motifs.

These are explanatory graphics, not screenshots. They can be created and revised entirely in this repository.

### B. Authentic Seculana captures

Captured from the actual product by the owner using Snagit or Camtasia.

Examples:

- the Playground;
- Why?/story views;
- Monte Carlo and decision views;
- reports;
- debugger/editor integration;
- a real CLI or REPL interaction.

Until a requested capture arrives, the website uses an intentional placeholder with meaningful alt/fallback text. Do not generate a fake screenshot to fill the hole.

### C. Optional editorial artwork

Non-product illustration may be generated or commissioned where it adds emotional texture without implying product behaviour.

Use sparingly. Seculana's own code, charts and flows should be the star.

## 2. Placeholder convention

Authentic media is referenced from:

```text
public/media/captures/
```

The website should be coded against the final intended filename even when the file does not exist yet.

Example:

```html
<img
  src="/media/captures/playground-why-lise-rrsp.webp"
  alt="Seculana Playground showing the financial story of Lise's RRSP in 2034."
>
```

When the asset is absent, the component should render a styled capture placeholder containing:

- the alt text;
- the capture ID;
- a small "authentic capture pending" treatment in development builds.

Missing authentic media must not break layout or navigation.

## 3. Capture request format

Every request gets an ID and should specify:

| Field | Meaning |
|---|---|
| ID | Stable identifier, e.g. `CAP-001` |
| Purpose | What the visitor should understand or feel |
| Product surface | Playground, report, VS Code, CLI, etc. |
| Model/state | Exact model/scenario/year/view |
| Action | What to click/type before capture |
| Frame | What must be visible |
| Crop | Aspect ratio / orientation |
| Theme | Light/dark if important |
| Output | PNG/WebP still or MP4/WebM source |
| Filename | Final repository name |
| Alt text | Meaning if the media is unavailable |
| Notes | Cursor, sensitive data, timing, etc. |

The request should be reproducible by someone who did not design the page.

## 4. Snagit still-image guidance

Unless a request says otherwise:

- capture at native resolution, not an enlarged browser screenshot;
- include only enough browser/editor chrome to orient the viewer;
- avoid desktop clutter, notifications, account names and unrelated tabs;
- leave breathing room around important UI;
- do not add callouts/arrows in Snagit unless the request specifically asks for them;
- prefer the product's own theme rather than recolouring afterward;
- save a lossless PNG master;
- the web build may derive WebP/AVIF later.

For a wide website feature, 16:9 or roughly 3:2 is usually easiest to place.

For a focused UI detail, a tighter crop is better than shrinking an entire desktop into unreadable confetti.

## 5. Camtasia motion guidance

Use motion only when the interaction itself is part of the argument.

Good candidates:

- dragging a time scrubber and seeing every view move;
- selecting a value and opening Why?/story;
- changing an assumption and watching results update;
- moving through Monte Carlo futures;
- optimizer/proposal progress;
- a short before/after scenario comparison.

Default target:

- 8–20 seconds;
- no narration required;
- deliberate cursor movement;
- no long pauses;
- one idea per clip;
- record a clean master at 1080p or higher;
- keep the original project/source when practical so timing/crops can be revised.

The website can loop a silent clip, but should not autoplay audio.

## 6. Audacity/audio guidance

Audio is optional, not a dependency for understanding the site.

If used, the strongest role is probably a short founder/creator voice element rather than narrated product tutorials.

Any spoken content must also exist as readable text/transcript.

Record clean, dry speech without music baked in. Music and mix decisions, if any, belong to the site/video edit so they can change independently.

## 7. Our collaboration loop

For each important visual:

1. **Website work reaches the point where the visual has a job.**
2. I add/update its request in this document with an exact capture recipe.
3. The site continues with a placeholder, so implementation is never blocked by media.
4. You capture the requested asset with Snagit/Camtasia/Audacity.
5. You add it to the repository, or upload it here and I add it.
6. I integrate it, tune crop/responsive behaviour/caption, and verify the surrounding narrative.
7. If the image reveals that the surrounding design is wrong, the website changes. The capture is evidence, not sacred furniture.

This keeps your time focused on authentic product moments rather than speculative screenshot production.

## 8. Visual direction before captures

The initial website should establish its visual language using things we can control without captures:

- strong typography;
- generous whitespace;
- code as a primary visual material;
- precise financial-flow diagrams;
- small amounts of motion;
- charts/lines used as structural motifs;
- status chips for implemented / roadmap / frontier;
- dark surfaces only when they make code or data glow, not as default "developer cool."

The product captures then arrive as proof inside an already coherent visual system.

## 9. Initial capture backlog

Do **not** make all of these immediately. They are candidates. Requests become "Ready" only after the page placement is built.

| ID | Status | Candidate |
|---|---|---|
| CAP-001 | planned | Playground overview with a serious model open |
| CAP-002 | planned | Why?/story of a value, showing Phase 70's new explanatory layer |
| CAP-003 | planned | Lise/Omar Glance report |
| CAP-004 | planned | Lise/Omar uncertainty/Chance report |
| CAP-005 | planned | optimizer or decision view that communicates "Seculana can choose" |
| CAP-006 | planned | Monte Carlo run/time interaction as a short Camtasia clip |
| CAP-007 | planned | VS Code language/debugging experience |
| CAP-008 | planned | a compact CLI story/explain interaction if it reads well visually |

We will promote these one by one and fill in exact instructions only when the site's composition makes their required framing clear.

## 10. The first likely hero proof

A product screenshot should probably **not** be the first thing on the page.

The opening can create curiosity with typography, live code and a purpose-built financial-flow visual. The first authentic screenshot can then arrive as a proof beat:

> "This isn't a mockup. This is the model explaining itself."

If the live Playground supports that moment cleanly, CAP-002 is likely to become the first high-priority capture.

## 11. Accessibility

Every meaningful image gets useful alt text.

For complex charts/screenshots:

- alt text states the main takeaway rather than transcribing the entire UI;
- nearby prose explains the claim the image supports;
- a text/data alternative is provided where the detail matters.

Video must not be the only way to learn something. Motion respects reduced-motion preferences.

## 12. Authenticity check before publication

Before a Seculana capture is published:

- the model is public/invented, never private household data;
- the figures shown are safe to publish;
- the feature is implemented at the current Loom head;
- captions do not claim more than the screen proves;
- the capture is not stale enough to misrepresent the current UI;
- alt text describes the actual final asset.

The website is allowed to be theatrical. The evidence must remain real.
