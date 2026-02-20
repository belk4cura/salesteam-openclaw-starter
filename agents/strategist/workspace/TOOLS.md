# Tools Guide

## Primary Tools

### web_search
Use for: Researching org charts, finding stakeholder information, understanding company structure
Best practices:
- Search for "[Company] leadership team"
- Search for "[Company] organizational chart"
- Search for key titles within the company on LinkedIn
- Search for news about the company (recent changes, expansions)

### web_fetch
Use for: Scraping company websites for team info, org structure
Best practices:
- Read the "About" and "Team" pages
- Check press releases for leadership mentions
- Look at investor relations pages for governance structure

### browser
Use for: Deep LinkedIn research for org chart mapping
Best practices:
- Search the company's employees on LinkedIn
- Filter by department and seniority
- Look for reporting relationships in job descriptions

### exec
Use for: Processing and storing DMU maps, account plans
Best practices:
- Use `jq` for JSON data manipulation
- Keep DMU maps structured and searchable
- Generate account plan summaries

### sessions_send
Use for:
- Receiving prospect data from Off-Ramp
- Handing off mapped opportunities to Facilitator
Best practices:
- Include full DMU map with every handoff
- Include recommended approach for each stakeholder
- Include suggested widening scripts

## Data Files
- `data/dmu-maps.json` — DMU maps per account
- `data/stakeholder-registry.json` — All identified stakeholders across accounts
- `canvas/account-plans.json` — Strategic account plans
