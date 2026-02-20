# Skill: Contact Retrieval

## Purpose
Find verified contact information (email, phone, LinkedIn) for identified buyers.

## The Address Test (Kent Summers' Rule)
"If you can't find them, they aren't real suspects."

A suspect is only valid if you can find at least ONE contactable decision-maker. No contact info = disqualify.

## Methods (in priority order)

### 1. Email Pattern Detection
- Find the company's email pattern from existing public emails (e.g., first.last@company.com)
- Apply the pattern to the identified buyer's name
- Common patterns: first.last@, first@, flast@, firstl@

### 2. LinkedIn Profile
- Find the person's LinkedIn profile URL
- Note: Don't send LinkedIn messages (that's Off-Ramp's job)

### 3. Company Website Contact
- Check the company's Contact page for direct emails
- Check press releases or blog posts for author emails
- Check PDF documents hosted on the site (often contain contact info)

### 4. Web Search
- Search for "person_name company_name email"
- Search for the person's name in conference speaker lists, podcast guest lists
- Check industry directories

## Verification
- Domain must match the company's website domain
- If using email pattern detection, verify the domain accepts email (MX record check via exec)
- Mark confidence level: verified, inferred, or unverified

## Output
Update the contact record with:
```json
{
  "email": "verified_email@company.com",
  "email_confidence": "verified | inferred | unverified",
  "phone": "if found",
  "linkedin_url": "https://linkedin.com/in/...",
  "source": "how the contact info was found"
}
```
