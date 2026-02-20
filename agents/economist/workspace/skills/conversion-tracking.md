# Skill: Conversion Rate Tracking

## Purpose
Monitor conversion rates between pipeline stages to identify where deals are dropping off and why.

## Conversion Funnel
```
Raw Leads → Suspects → Prospects → Discovery → Proposal → Negotiation → Closed Won
   100%       ?%          ?%          ?%          ?%          ?%           ?%
```

## Key Metrics

### Stage Conversion Rates
For each stage transition, calculate:
```
Conversion Rate = (Number entering next stage / Number entering this stage) × 100
```

### Drop-Off Rate
```
Drop-Off Rate = 100% - Conversion Rate
```

### Velocity (Days per Stage)
```
Average Days in Stage = Sum of days each deal spent in stage / Number of deals
```

## Benchmarks (Starting targets — adjust based on actual data)
| Transition | Target Rate | Red Flag |
|-----------|-------------|----------|
| Lead → Suspect | 30-50% | Below 20% = ICP too broad |
| Suspect → Prospect | 10-20% | Below 5% = Outreach not working |
| Prospect → Discovery | 50-70% | Below 30% = DMU mapping issues |
| Discovery → Proposal | 40-60% | Below 25% = Value prop not landing |
| Proposal → Negotiation | 50-70% | Below 30% = Pricing issues |
| Negotiation → Closed Won | 60-80% | Below 40% = Closing issues |

## Diagnosis

### Low Lead → Suspect Rate
**Problem:** Profiler is bringing in too many unqualified leads
**Fix:** Tighten ICP criteria, add more disqualifiers, focus on higher-density categories

### Low Suspect → Prospect Rate
**Problem:** Outreach isn't resonating, or contacts aren't reachable
**Fix:** Review Off-Ramp message templates, verify contact data quality, test different messaging

### Low Prospect → Discovery Rate
**Problem:** Interested prospects aren't converting to real conversations
**Fix:** Review Strategist's widening approach, check if we're multi-threading enough

### Low Discovery → Proposal Rate
**Problem:** Value proposition isn't landing in conversations
**Fix:** Review meeting prep quality, check if demos are being given too early (candy in the lobby)

### Low Proposal → Close Rate
**Problem:** Pricing objections, competitive losses, or decision-maker not engaged
**Fix:** Check DMU coverage (is Financial Buyer engaged?), review pricing strategy, check competitive positioning

### High Velocity (Too many days in a stage)
**Problem:** Deals are stalling
**Fix:** Check Freezer management, review follow-up cadence, consider more aggressive off-ramping

## Output
```json
{
  "report_date": "2026-02-17",
  "period": "monthly",
  "funnel": {
    "leads": 100,
    "suspects": 35,
    "prospects": 8,
    "discovery": 5,
    "proposal": 3,
    "negotiation": 2,
    "closed_won": 1
  },
  "conversion_rates": {
    "lead_to_suspect": 35,
    "suspect_to_prospect": 22.8,
    "prospect_to_discovery": 62.5,
    "discovery_to_proposal": 60,
    "proposal_to_negotiation": 66.7,
    "negotiation_to_close": 50,
    "overall_lead_to_close": 1
  },
  "velocity_days": {
    "suspect": 5,
    "prospect": 8,
    "discovery": 12,
    "proposal": 7,
    "negotiation": 10,
    "total_cycle": 42
  },
  "bottleneck": {
    "stage": "discovery",
    "issue": "Deals spending 12 days avg in discovery (target: 7)",
    "recommendation": "Check if Strategist DMU mapping is complete before entering discovery"
  }
}
```
