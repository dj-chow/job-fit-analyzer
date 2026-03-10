---
name: job-fit-analyzer
description: Analyze job fit when a user uploads their resume and LinkedIn profile alongside a job description, or asks how well they match a role, or wants to know their strengths and gaps for a specific position, or asks "should I apply for this job." Triggers on any request involving candidate-to-job evaluation, career fit assessment, or application decision-making. This is NOT a keyword matcher — it evaluates actual work performed regardless of job titles.
---

# Job Fit Analyzer

Evaluate how well a candidate's actual experience matches a job — by analyzing the work they've done, not the titles they've held.

## What This Skill Does NOT Do

- **Not keyword matching.** ATS tools already do that. This analyzes the substance of experience.
- **Not resume rewriting.** This evaluates fit. It flags where the resume undersells the candidate, but does not rewrite it.
- **Not generic career advice.** Every output must be specific to this candidate and this job description.
- **Not biased toward any role type.** This works for engineering, product, design, marketing, sales, operations, data science, or any other function. Adapt your evaluation criteria to the role.

## Inputs Required

Before starting analysis, you MUST have all three:

1. **Resume** (PDF or text) — the candidate's current resume
2. **LinkedIn profile** (PDF or text) — the candidate's LinkedIn export
3. **Job description** (pasted text or PDF) — the target role

If any input is missing, ask for it before proceeding. Do not attempt a partial analysis.

## Analysis Process

Work through these stages in order. Do not skip stages or combine them.

### Stage 1: Decode the Job Description

Before looking at the candidate, understand what this role actually needs.

1. **Identify the role type** (engineering, product, design, marketing, sales, ops, data, etc.) and seniority level
2. **Extract the 5-7 core requirements** — not every bullet point, just the ones that would actually determine a hire/no-hire decision. Distinguish between stated requirements and implied ones (e.g., "fast-paced environment" implies comfort with ambiguity and rapid prioritization)
3. **Identify the archetype** — what kind of person would the hiring manager be thrilled to hire? What's their ideal background? What company or role would they be coming from?
4. **Determine evaluation criteria for this role type.** Load [references/role-evaluation.md](references/role-evaluation.md) for guidance on how evaluation criteria differ across engineering, PM, design, marketing, sales, ops, and data roles. Apply the relevant criteria.
5. **Note the company context** — stage (startup/growth/enterprise), industry, and any signals about team structure or culture

### Stage 2: Extract Candidate Experience

Read both the resume and LinkedIn profile thoroughly. Your goal is to understand what this person has actually DONE, not what their titles say.

1. **Map their career trajectory** — roles, companies, durations, progression pattern
2. **Decompose each role into work activities.** Load [references/activity-framework.md](references/activity-framework.md) for the activity decomposition framework. Categorize what they did into: Strategic, Discovery, Definition, Execution, Growth, Technical, and Communication work.
3. **Identify where title and work diverge.** Use the title-to-work mismatch patterns in the activity framework reference. A "Solutions Architect" who prioritized backlogs and defined requirements was doing product management. A "Business Analyst" who built data pipelines was doing data engineering. Surface these.
4. **Corroborate across both documents.** LinkedIn often has richer context (descriptions, recommendations, activity). Resume may be sparse. Use LinkedIn to fill gaps in understanding, and note where the two documents tell different stories.
5. **Separate the person from their resume.** A poorly written resume does not mean a poor candidate. If the resume is vague but LinkedIn reveals strong, specific experience — the person is stronger than their resume suggests. Flag this.

### Stage 3: Evaluate Fit

Now map the candidate to the job. This is activity-level matching, not title matching.

For each of the 5-7 core requirements from Stage 1:

1. **Search for direct evidence** — did the candidate do this exact work?
2. **Search for adjacent evidence** — did they do work that develops the same underlying capability? (e.g., running A/B tests in marketing = experimentation capability relevant to a growth PM role)
3. **Assess depth** — did they own this work or contribute to it? How recently? For how long?
4. **Assign a confidence level:**
   - **Strong Match** — direct, recent evidence from their career with demonstrated outcomes
   - **Partial Match** — adjacent evidence, or direct evidence that's older/less deep
   - **Gap** — no meaningful evidence found in either document

### Stage 4: Generate the Analysis

Produce ALL of the following sections. Do not skip any.

---

## Output Format

### 1. Fit Score and Headline

**Score: X/100**

Provide a single score with a one-sentence headline summarizing the fit. The score reflects the candidate's actual capability match, not their resume presentation quality.

Calibration guide:
- **85-100:** Strong fit. Candidate could credibly perform this role based on demonstrated experience.
- **70-84:** Solid fit with manageable gaps. A good candidate who would need to close 1-2 specific areas.
- **50-69:** Partial fit. Real strengths in some areas but significant gaps in others.
- **30-49:** Stretch candidate. Adjacent experience exists but major capability gaps.
- **Below 30:** Poor fit. Limited overlap between experience and role requirements.

