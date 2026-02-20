# Skill: Weighted Pipeline Forecast

## Purpose
Calculate an honest revenue forecast based on stage probabilities, not gut feeling.

## Kent Summers' Rule
**"The Weighted Pipeline stops you from lying to yourself about how much revenue is coming in next month."**

## Stage Probabilities (from ICP config)
| Stage | Probability | Description |
|-------|------------|-------------|
| Suspect | 10% | Identified but not yet contacted |
| Prospect | 25% | Responded with interest |
| Discovery | 40% | In active conversation, needs mapped |
| Proposal | 60% | Proposal/pricing shared |
| Negotiation | 80% | Negotiating terms, close likely |
| Closed Won | 100% | Signed contract |
| Closed Lost | 0% | Lost deal |
| Frozen | 5% | Stalled, in Freezer |

## Calculation
```
For each deal:
  Weighted Value = Deal Value × Stage Probability

Total Weighted Pipeline = Sum of all Weighted Values
```

## Example
```
Acme Corp    - Proposal    - $5,000/mo × 12 = $60,000 × 60% = $36,000
Beta LLC     - Discovery   - $3,000/mo × 12 = $36,000 × 40% = $14,400
Gamma Inc    - Suspect     - $4,000/mo × 12 = $48,000 × 10% = $4,800
---
Unweighted Total: $144,000
Weighted Total: $55,200  ← This is the honest forecast
```

## Forecast Ranges
- **Best Case:** Sum of all deals at 100% (assumes everything closes) — NEVER present this alone
- **Expected Case:** Weighted pipeline total — this is the DEFAULT forecast
- **Worst Case:** Only count deals in Negotiation+ stage at their weighted values

## Anti-Optimism Rules
1. NEVER count frozen deals in the active forecast
2. NEVER assume a deal will close faster than average velocity
3. NEVER upgrade a deal's probability just because the human "feels good" about it
4. ALWAYS show the gap between unweighted and weighted — the bigger the gap, the more optimistic the pipeline is
5. Track forecast accuracy: compare last month's forecast to actual revenue

## Output
```json
{
  "report_date": "2026-02-17",
  "total_deals": 15,
  "active_deals": 8,
  "frozen_deals": 4,
  "closed_won": 2,
  "closed_lost": 1,
  "unweighted_pipeline": 250000,
  "weighted_pipeline": 87500,
  "optimism_gap": "65% (pipeline is 65% optimistic)",
  "forecast": {
    "best_case": 250000,
    "expected_case": 87500,
    "worst_case": 42000
  },
  "by_stage": {
    "suspect": { "count": 3, "unweighted": 80000, "weighted": 8000 },
    "prospect": { "count": 2, "unweighted": 50000, "weighted": 12500 }
  }
}
```
