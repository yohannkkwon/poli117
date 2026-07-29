# Bending the Curve: San Diego Transportation Plan, 2026 to 2036

An interactive companion site for a POLI 117R final project: a ten-year regional plan to cut
transportation emissions in San Diego County through equitable vehicle electrification paired
with reduced driving.

**Live site:** https://yohannkkwon.github.io/poli117/

## What's here

A single self-contained `index.html`. No frameworks, no build step, no external requests.
The chart is hand-drawn SVG generated in vanilla JavaScript, so nothing can break from a
dead CDN link and the page works offline.

**The centerpiece** is an animated chart of per-capita CO₂ from cars and light-duty trucks,
the metric California actually grades the region on under Senate Bill 375. Press play or drag
the scrubber to move through the plan period. Two paths diverge from 2026: business as usual,
which flattens just *above* the state's compliance line, and the plan path, which clears it.
Policy milestones appear as stations along the plan line as the timeline advances.

**The equity map** is a schematic diagram of the San Diego metro area showing the freeway
corridors, the Metropolitan Transit System trolley lines, half-mile transit access areas, and
the seven neighborhoods carrying the heaviest transportation pollution burden. Toggle between
Today and 2036 to see coverage expand and charging appear where the plan sites it. Hover or
tab to any red marker for that neighborhood's context. Distances are distorted for legibility,
as on any transit diagram.

## Data honesty

Every figure on the page is labeled either **Reported** or **Modeled**, and the method section
at the bottom lists each one with its source.

Reported values come from CARB's SB 375 target-setting documents (the 26 lbs per person per
weekday 2005 baseline, the 19% target), SANDAG's 2021 and 2025 Regional Plans (sector
inventory, transit access, mode share, the 19.35% and 20% projections), the California Energy
Commission (statewide ZEV sales share), and the Environmental Health Coalition.

Projections are generated from stated assumptions, listed in the method table. They are
illustrative of scale, not forecasts.

## Publishing to GitHub Pages

From inside this folder:

```bash
git init -b main && git add . && git commit -m "Bending the Curve: San Diego transportation plan site"
```


```bash
git remote add origin https://github.com/yohannkkwon/poli117.git && git push -u origin main
```

Then in the repository on GitHub: **Settings → Pages → Source: Deploy from a branch →
`main` / `root` → Save.** The site goes live at the URL above in a minute or two.

## Editing

All chart data lives in three arrays near the top of the `<script>` block: `history`, `bau`,
and `plan`. Each is a list of `[year, lbsPerPersonPerWeekday]` pairs. Milestones live in
`stations`, and the sector bars in `inventory`. Change the numbers and the chart, counters,
and timeline all update together.