### 2. Requirements Map

A table mapping each core job requirement to the candidate's experience:

| Requirement | Evidence From Candidate | Confidence | Source |
|---|---|---|---|
| [Requirement from JD] | [Specific experience that maps to this] | Strong / Partial / Gap | Resume / LinkedIn / Both |

For each row, be specific. Don't say "has relevant experience." Say "Led 8-person team at BMO delivering risk reporting platform, directly parallel to the cross-functional leadership this role requires."

### 3. Adjacent Work Recognition

This is the highest-value section. Identify 2-4 instances where the candidate performed work relevant to this role under a different title or in a different context.

For each instance:
- **What their title said:** [Official title]
- **What they actually did:** [The work activity, described in the target role's language]
- **Why it matters for this role:** [How this experience directly maps to a core requirement]
- **Strength of evidence:** [How confident are you in this translation — strong, moderate, or speculative]

If the candidate's career is a straight line to this role with matching titles, say so and skip this section.

### 4. What the Hiring Manager Is Thinking

Write 4-6 sentences of internal monologue from the perspective of the hiring manager reading this candidate's application. This should be honest, specific, and reflect the psychology of someone scanning resumes under time pressure.

Consider:
- What grabs their attention in the first 7 seconds?
- What makes them pause or feel uncertain?
- What biases might be at play (company prestige halo, title mismatch skepticism, industry familiarity)?
- Would this resume survive a 7-second scan, or does the candidate's real strength require deeper reading?
- Does the career trajectory "make sense" at a glance?

Be direct. If the hiring manager would think "Why is a bank person applying for this?" — say that. Then explain what they'd think if they read deeper.

### 5. Biggest Weakness + Flip Strategy

Identify the single biggest concern a hiring manager would have about this candidate for this specific role. Be blunt — name it clearly.

Then provide a concrete flip strategy:
- How can the candidate reframe this concern in their cover letter or interview?
- What specific evidence from their background partially addresses it?
- What would a strong 2-sentence response sound like if asked about this in an interview?

### 6. Top 3 Strongest Stories

Identify the 3 most compelling experiences from the candidate's background for THIS specific role (not their 3 best accomplishments in general).

For each story:
- **The experience** (1-2 sentences)
- **Why it resonates for this role** (which specific requirement it addresses)
- **The hook** (what makes this memorable — a metric, an unexpected outcome, a scale indicator)

Pull from whichever document has the richer detail. If LinkedIn has more context than the resume, use that.

### 7. Hygiene Check

Cross-reference the resume and LinkedIn profile for inconsistencies. Load [references/hygiene-checks.md](references/hygiene-checks.md) for the full list of patterns to check.

Check for:
- Date mismatches (start/end dates that don't align)
- Title discrepancies (inflated or different titles between documents)
- Missing roles (appears on one document but not the other)
- Metric inconsistencies (different numbers for the same achievement)
- Education mismatches (degrees, dates, institutions)

For each inconsistency found:
- **What conflicts:** [Specific discrepancy]
- **Risk level:** High (looks dishonest) / Medium (looks careless) / Low (minor formatting difference)
- **Recommendation:** What to fix and why

If no inconsistencies are found, explicitly state that the documents are consistent. This is a positive signal worth noting.

### 8. Resume Narrative Assessment

This section evaluates the resume AS A DOCUMENT — separately from the candidate's actual fit.

Flag issues like:
- Responsibilities listed instead of outcomes
- Vague language where specifics exist (check LinkedIn for the specifics)
- Missing quantification on impactful work
- Burying strong experience below weaker content
- Generic bullets that could apply to anyone

Rate the resume narrative: **Strong / Adequate / Underselling**

If underselling: list the 2-3 highest-impact improvements that would better represent the candidate's actual experience. Reference specific LinkedIn details that could strengthen specific resume bullets.

**Important:** This assessment does NOT affect the fit score. A candidate with a poorly written resume but strong LinkedIn-evidenced experience still gets a high fit score. The resume assessment is a separate improvement opportunity.

---

## Tone and Calibration

- Be direct and specific. Never use filler phrases like "demonstrates a strong background in" or "possesses excellent skills."
- Every claim must reference a specific piece of evidence from the candidate's documents.
- When uncertain, say so. "LinkedIn suggests X but the resume doesn't confirm it" is more useful than a confident guess.
- Calibrate honestly. Not every candidate is a strong fit, and saying so is more valuable than false encouragement.
- Adapt your language to the role type. Use engineering terminology for engineering roles, product language for PM roles, etc.
