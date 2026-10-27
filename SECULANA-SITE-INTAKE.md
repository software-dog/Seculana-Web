# Seculana Story Site - Codex Intake and Build Brief

> **Purpose of this file**
>
> This is a handoff from a ChatGPT Project that contains curated Seculana context into a Codex session working in the **live Loom/Seculana repository**. Treat this document as a product/story/design brief, not as a substitute for repository truth.
>
> **Critical instruction:** before implementing anything, inspect the current repository. Verify product capabilities, names, syntax, examples, screenshots, roadmap state, links, and architecture against the current code and docs. Where this intake conflicts with the live repository, the live repository wins.

---

## 1. Mission

Build a portable, high-impact web experience that introduces **Seculana**, a declarative financial-modeling language and environment.

The emotional sequence should be deliberate:

1. **Pique interest** - make the visitor wonder, “Why doesn’t financial modeling already work this way?”
2. **Build excitement** - reveal that Seculana models financial intent directly rather than disguising a spreadsheet as code.
3. **Show off** - demonstrate the language, stateful balances, flows, draws, scenarios, optimization, uncertainty, visual reports, explanation, and the Playground.
4. **Earn credibility** - show the architectural discipline, deterministic engine, testability, real-model methodology, and current limitations.
5. **Show the road ahead** - distinguish shipped capability from active work and speculative/future ideas.
6. **Issue a call-to-arms** - give developers, financial modelers, domain experts, testers, and curious early adopters concrete ways to engage.

This should feel like a **living technical/product story**, not a marketing brochure and not a traditional documentation dump.

The site should make a technically sophisticated visitor want to keep scrolling, then make them want to open the repository or Playground.

---

## 2. Core positioning

Seculana should be presented primarily as:

> **A language for describing financial systems in financial terms.**

Not:

- “Excel, but with syntax.”
- a generic programming language with finance examples;
- an AI financial adviser;
- a tax-compliance engine;
- a black-box optimizer;
- a collection of charts attached to formulas.

The important conceptual contrast is:

```text
Spreadsheet thinking:
cell A depends on B7 which depends on another cell hidden three tabs away

Seculana thinking:
this account grows, receives these inflows, pays these obligations,
and this remaining need is funded from these sources under this policy
```

The visitor should understand early that **declaration order is not calculation order**. Seculana discovers dependencies, evaluates on demand, and keeps financial state explicit.

---

## 3. Product principles that the site must communicate

Verify wording against the live repository, but preserve these ideas if they remain true:

### 3.1 Financial intent over formula plumbing

Models should read as descriptions of financial systems, not spreadsheet formulas translated into code.

### 3.2 State is explicit

Accounts and debts are modeled as balances/state machines with opening value, growth, inflows, outflows, paid amounts, shortfalls, and closing value.

### 3.3 Policy is separate from mechanics

The financial system can remain deterministic while scenarios, exploration, optimization, sensitivity, and Monte Carlo ask different questions of that system.

### 3.4 Inverse questions belong in the language

Seculana already supports forms of “I know the target; find the input/choice/driver” through mechanisms such as `solve`, `best`, `explore`, `optimize`, and `sensitivity`.

### 3.5 Explainability is engine-backed

Trace, dependency information, debugger/Why?-style explanations, and reports should derive from the same model evaluation rather than from a parallel storytelling layer.

### 3.6 AI is subordinate to deterministic calculation

If still current: AI may propose, edit a scratch copy, or explain; **Seculana calculates and verifies**. The user remains in control of application.

### 3.7 Rich features should reuse ordinary semantics when possible

A recurring architectural pattern is that balances, flows, draws, dimensions, submodels, explore, optimize, and sensitivity reuse or orchestrate the ordinary evaluator instead of creating unrelated engines.

### 3.8 Real models drive language evolution

The hundred-model exercise is important. It demonstrates that language/library/tooling decisions are being driven by actual modeling friction rather than speculative feature accumulation.

---

## 4. Source-of-truth rules for Codex

Before writing site copy, inspect at minimum the current versions of whatever repository files now correspond to:

- `CLAUDE.md`
- `docs/PROJECT_STATE.md`
- `docs/ARCHITECTURE.md`
- `docs/LANGUAGE.md`
- `docs/WEAKNESSES.md`
- `docs/DESIGN_IDEAS.md`
- `docs/HUNDRED.md`
- `docs/decisions/` / ADRs
- representative examples, especially retirement and broad household models
- current Playground source
- current report renderer/source
- current CLI and language-server/editor integration
- `lib/canada/`
- `lib/finance/`

Also search the repository for the current status of:

