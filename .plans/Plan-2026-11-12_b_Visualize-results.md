# Plan: Visualize results

## Goal and scope

Create a single-page website at `public/index.html` that puts the report's
everyday, food, transport and digital footprints into perspective.

This document is the specification for a later implementation pass.

The page contains, in order:

1. A strong headline and a short introduction.
2. One bar chart containing all 16 activities/modalities.
3. The full numerical summary table.
4. A short footer paragraph linking to the full report in this repository.

## Confirmed decisions

- Use emoji as the chart's visual activity labels; Include a short text-label/name alongside.
- Link each chart entry to its corresponding row in the table below.
- Use fixed quantities, not visitor-adjustable inputs (yet; maybe later).
- Increase some small activities to modest, realistic batches rather than
  thousands or tens of thousands of repetitions.
- Put transport on a common 100 km basis rather than showing full trips.
  Keep the original trip estimates in the table.
- Display the quantity prominently: a batch must never look like one occurrence.
- Keep this a static page, without a framework, backend or charting dependency.

## Source of truth

- Use [the report](../REPORT.md), specifically section 1, "Summary table (D2)",
  for all 16 entries, their emoji, functional units, estimates and uncertainty.
- Preserve the report's estimates rather than recomputing them from its research
  dossier, whose intermediate calculations can differ from the rounded summary.
- Preserve its context: compiled 12 November 2026; central estimates with
  low-high ranges; differences of about 10 times or more are meaningful, while
  differences of two times can be within uncertainty.
- Explain that these are different activities with explicitly stated quantities,
  not interchangeable services. Only transport shares a per-100-km basis;
  the rest uses the portions, durations and batches stated beside each entry.
- Do not add new research, silently correct the report or imply independent
  verification of its AI-assisted research. Do not change REPORT.md at all.

## Page structure and copy

### Header

- Working headline: **"Compare footprints 👣"**
- Supporting sentence: "Compare the estimated carbon footprint of travel, food
  and digital activities; to put your AI use into perspective."
- Add a short note explaining that the digital batches are illustrative amounts,
  not measured averages or scientifically established norms.
- Include a visible "See all the numbers" link to `#full-table`.

### One comparison chart

- Show central CO2e only. Do not mix carbon and energy on one axis.
- Use a horizontal bar chart so all 16 entries fit naturally on narrow screens.
- Use one shared **linear scale starting at zero**, labelled in kg CO2e, with
  light gridlines and readable ticks. Normalize input values to grams internally.
- Sort entries by the **displayed batch total**, descending; use report order to
  break ties. Table order remains the report's original per-unit ordering.
- Each entry shows its report emoji, a concise quantity/activity label and the
  formatted central total in g or kg. Emoji alone must not convey identity.
- Make the emoji/label an ordinary anchor pointing to a stable table row ID.
  Accessible link text identifies the activity, quantity and destination.
- Use links rather than custom tooltips for the first version. This meets the
  tooltip-or-link requirement without hover-only information or extra JS.
- Provide a caption explaining the units, fixed batches and uncertainty.

#### Proposed fixed quantities

These are implementation defaults, not claims about typical behaviour. Scale
transport to 100 km, keep food, parcel delivery and agent tasks at their report
units, and batch the smallest digital activities with simple, recognisable
quantities.

