# Seculana Web Delivery Plan

This repository tells the Seculana story. The product repository `software-dog/Loom` is the authoritative, read-only source for product facts, examples, architecture, status, and roadmap claims.

The build brief is [SECULANA-SITE-INTAKE.md](./SECULANA-SITE-INTAKE.md).

## Working rules

- Work in small increments. Every increment ends in a coherent commit on `main`.
- Before publishing a technical claim, verify it against the current Loom repository.
- Never modify Loom as part of this project.
- Distinguish shipped, active work, accepted design, and exploratory ideas.
- Do not fabricate Seculana screenshots. Missing Seculana media is intentional and should degrade to useful alt text/placeholders until a real capture is supplied.
- Keep the first experience fast, readable, responsive, accessible, and useful without JavaScript.
- Prefer simple static-web machinery unless a concrete requirement justifies more framework.
- Do not let documentation completeness flatten the narrative. The home page is a story; deeper pages carry proof.

## Narrative spine

**Curiosity → recognition → proof → spectacle → credibility → future → invitation**

The first visit should pique interest, build excitement, show what Seculana can actually do, establish technical credibility, show where it is heading, and end with concrete ways to participate.

## Phase 0 — Ground truth and project contract

### Increment 0.1 — Intake
Status: complete

- Add the full site intake/build brief.
- Establish Loom as read-only product truth.

### Increment 0.2 — Delivery roadmap
Status: this commit

- Record phases, increments, gates, and working rules.
- Make checkpoints explicit so future work can be reviewed incrementally.

### Increment 0.3 — Live-repository reconnaissance
Status: complete

Inspect Loom and create `docs/SOURCE-AUDIT.md` containing:

- current product state and phase/checkpoint;
- canonical terminology and public product name;
- verified implemented features relevant to the story;
- representative models worth showcasing;
- current Playground/report capabilities;
- current install/run/contribution/licensing facts;
- roadmap items classified by status;
- useful source paths for future fact checking;
- discrepancies between the intake snapshot and live repository.

**Gate:** no substantive public-facing copy is written until this audit exists.

### Increment 0.4 — Visual collaboration contract
Status: complete

Create `docs/VISUAL-COLLABORATION.md` so authentic Seculana media can be requested and integrated without blocking implementation. Product screenshots remain real captures; explanatory diagrams may be native HTML/CSS/SVG.

## Phase 1 — Story skeleton

### Increment 1.1 — Technical foundation
Status: complete

Create the smallest maintainable static-site foundation.

- local development and production build;
- semantic HTML baseline;
- typography/design tokens;
- responsive layout;
- accessible navigation;
- no mandatory JavaScript for core reading;
- GitHub Actions build validation;
- README with development instructions.

**Gate:** clean build from a fresh checkout.

### Increment 1.1a — GitHub Pages preview
Status: complete

- Build and upload the static site on every push to `main`.
- Deploy through the `github-pages` environment.
- Repository owner enabled **Settings → Pages → Source → GitHub Actions**.
- Successful pushes to `main` now publish the preview automatically.
- Current preview: `https://software-dog.github.io/Seculana-Web/`.

### Increment 1.2 — Home-page narrative skeleton
Status: complete

Build the complete story arc using verified copy but minimal ornament:

1. Hook
2. The modeling problem
3. Financial state
4. Ask questions, not just calculate
5. Showcase teaser
6. Why trust the engine
7. Road ahead
8. Get involved

Use code, CSS diagrams, and intentional media placeholders rather than synthetic Seculana screenshots.

**Gate:** a visitor can understand the central idea from one scroll.

### Increment 1.3 — Visual system and motion
Status: complete

Add the visual language that makes the site memorable:

- code treatment;
- financial-flow motifs;
- restrained animation/progressive reveal;
- light/dark behavior if justified;
- responsive polish;
- reduced-motion support.

**Gate:** visual effects support the story rather than compete with it.

## Phase 2 — Show, don't merely tell

### Increment 2.1 — Language and state showcase

Demonstrate verified examples of:

- balances;
- named flows and priorities;
- transfers;
- draws;
- shortfalls;
- time/dependencies.

Pair syntax with small explanatory visuals.

### Increment 2.2 — Decisions and inverse questions

Demonstrate, as currently supported:

- scenarios;
- solve/best;
- explore;
- optimize;
- sensitivity.

Make the distinction between calculation, policy, search, and explanation visible.

### Increment 2.3 — Uncertainty and reports

Show verified Monte Carlo/uncertainty/report capabilities. Prefer real Seculana output once captures are supplied.

**Capture gate:** generate a prioritized request list for the owner before requiring any screenshots or video.

### Increment 2.4 — Flagship model story

Use one representative model, likely the Canadian retirement model if still the strongest live example, to show how the pieces compose into a serious financial question.

**Gate:** claims and code snippets trace back to live repository sources.

## Phase 3 — Proof and depth

### Increment 3.1 — How it works

Explain the verified pipeline and architectural pattern:

source → parser/AST → binding/dependencies → evaluator → results

Show lowering/orchestration where appropriate without turning the page into compiler documentation.

### Increment 3.2 — Models and empirical design

Tell the hundred-model story using the current checkpoint:

- what kinds of models have been attempted;
- what was learned;
- how findings become library, language, tooling, diagnostics, or bug work.

### Increment 3.3 — Why/AI/verification

Explain engine-backed explanation and the current AI proposal workflow, if still current.

Central message: AI can propose or explain; Seculana calculates and verifies.

## Phase 4 — Roadmap and invitation

### Increment 4.1 — Roadmap

Build a provenance-conscious roadmap with clear visual status:

- available now;
- active/current work;
- accepted/design-approved;
- exploratory ideas.

The goal-directed/planning architecture may be featured as a frontier only if its status is labeled accurately.

### Increment 4.2 — Call to arms

Create concrete engagement paths for:

- people with difficult financial models;
- financial-domain experts;
- language/runtime developers;
- visualization/UX contributors;
- testers and early adopters.

Default thematic CTA: **Bring Seculana a hard financial model.**

Do not invent contribution channels that do not yet exist.

## Phase 5 — Real media and public readiness

### Increment 5.1 — Capture pack

Create/update `docs/CAPTURE-REQUESTS.md` with exact Snagit/Camtasia/Audacity requests:

- purpose;
- source screen/state;
- crop/aspect ratio;
- interaction sequence for video;
- desired duration;
- filename;
- alt text;
- placement.

Replace placeholders only with authentic captures.

### Increment 5.2 — Accessibility, performance, metadata

- keyboard and focus review;
- contrast and reduced-motion review;
- responsive QA;
- image dimensions/lazy loading;
- social metadata/favicon;
- link validation;
- performance pass.

### Increment 5.3 — Deployment

Choose and document the public deployment path. GitHub Pages is a natural first candidate but is not assumed until the build shape is known.

**Gate:** reproducible deployment from repository state.

## Phase 6 — Optional interactive evolution

Only after the narrative site works well:

- embedded live examples;
- WASM/Playground integration;
- generated model/report artifacts;
- richer interactive decision visualizations;
- automated synchronization of selected product facts.

These are enhancements, not prerequisites for a compelling first release.

## Check-in convention

Use focused commits with messages that describe a complete increment. At each checkpoint:

1. verify the changed files;
2. run available build/tests when the project has them;
3. record material source-truth discoveries;
4. leave no knowingly broken navigation/build state;
5. summarize what changed and what the next increment will do.

The roadmap itself may change as live-repository reconnaissance teaches us more. Update it explicitly rather than silently drifting from it.
