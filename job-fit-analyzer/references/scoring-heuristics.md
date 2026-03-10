# Scoring Heuristics

These rules apply across ALL roles. Role-specific criteria layer on top of these.

## Two-Layer Evaluation Model

This tool uses a two-layer model that mirrors how hiring actually works:

**Layer 1 - Screen Check (Will you get past the filter?)**
Hiring managers and recruiters screen on hard requirements first. If a JD says "2+ years managing a decision engine" and you have zero, you're filtered out before anyone reads your stakeholder alignment stories. The screen check catches this.

**Layer 2 - Fit Score (How well do you match the role?)**
Once past the screen, dimensional scoring evaluates how strong a candidate you are. This is the deeper analysis of capability, experience depth, and transferable skills.

Both layers run for every analysis. Even if the screen check says "Likely Filtered Out," the fit score still runs because it powers the roadmap and improvement actions. But the output is honest about the screening barrier.

## Layer 1: Screen Check

### What Makes a Requirement "Hard"

Hard gate requirements are specific, verifiable, and non-negotiable. They're the things a recruiter checks before reading the rest of the resume.

**Hard gates** have these characteristics:
- Name specific tools, platforms, or technologies ("Taktile," "FICO Blaze," "Salesforce," "Python")
- Name specific domains or product types ("MCA lending," "decision engines," "healthcare claims")
- Require specific certifications or clearances ("CPA required," "Secret clearance")
- Use non-negotiable language ("must have," "required," "minimum X years of [specific thing]")
- Can be answered with a yes/no question: "Have you managed a decision engine for 2+ years?"

**Soft signals** are everything else:
- General competencies ("strong analytical skills," "excellent communication")
- Broad experience requirements ("5+ years of product management experience")
- Cultural fit indicators ("fast-paced environment," "collaborative team player")
- Qualities assessed on a spectrum, not binary

### Classification Rules

When reading a JD, extract requirements and classify each one:

1. **If the requirement names a specific tool, platform, domain, or certification** and the JD uses "required" or "must have" language (explicit or implied): it's a Hard Gate.
2. **If the requirement describes a general competency** that most candidates in this role type would have at some level: it's a Soft Signal.
3. **If the requirement is specific but listed under "nice to have" or "preferred"**: it's a Soft Signal, not a Hard Gate.
4. **Years of general experience** (e.g., "5+ years PM experience") are Soft Signals. **Years of specific experience** (e.g., "2+ years managing a decision engine") are Hard Gates.
5. When in doubt, ask: "Would a recruiter auto-reject a candidate who is missing ONLY this one thing?" If yes, it's a Hard Gate.

Most JDs have 1-3 hard gates and 5-10 soft signals. Some JDs have zero hard gates (all general competencies). Flag when a JD has no hard gates - the screen check will show "No hard gates identified."

### Checking Each Hard Gate

For each hard gate requirement, check the candidate's resume and LinkedIn:

| Verdict | Criteria |
|---|---|
| **Pass** | Clear, direct evidence. The candidate has done this specific thing. Not adjacent, not inferred. |
| **Partial** | Adjacent experience that builds similar capability but isn't the exact thing. Or the exact thing but too old (7+ years) or too shallow (exposure, not ownership). |
| **Fail** | No evidence of direct or meaningfully adjacent experience. |

Be strict on Pass. "Worked with data teams" does not pass a "Python required" gate. "Built SQL pipelines" does not pass a "decision engine experience" gate. Adjacent is Partial, not Pass.

### Screen Verdict

Based on the hard gate results, produce one of three verdicts:

| Verdict | When to Use | What It Means |
|---|---|---|
| **Likely Passes Screen** | All hard gates Pass, or at most 1 Partial with strong adjacent evidence | This candidate would probably survive initial recruiter/hiring manager screening |
| **Borderline** | 1 hard gate Fail with strong adjacent evidence that a thoughtful recruiter might accept, or 2+ Partials | Could go either way. Depends on the recruiter, the pool, and how well the candidate frames their adjacent experience |
| **Likely Filtered Out** | 2+ hard gate Fails, or 1 Fail on a requirement that defines the role (e.g., the tool the entire job revolves around) | This candidate would probably be screened out before reaching a human evaluator, or rejected in the first 30 seconds of human review |

### How Screen Verdict Affects the Analysis

The screen verdict does NOT change the fit score calculation. Both layers are independent. But the screen verdict changes how the output is framed:

- **Likely Filtered Out**: The analysis leads with the screening barrier. The fit score is labeled "Fit Score (if screened in)" to make clear it's conditional. The roadmap prioritizes closing the hard gate gaps, not the dimensional gaps.
- **Borderline**: The analysis acknowledges the screening risk upfront. The fit score runs normally. The weakness section focuses on the borderline hard gate.
- **Likely Passes Screen**: Standard output. No special screening caveat needed.

## Layer 2: Fit Score

The fit score is 0-100. It answers one question: "Based on what this person has done, how likely are they to succeed in this specific role?"

It does NOT measure:
- How well the resume is written (that's a separate assessment)
- Whether the candidate would accept the role
- Culture fit or soft skills beyond what's evidenced in work history
- Potential beyond proven capability
- Whether the candidate will pass the initial screen (that's Layer 1)

## Score Calibration

| Range | What It Means | Hiring Outcome (assumes screen is passed) |
|---|---|---|
| 85-100 | Could step into this role and perform from week one. Direct experience in most core areas. Few or no gaps. | Phone screen, likely interview |
| 70-84 | Strong candidate with 1-2 manageable gaps. Would need some ramp time but has the foundation. | Phone screen, maybe interview |
| 55-69 | Mixed fit. Real strengths in some areas but real gaps in others. Would need significant support in gap areas. | Maybe pile. Depends on candidate pool. |
| 40-54 | Stretch candidate. Has related experience but this role would be a meaningful step-change. | Likely pass unless pool is thin |
| Below 40 | Poor fit. Limited overlap between what they've done and what the role needs. | Pass |

Important: the fit score assumes the candidate has gotten past the screen. A fit score of 72 with a screen verdict of "Likely Filtered Out" means "strong candidate who will probably never get the chance to prove it." That's a very different situation from a 72 with "Likely Passes Screen."

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