| Report entry | Chart quantity | Chart central CO2e |
| --- | --- | --- |
| Petrol car | 100 km, 1 car, 1 occupant | 17 kg |
| Flight | 100 passenger-km share of the AMS-GVA estimate, including RF | approximately 15 kg |
| EV | 100 km, 1 car, 1 occupant, NL grid | 5.4 kg |
| Beef burger | 1 burger, 113 g patty plus bun | 7 kg |
| Chicken | 1 portion, 150 g | 1.5 kg |
| Cheese | 1 portion, 50 g | 1.2 kg |
| Agent task, large | 1 task, approximately 1 hour | 210 g |
| Parcel, next-day | 1 parcel, NL, approximately 150 km | 150 g |
| Teams + recording | 1 meeting-hour, 4 people, recording kept 1 year | 60 g |
| Video streaming | 2 hours, HD | 100 g |
| Agent task, medium | 1 task, approximately 10 minutes | 18 g |
| Computer work | 8 hours, laptop plus monitor | 112 g |
| Music streaming | 8 hours, smartphone | 12 g |
| GitHub Actions CI | 10 runs of 5 minutes, Linux CPU runner | 6 g |
| Google search | 100 queries, no AI | 20 g |
| Chat query | 100 short prompts plus answers | 12 g |

#### Transport scaling

- Petrol and EV use a multiplier of `100 / 1000 = 0.1` on the summary's
  approximately 1,000 km trip estimates.
- Flight uses `100 / 740` on the summary's 110 kg central estimate: approximately
  14.9 kg, displayed as approximately 15 kg. The 740 km distance is the report's
  flight-path estimate including its path uplift, not the car's road distance.
- Describe the flight quantity as an allocated share of that route's estimate,
  not a real 100 km flight or a prediction that aviation emissions scale
  linearly across routes. Keep this explanation near the chart.
- Use the unrounded scaled values for bar proportions and ordering; round only
  for display.
- With these quantities, petrol is the largest bar at 17 kg, followed by the
  flight share, the burger and the EV. Do not force the flight to be largest.

**Visibility limitation:** even these batches are tiny beside 100 km of petrol
driving at 17 kg. Scaling down transport helps, but does not remove that gap.
Do not promise that realistic quantities will make all bar lengths distinguishable
on a single linear scale. Keep labels and values readable independently of bar
length. A small endpoint marker may make a tiny value discoverable, but must be
visually distinct from the proportional bar and explained as a marker, not extra
emissions. Do not apply a misleading minimum bar width, truncate the axis, enlarge
quantities automatically or introduce an undisclosed nonlinear scale.

If distinguishable lengths for every activity become a hard requirement, confirm
a scale change with the user before implementation rather than quietly changing
these quantities.

### Full numerical table

- Place a section with `id="full-table"` immediately below the chart.
- Reproduce all nine columns and all 16 rows from the report's summary:
  item, functional unit, central CO2e, CO2e range, final energy, primary energy,
  order of magnitude (g / Wh primary), chat-query equivalents and confidence.
- Preserve original per-unit values, units, rounding, missing-value dashes,
  CED annotations and qualifications such as flight emissions excluding RF,
  meeting emissions per person and the age of the search data.
- Add two clearly named columns: "Chart quantity (report units)" and
  "Chart CO2e total". This makes the relationship between the original numbers
  and the larger batches explicit.
- State that the original energy and equivalent columns are per report unit,
  not batch totals; do not silently scale only some original columns.
- Use stable, readable row IDs such as `activity-chat-query` and
  `activity-agent-large`.
- Highlight the linked row with `:target`, without relying on colour alone.
- Include the report's three key assumptions below the table: grid intensities,
  primary-energy factors/CED and flight RF treatment.

### Footer

- Suggested paragraph: "These figures are rough, AI-assisted (!) estimates intended
  to put orders of magnitude in perspective, not precise measurements. Read the
  full report for calculations, sources, assumptions and limitations."
- Link "full report" to
  `https://github.com/elwinschmitz/compare-footprints/blob/main/REPORT.md`.
- Use a full, absolute GitHub URL so the link also works when only `public/` is served.
- Mention that embodied emissions are excluded and that some sources remain
  unverified, as documented in the report.

## Visual design and accessibility

- Aim for a clear editorial style: a clean, solid neutral background, dark text,
  generous whitespace and a prominent headline. Use a bright, colourful accent
  that feels friendly rather than alarming, neon or visually harsh.
