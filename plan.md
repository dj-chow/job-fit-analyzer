# Job Fit Analyzer: Project Plan

## What We Built

A Claude skill that checks how well a person's background fits a job post. The user uploads their resume and LinkedIn profile, pastes a job post, and gets a 9-part report that goes past keyword matching. It spots work done under the wrong title (e.g., PM work by a "Solutions Architect"). It keeps resume quality apart from real fit. And it pulls out the person's best stories.

Ships as a Claude skill (ZIP with SKILL.md + references folder). Works on both Claude web (Customize > Skills > Upload) and Claude Code (drop into .claude/skills/).

## Seriousness Level

Launch-ready. Goal is a public GitHub repo that earns 40-50 stars. README shows product thinking (tradeoffs, choices, lessons). Shared via LinkedIn and PM groups.

## Phase 1: COMPLETE

### Core Skill

1. **SKILL.md.** The engine. Runs a 4-stage flow: Decode the JD, Extract Experience, Score Fit, Build Output.
2. **Nine outputs:**

   - **Fit Score + Headline.** 0-100 score with a one-line read, tuned to role type
   - **Dimension Scores.** Weighted split showing where the person is strong and where they're not
   - **Requirements Map.** Every key need mapped to real work with trust levels (Strong Match / Partial Match / Gap)
   - **Adjacent Work Recognition.** Work done under other titles. PM work by a Solutions Architect, tech work in non-tech roles, leading without the title
   - **What the Hiring Manager Is Thinking.** Honest inner voice of the person reading the app
   - **Biggest Weakness + Flip Strategy.** The top worry a hiring manager would have, said plainly, plus a plan to deal with it
   - **Top 3 Strongest Stories.** Best experiences for this exact role
   - **Score Improvement Roadmap.** Top 3 steps to close gaps, with score impact and time needed
   - **Hygiene Check.** LinkedIn vs resume mismatches (date gaps, title changes, missing roles)
   - **Resume Narrative Assessment.** Where the resume sells the person short. Scored apart from fit because a bad resume does not mean a bad person.

3. **Scoring system.** Clear, open scoring with per-role criteria files, weighted areas, gap hits, match bonuses, and manual override rules. All visible in markdown files anyone can read.

4. **4 tuned roles:**
   - Product Management (5 weighted areas)
   - AI/ML Product Management (6 weighted areas)
   - Software Engineering (5 weighted areas)
   - Business Analysis / BSA (5 weighted areas)

5. **Reference file system.** Role criteria, scoring rules, activity types (7 groups + title mismatch table), and hygiene checks. Loaded on demand to keep context use low.

### Repo and README

6. **README.md.** Parts: Problem, Solution, Demo, How to Use (Claude web + Claude Code), How It Works, Scoring System, Tradeoffs and Choices, What I Learned, Next Steps.
7. **Repo layout:**

   ```
   job-fit-analyzer/
   ├── job-fit-analyzer/                # THE SKILL (upload this folder as ZIP)
   │   ├── SKILL.md                     # Main engine. 4-stage analysis flow.
   │   └── references/                  # Loaded on demand, not at startup
   │       ├── roles.md                 # Role routing: which criteria file to use
   │       ├── scoring-heuristics.md    # Common rules: recency, depth, corroboration
   │       ├── activity-framework.md    # 7 activity categories + title mismatch table
   │       ├── hygiene-checks.md        # LinkedIn vs resume check patterns
   │       └── role-criteria/           # Per-role scoring dimensions and weights
   │           ├── product-management.md
   │           ├── ai-product-management.md
   │           ├── engineering.md
   │           └── business-analysis.md
   ├── examples/
   │   ├── sample-jd.txt               # Example job description input
   │   └── sample-output.md            # Full 9-section analysis output
   ├── ARCHITECTURE.md                  # System architecture with Mermaid diagrams
   ├── CLAUDE.md                        # Writing style rules
   ├── README.md                        # Project overview and setup
   ├── LICENSE                          # MIT
   ├── plan.md                          # This file
   └── .gitignore
   ```

8. **Shipped to GitHub.** github.com/dj-chow/job-fit-analyzer, clean commit history.

## Phase 2: Next

- [ ] Resume fixer mode: take the fit report and rewrite the resume for the job without making things up
- [ ] Batch mode: check many posts and rank by fit to pick where to apply
- [ ] Spider graph: plot the 5 key skills for the role (ideal vs actual) for a quick visual gap view
- [ ] More tuned roles: Design, Marketing, Data Science, Operations
- [ ] Claude Code `/job-fit` slash command

## Parking Lot: Ideas, No Timeline

- Score tracker: track fit scores across apps over time
- Web UI / Streamlit: for users who don't use Claude at all
- Compare mode: side-by-side view of 2-3 similar roles

## Tech Approach

No code. The whole product is a well-built Claude skill (SKILL.md + reference files). The value is in the prompt design and the scoring system.

The skill:

- Reads an uploaded resume PDF and LinkedIn PDF
- Takes a pasted job post
- Runs a 4-stage flow: (1) Decode the JD to find role type, seniority, and core needs, (2) Pull out work history using activity-based sorting across both docs, (3) Score each area from role-based criteria with weighted math, gap hits, and match bonuses, (4) Build all 9 output parts
- Routes to role-based scoring criteria from the JD. A PM run loads PM areas. An eng run loads eng areas. No mixing.

How users get it: Download the skill folder as a ZIP. Upload to Claude web (Customize > Skills) or drop into Claude Code skills folder.

## Resolved Decisions

1. **Repo name:** `job-fit-analyzer`. Clear and easy to find.
2. **License:** MIT. Most open for adoption.
3. **Fit score:** Yes, 0-100 with story. People love numbers, but the story stops it from being too simple.

---

Built by Dheeraj Chowdhary | [LinkedIn](https://www.linkedin.com/in/dheerajchowdhary) | [GitHub](https://github.com/dj-chow)
