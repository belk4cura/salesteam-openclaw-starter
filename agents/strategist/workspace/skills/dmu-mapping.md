# Skill: DMU Mapping

## Purpose
Map the Decision Making Unit for a prospect company — identify all people involved in the buying decision.

## The DMU Framework

### Financial Buyer (The Checkbook)
**Who:** The person who approves the budget for admin tools
**Signal titles:** COO, Managing Partner, VP/Director of Operations, Practice Administrator, Chief of Staff
**Key question they answer:** "Is this worth the money?"
**What they care about:** ROI, cost per seat, total cost of ownership, admin team productivity metrics
**Cura pitch angle:** "$200-500/mo per seat vs. $35K+/year for additional admin headcount"

### Technical Buyer (The Feasibility Check)
**Who:** The person who evaluates whether Cura works with existing systems
**Signal titles:** IT Director, CTO, Head of Technology, Systems Administrator
**Key question they answer:** "Will this work with our setup?"
**What they care about:** Mac compatibility, security, data privacy, integration requirements, SSO
**Cura pitch angle:** "Desktop-native macOS, runs locally (no cloud recording), integrates with your existing Asana/Gmail/Calendar"

### Operational Buyer (The End User)
**Who:** The admin staff who will actually use Cura
**Signal titles:** Executive Assistant, Office Manager, Practice Manager, Transaction Coordinator
**Key question they answer:** "Will this make my job easier?"
**What they care about:** Ease of use, time saved, reliability, learning curve
**Cura pitch angle:** "It runs invisibly during meetings and handles follow-ups you currently do manually"

### Champion (The Internal Advocate)
**Who:** The person who feels the admin pain most and will push for adoption
**Signal titles:** Senior EA, Office Manager (reporting to COO), Head of Administration
**Key question they answer:** "Will I look good for bringing this to the team?"
**What they care about:** Being seen as innovative, solving a visible problem, easy win
**Cura pitch angle:** "You'll be the person who freed up 10+ hours/week across the admin team"

## Research Process
1. Search LinkedIn for all employees at the prospect company
2. Categorize people by DMU role based on their titles
3. Identify reporting relationships where possible
4. Prioritize: Financial Buyer > Champion > Technical > Operational
5. Document findings in structured DMU map format

## Output Format
```json
{
  "company_name": "...",
  "lead_id": "lead-xxx",
  "dmu_map": {
    "financial_buyer": {
      "name": "...", "title": "...", "linkedin_url": "...",
      "status": "identified | contacted | engaged | champion",
      "pitch_angle": "..."
    },
    "technical_buyer": { "..." },
    "operational_buyer": { "..." },
    "champion": { "..." }
  },
  "coverage_score": "0-100 (% of DMU roles filled)",
  "gaps": ["missing technical buyer", "..."],
  "recommended_widening_approach": "..."
}
```