- Use system fonts and the platform emoji font; no remote font or asset requests.
- Use consistent category accents if useful, but never colour alone to identify
  entries or communicate quantities.
- Let the chart have a minimum width greater than 320 px when needed to show
  meaningful differences in bar lengths on the shared linear scale. On narrower
  screens, allow horizontal scrolling instead of shrinking the chart to fit.
  Keep labels and totals readable, with wrapping where useful.
- Put the chart and wide table in their own keyboard-focusable horizontal scroll
  regions with accessible names and visible scrolling hints when they overflow.
  Keep the surrounding page responsive without page-wide horizontal scrolling.
- Use semantic landmarks, one `h1`, logical section headings, a chart
  `figure`/`figcaption`, a table caption and scoped row/column headers.
- Ensure chart links have visible focus, sufficient contrast and comfortable
  touch targets; hide decorative emoji from assistive technologies when the
  adjacent text already names the activity.
- Retain full information without hover, colour perception or JavaScript.

## Implementation approach for the later generation pass

1. Create `public/index.html` with inline CSS and static semantic HTML.
2. Copy the summary data faithfully and calculate chart totals using the fixed
   multipliers above. Keep any chart-specific quantity metadata explicit.
3. Use HTML/CSS for bars and ordinary fragment links for navigation. No runtime
   fetch of Markdown, canvas-only chart, build pipeline or JavaScript is needed.
4. Add a brief comment identifying the report section and compilation date as
   the data source. When source data changes, update table values, batch totals,
   sort order and bar proportions together.
5. Add a short link to `public/index.html` in [the README](../README.md), keeping
   the existing report link and AI disclaimer intact.
6. Do not add deployment configuration, interactive calculators, metric
   switches, filtering or extra pages in this pass.

## Acceptance checks for the later implementation

- Opening `public/index.html` directly and serving `public/` both show a complete
  page without a build, runtime network requests or console errors.
- Exactly 16 entries appear in one chart and 16 corresponding table rows exist.
- All original summary-table cells match the report, including caveats.
- Each displayed chart total equals the source central estimate times its stated
  multiplier; specifically check 100 chats = 12 g, 100 searches = 20 g,
  10 CI runs = 6 g, 8 computer-work hours = 112 g, 100 km petrol = 17 kg,
  100 km EV = 5.4 kg and the 100 passenger-km flight share =
  `110 * 100 / 740` kg (approximately 15 kg).
- Bar proportions match those totals on the shared zero-based linear scale;
  for example the flight/car ratio is `(110 * 100 / 740) / 17` and EV/car
  is `5.4 / 17`. The largest value is 17 kg, not the original 170 kg trip.
- Chart ordering follows batch totals, not the unscaled report order.
- Every chart entry reaches the correct table row with mouse, keyboard and touch.
- At 320 px, 768 px and desktop viewport widths, the surrounding page fits the
  viewport. The chart may retain a wider minimum width: verify that horizontal
  scrolling reveals its full linear scale, labels and totals without compressing
  bar-length differences. Both chart and table scroll regions work with keyboard
  and touch, without requiring page-wide horizontal scrolling.
- Check keyboard focus, table semantics and readable content at 200% zoom.
- The footer reaches the full report when only `public/` is served.
- No implementation is considered finished merely because the tiny bars look
  larger: quantity transparency and truthful proportions take priority.

---

## Second pass, feedback on initial implementation

- No need for the double header headline component. Remove the top-most part. Keep the 'tagline', use it in the footer.
- Make the Design for mobile first and single column only. No need for layout changes on wider viewports, like for example the thing in the footer that it gets columns all of a sudden.
- Use normal body-sized text (at least 1rem) for chart labels, quantities, values,
  notes, table content and footer copy. Supporting information should not look
  like fine print; distinguish it through spacing, weight and colour instead.
- Footer tagline: "An order-of-magnitude comparison. Perspective, not precision."

