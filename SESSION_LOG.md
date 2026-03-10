# Session Log
*Reverse chronological — newest entries at top.*

---
## [2026-03-10 23:00] — Build Job Fit Analyzer from scratch

**Project:** job-fit-analyzer
**Duration:** Extended (50+ exchanges)

### Decisions
- Project: Claude skill that evaluates job fit by analyzing work activities, not titles/keywords
- Format: Claude web skill file (ZIP with SKILL.md) + works in Claude Code too
- MVP targets Claude web users first (18.9M MAU vs Claude Code's smaller base)
- 4 launch roles: Product Management, AI/ML PM, Software Engineering, Business Analysis
- Dropped Data Science role (not enough nuance for user delight)
- Added BA/BSA role (Dheeraj's background, knows the nuance)
- Scoring is fully transparent: weighted dimensions, level descriptions, auditable calculation
- Resume narrative quality scored separately from fit (bad resume != bad candidate)
- Repo name: job-fit-analyzer, License: MIT
- Fit score: number + narrative (people love numbers but narrative prevents it being reductive)
- No em dashes anywhere. Human-like writing. Target readability score 4-5.
- Sample output recalibrated: banking PM applying to AI PM scores 44/100, not 72 (AI-specific dimensions pull hard)

### Open Questions
- GitHub repo not yet created on github.com/dj-chow. Need to create and push.
- Readability score not yet validated against the AI Readability Index checker tool (target 4-5)
- Em dash cleanup needed in reference files (only SKILL.md and sample output cleaned so far)
- CONTRIBUTING.md not yet written (referenced in roles.md for community role additions)
- plan.md in the repo still references old structure (Data Science role, old file layout)

### Follow-ups
- [ ] Create GitHub repo github.com/dj-chow/job-fit-analyzer and push
- [ ] Test the skill by uploading to Claude web (Customize > Skills) with real resume + LinkedIn + JD
- [ ] Validate readability score on all content using the ARI checker
- [ ] Clean em dashes from all reference files (activity-framework.md, hygiene-checks.md, scoring files)
- [ ] Write CONTRIBUTING.md explaining how to add new role criteria
- [ ] Update plan.md to reflect final architecture (BA instead of Data Science, 9 sections not 6)
- [ ] Write a LinkedIn post announcing the launch (distribution plan for stars)
- [ ] Consider adding the spider graph visualization (parking lot item)

### What I Learned
- Claude skills are ZIP archives with a SKILL.md file. They work on both Claude web (Customize > Skills > Upload) and Claude Code (~/.claude/skills/). Same format, two audiences.
- AI PM evaluation is genuinely different from traditional PM. The core artifact shifted from PRDs to eval frameworks. A traditional PM with 10 years experience but zero AI products scores in the 40s on AI PM criteria. The market research from 7 Aakash Gupta articles confirmed this consistently.
- Top GitHub skills (anthropics/skills has 88K stars) follow a three-level loading pattern: metadata always loaded, SKILL.md body on trigger, reference files on demand. Keep SKILL.md under 500 lines.
- Scoring transparency is a product differentiator. The competitor (jdanalyzer, 0 stars) has implicit scoring. Making dimensions, weights, and calculation visible makes the tool trustworthy and contributable.

### Artifacts
- Created `C:\Users\Dheer\OneDrive\Dheeraj\Learning\portfolio\job-fit-analyzer\` (entire repo)
- Created `job-fit-analyzer/SKILL.md` — main analysis engine, 4 stages, 9 output sections
- Created `job-fit-analyzer/references/roles.md` — 4 launch roles with routing logic
- Created `job-fit-analyzer/references/scoring-heuristics.md` — common scoring rules
- Created `job-fit-analyzer/references/role-criteria/product-management.md` — 5 weighted dimensions
- Created `job-fit-analyzer/references/role-criteria/ai-product-management.md` — 6 weighted dimensions
- Created `job-fit-analyzer/references/role-criteria/engineering.md` — 5 weighted dimensions
- Created `job-fit-analyzer/references/role-criteria/business-analysis.md` — 5 weighted dimensions
- Created `job-fit-analyzer/references/activity-framework.md` — 7 activity categories + 14 title-mismatch patterns
- Created `job-fit-analyzer/references/hygiene-checks.md` — LinkedIn vs resume check patterns
- Created `examples/sample-jd.txt` — AI PM role at fintech startup
- Created `examples/sample-output.md` — full 9-section analysis, score 44/100
- Created `README.md` — project overview, setup for web + Code, tradeoffs, learnings
- Created `ARCHITECTURE.md` — 3 Mermaid diagrams (component flow, dependencies, scoring calc)
- Created `CLAUDE.md` — writing style rules (no em dashes, human tone, ARI 4-5)
- Created `LICENSE` — MIT
- Created `plan.md` — original project plan with parking lot

### Context
Built the entire job-fit-analyzer repo in one session. The skill is feature-complete with 9 output sections, transparent scoring for 4 roles, and architecture documentation. It has NOT been pushed to GitHub yet and has NOT been tested with a real skill upload to Claude web. The next session should start by pushing to GitHub, then doing a real test with Dheeraj's actual resume and LinkedIn against a real job posting. The sample output uses a profile similar to Dheeraj's, so the first real test should validate whether the scoring feels right. Research from 5 background agents (recruiter frameworks, Claude skill specs, top GitHub skills, adjacent skills mapping, hiring manager psychology) plus 1 agent reading 7 AI PM market articles informed the design.
