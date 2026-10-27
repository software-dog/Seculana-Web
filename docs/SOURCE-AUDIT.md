# Live Source Audit

**Audit date:** 2026-10-27  
**Product repository:** `software-dog/Loom`  
**Audited branch:** `master`  
**Audited head:** `9b3b4973e53c66c077cf9c5ed77ef36fb4971234`  
**Website repository:** `software-dog/Seculana-Web`

This document is the current bridge between the public storytelling site and the live Seculana repository. The product repository wins whenever this audit, the intake brief, or an older knowledge snapshot disagrees with it.

The website may summarize and dramatize verified product behaviour. It must not turn proposals into shipped features.

## 1. Current product state

Seculana is the public product name. The repository remains named `Loom`, and internal C# identifiers still use Loom. Source files use `.sec`, the command is `seculana`, and diagnostics use `SEC...` codes.

At the audited head:

- **Phase 70 is complete** as of 2026-10-27.
- Phase 70 is **The story of a value**, ADR 058.
- **Phase 71, Documentation from comments, is next.**
- Phases 70–77 are a sequence focused on understanding and usability.
- Phase 78 is the currently planned internationalization/"Seculana abroad" phase.
- Phase 69, local-model training material, is complete except for GPU-dependent training/scoring work to be resumed elsewhere.

Canonical status source: `docs/PROJECT_STATE.md`.

## 2. The strongest current one-line description

The live README currently leads with:

> Financial models that read like the plan, not like a spreadsheet.

It describes Seculana as a declarative language / 4GL for money over time: cash flow, accounts, taxes, life events, scenarios and Monte Carlo risk, calculated period by period with exact decimal money.

This is a stronger and more current public framing than the older Project snapshot. It should influence the website headline work, though the site does not need to copy the README.

Canonical source: `README.md`.

## 3. Verified capabilities worth showing

The following are implemented at the audited head and are suitable for public storytelling.

### Declarative financial modeling

- declarations are order-independent;
- dependencies determine evaluation;
- recurrence uses `@Name` plus an explicit first value;
- time can be annual or several shorter period conventions;
- money and rates are distinct types;
- money uses exact decimal arithmetic and is kept to cents;
- optional/missing values are explicit.

### Stateful money

- balances with opening, growth, inflows, outflows, available funds, paid amounts, shortfalls and closing;
- named flows;
- payment priorities;
- transfers between balances;
- multi-source draws;
- source-specific after-tax gross-up;
- ordered and proportional draws;
- scenarios that change draw order;
- optimization over withdrawal order.

This remains one of the clearest ways to distinguish Seculana from "formulas in text."

### Inverse and decision questions

Implemented mechanisms include:

- `solve`;
- `best`;
- scenarios and comparison;
- exploration;
- whole-model optimization with constraints;
- Monte Carlo optimization;
- sensitivity analysis.

The deterministic evaluator remains the authority while searches/orchestration run models repeatedly.

### Uncertainty

Implemented support includes multiple probability distributions, table sampling, correlated draws, Monte Carlo exploration, percentiles/chances, probability constraints and decision/uncertainty visualizations.

### Structure and reuse

Implemented support includes:

- libraries written in Seculana;
- submodels;
- namespaces;
- dimensions;
- functions;
- tables;
- events;
- data import from CSV and Excel.

### Explanation and debugging

This area is stronger than in the intake snapshot.

Seculana now has three useful levels of explanation:

1. **story**: the financial story of a value in a period;
2. **explain**: the model-level explanation;
3. **trace**: detailed calculation proof.

Phase 70 added the story layer across:

- `seculana explain ... --story`;
- the REPL;
- MCP;
- Playground "Why?";
- reports.

Stories can describe balances from their ledger movements, draws from their sources and taxes, transfers, money sums and other constructs, and suggest useful values to inspect next.

There is also a step-through debugger via DAP and editor support.

### Reports

`seculana report` produces deterministic, self-contained web pages. The report system supports, among other things:

- ordinary series charts;
- stacked account charts;
- scenario comparisons;
- exploration heat maps/curves;
- Monte Carlo fan and distribution views;
- balance-flow/Sankey-style diagrams;
- dependency/event/scenario/library diagrams;
- sensitivity views;
- decision views;
- cards, gauges, pies and waterfalls;
- story items.

Reports are particularly valuable to the website because they are authentic visual output rather than marketing illustrations.

### Playground

The Playground is not merely a design idea. The current repository records a substantial implemented system:

- native host via `seculana play`;
- browser host with the Seculana engine compiled to WebAssembly in a Web Worker;
- static-site form;
- installable offline web app;
- links that can carry a model;
- `<seculana-model>` embeds;
- editing and results;
- scenarios and what-ifs;
- "Why?";
- Monte Carlo;
- optimization;
- importing/exporting;
- tutorial/learning flows;
- optional AI proposal workflow.

The browser is intended to draw what the engine returns, not reproduce Seculana semantics itself.

Canonical sources: `docs/PROJECT_STATE.md`, `docs/WEB.md`, `docs/PLAYGROUND.md`, ADRs 039–042, Playground source/tests.

## 4. Phase 70 gives the website a new proof point

`docs/COMPREHENSION.md` measures whether someone handed a model can answer ten practical questions using the command line, without AI and without simply reading the source.

After Phase 70:

- Lise and Omar improved from **5/10 to 9/10** questions answered whole;
- Maren and Dev improved from **3/10 to 6/10**;
- example 004 improved from **4/9 to 8/9**.

For several questions, a chain of commands plus hand arithmetic became one `--story` command.

This is unusually good website material because it is not "we made explanation better." It is an explicit before/after comprehension measurement.

Do not generalize the scores beyond the tested questions/models.

Canonical source: `docs/COMPREHENSION.md`.

## 5. Representative models

### Lise and Omar

`examples/lise-and-omar.sec` remains a prime showcase.

It currently demonstrates a fictional retired BC couple using:

- Canadian tax, pension and RRIF libraries;
- a reusable `Person` submodel;
- mandatory RRIF minimums;
- pensions before discretionary withdrawals;
- taxable and tax-free balances;
- after-tax multi-account draws;
- alternative withdrawal-order scenarios;
- RRSP-meltdown policy;
- optimization over all 120 orders of five sources;
- combined order + meltdown optimization;
- sensitivity;
- Monte Carlo market uncertainty;
- multiple reports including a glance report and uncertainty report.

The model itself says the people and figures are invented and that it is a planning sketch, not advice. Preserve that framing anywhere the website features it.

### Maren and Dev

`examples/maren-and-dev.sec` is useful for more complicated money movement, including pass-through before-tax balances and a corporation. It is also one of the comprehension benchmark models.

### Sam and Alex

`examples/sam-and-alex.sec` is used heavily by the README as a progressive introduction and is useful for approachable onboarding.

### Other useful examples

The repository contains many additional examples, including `noor-and-mateo.sec`, `uk-retirement.sec`, `oil-well.sec`, `market-history.sec`, `showcase.sec` and numbered examples. Selection should be driven by the story rather than trying to catalogue everything on the home page.

## 6. Current roadmap status

The website must render roadmap items by status, not as one undifferentiated future list.

### Complete

- Phase 70: The story of a value.

### Next / planned in the recorded roadmap

- **71:** documentation from comments and generated/reference help;
- **72:** inferred roles, one results view and a more readable `run`;
- **73:** the model grid as a rich inspection surface;
- **74:** starting and fixing, including `seculana new` and language-server quick fixes;
- **75:** a workbook export that retains semantic meaning and optional audit information;
- **76:** stable/tidy results for Python and R;
- **77:** a terminal viewer;
- **78:** internationalization/"Seculana abroad."

These are roadmap entries, not implemented behaviour unless later repository evidence says otherwise.

### Ideas, not roadmap commitments

`docs/DESIGN_IDEAS.md` and discussion ideas can be visually separated as "frontier" or "exploratory."

The recently discussed goal-directed/planner architecture belongs here unless and until the product roadmap/ADRs elevate it. It may be used as a provocative future question, never as a promised feature.

## 7. Product architecture claims safe for public use

The broad pipeline is still:

```text
source
→ parse / AST
→ bind names, types and dependencies
→ deterministic evaluation
→ results / observer events
```

Rich constructs commonly lower to ordinary model machinery before or around the evaluator. Search-like features commonly orchestrate repeated ordinary runs.

The public site should explain this at the level needed to establish trust. Detailed compiler/runtime design belongs on a deeper architecture page.

Canonical sources: `docs/ARCHITECTURE.md`, ADRs, implementation.

## 8. Installation and distribution status

There is packaging machinery for native AOT releases. The packaging documentation says Seculana can ship as one native executable plus its standard library/examples/docs and does not require .NET to be installed at runtime.

However, public-site copy must currently be conservative:

- the authoritative Loom repository is **private** at audit time;
- `packaging/package.config.json` still contains a placeholder repository value, `OWNER/seculana`;
- no public release/download URL has been established by this audit;
- the README/usability notes still contain installation work that is evolving.

Therefore, do not yet put a prominent "Download Seculana" CTA on the public site unless a current public distribution endpoint is verified at implementation time.

## 9. Licence and contribution status: launch gate

At the audited head:

- GitHub reports **no repository licence**;
- there is no root `LICENSE` file in the repository listing;
- `packaging/package.config.json` has empty `license` and `licenseUrl`;
- no `CONTRIBUTING.md` was found by this audit;
- the Loom repository is private.

This matters for the requested call-to-arms.

The site may invite people to **engage, test ideas, bring difficult models, report experiences, or express interest** once a channel is provided. It should not imply that Seculana is open source or invite people to fork/submit code under an unspecified licence.

Before a public "help build Seculana" developer CTA, decide:

1. whether the product repository will become public;
2. the licence;
3. the contribution policy;
4. the public issue/discussion/contact channel.

This is a product decision, not a website implementation detail.

## 10. Testing/build truth

The live README badge/text says **2,400+ passing tests**.

The latest Phase 70 commit message also records that **four end-to-end tests are stale since Phases 67 and 68**.

The website should avoid a stronger blanket claim such as "all tests pass" until a current clean build/test run has been observed. "2,400+ passing tests" can be used only if rechecked near publication.

The GitHub connector used for this audit can inspect repository state but does not substitute for running the full local build/test suite.

## 11. Discrepancies from the intake snapshot

The intake was informed by a knowledge snapshot around Phase 61b. The live repository has advanced materially.

Major changes to account for:

- current phase is 70, not 61b;
- the usability/comprehension program is now a major current product direction;
- "story of a value" is implemented;
- explanation is significantly richer;
- the Playground/browser story is more mature and explicitly includes a WASM static-site/offline form;
- the roadmap now has concrete Phases 71–78;
- the website can tell a stronger "understand the model" story than the original intake anticipated.

The intake remains useful for narrative goals and visual/product direction. This audit supersedes it for feature status.

## 12. Source map for website fact checking

Use these live paths first:

| Topic | Canonical / useful sources |
|---|---|
| Current status | `docs/PROJECT_STATE.md` |
| Roadmap | `docs/ROADMAP.md` |
| Product introduction | `README.md` |
| Language semantics | `docs/LANGUAGE.md` |
| Architecture | `docs/ARCHITECTURE.md` |
| Comprehension measurement | `docs/COMPREHENSION.md` |
| Usability findings | `docs/USABILITY.md` |
| Playground | `docs/PLAYGROUND.md` |
| Browser/WASM | `docs/WEB.md` |
| Design ideas | `docs/DESIGN_IDEAS.md` |
| Architectural decisions | `docs/decisions/` |
| Canadian retirement showcase | `examples/lise-and-omar.sec` |
| Broader complex household | `examples/noor-and-mateo.sec` |
| Corporate/pass-through example | `examples/maren-and-dev.sec` |
| Approachable introduction | `examples/sam-and-alex.sec` |
| Standard finance rules | `lib/` |
| Packaging/release machinery | `packaging/` |
| Editor support | `tools/vscode-loom/`, `tools/nvim-loom/`, `tools/zed-loom/` |

## 13. Implications for the site narrative

The live repository suggests a slight refinement of the intake's story arc:

**Pique interest**  
"Financial models that read like the plan, not like a spreadsheet."

**Recognition**  
Money is not just arithmetic. It has time, accounts, taxes, constraints, priorities, uncertainty and choices.

**Proof**  
Show a small model, then show the engine calculating real state and explaining why.

**Show off**  
Use Lise/Omar plus authentic Playground/report captures to demonstrate draws, scenarios, optimization, sensitivity and uncertainty.

**Credibility**  
Show deterministic verification, trace/debugging, libraries as readable Seculana, and the measured comprehension work.

**Road ahead**  
Phases 71–78 as the committed/recorded roadmap; exploratory planning/goal-directed ideas in a visibly different frontier band.

**Invitation**  
The most distinctive invitation remains: **Bring Seculana a hard financial model.**  
The exact public mechanism for doing that still needs to be chosen.

## 14. Audit rule going forward

Before each major website increment:

1. check the Loom head;
2. re-read `docs/PROJECT_STATE.md` and relevant current source;
3. update this audit when status materially changes;
4. never silently promote a roadmap item or design idea to "available now."

Seculana is moving quickly. The website should feel alive without becoming inaccurate.
