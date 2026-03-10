# Job Fit Analyzer — Project Plan

## What We're Building

A Claude skill that evaluates how well a candidate's background matches a job posting — for any role, not just PM or sales. The user uploads their resume and LinkedIn profile, pastes a job description, and gets a structured analysis that goes beyond keyword matching. It recognizes adjacent and transferable work (e.g., someone who did product work under a "Solutions Architect" title), separates resume writing quality from actual fit, identifies the biggest weakness a hiring manager would flag, and surfaces the candidate's strongest stories. It also cross-checks LinkedIn against the resume for inconsistencies.

Ships as a Claude skill (ZIP with SKILL.md) that works on both Claude web (Customize > Skills > Upload) and Claude Code (drop into .claude/skills/).

## Seriousness Level

Launch-quality. Goal is a public GitHub repo that earns 40-50 stars. README must show product thinking (tradeoffs, decisions, learnings). Distribution via LinkedIn and PM communities.

## Phase 1 Scope — What We're Doing TODAY

### Core Skill

1. **SKILL.md** — The analysis engine. Single file with YAML frontmatter + detailed instructions. Role-agnostic design that adapts to any job type.
2. **Six analysis outputs:**

   - **Requirements Map** — Every key requirement from the JD mapped to specific experience from resume/LinkedIn, with confidence level (Strong Match / Partial Match / Gap)
   - **Adjacent Work Recognition** — PM work done under other titles, technical work done in non-technical roles, leadership without the title, etc. The tool identifies transferable experience the candidate might not even realize they have
   - **Biggest Weakness + Flip Strategy** — The #1 concern a hiring manager would have, stated bluntly, plus a concrete strategy to address it (inspired by the "flip your weakness" framework)
   - **Top 3 Strongest Stories** — The most compelling experiences from LinkedIn and/or resume, with explanation of why they'd resonate for this specific role
   - **Hygiene Check** — Conflicts between LinkedIn and resume (date mismatches, title differences, missing roles, inconsistent metrics)
   - **Overall Fit Narrative** — Not just a score. A 3-4 sentence assessment written from the hiring manager's perspective: "What the Hiring Manager Is Thinking" when they see this application
3. **Resume narrative quality** flagged separately — If the resume is poorly written or undersells the candidate, that's called out as a separate improvement opportunity. It does NOT reduce the fit assessment. The tool evaluates the person, not just their document.

### Repo & README

4. **README.md** — Using the PROJECT-README template. Sections: Problem, Solution, Demo (screenshot of output), How to Use (both Claude web and Claude Code paths), How It Works, Tradeoffs and Decisions, What I Learned, Next Steps.
5. **Repo structure:**

   ```
   job-fit-analyzer/
   ├── job-fit-analyzer/
   │   └── SKILL.md          # The skill file
   ├── examples/
   │   ├── sample-output.md  # Example analysis output
   │   └── sample-jd.txt     # Example job description
   ├── README.md
   ├── LICENSE
   └── plan.md
   ```
6. **Ship to GitHub** — New repo under github.com/dj-chow, clean commit history.

## Parking Lot — Deferred to Later

- **Claude Code slash command wrapper** (MVP 1.1) — `/job-fit` command for Claude Code power users
- **Resume Customizer mode** — Take the fit analysis and rewrite the resume for the job, improving keyword coverage without fabricating experience
- **Batch mode** — Analyze multiple postings, rank by fit, help prioritize where to apply
- **Score tracker** — Track fit scores across applications over time
- **Web UI / Streamlit** — For users who don't use Claude at all
- **Comparison mode** — Side-by-side analysis of 2-3 similar roles
- **Spider Graph** -  Get the 5 most important skills. Track the ideal spider graph for the role, then plot the spider graph for the candidate making it easier in one visual to see the strengths and weaknesses for the role

## Tech Approach

No code. The entire product is a well-engineered Claude skill file (SKILL.md with YAML frontmatter + markdown instructions). The value is in the prompt architecture — how we structure Claude's analysis to be thorough, role-agnostic, and genuinely useful.

The skill:

- Reads uploaded resume PDF and LinkedIn PDF
- Accepts a pasted job description
- Runs a multi-stage analysis: (1) parse the JD to understand what the role actually values, (2) extract candidate experience from both documents, (3) map and evaluate fit, (4) identify gaps and strengths, (5) generate the six outputs
- Adapts its evaluation criteria based on the role type — what matters for a PM role is different from what matters for a data engineer or marketing manager

Distribution: Users download the skill folder as a ZIP, upload to Claude web (Customize > Skills) or drop into Claude Code skills directory.

## Open Questions — Need Decisions Before Building

1. **Repo name:** `job-fit-analyzer` vs something catchier? Repo name matters for discoverability and stars. Recommendation: keep it descriptive for now, can rename later. ok
2. **License:** MIT (maximum adoption) vs something more restrictive? Recommendation: MIT — we want stars and usage, not gatekeeping. ok
3. **Do we want a fit score number?** The jdanalyzer uses 0-100%. We could do a score + narrative, or narrative only. Recommendation: Include a score (people love numbers) but lead with the narrative so it's not reductive. yes score and narrative

---

Built by Dheeraj Chowdhary | [LinkedIn](https://www.linkedin.com/in/dheerajchowdhary) | [GitHub](https://github.com/dj-chow)