- Playground hosting modes;
- WebAssembly/browser support;
- report formats;
- chart types;
- optimization and Monte Carlo optimization;
- sensitivity;
- AI proposal workflow;
- current hundred-model checkpoint;
- current roadmap/phase numbering;
- current public links and repository URLs;
- installation/run instructions;
- licensing and contribution guidance.

Do not copy old phase numbers or “next” tasks from this intake without verification.

---

## 5. Desired format

### 5.1 Primary artifact

Prefer a **static web site** that can be:

- served locally;
- deployed to GitHub Pages, Cloudflare Pages, Netlify, Azure static hosting, or equivalent;
- zipped and shared;
- kept in version control;
- updated by Codex/Claude Code alongside Seculana;
- progressively enhanced with JavaScript without requiring JavaScript for basic reading.

Do not choose a framework merely because it is fashionable. Inspect the repository first and reuse an existing web stack if doing so materially reduces duplication or makes reuse of report/Playground components practical.

If there is no strong reuse benefit, prefer the simplest maintainable implementation.

### 5.2 Suggested information architecture

The default design should have a **high-energy scrolling home/story page** plus deeper pages for visitors who want proof.

Suggested structure:

```text
/
  The story: curiosity → excitement → proof → invitation

/why-seculana/
  The conceptual case: financial systems, not cells/formulas

/showcase/
  Curated demos: balances, draws, retirement, uncertainty, optimization,
  sensitivity, reports, explanation, AI proposal workflow

/how-it-works/
  Parser → AST → binder → dependency analysis → evaluator → results
  Rich syntax lowering/orchestration patterns

/models/
  Representative real modeling problems and the hundred-model method

/roadmap/
  Now / active work / accepted design / ideas, with provenance

/get-involved/
  Concrete participation paths
```

If a single-page implementation produces a stronger first version, that is acceptable, provided anchors and routing make future decomposition easy.

---

## 6. Narrative architecture for the home page

The home page is not documentation ordered by feature taxonomy. It is a story.

### Act 1 - The hook: “Financial models deserve a language of their own”

**Goal:** earn the next 20 seconds.

Possible headline territory, not mandatory copy:

- “What if a financial model described the finances, not the spreadsheet?”
- “Money has state. Financial decisions have constraints. Model them that way.”
- “A financial model should read like finance.”

Subhead should introduce Seculana in one sentence, with no jargon wall.

Immediately show one compact, visually appealing Seculana fragment. Favor a balance or retirement need example over a toy `hello world`.

Example shape to verify against current syntax:

```sec
balance Savings opening $650,000 growth Return
    inflow Contributions = Saved
    outflow Living = Need
```

Then reveal the idea:

- `Savings` is state, not a hand-maintained recurrence.
- `Living` is a named flow.
- insufficient money becomes an inspectable shortfall.
- dependencies determine calculation order.

**Do not** open with compiler architecture.

---

### Act 2 - Recognition: “This is the problem you already have”

**Goal:** connect with anyone who has built a serious spreadsheet or financial program.

Show a compact comparison between:

- hidden cell dependencies;
- repeated “remaining need” plumbing;
- accidental circular references;
- duplicated tax/account logic;
- scenario sheets copied into oblivion;

and the Seculana concepts that make those relationships explicit.

Avoid attacking Excel. Excel is extraordinarily useful. The message is that some financial systems have outgrown cell-address semantics.

A good line of argument:

> Spreadsheets are great at tables. Financial plans are systems that evolve through time.

---

### Act 3 - The reveal: “Seculana understands financial state”

**Goal:** first major “this is different” moment.

Feature a visual explanation of a balance:

```text
Opening
  + Growth
  + Inflows
  - Outflows actually paid
  = Closing → next period Opening

requested outflow > available funds
  → Paid + Shortfall
```

Then show named flows, priorities, and transfers.

The visualization should make accounting semantics legible, not merely decorative.

**Preferred visual:** actual Seculana balance/flow UI or report capture if the live product has one. Otherwise use a lightweight HTML/CSS diagram derived from verified semantics.

---

### Act 4 - Escalation: “Now ask a real financial question”

**Goal:** move from language syntax to decision modeling.

Introduce a required spending need funded from multiple accounts.

Use a verified version of a draw similar to:

```sec
draw Living = Need from
    Cash,
    Rrsp after tax(g) = TaxOn(BaseIncome + g) - TaxOn(BaseIncome),
    Tfsa
```

Explain, visually:

1. there is a **need**;
2. sources have availability and policy/order;
3. taxable withdrawals may require solving for gross withdrawal needed to deliver a desired net amount;
4. the model exposes what was actually paid, shortfall, and tax effects;
5. a scenario can change policy without rewriting the financial system;
6. optimization can search policy choices where supported.

This should be one of the strongest demonstrations on the site.

---

### Act 5 - Showpiece: retirement income sourcing

**Goal:** demonstrate that Seculana can model interactions that are annoying in ordinary spreadsheet plumbing.

Prefer the current repository’s strongest retirement model. Historically a Lise/Omar example has been useful because it separates:

- CPP/OAS/workplace or other deterministic income;
- RRIF minimum withdrawals as mandatory flows;
- cash/non-registered/tax-deferred/tax-free stateful accounts;
- base tax;
- remaining spending need;
- discretionary multi-source draws;
- incremental tax;
- withdrawal policy/order;
- optimization;
- sensitivity;
- Monte Carlo uncertainty.

Important story:

```text
mandatory rules happen
        ↓
base income and tax are known
        ↓
household need is known
        ↓
discretionary policy funds the remaining need
        ↓
tax interactions are calculated
        ↓
we can compare or optimize policy
```

Make the distinction between **mandatory** and **discretionary** visually obvious.

Do not imply that an optimizer can “choose away” statutory/contractual requirements.

---

### Act 6 - Spectacle with substance: uncertainty and decisions

**Goal:** this is the “show off” section.

Use actual product captures wherever possible for the strongest currently implemented visualizations.

Candidates, subject to current repo verification:

- Monte Carlo fan/spaghetti views;
- histogram / distribution view;
- chance-of-success or ruin view;
- sensitivity tornado chart;
- sensitivity spider chart;
- correlation/variance contribution;
- Pareto frontier;
- feasibility chart;
- contour/breakeven visualization;
- optimization constraint margins;
- parallel coordinates;
- scenario radar;
- discounted/payback visualizations.

Do not create a wall of thumbnails. Pick 3–5 visuals with a clear “question → picture → interpretation” sequence.

Possible framing:

```text
“What could happen?”       → uncertainty
“What choice is best?”     → optimization
“What constrains it?”      → feasibility / margins
“What matters most?”       → sensitivity
“Why did I get this?”      → trace / Why?
```

---

### Act 7 - Trust: “The engine, not the AI, owns the arithmetic”

**Goal:** make the AI story credible rather than fashionable.

If still current, describe the workflow approximately as:

```text
user request
  → AI edits a scratch model
  → Seculana checks/runs it
  → host computes actual diff + numerical before/after
  → user accepts, partially accepts, or rejects
```

The core message:

> AI can propose. Seculana calculates and verifies.

If local-model support, consent rules, or external-agent behavior have changed, update from current sources.

A screenshot/video of the proposal diff is preferable to generic AI imagery.

**Never use stock “glowing AI brain” graphics.**

---

### Act 8 - Credibility: “The language is being tested against real modeling work”

**Goal:** show engineering/product discipline.

Feature the hundred-model exercise prominently.

Explain that representative models are written as a modeler would actually write them, friction is classified, recurring pain is tallied, and changes are routed toward the appropriate layer:

- finance library;
- language/semantics;
- diagnostics/tooling;
- bug fix.

If still current, show categories such as:

- `Missing`
- `Long`
- `Message`
- `Bug`
- `Good`

Show the **current** checkpoint from the repository, not the historical checkpoint in this brief.

This is a differentiator. Treat it as evidence, not process trivia.

---

### Act 9 - Under the hood

**Goal:** reward technical visitors without slowing down everyone else.

Show the verified architecture:

```text
source
  → lexer/parser
  → parse tree
  → AST
  → binder
      names
      types
      units
      rewrites
      dependency analysis
  → bound model
  → evaluator
  → values + diagnostics + observer/report events
```

Then explain the recurring pattern:

```text
rich financial syntax
        ↓
desugar/lower to ordinary model machinery
        ↓
normal deterministic evaluation
```

and/or:

```text
search / explore / optimize / sensitivity
        ↓
controlled repeated ordinary model runs
```

This section should help a compiler/runtime-minded developer understand why Seculana is not a pile of special cases.

---

### Act 10 - Roadmap: “What exists, what is next, what is merely an idea”

**Goal:** create anticipation without blurring status.

The roadmap must use explicit status labels. Recommended taxonomy:

1. **Implemented** - currently works in the repository.
2. **Active / next** - current scheduled or in-progress work, if repository evidence supports this.
3. **Accepted design** - design-approved but not yet implemented.
4. **Idea / exploration** - recorded possibility or discussion, not a commitment.

