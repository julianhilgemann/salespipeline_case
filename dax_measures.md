**DAX Measures — here's the complete set:**

**Core KPIs:**
- `Total Pipeline Value` = SUM of Expected Order Volume where stage is not Won/Lost
- `Weighted Pipeline Value` = SUMX over open deals, volume × probability
- `Total Won Revenue` = SUM of volume where stage = Won
- `Total Lost Value` = SUM of volume where stage = Lost
- `Open Deals` = COUNT of deals where stage not in {Won, Lost}
- `Win Rate` = DIVIDE(count of Won, count of Won + Lost) — only closed deals in denominator
- `Avg Deal Size` = AVERAGE of Expected Order Volume (all deals or scoped as needed)

**Rep/Leaderboard measures:**
- `Deals Won` = COUNT where stage = Won
- `Deals Lost` = COUNT where stage = Lost
- `Deal Count` = COUNT of all deals (for context alongside win rate)

**Funnel/Stage measures:**
- `Stage Deal Count` = COUNT by stage (implicit via visual grouping, but a measure is cleaner)
- `Stage Value` = SUM of volume by stage
- `Stage Weighted Value` = SUMX, volume × probability by stage

**Loss analysis:**
- `Loss Count` = COUNT where stage = Lost (sliceable by Loss Reason)
- `Loss Rate by Source` = DIVIDE(lost deals from source, total deals from source) — this is the trickiest one, needs CALCULATE with ALL on Stage to get the denominator right

**Helper/Technical:**
- `Stage Sort Order` = a SWITCH on stage name returning 1-6, used for visual sort order (Lead=1, Qualified=2, Proposal=3, Negotiation=4, Won=5, Lost=6). Could also be a calculated column instead.
- `Is Open` = calculated column, TRUE if stage not in {Won, Lost} — simplifies several filters
- `Is Closed` = calculated column, inverse