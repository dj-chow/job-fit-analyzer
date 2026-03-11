# Job Fit Analyzer

A Claude skill that tells you how well you match a job. It looks at the work you've done, not just your titles.

## The Problem

Most fit tools just match words. They check if your resume has the same words as the job post. Then they call it a "match score." This fails two ways:

1. **It misses real work.** A person with the title "Solutions Architect" who ran backlogs and wrote specs for 3 years was doing PM work. A word matcher would never catch that.
2. **It punishes bad resumes, not bad people.** Some people undersell their work on paper. They still did the work. The tool should judge the person, not just their file.

If you've ever thought "I've done this work, just not with that title," this tool is for you.

## The Solution

Upload your resume and LinkedIn profile. Paste a job post. Get a two-part review. First, a screen check tells you if you'd pass the first filter. Then a 10-part review scores your real work against what the role needs.

The skill ships with **4 roles** (Product Management, AI/ML PM, Software Engineering, Business Analysis). Each has clear scoring rules. Each role has weighted parts, level guides, and notes. You can see how the score is found.

### What You Get

| Section | What It Does |
|---|---|
| **Screen Check** | Hard gate items checked as Pass/Partial/Fail with a verdict: Likely Passes Screen, Borderline, or Likely Filtered Out |
| **Fit Score + Headline** | 0-100 score with a one-line read, tuned to the role type |
| **Dimension Scores** | Weighted breakdown showing where you're strong and where you're not |
| **Requirements Map** | Every key need mapped to your specific work with confidence levels |
| **Adjacent Work Recognition** | Finds where you did the job's work under a different title |
| **What the Hiring Manager Is Thinking** | Honest inner thoughts from the person reading your application |
| **Biggest Weakness + Flip Strategy** | The #1 concern a hiring manager would have, plus how to fix it |
| **Top 3 Strongest Stories** | Your best work stories for this specific role |
| **Score Improvement Roadmap** | Top 3 actions to close gaps, with score impact and time needed |
| **Hygiene Check** | LinkedIn vs resume gaps that could raise red flags |
| **Resume Narrative Assessment** | Where your resume undersells you (scored apart from fit) |

## What Makes This Different

1. **Two-part review (Screen Check + Fit Score).** Most tools give you one number. A person missing a key need can still score 75% since other skills make up for it. This tool splits "Will you pass the screen?" from "How well do you fit?" Those are the same two steps real hiring uses. No other tool does this.

2. **Work-based matching, not word matching.** The tool breaks each role into 7 work types (Strategic, Discovery, Definition, Execution, Growth, Technical, Communication). A person who ran backlogs and led team talks was doing PM work. Word matchers miss this.

3. **Open, clear scoring.** Every part, weight, and formula lives in a plain markdown file. You can see how the score was found and why. Most AI tools are black boxes. This one shows its work. If you don't agree with a weight, you can find it and suggest a change.

4. **Resume quality scored apart from fit.** A bad resume doesn't mean a bad person for the role. Many strong people undersell their work. The fit score judges the person. The resume review judges the file. They are kept apart.

5. **Adjacent work found.** The tool finds where you did the role's work under the wrong title. 14 common title-to-work gaps are mapped out. This catches skills that word matching always misses.

6. **"What the Hiring Manager Is Thinking."** Not vague feedback. An honest inner voice from the person reading your file. It names the exact pause, the bias behind it, and what would change their mind.

## Demo

Here's a snippet from a [full sample output](examples/sample-output.md). A banking PM applying for an AI PM role at a fintech startup:

> **Screen Verdict: Borderline**
> ML/AI product experience: Fail | Working with ML engineers: Partial

> **Score: 44/100**
>
> A strong product person who knows banking systems well. But the AI gap is real. This person has never shipped an AI product, never written evals, and never worked with ML engineers.

**Adjacent Work Recognition:**
> **"Solutions Architect" at Meridian Bank (2021-2024) = Product Manager**
> Title says architect. Work says PM. This person looked into repeat issues by mapping workflows across systems. They led cross-team sessions to align people on what the problem was...

**What the Hiring Manager Is Thinking:**
> "Nine years at one bank. Okay, loyal or stuck? Let me scan. Product Owner, Solutions Architect, Delivery Lead. None of these scream AI PM. The regulatory angle is interesting though..."

[See the full sample output](examples/sample-output.md)

## Setup

You need a Claude account (Free, Pro, or Team plan). Pick the option that fits how you use Claude.

### Option 1: Claude Code (one-liner)

```bash
git clone https://github.com/dj-chow/job-fit-analyzer.git /tmp/job-fit-analyzer && \
  mkdir -p ~/.claude/skills && \
  cp -r /tmp/job-fit-analyzer/skill ~/.claude/skills/job-fit-analyzer
```

### Option 2: Claude Code (symlink for auto-updates)

```bash
git clone https://github.com/dj-chow/job-fit-analyzer.git ~/job-fit-analyzer && \
  mkdir -p ~/.claude/skills && \
  ln -s ~/job-fit-analyzer/skill ~/.claude/skills/job-fit-analyzer
```

Pull new updates any time with `cd ~/job-fit-analyzer && git pull`.

### Option 3: Claude Web (claude.ai)

