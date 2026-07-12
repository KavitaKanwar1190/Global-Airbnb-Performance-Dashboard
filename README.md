 # Global Airbnb Performance Dashboard

**Author:** Kavita Kanwar
**LinkedIn:** [linkedin.com/in/kavita-kanwar1190](https://www.linkedin.com/in/kavita-kanwar1190)
**Email:** kavita.kanwar1190@gmail.com

A Power BI analysis of **279,712 Airbnb listings** and **5.37M reviews** across 10 global cities — built to answer the questions a market-expansion, pricing, or trust & safety team would actually ask.

---

## Dashboard Preview

![Overview Dashboard](images/01-overview.png)
*Overview — platform scale and listing growth from 2008–2020, with pandemic and regulatory impact visible in the trend.*

![Market Share and Ratings - Overall View](images/02-market-share-ratings-overall.png)
*Market Share & Ratings (Overall view) — city concentration, superhost mix, pricing vs. hotels, and a ratings heatmap by sub-metric.*

![Market Share and Ratings - Detailed View](images/03-market-share-ratings-detailed.png)
*Market Share & Ratings (Detailed view) — same page, toggled via bookmark to a ranked bar chart of overall city rating.*

![Reviews and Trust Dashboard](images/04-reviews-trust.png)
*Reviews & Trust — reviewer behaviour, seasonal demand by city, and host verification breakdown.*

---

## Project Highlights

- Analyzed **279,712 listings** and **5.37M reviews** across **10 cities** and **144 property types**
- Designed a **star-schema data model** (2 tables, 1 relationship) from raw source data
- Built **32 DAX measures + 4 calculated columns**, including two independent Pareto/running-total patterns
- Delivered **3 interactive dashboard pages** covering growth, market share, pricing, ratings, seasonality, and trust
- Implemented a **bookmark-driven view toggle** (no slicers) to switch chart types without adding a page
- Surfaced a genuine **data-quality anomaly** in reviewer behaviour through exploratory analysis
- Translated every chart into a specific, named **business decision** it supports

---

## Business Objective

Give stakeholders — market expansion, pricing, and trust & safety teams — a single dashboard to answer: where is Airbnb's supply concentrated, how does it price against hotels, where are guests least satisfied, when does demand peak by city, and how trustworthy is the host base, without relying on manual spreadsheet analysis.

---

## Dataset Overview

| Table | Rows | Description |
|---|---|---|
| `Listings` | 279,712 | Listing, host, geography, pricing, and review-score attributes |
| `Reviews` | 5,373,144 | Individual review records (`listing_id`, `review_id`, `date`, `reviewer_id`) |

**Relationship:** `Listings[listing_id]` (1) → `Reviews[listing_id]` (*)
Data was received clean — no imputation or de-duplication required.

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Power BI Desktop | Data modeling, DAX, report design |
| Power Query | Data import |
| DAX | 32 measures, 4 calculated columns |

---

## Data Model

Two-table star schema. `Listings` holds both descriptive attributes (city, room type) and measurable facts (price, ratings); `Reviews` is a pure transactional fact table joined one-to-many on `listing_id`.

\`\`\`
Listings (1) ─────────< Reviews (*)
   listing_id                listing_id (FK)
\`\`\`

---

## Dashboard Overview

| Page | Key Visuals | Core Business Question |
|---|---|---|
| **Overview** | 5 KPI cards, new-listings stacked area (by room type, with lifecycle eras) | How has platform supply grown, and what disrupted it? |
| **Market Share & Ratings** | City Pareto chart, avg. price by room type, ratings heatmap ↔ bar chart (bookmark toggle) | Where is supply concentrated, and how are we priced and rated? |
| **Reviews & Trust** | Review-frequency Pareto, seasonality streamgraph, host-trust matrix | How do guests review, when do they book, and how trustworthy are hosts? |

---

## Key Insights

- Paris, New York City, and Sydney account for **~50% of listings and 48% of reviews** — Paris hotel prices run roughly 2x Airbnb prices, a plausible driver.
- **86.3% of reviewers** wrote exactly one review; a 283-review outlier (two reviews logged the same day, two different Bangkok listings) points to a likely data-quality issue.
- Paris and Rome dominate review share **April–August**; New York spikes in **November–December**.
- Mexico City and Rio de Janeiro are the highest-rated cities; Hong Kong and Istanbul the lowest — **cleanliness and value-for-money** are the weakest sub-metrics overall.
- **66.9% of hosts** are fully identity-verified with a profile picture; only 0.3% have neither trust signal.

---

## Business Recommendations

- Prioritize host-acquisition spend in the top 3–4 cities, given their share of supply and engagement.
- Flag the 283-review outlier for a data-quality review before trusting extreme values in future review metrics.
- Target city-specific operational coaching (e.g. cleanliness in Hong Kong) instead of a blanket ratings initiative.
- Align marketing campaign timing to each city's actual seasonal peak rather than one global calendar.

---

## Skills Demonstrated

`Power BI` · `Power Query` · `DAX` · `Data Modeling` · `Data Visualization` · `Business Analysis` · `Interactive Dashboards` · `Bookmarks` · `KPI Design` · `Data Storytelling`

---

## Project Features

- Full star-schema model built from raw CSV sources
- Reusable Pareto/running-total DAX pattern applied across two tables
- Bookmark + Selection-pane driven multi-view toggle (Overall ↔ Detailed ratings)
- Every chart mapped to a specific business decision, not just a metric

---

## Challenges

- Building a reusable running-total (Pareto) pattern in DAX (`RANKX` + `VAR` + `FILTER`) and applying it consistently across two different tables.
- Designing an inclusion-flag calculated column (`Show in Review Frequency Chart`) to isolate meaningful reviewer buckets without a formal statistical test.

---

## Learnings

- When to use a calculated column (row context) versus a measure (aggregation context) — e.g. `Reviews per Reviewer` vs. `Total Reviewers`.
- Building cumulative/running-total measures with `RANKX` + `VAR` + `FILTER`.
- Using bookmarks and the Selection pane to deliver multiple chart views on one page without slicers or extra pages.

---

## Future Improvements

- Add a dedicated Date dimension table for cleaner time intelligence.
- Add a City dimension table if external benchmark data (e.g. hotel pricing) becomes available.
- Replace the hard-coded review-frequency threshold with a statistically derived cutoff.

---

 
