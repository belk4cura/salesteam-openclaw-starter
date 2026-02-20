# Skill: Reciprocity Planning

## Purpose
Plan what "candy" (value, insight, content) to offer each stakeholder in exchange for their time, access, or information. Give before you get.

## Kent Summers' Rule
**"Don't spill your candy in the lobby."**
Meter out your value strategically. Every piece of insight you share should earn something in return — a meeting, access to a stakeholder, verification of budget, or timeline.

## The Give/Get Framework

### For Financial Buyers
**Give (Candy):**
- Admin productivity benchmark report (industry-specific)
- ROI calculator showing cost of admin time vs. Cura subscription
- Case study from a similar company in their industry
- Competitive analysis (Otter vs. Fireflies vs. Cura — honest comparison)

**Get (In Return):**
- Budget range confirmation
- Timeline for decision
- Number of potential seats
- Access to Technical Buyer for compatibility check

### For Technical Buyers
**Give (Candy):**
- Technical architecture overview (how Cura runs locally, privacy-first)
- Security whitepaper or compliance documentation
- Integration compatibility checklist
- Free trial or sandbox access

**Get (In Return):**
- Technical approval / no objections
- Infrastructure requirements sign-off
- Security review completion
- Integration testing participation

### For Operational Buyers (End Users)
**Give (Candy):**
- Free hands-on demo tailored to their specific workflows
- "Day in the life" comparison (with Cura vs. without)
- Templates for their most common post-meeting tasks
- Training plan showing minimal learning curve

**Get (In Return):**
- Confirmation that Cura solves their pain points
- Specific use cases from their daily work
- Internal advocacy to Financial Buyer
- Pilot participation commitment

### For Champions
**Give (Candy):**
- Make them look smart: provide talking points they can use with their boss
- Executive summary they can forward up the chain
- Internal proposal template they can customize
- Early access or beta features

**Get (In Return):**
- Introduction to Financial Buyer
- Internal meeting facilitation
- Org chart information
- Competitive intelligence (what else they're evaluating)

## Tracking
Log every give/get exchange in the deal record's `give_get_log` array:
```json
{
  "date": "2026-02-17",
  "stakeholder": "Jane Smith (COO)",
  "gave": "Admin productivity benchmark report for financial services",
  "got": "Confirmed budget of $5K/mo, introduced us to IT Director"
}
```

## Planning Output
For each prospect, create a reciprocity plan:
- What candy do we have ready for each stakeholder type?
- What do we need to get from each stakeholder?
- What's the sequence? (Who do we trade with first?)
- What candy do we need to CREATE? (Suggest content to the human)