Do not turn `DESIGN_IDEAS.md` into promises.

A future goal-directed/planning architecture may be compelling if it exists in current design discussion, especially around distinctions such as:

- exogenous facts/assumptions;
- mandatory actions;
- discretionary decisions;
- goals/objectives;
- planner proposes policy;
- deterministic evaluator verifies.

However, present this only at its actual repository status.

The roadmap should visibly include limitations/open problems where useful. Credibility rises when the site admits the hard edges.

Potential current-limit categories to verify:

- period-dependent draw order;
- start-of-period withdrawal semantics;
- same-period source/sink cycles;
- two-way transfer/rebalancing cycles;
- limits of `solve`/`best` search behavior;
- local-vs-global optimization guarantees;
- Monte Carlo/search cost;
- dimension expansion cost.

Do not list stale limitations that have been fixed.

---

### Act 11 - Call to arms

**Goal:** turn admiration into action.

Avoid the generic “Join our community!” ending unless there is an actual community destination.

Instead create role-specific invitations, each with one concrete next step verified from the repository/public project surfaces.

Possible tracks:

#### Developers

- run the project;
- inspect an issue tagged appropriately;
- improve diagnostics/tooling;
- help with language server/editor integration;
- improve WebAssembly/Playground/reporting;
- add tests.

#### Financial modelers / planners

- try to model a real problem;
- contribute a model to the hundred-model exercise or its successor;
- report where the language becomes awkward;
- challenge assumptions and abstractions.

#### Finance/tax/domain experts

- review planning libraries;
- identify missing rules and approximation risks;
- help separate planning abstractions from compliance requirements;
- contribute jurisdiction/year-specific rule updates where the project’s contribution model permits.

#### Visualization / UX people

- improve how uncertainty, trade-offs, dependencies, and flows are explained;
- make complex models understandable in one minute.

#### Curious early adopters

- run one example;
- open the Playground;
- compare a scenario;
- ask “Why?”;
- report the first confusing thing.

Every CTA must point somewhere real. If contribution docs/issues/discussions do not exist, say so in the implementation notes rather than inventing destinations.

---

## 7. Representative examples to look for in the repository

Use current repository examples rather than reproducing these blindly.

The site will be stronger if it can show a range like:

- retirement feasibility;
- retirement income sourcing;
- Monte Carlo retirement;
- buy vs. rent;
- mortgage vs. investing;
- debt avalanche/snowball;
- DCF valuation;
- lump-sum vs. DCA;
- rental property;
- portfolio rebalancing;
- a broad young-family model with dimensions/submodels;
- Canadian retirement/tax/pension planning.

A gallery should answer “what kinds of things can I model?” rather than merely showing filenames.

For each showcased model, prefer:

```text
Question
  → 5–15 lines of meaningful Seculana
  → one result/visual
  → one insight about the modeling abstraction
```

---

## 8. Media and asset policy

### 8.1 Cost constraint

**Do not generate expensive decorative imagery for Seculana product views.**

If the site needs a screenshot, recording, diagram, or audio clip that must come from the real Seculana product, create a placeholder reference and provide a capture instruction. The human owner will create the asset with **Snagit, Camtasia, or Audacity**.

For product screenshots, prefer a deliberately missing asset with useful `alt` text over generating fake UI.

Example:

```html
<img
  src="/assets/captures/playground-overview.png"
  alt="CAPTURE NEEDED: Seculana Playground showing a retirement model in the editor with a result chart and the Why panel visible. Capture at 1600×900 or larger, no other desktop windows visible."
/>
```

Use a stable filename so the owner can later drop the file into place without changing markup.

If broken-image rendering is visually ugly in the chosen implementation, add CSS/markup that presents the alt/capture request as an intentional placeholder card while preserving meaningful `alt` text for the eventual image.

### 8.2 Do not fabricate product UI

HTML/CSS conceptual diagrams are fine when they explain verified semantics.

Do **not** generate or hand-design a fake screenshot of the Playground, VS Code extension, report UI, optimizer, or charts and present it as if it were the actual product.

---

## 9. Capture request registry

Codex should inspect the current UI and revise these requests before finalizing them. Remove requests for features that do not exist and add requests where a current feature tells the story better.

Use the IDs and filenames below as a starting convention.

### CAP-01 - Playground hero

**File:** `assets/captures/playground-overview.png`  
**Tool:** Snagit  
**Target:** 1600×900 minimum, preferably 2× density if practical.  
**Capture:** A strong real model open in the Playground with enough editor text to look substantive and one compelling result/chart visible. If a Why/explanation panel can coexist without clutter, include it.  
**Purpose:** Hero proof that Seculana is a real working environment.  
**Avoid:** empty editor, toy model, browser chrome dominating the image, private data.

