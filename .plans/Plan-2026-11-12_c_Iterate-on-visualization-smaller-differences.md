# Plan: Iterate on visualization for smaller differences

## Goal and scope

Update [the existing page](../public/index.html) so one beef burger is the largest
chart comparator. Remove transport from the chart only, bringing the smaller
activities into a tighter linear range without changing their quantities or
estimated emissions.

This is an implementation-ready plan, not an instruction to modify the page yet.
It supersedes the earlier plan's transport-chart and axis requirements only;
preserve the current mobile-first, single-column layout, normal-sized text,
colours, horizontal scrolling and accessibility.

## 1. Remove the three transport entries from the chart

- In `.chart-list`, remove the complete `.chart-row` elements linking to
  `#activity-petrol`, `#activity-flight` and `#activity-ev`, including their bars,
  labels and totals.
- Keep all remaining 13 chart entries, with their current quantities, gram
  values and descending order. The burger becomes the first entry.
- Do not remove the corresponding table rows or their IDs.
- Do not modify [REPORT.md](../REPORT.md).

## 2. Make one burger the full-width reference

- Set the shared zero-based linear axis maximum to **7 kg CO₂e (7,000 g)**,
  matching one burger with a 113 g beef patty plus bun.
- Update the `.bar` width calculation from `var(--grams) / 200 * 1%` to
  `var(--grams) / 70 * 1%`. Update the adjacent CSS comment from a 20 kg axis
  to a 7 kg axis.
- Replace `.axis-ticks` with eight ticks labelled **0, 1, 2, 3, 4, 5, 6, 7**,
  positioned at `0/7` through `7/7` of the track width. Keep the kg CO₂e label.
- Update `.track` gridlines from four equal intervals to seven equal intervals,
  so each gridline represents 1 kg and aligns with its tick.
- Retain proportional widths with no minimum bar width or logarithmic scaling.
  Keep the existing endpoint markers and their explanation.
- Do not resize or multiply the remaining activities to fill space. The tighter
  axis makes them larger on screen, not closer in actual emissions; some bars
  will still be tiny.

## 3. Replace the transport explanation with a separate flight side note

- Replace the existing `.context-note` headed "Why 100 km?" with a standalone
  burger-to-flight comparison, outside the chart and its scale.
- Suggested copy:

  > **A burger, in travel perspective.** One beef burger is estimated at 7 kg
  > CO₂e, about 6% of one passenger's one-way Amsterdam–Geneva flight
  > (110 kg CO₂e, including non-CO₂ effects). That flight is roughly 16 burgers'
  > worth of emissions. Travel stays in the full table, not in this chart.

- Use the **full one-way flight**, not the previous 100 passenger-km allocation:
  `7 / 110 × 100 ≈ 6.4%`; conversely, `110 / 7 ≈ 15.7`.
- Give the aside an accessible name describing this comparison.
- Link the flight reference to `#activity-flight` and optionally the burger
  reference to `#activity-burger` using ordinary fragment links.
- Keep this an approximate emissions comparison, not a claim that the activities
  are interchangeable. Preserve the existing uncertainty disclaimer.
- Do not add a flight bar, inset chart, secondary axis or flight-sized background
  reference inside the chart.

## 4. Keep transport in the full numerical table

- Retain all **16 table rows**, their IDs and the original nine report columns
  unchanged, including full-trip central values of 170 kg petrol, 110 kg flight
  and 54 kg EV.
- For those three transport rows only, replace "Chart quantity (report units)"
  with **"Not charted"** and "Chart CO₂e total" with **"—"**. Remove the obsolete
  100 km chart allocations from these cells.
- Keep both chart-specific columns and their existing values for the other
  13 activities.
- Update the table introduction to explain that transport is retained for
  context but excluded from the chart, and that the last two columns apply
  only to charted activities.
- Keep the report's grid, energy and flight-RF assumptions below the table.

## 5. Keep nearby copy consistent

- Update the introduction and chart description to identify food, deliveries
  and digital activities as the chart's scope, with travel available separately
  in the table and side note.
- Mention that one burger is the chart's largest comparator at 7 kg CO₂e.
- Remove remaining descriptions of transport as charted 100 km quantities.
- Preserve the report link, footer tagline and existing dated session-energy
  estimate. Do not silently present that historical estimate as newly measured
  or updated usage.
- Keep the page static and dependency-free; no JavaScript is needed.

## Acceptance checks for the later implementation

- Exactly **13 chart entries** and **16 table rows** remain.
- The burger is first at 7,000 g and occupies 100% of the 7 kg track.
- Tick labels and gridlines align from 0 to 7 kg on a shared linear scale.
- Check representative widths: large agent task = `210 / 7000 = 3%`;
  computer work = `112 / 7000 = 1.6%`; 100 chat queries =
  `12 / 7000 ≈ 0.1714%`. All quantities and totals remain unchanged.
- No chart entry links to a transport row, but side-note links still reach
  the preserved table rows.
- Transport rows say "Not charted" and "—" in the last two columns;
  all original report cells and REPORT.md remain unchanged.
- The side note compares 7 kg with the full 110 kg flight, outside the chart.
- Existing horizontal scrolling, readable labels, target highlighting and
  single-column presentation remain intact.
