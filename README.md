# ORCA BERG
<p align-items=center>
   <img src=https://github.com/NEURAL-Y/ice-orca/blob/main/public/logo.png width=800>
</p>

![Rust](https://img.shields.io/badge/Rust-1.XX%2B-orange?logo=rust)
![Status](https://img.shields.io/badge/status-under%20development-yellow)
[![License](https://img.shields.io/badge/license-BSD--3--Clause-blue)](https://github.com/NEURAL-Y/ice-orca/blob/main/LICENSE)

> **Explore data, don't just plot it.**

ORCA BERG is a Rust-native data analytics and visualization library designed for **interactive exploratory data analysis**.

It aims to combine DataFrame-based analytics, automatic visualization, compact statistical summaries, and a modern investigation-focused GUI.

Instead of forcing users to manually create dozens of plots, ORCA BERG provides a compact overview of a dataset and lets users **dive deeper into individual features by interacting directly with the visualizations**.

## ✨ Vision

Traditional data analysis often looks like this:

```text
load data
   ↓
describe()
   ↓
create plot
   ↓
create another plot
   ↓
inspect another column
   ↓
create another plot
```

ORCA BERG aims to make this:

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

The goal is simple:

> **Help users discover what is interesting in their data, rather than merely drawing whatever chart they manually requested.**

## 🔬 Example Concept

A dataset overview could look like:

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

The compact distribution gives an immediate visual indication of the shape of each feature without requiring a separate plot.

Selecting a feature can open a detailed investigation view containing:

* Distribution
* Mean
* Median
* Standard deviation
* Minimum and maximum
* Quantiles
* Skewness
* Kurtosis
* Missing values
* Outliers
* Correlations
* Feature-specific diagnostics

## 🖱️ Click to Investigate

One of ORCA BERG's core ideas is that **visualizations should be interactive entry points into analysis**.

For example:

```text
salary       ▁▁▂▃▅▇█▆▃▂
                │
              CLICK
                ↓
       ┌──────────────────────┐
       │ salary               │
       │                      │
       │      ╭────╮          │
       │   ╭──╯    ╰──╮       │
       │ ╭─╯          ╰────   │
       │─╯                    │
       │                      │
       │ Mean       54,203    │
       │ Median     49,100    │
       │ Std        18,203    │
       │ Skewness      2.73   │
       │ Kurtosis      11.42  │
       │ Missing        1.1%  │
       └──────────────────────┘
```

Users should be able to click the **actual visualization**, not just the column name.

The interaction model is:

```text
See
 ↓
Notice
 ↓
Click
 ↓
Visualize
 ↓
Investigate
```

A user can move from a tiny distribution in an overview directly into a full visualization and inspect the information behind it.

Future interactions may include:

```text
Click distribution
        ↓
   Full plot
        │
   ┌────┼──────────────┐
   ↓    ↓              ↓
Stats Outliers      Distribution
   │
   └──────→ Correlations
```

## 🚀 Planned Features

### Data Analytics

* DataFrame-based analysis
* Descriptive statistics
* Quantiles and percentiles
* Skewness
* Kurtosis
* Missing-value analysis
* Duplicate detection
* Outlier detection
* Cardinality analysis
* Correlation analysis
* Grouped statistics

### Automatic Visualization

ORCA BERG will automatically select useful visual representations based on the data type.

```text
Numeric
    → distribution
    → box plot
    → outliers
    → statistics

Categorical
    → frequency
    → category distribution

Datetime
    → temporal distribution
    → trends

Boolean
    → proportions
```

The objective is not to automatically generate as many charts as possible.

It is to generate the **most useful visual information with the least manual work**.

### 📊 Micro-Visualizations

Compact visualizations will be embedded directly into statistical summaries.

```text
age          ▁▂▅▇█▇▅▃▂▁
salary       ▁▁▂▃▅▇█▆▃▂
experience   ▁▂▄▆█▇▅▃▂
```

These provide a quick visual representation of distributions directly inside the dataset overview.

### 🔎 Interactive Investigation

The GUI will be designed around:

> **See → notice → click → investigate.**

A suspicious distribution, high missingness, unusual skewness, strong correlation, or potential outlier should become directly explorable.

### 🧪 Data Quality

ORCA BERG is intended to identify potentially important issues such as:

```text
⚠ High missingness
⚠ Strong skew
⚠ Heavy-tailed distribution
⚠ Extreme outliers
⚠ Near-constant feature
⚠ Highly correlated features
⚠ Potential duplicate rows
```

Rather than simply displaying a warning, the GUI should eventually allow users to **click the warning and inspect the underlying data**.

### 🤖 ML-Oriented Exploration

Future versions may provide analysis specifically useful for machine-learning workflows:

* Target-aware feature analysis
* Class imbalance
* Feature-target relationships
* Train/test distribution comparison
* Data drift
* Potential data leakage indicators
* Feature redundancy
* Feature importance exploration

## 🦀 Rust First

ORCA BERG is designed specifically for the Rust ecosystem.

The long-term goal is to provide a modern experience for data scientists and ML engineers while retaining the performance, safety, and portability of Rust.

The project is not intended to simply reproduce existing Python libraries API-for-API.

Instead, it aims to explore what **data analysis could look like when analytics and visualization are designed together from the beginning**.

## 🧭 Planned Architecture

```text
                         ORCA BERG
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

The project will initially build on existing Rust data infrastructure where appropriate rather than unnecessarily reinventing mature components.

## 🛠️ Development Status

**Under Development**

ORCA BERG is a long-term project under active development.

The initial development focus is:

```text
1. Data representation
2. Statistical engine
3. Distribution analysis
4. Terminal micro-visualizations
5. Visualization engine
6. Interactive GUI
7. Click-to-investigate workflow
8. Advanced EDA
9. ML-oriented analysis
```

The project is intentionally being developed incrementally.

## 🎯 Long-Term Goal

ORCA BERG aims to become a unified environment for:

```text
Data
 │
 ├── Analyze
 │
 ├── Visualize
 │
 ├── Investigate
 │
 └── Understand
```

The ultimate goal is not to provide the largest number of charts.

It is to make **finding useful information inside a dataset faster, more visual, and more interactive**.

## 📜 License

ORCA BERG is licensed under the **BSD 3-Clause License**.

See the `LICENSE` file for the full license text.