Suggested alt:

> Seculana Playground with a real financial model, calculated results, and an explanatory visualization.

### CAP-02 - Balance / money-flow explanation

**File:** `assets/captures/balance-flow.png`  
**Tool:** Snagit  
**Capture:** The best current product view that makes opening balance, inflows/outflows, closing balance, paid amount, and shortfall understandable.  
**Purpose:** Demonstrate explicit financial state.

If no current UI expresses this well, do not fake one. Use an HTML/CSS semantic diagram instead.

### CAP-03 - Why? / dependency explanation

**File:** `assets/captures/why-dependency.png`  
**Tool:** Snagit  
**Capture:** A nontrivial value selected with the current Why?/trace/dependency explanation visible. Pick a value whose explanation is understandable to someone seeing Seculana for the first time.  
**Purpose:** Prove engine-backed explainability.

### CAP-04 - Scenario comparison

**File:** `assets/captures/scenario-comparison.png`  
**Tool:** Snagit  
**Capture:** Two or more meaningful scenarios in a chart/table where the effect of changing policy or assumptions is obvious.  
**Purpose:** Show that alternative worlds are first-class rather than cloned spreadsheet tabs.

### CAP-05 - Withdrawal/draw policy optimization

**File:** `assets/captures/draw-optimization.png`  
**Tool:** Snagit  
**Capture:** Current UI/report showing withdrawal-source order/policy optimization or the strongest analogous optimization result. Include objective/constraint information if readable.  
**Purpose:** Show “financial policy as a decision variable.”

### CAP-06 - Monte Carlo uncertainty

**File:** `assets/captures/monte-carlo.png`  
**Tool:** Snagit  
**Capture:** The strongest uncertainty visualization currently implemented, ideally fan/spaghetti/chance-of-success plus a concise summary metric.  
**Purpose:** Visual spectacle backed by real model semantics.

### CAP-07 - Sensitivity

**File:** `assets/captures/sensitivity.png`  
**Tool:** Snagit  
**Capture:** Tornado chart or best sensitivity view with labels readable.  
**Purpose:** Answer “what actually matters?”

### CAP-08 - Decision visualization

**File:** `assets/captures/decision-view.png`  
**Tool:** Snagit  
**Capture:** Choose the current decision visualization that is both visually striking and quickly understandable: Pareto frontier, feasibility, contour/breakeven, constraint margins, parallel coordinates, or similar.  
**Purpose:** Show that Seculana communicates trade-offs, not only point answers.

### CAP-09 - AI proposal / diff workflow

**File:** `assets/captures/ai-proposal.png`  
**Tool:** Snagit  
**Capture:** AI proposal on a scratch model with actual diff and before/after numerical effect, if this UI currently exists. Ensure no secrets/API keys/provider details are visible.  
**Purpose:** Support “AI proposes; Seculana verifies.”

### CAP-10 - Editor / language tooling

**File:** `assets/captures/editor-tooling.png`  
**Tool:** Snagit  
**Capture:** Current VS Code/editor integration showing syntax highlighting plus a genuinely useful diagnostic, hover, completion, go-to-definition, or other implemented language feature.  
**Purpose:** Appeal to developers and show tooling maturity.

### CAP-11 - Self-contained report

**File:** `assets/captures/report.png`  
**Tool:** Snagit  
**Capture:** A polished generated report with at least one chart and one meaningful result section.  
**Purpose:** Demonstrate portable output, not only an IDE experience.

### CAP-12 - CLI / reproducibility

**File:** `assets/captures/cli-run.png`  
**Tool:** Snagit  
**Capture:** A concise terminal run of a representative model, with command and successful output visible. Keep terminal clean.  
**Purpose:** Reinforce that the engine is scriptable/testable and not trapped in a GUI.

---

## 10. Optional motion/video captures

Video should be short, purposeful, and muted by default. No autoplay audio.

### VID-01 - “Change → recalculate → understand”

**File:** `assets/video/playground-loop.mp4`  
**Tool:** Camtasia  
**Length:** 20–45 seconds  
**Capture sequence:**

1. Open a meaningful existing model.
2. Change one understandable assumption or slider/input.
3. Recalculate if calculation is not automatic.
4. Show the chart/result change.
5. Open Why?/explanation for one result if the interaction remains legible.

**Purpose:** Compress the Playground loop into one visual proof.

