# Job Fit Analyzer

A Claude skill that tells you how well your experience matches a job. It looks at the work you've actually done, not just your titles and keywords.

## The Problem

Most job fit tools are keyword matchers. They check if your resume has the same words as the job description. Then they call it a "match score." This fails two ways:

1. **It misses adjacent experience.** A Solutions Architect who spent 3 years running backlogs, writing requirements, and aligning stakeholders was doing Product Management. A keyword matcher would never catch that.
2. **It punishes bad resumes, not bad candidates.** Someone who undersells their experience on paper still has that experience. The tool should evaluate the person, not just their document.

If you've ever thought "I've done this work, just not under that title," this tool is for you.

## The Solution

Upload your resume and LinkedIn profile. Paste a job description. Get an 8-section analysis that evaluates your real work history against what the role needs.

The skill launches with **4 calibrated roles** (Product Management, AI/ML PM, Software Engineering, Business Analysis) with transparent scoring criteria. Each role has weighted dimensions, level descriptions, and calibration notes. You can see exactly how the score is calculated.

### What You Get

| Section | What It Does |
|---|---|
| **Fit Score + Headline** | 0-100 score with a one-sentence assessment, calibrated to the role type |
| **Dimension Scores** | Weighted breakdown showing exactly where you're strong and where you're not |
| **Requirements Map** | Every key requirement mapped to your specific experience with confidence levels |
| **Adjacent Work Recognition** | Finds where you did the job's work under a different title |
| **What the Hiring Manager Is Thinking** | Honest internal monologue from the person reading your application |
| **Biggest Weakness + Flip Strategy** | The #1 concern a hiring manager would have, plus how to address it |
| **Top 3 Strongest Stories** | Your most compelling experiences for this specific role |
| **Hygiene Check** | LinkedIn vs resume inconsistencies that could raise red flags |
| **Resume Narrative Assessment** | Where your resume undersells you (scored separately from fit) |

## Demo

Here's a snippet from a [full sample analysis](examples/sample-output.md). A banking PM applying for an AI PM role at a fintech startup:

> **Score: 44/100**
>
> A strong product operator who knows regulated financial systems inside out. But the AI gap is real. This candidate has never shipped an AI product, never written evals, and never worked directly with ML engineers.

**Adjacent Work Recognition:**
> **"Solutions Architect" at BMO (2021-2024) = Product Manager**
> Title says architect. Work says PM. This person investigated recurring issues by mapping end-to-end workflows across systems. They led cross-team sessions to align stakeholders on problem definitions...

**What the Hiring Manager Is Thinking:**
> "Nine years at one bank. Okay, loyal or stuck? Let me scan. Product Owner, Solutions Architect, Delivery Lead. None of these scream AI PM. The regulatory angle is interesting though..."

[See the full sample output](examples/sample-output.md)

## How to Use

### Prerequisites
- A Claude account (Free, Pro, or Team plan)

### Setup for Claude Web (claude.ai)

