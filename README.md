<div align="center">

<img src="https://raw.githubusercontent.com/NEURAL-Y/ice-orca/main/public/logo.png" alt="ICE ORCA" width="640"/>

# ICE ORCA

**A Rust-native data analytics and visualization library for interactive exploratory data analysis.**

![Rust](https://img.shields.io/badge/Rust-1.XX%2B-orange?logo=rust)
![Status](https://img.shields.io/badge/status-under%20development-yellow)
[![License](https://img.shields.io/badge/license-BSD--3--Clause-blue)](https://github.com/NEURAL-Y/ice-orca/blob/main/LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](#contributing)

> **Explore data, don't just plot it.**

[Vision](#vision) • [Example](#example-concept) • [Planned Features](#planned-features) • [Architecture](#planned-architecture) • [Status](#development-status) • [Contributing](#contributing)

</div>

---

ICE ORCA combines DataFrame-based analytics, automatic visualization, compact statistical summaries, and a modern investigation-focused GUI. Instead of manually creating dozens of plots, it gives you a compact overview of a dataset and lets you **dive into individual features by interacting directly with the visualizations**.

## Vision

Traditional EDA tends to look like this:

```text
load data → describe() → create plot → create another plot → inspect column → create another plot → ...
```

ICE ORCA aims to make it this:

```text
              Dataset
                 │
                 ▼
          Automatic Overview
                 │
       ┌─────────┼─────────┐
       ▼         ▼         ▼
   Statistics  Distribution  Data Quality
       │         │         │
       └─────────┼─────────┘
                 ▼
          Click to Explore
                 │
                 ▼
          Detailed Analysis
```

> **Help users discover what is interesting in their data, rather than merely drawing whatever chart they manually requested.**

## Example Concept

A dataset overview, with distributions embedded directly in the summary:

```text
┌─────────────────────────────────────────────────────────────┐
│ Dataset Overview                                            │
├────────────┬───────┬────────┬────────┬──────────────────────┤
│ Column     │ Mean  │ Std    │ Median │ Distribution         │
├────────────┼───────┼────────┼────────┼──────────────────────┤
│ age        │ 32.4  │ 8.2    │ 31     │ ▁▂▅▇█▇▅▃▂▁          │
│ salary     │ 54k   │ 18k    │ 49k    │ ▁▁▂▃▅▇█▆▃▂          │
│ experience │ 6.1   │ 4.2    │ 5      │ ▁▂▄▆█▇▅▃▂           │
└────────────┴───────┴────────┴────────┴──────────────────────┘
```

Clicking a feature — the **visualization itself**, not just the column name — opens a detailed view:

```text
salary       ▁▁▂▃▅▇█▆▃▂
                │
              CLICK
                ↓
       ┌──────────────────────┐
       │ salary               │
       │      ╭────╮          │
       │   ╭──╯    ╰──╮       │
       │ ╭─╯          ╰────   │
       │─╯                    │
       │ Mean       54,203    │
       │ Median     49,100    │
       │ Std        18,203    │
       │ Skewness      2.73   │
       │ Kurtosis      11.42  │
       │ Missing        1.1%  │
       └──────────────────────┘
```

The interaction model driving the whole GUI: **see → notice → click → investigate.**

## Planned Features

**Data Analytics** — descriptive statistics, quantiles/percentiles, skewness & kurtosis, missing-value and duplicate detection, outlier detection, cardinality and correlation analysis, grouped statistics.

**Automatic Visualization** — ICE ORCA picks a useful representation based on data type, aiming for the most useful visual information with the least manual work:

```text
Numeric     → distribution, box plot, outliers, statistics
Categorical → frequency, category distribution
Datetime    → temporal distribution, trends
Boolean     → proportions
```

**Micro-Visualizations** — compact sparkline-style distributions embedded directly into summaries:

```text
age          ▁▂▅▇█▇▅▃▂▁
salary       ▁▁▂▃▅▇█▆▃▂
experience   ▁▂▄▆█▇▅▃▂
```

**Data Quality** — surfaces issues as clickable, investigable warnings rather than static text:

```text
⚠ High missingness        ⚠ Extreme outliers
⚠ Strong skew              ⚠ Near-constant feature
⚠ Heavy-tailed distribution   ⚠ Highly correlated features
⚠ Potential duplicate rows
```

**ML-Oriented Exploration** *(future)* — target-aware feature analysis, class imbalance, feature-target relationships, train/test distribution comparison, data drift, potential leakage indicators, feature redundancy and importance exploration.

## Rust First

ICE ORCA is built specifically for the Rust ecosystem — not a port of an existing Python library API-for-API. The goal is a modern EDA experience for data scientists and ML engineers, backed by Rust's performance, safety, and portability, exploring what analysis looks like when **analytics and visualization are designed together from the start**.

## Planned Architecture

```text
                         ICE ORCA
                             │
             ┌───────────────┼───────────────┐
             │               │               │
             ▼               ▼               ▼
         Analytics      Visualization       GUI
             │               │               │
             ▼               ▼               ▼
        Statistics        Renderer       Interaction
             │               │               │
             └───────────────┼───────────────┘
                             │
                             ▼
                         DataFrame
```

Where sensible, ICE ORCA builds on existing mature Rust data infrastructure rather than reinventing it.

## Development Status

**Under active, long-term development.** Build order:

```text
1. Data representation           6. Interactive GUI
2. Statistical engine            7. Click-to-investigate workflow
3. Distribution analysis         8. Advanced EDA
4. Terminal micro-visualizations 9. ML-oriented analysis
5. Visualization engine
```

Being developed incrementally — expect the API surface to shift as the analytics and visualization layers take shape.

## Long-Term Goal

```text
Data → Analyze → Visualize → Investigate → Understand
```

Not the largest number of charts — **finding useful information inside a dataset, faster, more visually, more interactively.**

## Contributing

1. Fork the repo and branch from `main`.
2. Make focused commits; add tests where relevant.
3. Open a PR describing the change and motivation.

Since the analytics/visualization architecture is still settling, open an issue before tackling a large roadmap item to align on approach first.

## License

ICE ORCA is licensed under the [APACHE 2.0 License](https://github.com/NEURAL-Y/ice-orca/blob/main/LICENSE).

---

<div align="center">

**Explore data, don't just plot it.**

</div>
