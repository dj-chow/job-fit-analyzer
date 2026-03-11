# Contributing

This tool scores job fit for set roles. The main way to help is to add new roles. You can also tune how roles are scored or flag bad scores.

## File Structure

Know where things live before you start.

```
job-fit-analyzer/
├── skill/                         # The skill itself
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

The key files for those who help: `roles.md` routes to the right criteria file. Each file in `role-criteria/` lists scored areas with weights. `scoring-heuristics.md` holds the shared rules for every role.

## Adding a New Role

This is the biggest way you can help. Planned roles are listed in `roles.md` under "Unsupported Roles."

### Step 1: Pick a role you know well

You need real hiring context. "I've hired 5 data folks" or "I've been a UX person for 6 years." That kind of know-how. Book smarts alone won't make good scoring.

### Step 2: Define the core question

Each role criteria file starts with one question. It states what the role truly needs. Look at the ones we have for the pattern:

- PM: "Can this person own a product area, make good calls on what to build, and ship results through teams?"
- AI PM: "Can this person build AI products that work for real users, while handling the doubt that comes with models?"

Write yours in one sentence. If you can't, the scope is too wide.

### Step 3: Define 5-7 scored areas

Each area needs:
- A name and weight (all weights must add up to 100%)
- A one-line note on what it checks
- A scoring rubric with 5 levels: Strong (80-100), Solid (60-79), Partial (40-59), Weak (20-39), Gap (0-19)

Look at `role-criteria/product-management.md` as a guide. Copy the form exactly.

Rules for areas:
- 5 areas at least, 7 at most
- The top-weight area should be the best signal for the role
- No area should weigh less than 10%
- Every level in the rubric needs a clear note, not just "good" or "bad"

### Step 4: Add seniority tuning

State how the bar shifts across levels (junior, mid, senior, director+). The same areas apply at every level. The bar moves.

### Step 5: Add common scoring traps

List 3-5 errors a scorer might make for this role. These are cases where the math gives the wrong answer. See the "Common Scoring Traps" part in the PM criteria for samples.

### Step 6: Create the file and update roles.md

1. Save your criteria file as `role-criteria/your-role-name.md`
2. Add an entry to `roles.md` under "Launch Roles" with:
   - What titles it covers
   - What titles it does NOT cover (and where to route those)
   - The criteria file path
3. Remove it from the "Unsupported Roles" list

### Step 7: Test it

Run the tool on 3+ real people you already know the answer for. If you've hired or judged people for this role, use those as test cases. The score should land within 10 points of your gut feel. If it doesn't, tweak your weights and rubrics.

### What a good one looks like

- Criteria file follows the exact form of the ones we have
- Weights reflect real hiring needs, not equal splits
- Rubric notes are clear enough that two people would score the same person within 10 points
- Seniority tuning exists
- At least 3 scoring traps listed
- Tested on real people (say so in your PR)

## Improving Existing Role Scoring

If a role's weights or rubrics feel off, you can suggest changes. But you need proof.

### What counts as proof

- "I ran this on 5 people I've met in person. The tool scored X at 78 but they bombed the chat because Y." That's useful.
- "I think Tech Skill should weigh more for PMs." That's a view, not proof.

### How to submit

1. Open an issue about the scoring gap
2. Include the area, the current weight/rubric, and your fix
3. Say why, with real cases (hide names)
4. If you can, show the fix helps across many cases, not just one

Don't submit weight changes that fix one edge case but break the normal case.

## Reporting Scoring Issues

At times the tool gives a score that is clearly wrong. Not 5 points off, but 20+ points off from what any fair person would say.

### How to report

Open an issue with:
- The role type (PM, Eng, etc.)
- The score the tool gave
- What you think the right score is (roughly)
- Why the gap exists. Which area scored wrong? Was proof missed? Was nearby work over-counted?

You don't need to share the full resume or LinkedIn. But share enough to make the issue clear.

### Common causes of bad scores

- The role criteria misses a common path into that role
- An area rubric has a blind spot (e.g., doesn't count open source work as "shipped product")
- The seniority tuning is wrong for a given context (startup vs large firm)

If you can trace the issue to a set rubric line, that makes the fix much faster.

## Writing Style

All text in this repo follows the rules in `CLAUDE.md`. The short form:
- No em dashes
- Simple words, short lines
- Write like a person, not a press release
- Target a score of 4-5 on the Automated Readability Index