**Editing:** no narration required; add minimal cursor emphasis only if helpful. Do not use splashy transitions.

### VID-02 - “Compare policy”

**File:** `assets/video/policy-comparison.mp4`  
**Tool:** Camtasia  
**Length:** 20–45 seconds  
**Capture sequence:** switch a scenario or withdrawal/order policy, then show the result comparison or optimization outcome.  
**Purpose:** Demonstrate policy separation from financial mechanics.

### VID-03 - “AI proposal, engine verification” (only if currently implemented and stable)

**File:** `assets/video/ai-proposal.mp4`  
**Tool:** Camtasia  
**Length:** ≤60 seconds  
**Capture sequence:** natural-language request → proposal/diff → check/run → before/after → user acceptance controls.  
**Purpose:** Make the trust model concrete.

---

## 11. Optional audio

Audio is **not required for v1**. Do not add generic background music.

If the owner wants a personal/founder voice later, a short clip could work at the beginning or roadmap section.

### AUD-01 - Founder intent (optional)

**File:** `assets/audio/why-seculana.mp3`  
**Tool:** Audacity  
**Length:** 20–40 seconds  
**Prompt for recording:**

> In your own words, explain the moment that made you think financial modeling deserved something better than cell references or ordinary general-purpose code. Focus on the problem, not on a feature list.

Provide a transcript on the page. Never autoplay.

---

## 12. Visual direction

The site should look like a serious technical product with financial intelligence, not a bank, brokerage, cryptocurrency project, or generic SaaS template.

### Desired qualities

- calm confidence;
- crisp typography;
- generous whitespace;
- readable code;
- visual hierarchy strong enough for skimming;
- data visualizations doing real explanatory work;
- subtle motion where it clarifies dependency/flow;
- restrained accent color;
- dark/light behavior consistent with current product branding if branding exists.

### Avoid

- stock photos of retirees shaking hands;
- coins stacked beside seedlings;
- glowing AI heads;
- crypto gradients;
- fake dashboards;
- giant metric cards with invented numbers;
- buzzword fog;
- unexplained compiler jargon in the first screen;
- excessive scroll-jacking.

If the repository already has a recognizable design language in the Playground/reports, reuse or harmonize with it rather than inventing a parallel brand.

---

## 13. Code presentation

Code is part of the visual identity.

Requirements:

- use real, verified Seculana syntax;
- prefer examples from repository models;
- keep hero snippets short enough to read without scrolling;
- allow longer examples to expand/collapse;
- syntax highlighting should distinguish keywords, money, rates, names, and comments if current tooling supports it;
- never show malformed “marketing pseudocode” as if it is valid Seculana;
- where possible, link a snippet to its source example in the repository.

A useful repeated pattern is:

```text
plain-English question
        ↓
small Seculana fragment
        ↓
actual result / chart
        ↓
one-sentence interpretation
```

---

## 14. Interactivity

Use interaction to clarify ideas, not to create a toy casino.

Good candidates:

- toggle between spreadsheet-ish plumbing and Seculana intent;
- animate a dependency path on hover;
- animate money flow through a balance diagram;
- switch between scenarios using precomputed/verified outputs;
- reveal the stages of parsing/binding/evaluation;
- scrub a before/after assumption if values can be sourced reliably;
- expand model snippets;
- step through mandatory → discretionary retirement flow.

For v1, do **not** reimplement financial semantics in JavaScript merely to create an interactive demo. If live calculation can call the actual Seculana engine safely through an existing browser/WASM interface, reuse that. Otherwise use precomputed verified results or link to the Playground.

The website must not become a second financial engine.

---

## 15. Roadmap presentation rules

Roadmap content can create excitement but is a major truthfulness risk.

Every roadmap item shown publicly must include or derive from a verifiable source in the live repo.

Recommended visual treatment:

```text
NOW
Implemented and demonstrable

NEXT
Current active work / explicitly planned work

DESIGNED
Accepted direction not yet implemented

EXPLORING
Ideas worth investigating, not commitments
```

For future goal-seeking/planner concepts, if still only exploratory, say so clearly.

A compelling framing, if repository evidence supports it:

> Today Seculana can model the system, explore alternatives, solve inverse questions, and optimize choices. A longer-term question is how far a planner can go in proposing strategies while the deterministic evaluator remains the authority that verifies every candidate.

Do not claim a “new goal-seeking engine” exists unless it actually does.

---

## 16. Call-to-arms design

The final section should feel like an open workshop door rather than a newsletter signup wall.

Suggested structure:

