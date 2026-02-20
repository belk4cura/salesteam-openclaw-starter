# Skill: COCA Calculation

## Purpose
Calculate the Cost of Customer Acquisition — the total cost to acquire one new customer.

## Formula
```
COCA = Total Sales & Marketing Spend / Number of New Customers Acquired
```

## What Counts as Spend
- **Software/Tools:** CRM, outreach tools, Cura's own costs, OpenClaw/API costs
- **Advertising:** Any paid ads, sponsored content, event sponsorships
- **Human Time:** Founder's time on sales (estimated hourly rate × hours spent)
- **Content:** Cost of creating sales materials, case studies, benchmark reports
- **Travel:** Any in-person meeting costs

## What Counts as a New Customer
- A company that signs a paid contract (not a trial, not a pilot unless it converts)
- Count by company, not by seat

## Tracking
Maintain a spend log in `data/spend-log.json`:
```json
{
  "entries": [
    {
      "date": "2026-02-17",
      "category": "software | advertising | human_time | content | travel | other",
      "description": "OpenClaw API costs for February",
      "amount": 150.00
    }
  ],
  "monthly_totals": {
    "2026-02": { "total": 1500, "breakdown": { "software": 500, "human_time": 800, "content": 200 } }
  }
}
```

## Reporting
- Calculate COCA monthly
- Track COCA trend over time (is it going up or down?)
- Compare to customer lifetime value (LTV) — COCA should be < LTV/3
- For Cura at $300/mo average, annual LTV ≈ $3,600. Target COCA < $1,200.

## Kent Summers' Rule
**"Yield more than $1 of cash flow for every $1 spent."**
If COCA > customer revenue in first 3 months, something is wrong. Either:
1. Spending too much on the wrong channels
2. Conversion rates are too low (fix the pipeline)
3. Targeting the wrong ICP (fix the Profiler)
