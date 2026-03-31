Dashboard Wireframe

```
┌─────────────────────────────────────────────────────────────┐
│  SALES PIPELINE DASHBOARD                        [Company]  │
├──────────┬──────────┬──────────┬──────────┬─────────────────┤
│ SLICERS: │ Rep  [v] │ Industry │ Country  │ Lead Source [v] │
│          │          │   [v]    │   [v]    │                 │
├──────────┴──────────┴──────────┴──────────┴─────────────────┤
│                                                             │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌────────┐ ┌────────┐  │
│  │ Open    │ │Weighted │ │  Won    │ │  Win   │ │  Avg   │  │
│  │ Deals   │ │Pipeline │ │ Revenue │ │  Rate  │ │  Deal  │  │
│  │   112   │ │  €XXXk  │ │ €483k   │ │  53%   │ │ €28.1k │  │
│  └─────────┘ └─────────┘ └─────────┘ └────────┘ └────────┘  │
│                                                             │
├─────────────────────────────────┬───────────────────────────┤
│                                 │                           │
│  PIPELINE BY STAGE              │  REP PERFORMANCE          │
│                                 │                           │
│  Lead         ████████  31      │  Rep   Deals Won  WinRate │
│  Qualified    █████     22      │  ───── ───── ───  ─────── │
│  Proposal     ██████████ 35     │  Rep 1   27    4    80%   │
│  Negotiation  ███████   24      │  Rep 2   36    6    40%   │
│  Won          █████     20      │  Rep 3   27    4    50%   │
│  Lost         ████      18      │  Rep 4   22    4   100%   │
│                                 │  Rep 5   38    2    33%   │
│  [bar length = value, not count]│                           │
│                                 │  [conditional formatting  │
│                                 │   on win rate column]     │
├─────────────────────────────────┬───────────────────────────┤
│                                 │                           │
│  LOSS REASONS                   │  LEAD SOURCE CONVERSION   │
│                                 │                           │
│  Timing     ██████  6           │  Inbound   ██████████ 28  │
│  Competitor █████   5           │  Outbound  ████████   25  │
│  Price      ████    4           │  Event     ███████    23  │
│  No Budget  ██      2           │  Referral  █████████  34  │
│  Other      █       1           │  Website   ██████     17  │
│                                 │  Other     ██████     22  │
│                                 │                           │
│                                 │  [stacked: won/open/lost  │
│                                 │   to show conversion]     │
└─────────────────────────────────┴───────────────────────────┘
```