```text
Seculana needs people who enjoy hard models.

Build the language.          [developer CTA]
Break the abstractions.      [modeler CTA]
Challenge the finance rules. [domain expert CTA]
Make the results legible.    [visualization/UX CTA]
Try one real problem.        [early adopter CTA]
```

These are tonal suggestions, not mandatory wording.

Codex must discover and use actual current destinations, potentially including:

- repository;
- contribution guide;
- issues;
- discussions;
- examples;
- Playground;
- install/run instructions.

If some destinations do not exist, surface that as a project gap rather than fabricating links.

---

## 17. Technical constraints

Unless current repository architecture strongly suggests otherwise:

- static-first;
- responsive from mobile through large desktop;
- semantic HTML;
- accessible keyboard navigation;
- descriptive alt text;
- visible focus states;
- honors reduced-motion preference;
- no autoplay audio;
- lazy-load heavy media below the fold;
- avoid large JavaScript bundles for purely decorative interaction;
- code blocks must remain readable on phones;
- screenshots must not contain private client/user data;
- external links should be clearly distinguishable;
- page should remain useful when product screenshots are missing.

### Missing-media behavior

Product capture placeholders are expected in the first build.

The site must still look intentional when files such as:

```text
assets/captures/playground-overview.png
assets/captures/monte-carlo.png
assets/video/playground-loop.mp4
```

have not yet been supplied.

Provide a consistent placeholder treatment based on the media element’s alt/capture request. Do not require binary placeholder images.

---

## 18. Accuracy and legal/scope guardrails

Seculana’s Canadian finance libraries have historically been planning-oriented and not a substitute for tax/legal advice. Verify current wording and preserve appropriate caveats.

For year/jurisdiction-specific tax material:

- show the modeled year/jurisdiction when relevant;
- do not silently imply current compliance accuracy;
- distinguish planning approximations from compliance calculations;
- do not invent tax thresholds or legislation for marketing copy.

Likewise, do not state optimization guarantees stronger than the implementation supports.

If an optimizer is local/derivative-free rather than a proof of global optimality, the site should not imply “mathematically guaranteed best” unless the specific search actually provides that guarantee.

---

## 19. Build process for Codex

### Phase A - Repository reconnaissance

Before implementation, produce a short internal/site-build note containing:

1. current product status;
2. current hundred-model checkpoint;
3. strongest 3–5 demos in the repo;
4. strongest current charts/visualizations;
5. current Playground/report architecture worth reusing;
6. current install/run commands;
7. current public contribution destinations;
8. current roadmap source(s);
9. stale assumptions found in this intake.

Do not block implementation waiting for the owner unless a decision is truly irreversible.

### Phase B - Story skeleton

Create the page structure with real text, real code excerpts, conceptual diagrams, and media placeholders.

The page should already tell a coherent story even before screenshots arrive.

### Phase C - Product captures

Generate/maintain a `CAPTURE-REQUESTS.md` file from the actual implemented placeholders. Each entry should include:

- asset path;
- capture ID;
- exact screen/state to capture;
- recommended dimensions/aspect ratio;
- Snagit/Camtasia/Audacity instructions;
- privacy/sanitization notes;
- final alt text;
- where the asset appears on the site.

This becomes the human owner’s recording checklist.

### Phase D - Integration

When real captures are added, no copy or markup rewrites should be necessary. Dropping files at the documented paths should replace placeholders.

### Phase E - QA

Test:

- missing-media state;
- final-media state;
- mobile;
- desktop;
- keyboard navigation;
- reduced motion;
- page performance;
- broken links;
- accuracy of every Seculana snippet;
- roadmap status labels;
- claims against repository truth.

---

## 20. Definition of done for v1

A v1 is successful if a technically literate visitor can answer these questions after 5–10 minutes:

1. What is Seculana?
2. Why is it different from just using a spreadsheet or a general-purpose language?
3. How does it model financial state?
4. What can balances, flows, transfers, draws, scenarios, optimization, sensitivity, and uncertainty do?
5. Why should I trust its calculations more than an AI-generated answer?
6. What real problems has it been tested against?
7. What does the Playground/reporting experience look like?
8. What is implemented now?
9. What is on the roadmap versus merely being explored?
10. How can I participate?

The first screen should create curiosity. The first third should create excitement. The middle should contain undeniable proof. The ending should make participation feel concrete.

---

## 21. Content quality bar

Before shipping each section, ask:

- Is this claim verified against the current repo?
- Is this explaining a financial idea or merely naming a feature?
- Can a screenshot/code/result prove it?
- Is the visual doing explanatory work?
- Have we confused an idea with an implementation?
- Is this understandable to someone who did not build Seculana?
- Is there a more interesting real model we could use?
- Does this preserve the principle that Seculana, not the web front end or AI, owns the semantics?

