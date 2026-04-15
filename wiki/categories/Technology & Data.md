---
tags:
  - category
---

# Category: Technology & Data

App metrics, data governance, attribution platforms, technical performance, and measurement infrastructure at Property Finder.

## Articles in this category

- [[Kochava]] — Mobile attribution platform; recurring data quality and tracking failures across W3, W10, W11
- [[Exposure LPL]] — Leads per listing metric (eLPL); key demand proxy used in client conversations; collapsed in March
- [[NPS]] — Net Promoter Score; B2C sentiment measurement; hit 3 in January (–10 YoY)
- [[sources/wbr-week-10]] — Simultaneous Kochava and CHEQ failures on the most critical measurement week of the quarter
- [[sources/wbr-week-11]] — Kochava vs Redshift and GA4 vs Redshift discrepancies flagged alongside record-low B2B incidents

## Related categories
- [[categories/Property Finder Performance]]
- [[categories/Claude Usage & Prompting]]

## Key Insights

- **Data infrastructure failures clustered at the worst possible moments**: Kochava failed in W3 (losing two days of app session data), and then both Kochava and CHEQ failed simultaneously in W10 — the first week of the conflict, exactly when accurate baseline data was most needed to understand the shock's magnitude. Data governance problems during calm periods are operational issues; during a crisis they become strategic blindspots.

- **Kochava vs Redshift vs GA4 discrepancies (flagged in W11) suggest the data stack has unresolved reconciliation problems**: Three separate systems measuring overlapping dimensions of the same user activity, with known gaps between them, means every metric derived from these systems carries an implicit error range. LPL calculations (which flow into client-facing dashboards), session counts, and conversion rates are all affected. This is not a new problem that appeared in March — it is a technical debt that was visible but unresolved since at least January.

- **Exposure LPL's collapse to 3.7 Buy vs 7.6 target (–51%) is the most client-visible technology failure of the quarter**: eLPL is calculated from lead volume divided by active listings. The March crash in leads wasn't just a business problem — it showed up directly in client dashboards, eroding the perceived value of the product in real time. Q2 targets will be reset, but clients who experienced months of below-target LPL have already updated their ROI expectations downward.

- **Mobile INP finally hitting 72% target in W11 after a full quarter of misses shows product delivery under pressure**: Engineering held the INP improvement programme even during the conflict disruption, delivering the milestone in week 11 — the same week B2B incidents hit a record low (17 MtD). The combination suggests operational excellence at the product level was maintained even when commercial conditions were deteriorating. This is a positive leading indicator for product quality in Q2.

- **B2C NPS at 3 in January is a product health signal that predates and is independent of the conflict**: A score of 3 — down 9 MoM and 10 YoY — during a bull market period suggests the user experience was eroding while usage was growing. High MAU and install numbers coexisting with a near-zero NPS means users are coming because they have to (market liquidity), not because they're satisfied. This is the kind of NPS reading that precedes churn at scale once market conditions give users a viable alternative.
