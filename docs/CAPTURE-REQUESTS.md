# Capture Requests

These are the first authentic Seculana media requests that now have a real job in the website composition.

Do not capture private household data. Use only the public/invented examples named below.

## General setup

Unless a request overrides it:

- Use the current Loom/Seculana `master` build.
- Prefer a 1440 × 900 or 1600 × 1000 browser content area at 100% zoom.
- Hide bookmarks, unrelated tabs, notifications, account names and desktop clutter.
- Keep the Seculana UI itself unretouched. Do not add arrows, labels or fake highlights in Snagit.
- Save a PNG master.
- Do not optimize/compress aggressively. The website can derive web formats later.
- If your current UI differs from the instructions because Seculana has moved on, capture the current truthful UI and note what changed.

---

## CAP-002 — The model tells its story

**Status:** Ready  
**Priority:** First  
**Tool:** Snagit  
**Target filename:** `public/media/captures/playground-story-lise-rrsp.png`  
**Placement:** Home page, "The model can tell you what happened" proof section  
**Desired shape:** roughly 3:2 landscape  
**Alt text:** Seculana Playground showing the financial story of Lise's RRSP in 2034 above the Why explanation.

### Purpose

This is the first authentic product proof on the site.

The visitor should see, almost instantly, that the product is not merely producing a number. The engine can tell the financial story behind an account in a particular year and then expose deeper evidence.

### Prepare

From the Loom repository, open the public example in the current Playground:

```text
seculana play examples/lise-and-omar.sec
```

In the Playground:

1. choose year **2034**;
2. select **Lise.Rrsp**;
3. open **Why?** from the selected value's control or palette;
4. leave the new **story** visible at the top of Why?, with enough of the explanation/tree below it to establish that deeper evidence exists.

The current product manual says Why? shows Seculana's explanation for the selected value in the chosen period, and Phase 70 puts the story above the Why? tree.

### Frame

Try to include:

- enough of the Seculana editor or selected-value context that this is clearly a live model;
- the selected value `Lise.Rrsp`;
- year 2034;
- the financial story sentences;
- the top of the deeper Why?/dependency/calculation material underneath.

Do not try to show the entire Playground. Readability beats completeness.

### Capture notes

- Capture the product at normal scale.
- A dark or light product theme is fine; use whichever is currently the strongest default.
- If a divider can be dragged, give the story enough width that sentences are comfortably readable.
- Keep the cursor off important text.
- Do not include AI-generated explanation. The point is engine-backed story/Why?, not the assistant.

---

## CAP-003 — Lise and Omar at a glance

**Status:** Ready  
**Priority:** Second  
**Tool:** Snagit  
**Target filename:** `public/media/captures/lise-omar-glance-report.png`  
**Placement:** Home page, flagship-model showcase  
**Desired shape:** roughly 3:2 landscape  
**Alt text:** Lise and Omar Glance report with key result cards, account views, and financial flows.

### Purpose

Show that Seculana can turn a substantial financial model into a polished, communicative artifact rather than leaving the user with a terminal table.

### Prepare

Generate the model's real `Glance` report:

```text
seculana report examples/lise-and-omar.sec Glance -o lise-omar-glance.html
```

Open the generated HTML in a browser.

### Frame

The report definition currently contains:

- a title with `EstateToday`;
- explanatory text;
- cards for `Savings`, `TaxPaid`, and `YearsShort`;
- a savings gauge;
- a pension-income pie;
- a TFSA waterfall;
- a financial-flow diagram;
- a scenario comparison matrix.

For the first site capture, prefer a composition that shows the **title plus the first strong visual row**. If the cards and gauge fit comfortably together, include those. If the report naturally presents another stronger first viewport at the current head, use that instead.

The goal is not to show every chart. It is to make the viewer want to inspect the report.

### Capture notes

