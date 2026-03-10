# Job Fit Analyzer

A Claude skill that evaluates how well your experience matches a job — by analyzing the work you've actually done, not just your titles and keywords.

## The Problem

Most job fit tools are glorified keyword matchers. They check if your resume contains the same words as the job description and call it a "match score." This fails in two critical ways:

1. **It misses adjacent experience.** A Solutions Architect who spent 3 years prioritizing backlogs, defining requirements, and aligning stakeholders was doing Product Management — but a keyword matcher would never flag that.
2. **It penalizes bad resumes, not bad candidates.** A candidate who undersells their experience on paper still has that experience. The tool should evaluate the person, not just their document.

If you've ever felt "I've done this work, just not under that exact title" — this tool is for you.

## The Solution

Upload your resume and LinkedIn profile, paste a job description, and get an 8-section analysis that evaluates your actual work history against what the role needs.

The skill works for **any role type** — engineering, product, design, marketing, sales, operations, data science — and adapts its evaluation criteria based on what actually matters for that function.

### What You Get

| Section | What It Does |
|---|---|
| **Fit Score + Headline** | 0-100 score with a one-sentence assessment calibrated to the role |
| **Requirements Map** | Every key requirement mapped to your specific experience with confidence levels |
| **Adjacent Work Recognition** | Identifies where you did the job's work under a different title |
| **What the Hiring Manager Is Thinking** | Honest internal monologue from the person reading your application |
| **Biggest Weakness + Flip Strategy** | The #1 concern a hiring manager would have, plus how to address it |
| **Top 3 Strongest Stories** | Your most compelling experiences for this specific role |
| **Hygiene Check** | LinkedIn vs resume inconsistencies that could raise red flags |
| **Resume Narrative Assessment** | Where your resume undersells you (scored separately from fit) |

## Demo

Here's a snippet from a [full sample analysis](examples/sample-output.md) — a banking PM applying for an AI PM role at a fintech startup:

> **Score: 72/100**
>
> Strong regulatory and risk domain expertise with demonstrated product ownership, but limited direct AI/ML product experience and no startup experience — a candidate who knows the problem space deeply but would need to adapt to the pace and technical depth this role demands.

**Adjacent Work Recognition:**
> **"Solutions Architect" = Product Manager (3 years)**
> The candidate's Solutions Architect role was product management work under a different title. Evidence: investigated recurring issues by mapping end-to-end workflows, led cross-team working sessions to align stakeholders on problem definitions, decomposed regulatory requirements into implementable use cases with acceptance criteria...

**What the Hiring Manager Is Thinking:**
> "Nine years at one bank — interesting. Loyal, or stuck? The regulatory experience is exactly what we need, nobody else in the pipeline will know FRTB like this person. But I need someone who can work with our ML team day-to-day..."

[See the full sample output →](examples/sample-output.md)

## How to Use

### Prerequisites
- A Claude account (Free, Pro, or Team plan)

### Setup — Claude Web (claude.ai)

1. Download this repo as a ZIP (Code → Download ZIP)
2. Go to [claude.ai](https://claude.ai) → Settings → Customize → Skills
3. Click "+" → Upload a skill
4. Upload the `job-fit-analyzer` folder as a ZIP file
5. Start a new conversation, upload your resume PDF + LinkedIn PDF, paste a job description, and ask Claude to analyze your fit

### Setup — Claude Code

1. Clone this repo
2. Copy the `job-fit-analyzer/` folder to `~/.claude/skills/`
3. In any Claude Code session, the skill activates when you provide a resume, LinkedIn profile, and job description

```bash
git clone https://github.com/dj-chow/job-fit-analyzer.git
cp -r job-fit-analyzer/job-fit-analyzer ~/.claude/skills/
```

### Example

**Input:**
- Resume PDF
- LinkedIn PDF
- Pasted job description

**Output:**
An 8-section structured analysis ([see full example](examples/sample-output.md))

## How It Works

The skill runs a 4-stage analysis pipeline:

1. **Decode the JD** — Extracts the 5-7 requirements that actually determine hire/no-hire, identifies the ideal candidate archetype, and calibrates evaluation criteria to the role type (what matters for a PM role is different from what matters for a data engineer)
2. **Extract candidate experience** — Reads both documents and decomposes each role into 7 work activity categories (Strategic, Discovery, Definition, Execution, Growth, Technical, Communication) rather than relying on job titles
3. **Evaluate fit** — Maps requirements to experience at the activity level, searching for both direct and adjacent evidence. Assigns confidence levels (Strong Match / Partial Match / Gap) with specific citations
4. **Generate analysis** — Produces all 8 output sections, including the hiring manager perspective and weakness flip strategy

The skill loads [reference files](job-fit-analyzer/references/) on demand for role-specific evaluation criteria, the activity decomposition framework, and hygiene check patterns.

## Tradeoffs and Decisions

**Why activity-based matching instead of keyword matching:**
Keywords tell you if someone's resume contains the right words. Activities tell you if they've done the right work. A "Business Analyst" who built SQL pipelines and data models has data engineering experience — even if "data engineer" never appears on their resume. This approach catches transferable experience that keyword matching systematically misses. The tradeoff is that it requires Claude to reason about the substance of each role, which means analysis takes longer and costs more tokens than a simple keyword scan.

**Why resume quality is scored separately from fit:**
A poorly written resume doesn't mean a poor candidate. Many strong professionals undersell their experience because they describe what they were responsible for, not what they achieved. By separating "how good is this person for the role" from "how well does their resume communicate that," we give candidates actionable feedback on both dimensions without conflating them.

**Why the "What the Hiring Manager Is Thinking" section exists:**
Most candidates have never sat on the other side of the hiring table. They don't know that resume review is a 7-second pattern-matching exercise under cognitive load, or that a title mismatch can put them in the reject pile before their experience is even read. Surfacing this perspective helps candidates understand not just their gaps, but how their application is being processed.

## What I Learned

**Titles are a terrible proxy for work.** While building the title-to-work mismatch mapping, I found at least 14 common job titles where the actual work performed regularly diverges from what the title implies. The "Solutions Architect to PM" pipeline is one example, but it happens across every function. This has real consequences — ATS systems filter on titles, so candidates doing PM work under an architect title may never reach a human reviewer.

**Evaluation criteria vary dramatically across roles.** Engineering hires are evaluated primarily on technical depth and system scale. PM hires are evaluated on decision quality under uncertainty. Sales hires live and die by quota attainment numbers. A generic "fit score" that doesn't account for these differences is misleading. The skill needed role-specific calibration to produce honest assessments.

**The hardest section to get right was "What the Hiring Manager Is Thinking."** It's easy to make it either too generic ("looks like a strong candidate") or too harsh ("instant reject"). The right calibration is honest but specific — naming the exact moment of hesitation, the bias that triggers it, and what would change the hiring manager's mind.

## Next Steps

- [ ] Resume customizer mode — take the fit analysis and rewrite the resume for the job without fabricating experience
- [ ] Batch mode — analyze multiple postings and rank by fit to prioritize applications
- [ ] Spider graph visualization — plot the 5 key skills for the role (ideal vs candidate) for instant visual gap analysis
- [ ] Claude Code slash command wrapper for `/job-fit` invocation

## Built With

- [Claude](https://claude.ai) — powers the analysis engine via the Claude skill system
- Research from O*NET occupational frameworks, recruiter evaluation studies, and hiring manager psychology literature

---

Built by [Dheeraj Chowdhary](https://www.linkedin.com/in/dheerajchowdhary) | [GitHub](https://github.com/dj-chow)