1. Download this repo as a ZIP (Code > Download ZIP)
2. Go to [claude.ai](https://claude.ai) > Settings > Customize > Skills
3. Click "+" then "Upload a skill"
4. Upload the `skill/` folder from the ZIP

### Verify (Claude Code)

```bash
ls ~/.claude/skills/job-fit-analyzer/
# You should see: SKILL.md  references/
```

### Use It

Upload your resume PDF and LinkedIn PDF. Paste a job post. Ask Claude to check your fit. The skill kicks in on its own.

### Example

**Input:**
- Resume PDF
- LinkedIn PDF
- Pasted job post

**Output:**
A full review with scores, needs mapping, and clear next steps ([see full example](examples/sample-output.md))

## How It Works

The skill runs a 5-stage review:

1. **Decode the job post.** Pulls out the 5-7 needs that decide hire or no-hire. Marks each as a hard gate or soft signal. Finds the ideal person profile. Loads role-specific scoring rules.
2. **Extract your work.** Reads both files. Breaks each role into 7 work types (Strategic, Discovery, Definition, Execution, Growth, Technical, Communication) instead of relying on titles.
3. **Screen check.** Checks hard gates against your proof. Gives Pass/Partial/Fail for each. Makes a verdict: Likely Passes Screen, Borderline, or Likely Filtered Out.
4. **Score and review.** Scores each part from the role criteria file. Finds the weighted score with gap penalties and proof bonuses. Maps needs to proof.
5. **Build the output.** Creates all 10 sections. This includes the hiring manager view and the weakness flip plan.

### Scoring Infrastructure

The scoring system is open and clear. Anyone can look under the hood:

```
skill/references/
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
- 5-6 scored parts with specific weights
- Level guides (Strong/Solid/Partial/Weak/Gap) with score ranges
- Seniority notes
- Common scoring traps to avoid

## Tradeoffs and Decisions

**Why work-based matching instead of word matching:**
Words tell you if a resume has the right terms. Work tells you if the person has done the right tasks. A "Business Analyst" who built SQL pipelines and data models has data engineering skills, even if "data engineer" never shows up on their resume. This catches skills that word matching always misses. The tradeoff: Claude needs to think about each role's real work, so it takes longer and uses more tokens than a word scan.

**Why resume quality is scored apart from fit:**
A bad resume doesn't mean a bad person for the role. Many strong people undersell their work. They list tasks instead of results. Keeping "how good is this person" apart from "how well does their resume show it" gives feedback on both without mixing them up.

**Why only 4 roles at launch:**
We could have shipped 10+ roles with generic rules. But generic scoring gives generic results. Each role has different signals that matter. Engineers get scored on technical depth. PMs get scored on decision quality. BAs get scored on needs gathering. We chose depth over breadth. The 4 launch roles have specific parts, weights, and notes. More roles will come as we get the data to tune them well.

**Why the screen check is apart from the fit score:**
Most job tools make one score. A person missing a key hard need (like "2+ years managing a decision engine") can still score 75% since other skills make up for it. That's misleading. Real hiring has two steps: first you pass the screen, then you're judged on fit. This tool mirrors that. The screen check tells you if you'd survive the first filter. The fit score tells you how you'd do if you got past it. A high fit score with a "Likely Filtered Out" screen means "strong person who will likely never get the chance to prove it."

**Why the scoring is fully visible:**
Most AI tools are black boxes. You get a number but no idea how it was found. Every part, weight, and rule in this tool is in a plain markdown file. If you don't agree with a weight, you can see what it is and why. This also means others can suggest better tuning based on real hiring data.

## What I Learned

**Titles are a bad proxy for work.** Building the title-to-work gap table showed 14+ common titles where the real work often differs from what the title implies. "Solutions Architect" doing PM work is just one case. This happens in every function. ATS systems filter on titles. So a person doing PM work under an architect title may never reach a human reviewer.

**AI PM is truly different from normal PM.** After reading hiring talks from OpenAI, Google, and Meta, it became clear that AI PM roles need their own scoring rules. The core output shifts from PRDs to eval frameworks. Results are less certain. Planning happens "in pencil, not pen." A normal PM with 10 years of work but zero AI products will score in the 40s on AI PM criteria. That's honest, and the tool should show it.

**PII leaks are easy to miss.** The first version of our sample output used real company names and dates from the test candidate. Combined with the author credit in the README, anyone could trace the sample back to a real person. We caught it and swapped in fictional names. Lesson: treat all personal data as privileged. Always anonymize before committing. This is now a rule in our CLAUDE.md.

**The hardest section was "What the Hiring Manager Is Thinking."** It's easy to make it too vague ("looks like a strong person") or too harsh ("instant reject"). The right tone is honest but specific. Name the exact pause, the bias behind it, and what would change their mind.

## Next Steps

- [ ] Resume customizer mode: take the fit review and rewrite the resume for the job without making things up
- [ ] Batch mode: review many postings and rank by fit to focus your time
- [ ] Spider graph: plot the 5 key skills for the role (ideal vs you) for a quick visual gap view
- [ ] More tuned roles: Design, Marketing, Data Science, Operations
- [ ] Claude Code `/job-fit` slash command

## Built With

- [Claude](https://claude.ai) via the Claude skill system
- Research from O*NET job frameworks, recruiter studies, hiring manager research, and AI PM market data
- The two-part review model is shaped by I/O psychology research on multi-step hiring models and recruiter screening studies

---

Built by [Dheeraj Chowdhary](https://www.linkedin.com/in/dheerajchowdhary) | [GitHub](https://github.com/dj-chow)