---

## 22. Product facts from the handoff context that must be re-verified

These were true in the source snapshot used to prepare this intake, but the live repository may have moved on:

- Seculana is a declarative financial-modeling language implemented in C#/.NET with ANTLR.
- Declaration order is independent from calculation order; dependency analysis drives evaluation.
- Evaluation is on-demand and memoized.
- Time is a privileged axis; dimensions are separate from time.
- Balances are first-class state/account abstractions.
- Named flows expose paid/shortfall behavior and priorities.
- Transfers preserve the actual paid amount from source to destination.
- Draws allocate a need across sources and can include after-tax gross-up.
- `solve`, `best`, scenarios, explore, optimize, sensitivity, and Monte Carlo support inverse/decision/uncertainty questions in different ways.
- Some rich language features lower to ordinary declarations before binding.
- Some analysis/search features wrap repeated ordinary model runs.
- Reports are self-contained web output with financial/decision visualizations.
- The Playground uses the real Seculana engine rather than reproducing financial semantics in the front end.
- AI works on a proposal/scratch path and Seculana verifies the result.
- Financial-domain rules live in Seculana libraries where practical.
- A hundred-model empirical exercise is used to drive language/library/tooling evolution.

Codex: **verify all of these before turning them into public copy.**

---

## 23. Questions / gaps for the owner

These should **not block a first implementation**. Use the defaults below unless the owner answers differently.

### Q1 - Who is the primary first audience?

Possible answers:

- compiler/language developers;
- financial planners/modelers;
- fintech developers;
- open-source contributors;
- potential users/early adopters;
- a mixed technical audience.

**Default:** mixed technical audience, with the home page accessible to a sophisticated non-compiler person and deeper architecture for developers.

### Q2 - Is Seculana intended to be presented publicly as open source today?

**Default:** Codex must inspect the repository license/public status and word CTAs accordingly. Do not assume.

### Q3 - What is the primary desired CTA?

Examples:

- star/watch the repo;
- run the Playground;
- install tooling;
- contribute a model;
- open an issue;
- join discussions;
- contact the owner.

**Default:** “Try a real model” as primary, “contribute/challenge it” as secondary, using only destinations that actually exist.

### Q4 - How much founder/personal story should appear?

**Default:** very little in v1. Let the problem, product, and models carry the site. Add a short founder note later if desired.

### Q5 - Should the historical name “Loom” appear publicly?

**Default:** no, except where needed to explain repository/project naming or historical namespaces. Public-facing product name is Seculana.

### Q6 - Are the named household examples safe to publish as examples?

**Default:** use only examples already committed/public in the repository and avoid implying that names correspond to real clients.

### Q7 - Is the roadmap meant to attract collaborators or potential users?

**Default:** both, but favor a credible technical roadmap over sales-style promises.

---

## 24. Recommended first Codex command/prompt after placing this file in the repo

Use something close to:

```text
Read SECULANA-SITE-INTAKE.md completely.

Then inspect the live repository before writing code. Reconcile the intake against
current PROJECT_STATE, architecture/language docs, ADRs, HUNDRED.md, representative
examples, Playground, report renderer, finance libraries, contribution docs, and
current roadmap/status.

Create a concise SITE-RECONNAISSANCE.md recording what is current, what in the intake
is stale, the strongest demos to feature, and the implementation approach you choose.
Then build the v1 Seculana story site described in the intake.

Do not generate fake Seculana screenshots. For any real-product image/video/audio,
use a missing asset path plus descriptive alt/placeholder text, and maintain
CAPTURE-REQUESTS.md with exact Snagit/Camtasia/Audacity instructions.

Keep roadmap statuses explicit. Do not turn design ideas into shipped claims.
Use the real Seculana engine or precomputed verified outputs; do not reimplement
financial semantics in the web front end.

Run the site locally, test it, and leave the repository in a working state.
```

---

## 25. Final design intent

This site should leave the visitor with a progression roughly like this:

> “Interesting. A language specifically for financial models.”
>
> “That balance syntax is much cleaner than the plumbing I usually write.”
>
> “Wait, it understands withdrawal sources and tax gross-up?”
>
> “It can compare policy, run uncertainty, optimize, and explain results?”
>
> “The reports and Playground are real, and the AI does not own the arithmetic.”
>
> “They are testing the language by actually building lots of models.”
>
> “There are hard unsolved problems here.”
>
> **“I want to try this / break this / contribute to this.”**

That last transition is the site’s job.