- Use the report's own light/dark theme, whichever makes the charts and numbers easiest to read.
- Keep the report title visible.
- Avoid a crop where chart legends or values are cut in half.
- Do not annotate in Snagit.

---

## CAP-004 — When the markets move

**Status:** Ready  
**Priority:** Third  
**Tool:** Snagit  
**Target filename:** `public/media/captures/lise-omar-chance-report.png`  
**Placement:** Home page, flagship-model showcase beside CAP-003  
**Desired shape:** roughly 3:2 landscape  
**Alt text:** Lise and Omar uncertainty report showing the distribution of estate outcomes across 500 market futures.

### Purpose

This should be the visual "show-off" moment for uncertainty.

The visitor should understand that the same model can move from one deterministic plan to hundreds of reproducible futures and communicate the distribution, not just a single forecast.

### Prepare

Generate the public model's `Chance` report:

```text
seculana report examples/lise-and-omar.sec Chance -o lise-omar-chance.html
```

The model defines `Risk` as 500 runs, seed 7, in the `Markets` scenario.

Open the generated HTML in a browser.

### Frame

The current report begins with the estate-outcome histogram and continues with savings boxes, paths, chance of shortfall, correlations and coverage.

For this capture:

- keep the report title or explanatory sentence visible if it does not crowd the chart;
- make the **EstateToday histogram over 500 runs** the dominant visual;
- if the top of the next uncertainty chart fits naturally, it may remain in frame;
- ensure labels are readable.

### Capture notes

- Do not substitute a generic chart exported from another tool.
- This must be the actual Seculana report.
- Keep the seed/run description visible if the layout makes it easy, since reproducibility is part of the story.

---

## CAP-005 — A policy being chosen

**Status:** Ready  
**Priority:** Fourth  
**Tool:** Snagit  
**Target filename:** `public/media/captures/lise-omar-best-order.png`  
**Placement:** Decision-engine showcase, optimization section  
**Desired shape:** roughly 3:2 landscape  
**Alt text:** Seculana Playground optimizer showing the chosen withdrawal order for Lise and Omar and the no-shortfall constraint.

### Purpose

This is the visual proof for the claim that Seculana can search over policy while the deterministic model remains the authority.

The visitor should see an actual optimization answer, not merely an `optimize` block.

### Prepare

Open the public Lise and Omar model in the current Playground:

```text
seculana play examples/lise-and-omar.sec
```

Open **Optimize**. The model already contains `BestOrder`:

```text
optimize BestOrder {
    vary order of Living
    for highest EstateToday
    keep YearsShort == 0
}
```

Run the model's **BestOrder** optimization.

The current Playground manual says the Optimize view can run optimizations already written in the model and shows the choice, result, constraints, the orders tried, and the block as the model would write it.

### Frame

Prefer a result state that visibly includes:

- **BestOrder** or enough context to identify the optimization;
- the **chosen withdrawal order**;
- the objective, **EstateToday**;
- the constraint **YearsShort == 0**, with its successful result;
- several of the orders tried, if they fit without making the important text tiny.

Include enough surrounding Playground chrome to establish that this is the real product, but let the optimization answer dominate the frame.

### Capture notes

- Capture after the optimization has completed, not while progress is still moving.
- Do not click **Write the answer into the text** before the capture. We want the optimizer's answer visible as an answer.
- Do not include the AI assistant.
- If the optimizer result has multiple collapsible/detail areas, prioritize the chosen order and the constraint over the full search history.
- Keep the cursor away from the chosen order and result values.

## CAP-006 — Chance in motion

**Status:** Planned, not ready  
**Tool:** Camtasia

Likely subject: scrub through Monte Carlo futures or model time and show the views change.

Do not capture yet. We will write an exact cursor/timing script once the still captures are integrated.

## Delivery

If convenient, add finished files directly to the exact repository paths above.

If you would rather upload them in chat, upload the PNG masters and keep the filenames. I can then integrate them and tune crop/caption/responsive behavior in the site.