1. Download this repo as a ZIP (Code > Download ZIP)
2. Go to [claude.ai](https://claude.ai) > Settings > Customize > Skills
3. Click "+" then "Upload a skill"
4. Upload the `job-fit-analyzer` folder as a ZIP
5. Start a new conversation, upload your resume PDF + LinkedIn PDF, paste a job description, and ask Claude to analyze your fit

### Setup for Claude Code

1. Clone this repo
2. Copy the `job-fit-analyzer/` folder to `~/.claude/skills/`
3. The skill activates when you provide a resume, LinkedIn profile, and job description

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
A structured analysis with dimension scores, requirements mapping, and actionable insights ([see full example](examples/sample-output.md))

## How It Works

The skill runs a 4-stage analysis:

1. **Decode the JD.** Pulls out the 5-7 requirements that actually determine hire/no-hire. Identifies the ideal candidate profile. Loads role-specific scoring criteria.
2. **Extract candidate experience.** Reads both documents. Breaks each role into 7 work activity categories (Strategic, Discovery, Definition, Execution, Growth, Technical, Communication) instead of relying on titles.
3. **Score and evaluate.** Scores each dimension from the role criteria file. Calculates the weighted score with gap penalties and corroboration bonuses. Maps requirements to evidence.
4. **Generate analysis.** Produces all output sections including the hiring manager perspective and weakness flip strategy.

### Scoring Infrastructure

The scoring system is transparent and auditable. Anyone can look under the hood:

```
job-fit-analyzer/references/
├── roles.md                         # Which roles are supported
├── scoring-heuristics.md            # Common scoring rules across all roles
├── role-criteria/
│   ├── product-management.md        # PM scoring: 5 weighted dimensions
│   ├── ai-product-management.md     # AI PM scoring: 6 weighted dimensions
│   ├── engineering.md               # Engineering scoring: 5 weighted dimensions
│   └── business-analysis.md         # BA/BSA scoring: 5 weighted dimensions
├── activity-framework.md            # Work activity categories + title mapping
└── hygiene-checks.md                # LinkedIn vs resume check patterns
```

Each role criteria file defines:
- The core question the role answers
- 5-6 scored dimensions with specific weights
- Level descriptions (Strong/Solid/Partial/Weak/Gap) with numeric ranges
- Seniority calibration notes
- Common scoring traps to avoid

## Tradeoffs and Decisions

**Why activity-based matching instead of keyword matching:**
Keywords tell you if a resume has the right words. Activities tell you if the person has done the right work. A "Business Analyst" who built SQL pipelines and data models has data engineering experience, even if "data engineer" never shows up on their resume. This catches transferable experience that keyword matching systematically misses. The tradeoff: Claude needs to reason about each role's substance, so analysis takes longer and uses more tokens than a keyword scan.

**Why resume quality is scored separately from fit:**
A bad resume doesn't mean a bad candidate. Many strong professionals undersell their experience because they list responsibilities instead of outcomes. Separating "how good is this person for the role" from "how well does their resume show that" gives candidates feedback on both without mixing them up.

**Why only 4 roles at launch:**
We could have launched with 10+ roles using generic criteria. But generic scoring produces generic results. Each role has different signals that matter (engineers get evaluated on technical depth, PMs on decision quality, BAs on requirements engineering). We chose depth over breadth. The 4 launch roles have specific dimensions, weights, and calibration notes. More roles will come as we get the data to calibrate them properly.

**Why the scoring is fully visible:**
Most AI tools are black boxes. You get a number but no idea how it was calculated. Every dimension, weight, and calibration rule in this tool is in a readable markdown file. If you disagree with a weight, you can see exactly what it is and why. This also means the community can propose better calibration based on real hiring data.

## What I Learned

**Titles are a terrible proxy for work.** Building the title-to-work mismatch table surfaced 14+ common titles where the actual work regularly diverges from what the title implies. "Solutions Architect" doing PM work is just one example. This happens across every function. ATS systems filter on titles, so candidates doing PM work under an architect title may never reach a human reviewer.

**AI PM is genuinely different from traditional PM.** After reading hiring manager interviews from OpenAI, Google, and Meta, it became clear that AI PM roles need their own scoring criteria. The core artifact shifts from PRDs to evaluation frameworks. Outcomes are probabilistic. Planning happens "in pencil, not pen." A traditional PM with 10 years of experience but zero AI products will score in the 40s on AI PM criteria. That's honest, and the tool should reflect it.

**The hardest section was "What the Hiring Manager Is Thinking."** It's easy to make it either too generic ("looks like a strong candidate") or too harsh ("instant reject"). The right tone is honest but specific. Name the exact moment of hesitation, the bias that triggers it, and what would change their mind.

## Next Steps

- [ ] Resume customizer mode: take the fit analysis and rewrite the resume for the job without fabricating experience
- [ ] Batch mode: analyze multiple postings and rank by fit to prioritize applications
- [ ] Spider graph: plot the 5 key skills for the role (ideal vs candidate) for instant visual gap analysis
- [ ] More calibrated roles: Design, Marketing, Data Science, Operations
- [ ] Claude Code `/job-fit` slash command

## Built With

- [Claude](https://claude.ai) via the Claude skill system
- Research from O*NET occupational frameworks, recruiter evaluation studies, hiring manager psychology literature, and AI PM market analysis

---

Built by [Dheeraj Chowdhary](https://www.linkedin.com/in/dheerajchowdhary) | [GitHub](https://github.com/dj-chow)
