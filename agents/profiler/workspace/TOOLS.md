# Tools Guide

## Primary Tools

### web_search
Use for: Finding companies in target industries, searching for specific job titles on LinkedIn, finding company information
Best practices:
- Search by industry + geography + company size
- Search for job postings (indicates admin hiring = buying trigger)
- Search for competitors' customers (they know the category)

### web_fetch
Use for: Scraping company websites to verify size, industry, and tech stack
Best practices:
- Check the "About" page for employee count and industry
- Check the "Team" or "Leadership" page for decision-maker names
- Check the careers page for admin hiring signals

### browser
Use for: LinkedIn research, navigating complex company websites
Best practices:
- Search LinkedIn for companies matching ICP criteria
- Look at employee lists to count admin/assistant roles
- Check if the company uses Mac (look for IT job postings mentioning macOS)

### exec
Use for: Processing and storing lead data, running scripts
Best practices:
- Use `jq` to manipulate JSON data files
- Use scripts to deduplicate and merge lead records
- Keep data files clean and well-structured

### sessions_send
Use for: Handing off qualified suspects to the Off-Ramp agent
Best practices:
- Always include the full Lead Record JSON
- Send in batches of 5-10 suspects at a time
- Include a summary of the batch (count, top industries, key findings)

## Data Files
- `data/suspects.json` — Qualified suspects (append-only, keep growing)
- `data/disqualified.json` — Disqualified leads with reasons
- `data/raw-leads.json` — Incoming unprocessed leads
- `canvas/icp-config.json` — ICP criteria (read from shared-canvas)

## File Editing — IMPORTANT

When you need to edit files (like JSON data files), use the `exec` tool with shell commands:

### To write a new file:
```bash
cat > data/suspects.json << 'EOF'
[{"id": "lead-001", "company": {"name": "Example Corp"}}]
EOF
```

### To update a JSON file:
```bash
# Read, modify, write back using jq
jq '.key = "new_value"' data/file.json > /tmp/tmp.json && mv /tmp/tmp.json data/file.json
```

### To append to a JSON array:
```bash
jq '. += [{"id": "new-item"}]' data/suspects.json > /tmp/tmp.json && mv /tmp/tmp.json data/suspects.json
```

### DO NOT use the `edit` tool with `newText` or `new_string` parameters — use `exec` with shell commands instead.
