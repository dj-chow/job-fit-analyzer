# Contributing

This tool scores job fit for specific roles. The main way to contribute is adding new roles. You can also improve existing role calibration or report scoring issues.

## File Structure

Know where things live before you start.

```
job-fit-analyzer/
├── job-fit-analyzer/              # The skill itself
│   ├── SKILL.md                   # Main analysis engine (4-stage flow)
│   └── references/
│       ├── roles.md               # Lists supported roles and routing rules
│       ├── scoring-heuristics.md  # Shared scoring rules (recency, depth, etc.)
│       ├── activity-framework.md  # 7 activity categories + title mismatch table
│       ├── hygiene-checks.md      # LinkedIn vs resume consistency checks
│       └── role-criteria/         # One file per role
│           ├── product-management.md
│           ├── ai-product-management.md
│           ├── engineering.md
│           └── business-analysis.md
├── examples/
│   ├── sample-jd.txt
│   └── sample-output.md
├── ARCHITECTURE.md                # System design and scoring flow
└── CLAUDE.md                      # Writing style rules for all content
```

The key files for contributors: `roles.md` routes to the right criteria file. Each criteria file in `role-criteria/` defines scored dimensions with weights. `scoring-heuristics.md` has the shared rules that apply to every role.

## Adding a New Role

This is the biggest contribution you can make. The planned roles are listed in `roles.md` under "Unsupported Roles."

### Step 1: Pick a role you know well

You need real hiring context for this. "I've hired 5 data scientists" or "I've been a UX designer for 6 years" - that kind of knowledge. Book smarts alone won't produce good calibration.

### Step 2: Define the core question

Every role criteria file starts with one question. It captures what the role really needs. Look at the existing ones for the pattern:

- PM: "Can this person own a product area, make good prioritization decisions, and ship outcomes through cross-functional teams?"
- AI PM: "Can this person build AI-powered products that work for real users, while navigating the uncertainty that comes with probabilistic systems?"

Write yours in one sentence. If you can't, the scope is too broad.

### Step 3: Define 5-7 scored dimensions

Each dimension needs:
- A name and weight (all weights must add up to 100%)
- A one-line description of what it measures
- A scoring rubric with 5 levels: Strong (80-100), Solid (60-79), Partial (40-59), Weak (20-39), Gap (0-19)

Look at `role-criteria/product-management.md` as a template. Copy the structure exactly.

Rules for dimensions:
- 5 dimensions minimum, 7 maximum
- The top-weighted dimension should be the single strongest signal for the role
- No dimension should weigh less than 10%
- Every level in the rubric needs a concrete description, not just "good" or "bad"

### Step 4: Add seniority calibration

Define how the bar shifts across levels (junior, mid, senior, director+). Same dimensions apply at every level. The expectations change.

### Step 5: Add common scoring traps

List 3-5 mistakes a scorer might make for this role. These are patterns where the math gives the wrong answer. See the "Common Scoring Traps" section in the PM criteria for examples.

### Step 6: Create the file and update roles.md

1. Save your criteria file as `role-criteria/your-role-name.md`
2. Add an entry to `roles.md` under "Launch Roles" with:
   - What titles it covers
   - What titles it does NOT cover (and where to route those instead)
   - The criteria file path
3. Remove it from the "Unsupported Roles" list

### Step 7: Test it

Run the tool against 3+ real candidates you already know the answer for. If you've hired or evaluated people for this role, use those as calibration cases. The score should land within 10 points of your gut assessment. If it doesn't, adjust your weights and rubrics.

### What a good submission looks like

- Criteria file follows the exact structure of existing ones
- Weights reflect real hiring priorities, not equal distribution
- Rubric descriptions are specific enough that two different people would score the same candidate within 10 points
- Seniority calibration exists
- At least 3 scoring traps listed
- Tested against real candidates (mention this in your PR)

## Improving Existing Role Calibration

If a role's weights or rubrics feel off, you can propose changes. But you need evidence.

### What counts as evidence

- "I ran this against 5 candidates I've interviewed. The tool scored X at 78 but they bombed the interview because Y." That's useful.
- "I think Technical Fluency should weigh more for PMs." That's an opinion, not evidence.

### How to submit

1. Open an issue describing the scoring gap
2. Include the specific dimension, the current weight/rubric, and your proposed change
3. Explain why with real examples (anonymize candidates)
4. If possible, show that the change improves accuracy across multiple cases, not just one

Don't submit weight changes that fix one edge case but break the common case.

## Reporting Scoring Issues

Sometimes the tool gives a score that's clearly wrong. Not 5 points off - more like 20+ points off from what any reasonable person would say.

### How to report

Open an issue with:
- The role type (PM, Engineering, etc.)
- The score the tool gave
- What you think the right score is (roughly)
- Why the gap exists. Which dimension scored wrong? Was evidence ignored? Was adjacent experience over-credited?

You don't need to include the full resume or LinkedIn. But include enough context to understand the issue.

### Common causes of bad scores

- The role criteria doesn't account for a common career path into that role
- A dimension rubric has a blind spot (e.g., doesn't recognize open source work as "shipped product")
- The seniority calibration is wrong for a specific context (startup vs enterprise)

If you can trace the issue to a specific rubric line, that makes fixing it much faster.

## Writing Style

All content in this repo follows the rules in `CLAUDE.md`. The short version:
- No em dashes
- Simple words, short sentences
- Write like a person, not a press release
- Target readability score of 4-5 on the Automated Readability Index
