# Job Fit Analyzer: Project Plan

## What We Built

A Claude skill that evaluates how well a candidate's background matches a job posting. The user uploads their resume and LinkedIn profile, pastes a job description, and gets a structured 9-section analysis that goes beyond keyword matching. It recognizes adjacent and transferable work (e.g., someone who did product work under a "Solutions Architect" title), separates resume writing quality from actual fit, and surfaces the candidate's strongest stories.

Ships as a Claude skill (ZIP with SKILL.md + references folder) that works on both Claude web (Customize > Skills > Upload) and Claude Code (drop into .claude/skills/).

## Seriousness Level

Launch-quality. Goal is a public GitHub repo that earns 40-50 stars. README shows product thinking (tradeoffs, decisions, learnings). Distribution via LinkedIn and PM communities.

## Phase 1: COMPLETE

### Core Skill

1. **SKILL.md.** The analysis engine. Runs a 4-stage pipeline: Decode the JD, Extract Candidate Experience, Evaluate Fit, Generate Analysis.
2. **Nine analysis outputs:**

   - **Fit Score + Headline.** 0-100 score with a one-sentence assessment, calibrated to role type
   - **Dimension Scores.** Weighted breakdown showing exactly where the candidate is strong and where they're not
   - **Requirements Map.** Every key requirement mapped to specific experience with confidence levels (Strong Match / Partial Match / Gap)
   - **Adjacent Work Recognition.** Work done under different titles. PM work by a Solutions Architect, technical work in non-technical roles, leadership without the title
   - **What the Hiring Manager Is Thinking.** Honest internal monologue from the person reading the application
   - **Biggest Weakness + Flip Strategy.** The #1 concern a hiring manager would have, stated bluntly, plus a concrete strategy to address it
   - **Top 3 Strongest Stories.** Most compelling experiences for this specific role
   - **Score Improvement Roadmap.** Top 3 actions to close gaps, with estimated score impact and time investment
   - **Hygiene Check.** LinkedIn vs resume inconsistencies (date mismatches, title differences, missing roles)
   - **Resume Narrative Assessment.** Where the resume undersells the candidate. Scored separately from fit because a bad resume does not mean a bad candidate.

3. **Scoring infrastructure.** Transparent, auditable scoring system with per-role criteria files, weighted dimensions, gap penalties, corroboration bonuses, and manual override rules. All visible in markdown files anyone can inspect.

4. **4 calibrated roles:**
   - Product Management (5 weighted dimensions)
   - AI/ML Product Management (6 weighted dimensions)
   - Software Engineering (5 weighted dimensions)
   - Business Analysis / BSA (5 weighted dimensions)

5. **Reference file system.** Role criteria, scoring heuristics, activity framework (7 categories + title mismatch table), and hygiene checks. Loaded on demand to keep context usage efficient.

### Repo and README

6. **README.md.** Sections: Problem, Solution, Demo, How to Use (Claude web + Claude Code), How It Works, Scoring Infrastructure, Tradeoffs and Decisions, What I Learned, Next Steps.
7. **Repo structure:**

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

- [ ] Resume customizer mode: take the fit analysis and rewrite the resume for the job without fabricating experience
- [ ] Batch mode: analyze multiple postings and rank by fit to prioritize applications
- [ ] Spider graph: plot the 5 key skills for the role (ideal vs candidate) for instant visual gap analysis
- [ ] More calibrated roles: Design, Marketing, Data Science, Operations
- [ ] Claude Code `/job-fit` slash command

## Parking Lot: Ideas, No Timeline

- Score tracker: track fit scores across applications over time
- Web UI / Streamlit: for users who don't use Claude at all
- Comparison mode: side-by-side analysis of 2-3 similar roles

## Tech Approach

No code. The entire product is a well-engineered Claude skill (SKILL.md + reference files). The value is in the prompt architecture and the scoring infrastructure.

The skill:

- Reads uploaded resume PDF and LinkedIn PDF
- Accepts a pasted job description
- Runs a 4-stage analysis: (1) Decode the JD to identify role type, seniority, and core requirements, (2) Extract candidate experience using activity-based decomposition across both documents, (3) Score each dimension from role-specific criteria with weighted averages, gap penalties, and corroboration bonuses, (4) Generate all 9 output sections
- Routes to role-specific scoring criteria based on the JD. A PM analysis loads PM dimensions. An engineering analysis loads engineering dimensions. No cross-contamination.

Distribution: Users download the skill folder as a ZIP, upload to Claude web (Customize > Skills) or drop into Claude Code skills directory.

## Resolved Decisions

1. **Repo name:** `job-fit-analyzer`. Descriptive, discoverable.
2. **License:** MIT. Maximum adoption.
3. **Fit score:** Yes, 0-100 with narrative. People love numbers, but the narrative prevents it from being reductive.

---

Built by Dheeraj Chowdhary | [LinkedIn](https://www.linkedin.com/in/dheerajchowdhary) | [GitHub](https://github.com/dj-chow)
