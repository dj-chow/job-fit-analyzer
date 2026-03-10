# Scoring Heuristics

These rules apply across ALL roles. Role-specific criteria layer on top of these.

## How the Score Works

The fit score is 0-100. It answers one question: "Based on what this person has done, how likely are they to succeed in this specific role?"

It does NOT measure:
- How well the resume is written (that's a separate assessment)
- Whether the candidate would accept the role
- Culture fit or soft skills beyond what's evidenced in work history
- Potential beyond demonstrated capability

## Score Calibration

| Range | What It Means | Hiring Outcome |
|---|---|---|
| 85-100 | Could step into this role and perform from week one. Direct experience in most core areas. Few or no gaps. | Phone screen, likely interview |
| 70-84 | Strong candidate with 1-2 manageable gaps. Would need some ramp time but has the foundation. | Phone screen, maybe interview |
| 55-69 | Mixed fit. Real strengths in some areas but real gaps in others. Would need significant support in gap areas. | Maybe pile. Depends on candidate pool. |
| 40-54 | Stretch candidate. Has related experience but this role would be a meaningful step-change. | Likely pass unless pool is thin |
| Below 40 | Poor fit. Limited overlap between what they've done and what the role needs. | Pass |

Important: a 72 means "strong with gaps." If the score feels high at first glance, check whether you're accounting for adjacent experience. A banking PM with 9 years of regulatory product work might feel like a stretch for an AI PM role, but the domain overlap is real. The score should reflect that overlap honestly, while the weakness section calls out the gap.

## Common Scoring Rules

### 1. Recency Weighting
- Experience from the last 3 years counts at full weight
- Experience from 3-7 years ago counts at roughly 70% weight
- Experience older than 7 years counts at roughly 40% weight
- Exception: foundational skills (leadership, stakeholder management) don't decay as fast as technical skills

### 2. Depth Over Breadth
- Owning an area scores higher than contributing to it
- 2 years of deep ownership beats 5 years of light exposure
- Look for evidence of progression within a skill area (went from contributing to owning)

### 3. Title vs Work Mismatch Handling
- When title doesn't match but work activities do, score based on the WORK, not the title
- Flag the mismatch explicitly in the Adjacent Work section
- Reduce confidence by one level when the only evidence comes from self-described LinkedIn content without corroboration from the resume

### 4. Corroboration Between Documents
- Same achievement described in both documents: highest confidence
- Achievement in one document only: reduce confidence slightly
- Conflicting information between documents: flag in hygiene check, use the more conservative claim for scoring

### 5. Metric Quality
- Specific metrics with context ("reduced processing time from 4 hours to 20 minutes") score higher than relative metrics ("improved efficiency by 80%")
- Any quantified outcome scores higher than unquantified claims
- Missing metrics don't automatically mean weak experience. Some domains (compliance, infrastructure) have fewer obvious metrics

### 6. Company Context Adjustment
- Scale matters. A PM at a 10-person startup did different work than a PM at Google. Neither is better, but the type of experience differs.
- Regulated industry experience transfers well to other regulated industries
- Startup experience transfers to startup roles. Enterprise experience transfers to enterprise roles. Cross-context transfers are possible but reduce confidence.

### 7. Dimension Scoring

Each role has 5-7 scored dimensions. For each dimension:

| Level | Score | What It Looks Like |
|---|---|---|
| Strong | 80-100 | Direct, recent, deep experience with clear outcomes |
| Solid | 60-79 | Good evidence but missing depth, recency, or outcomes |
| Partial | 40-59 | Adjacent experience or light direct exposure |
| Weak | 20-39 | Minimal relevant experience, mostly inferred |
| Gap | 0-19 | No meaningful evidence in either document |

### 8. Overall Score Calculation

The overall score is NOT a simple average of dimensions. It works like this:

1. Score each dimension for the role (using the role-specific criteria file)
2. Apply the weights defined in the role criteria
3. Calculate the weighted average
4. Apply a "critical gap penalty": if ANY dimension scores below 20, reduce the overall score by 10 points. Two or more gaps below 20 reduce by 20 points. This reflects reality: a single critical gap can disqualify a candidate regardless of other strengths.
5. Apply a "corroboration bonus": if 3+ dimensions are corroborated across both documents, add 3 points. This reflects the trust signal of consistency.

### 9. When to Override the Score

Sometimes the math produces a score that doesn't match reality. Override when:
- The candidate has a rare combination that's uniquely valuable for this role (score up)
- The candidate has a disqualifying gap that the dimensions don't fully capture (score down)
- The role has an unusual requirement that doesn't map to standard dimensions (adjust and explain)

Always explain overrides explicitly. Never silently adjust.
