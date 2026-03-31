**Table: Sales_Pipeline**

**Granularity:** One row per sales opportunity (deal). Each row represents a unique lead/deal in the pipeline. 150 records total.

**Context:** B2B sales pipeline for a DACH-region company. Snapshot data — each record reflects the current/latest state of the deal, not a history of stage transitions. No stage change log exists; only the most recent stage and its change date are captured.

**Columns:**

**Lead ID** (Text) — Primary key. Format: two-letter prefix derived from customer name + hyphen + sequential number (e.g., "AL-1004"). 150 unique values, no nulls.

**Customer Name** (Text) — Account/company name. Only 3 unique customers: AlphaTech GmbH, BetaLogics GmbH, GammaSolutions GmbH. Multiple opportunities per customer. This is the account-level grain, not the deal-level grain.

**Contact Person** (Text) — Named contact for the deal. 150 unique values (one per deal). Generic placeholder format ("Contact 0", "Contact 1", …). No analytical value.

**Lead Source** (Text, Dimension) — Channel through which the lead originated. 6 categories: Event, Inbound, Other, Outbound, Referral, Website. No nulls.

**Sales Rep** (Text, Dimension) — Assigned sales representative. 5 values: Rep 1 through Rep 5. No nulls. Anonymized names.

**Opportunity Name** (Text) — Deal identifier label. 150 unique values. Generic placeholder format ("Opportunity 0", "Opportunity 1", …). No analytical value beyond identification.

**Stage** (Text, Dimension — Ordinal) — Current pipeline stage. 6 values with a logical order: Lead → Qualified → Proposal → Negotiation → Won / Lost. Won and Lost are terminal states. No nulls. Distribution: Proposal (35), Lead (31), Negotiation (24), Qualified (22), Won (20), Lost (18).

**Stage Change Date** (Date) — Date the deal entered its current stage. Range: 2024-11-24 to 2025-06-13. This is NOT a creation date and NOT a full history — only the latest transition is recorded.

**Probability (%)** (Decimal, 0–1) — Win probability. Deterministically mapped to Stage: Lead=0.05, Qualified=0.10, Proposal=0.25, Negotiation=0.50, Won=1.00, Lost=0.00. Not an independent signal — it is redundant with Stage and carries no additional information.

**Expected Close Date** (Date) — Projected deal close date. Range: 2024-12-27 to 2025-08-09. The difference to Stage Change Date ranges from 15–60 days. Can be used for a forward-looking pipeline schedule but not for velocity analysis.

**Expected Order Volume (€)** (Integer) — Deal value in euros. Range: ~€10k–€50k, mean ~€28k. No nulls. This is the primary monetary measure.

**Loss Reason** (Text, Dimension) — Reason for deal loss. 5 categories: Timing (6), Competitor (5), Price (4), No Budget (2), Other (1). Null for all non-lost deals (132 nulls out of 150). Only populated when Stage = Lost.

**Industry** (Text, Dimension) — Customer's industry vertical. 4 values: Finance, Healthcare, Manufacturing, Software. No nulls.

**Country** (Text, Dimension) — Customer's country. 3 values: Austria, Germany, Switzerland (DACH region). No nulls.

**Notes** (Float/Empty) — Entirely empty across all 150 rows. No data. Should be excluded from the model.

---

**Key limitations for any consuming system:**
No date dimension suitable for time intelligence (no continuous transaction date, no stage history). Probability is not an independent feature — do not use it as a separate analytical axis from Stage. Only 3 customers, so customer-level analysis is very thin. Small dataset (n=150), so any cross-filtered slices get sparse fast (e.g., Rep × Industry × Country can produce single-digit cells).
