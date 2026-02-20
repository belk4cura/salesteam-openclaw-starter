# Skill: ICP Matching

## Purpose
Evaluate a company against the Ideal Customer Profile criteria and produce a match score.

## Process
1. Read the ICP config from `~/.openclaw/shared-canvas/icp-config.json`
2. For each company, evaluate against these criteria:

### Must-Have Criteria (each worth 15 points, total 60)
- **Industry match:** Is the company in one of the 6 target categories?
- **Employee range:** Does it have 10-500 employees?
- **Admin staff:** Does it appear to have 5+ admin/assistant roles?
- **Platform:** Is there evidence of Mac usage?

### Strong Signals (each worth 10 points, total 40)
- **Website exists:** Can we verify the company online?
- **Budget holder findable:** Can we identify a decision-maker by name?
- **Meeting-heavy culture:** Evidence of frequent meetings (Zoom/Teams subscriptions, calendar tool usage)?
- **Project management tools:** Evidence of Asana, Monday, ClickUp usage?

### Buying Triggers (bonus points, +5 each)
- Recently hired admin staff
- Job postings for admin/assistant roles
- Currently using Otter.ai, Fireflies, or similar
- Recent office expansion
- Using multiple Cura-integrated SaaS tools

### Disqualifiers (instant fail)
- Fewer than 10 employees total
- Windows-only environment
- Government entity
- Already a Cura customer
- No web presence
- Less than 2 years in business

## Output
```json
{
  "company_name": "...",
  "icp_match_score": 0-100,
  "icp_match_reasons": ["reason1", "reason2"],
  "disqualification_reasons": [],
  "status": "suspect | disqualified",
  "recommended_action": "qualify | disqualify | needs_more_research"
}
```
