# Architecture

## Skill Component Flow

```mermaid
flowchart TD
    subgraph INPUTS["User Inputs"]
        R["Resume PDF"]
        L["LinkedIn PDF"]
        JD["Job Description"]
    end

    subgraph STAGE1["Stage 1: Decode the JD"]
        S1A["Identify role type + seniority"]
        S1B["Extract 5-7 core requirements"]
        S1C["Classify requirements as Hard Gate vs Soft Signal"]
        S1D["Identify ideal candidate archetype"]
        S1E["Load role criteria"]
        S1F["Note company context"]
    end

    subgraph STAGE2["Stage 2: Extract Candidate Experience"]
        S2A["Map career trajectory"]
        S2B["Decompose roles into 7 activity categories"]
        S2C["Identify title-work mismatches"]
        S2D["Corroborate across both documents"]
        S2E["Separate person from resume quality"]
    end

    subgraph STAGE3["Stage 3: Screen Check"]
        S3A["Evaluate each hard gate requirement"]
        S3B["Produce Pass / Partial / Fail per gate"]
        S3C["Generate screen verdict:<br/>Likely Passes Screen /<br/>Borderline / Likely Filtered Out"]
    end

    subgraph STAGE4["Stage 4: Evaluate Fit"]
        S4A["Score each dimension from role criteria"]
        S4B["Calculate weighted average"]
        S4C["Apply gap penalty + corroboration bonus"]
        S4D["Map requirements to evidence"]
    end

    subgraph STAGE5["Stage 5: Generate Analysis"]
        O0["0. Screen Check"]
        O1["1. Fit Score + Headline"]
        O2["2. Requirements Map"]
        O3["3. Adjacent Work Recognition"]
        O4["4. What the Hiring Manager Is Thinking"]
        O5["5. Biggest Weakness + Flip Strategy"]
        O6["6. Top 3 Strongest Stories"]
        O7["7. Score Improvement Roadmap"]
        O8["8. Hygiene Check"]
        O9["9. Resume Narrative Assessment"]
    end

    R --> STAGE2
    L --> STAGE2
    JD --> STAGE1

    STAGE1 --> STAGE3
    STAGE2 --> STAGE3
    STAGE3 --> STAGE4
    STAGE4 --> STAGE5
    STAGE3 -->|"Screen verdict<br/>affects output framing"| STAGE5

    S1A --> S1E
    S3A --> S3B --> S3C
    S4A --> S4B --> S4C --> S4D
```

## Reference File Dependencies

```mermaid
flowchart LR
    SKILL["SKILL.md<br/>Main analysis engine"]

    subgraph REFS["Reference Files (loaded on demand)"]
        ROLES["roles.md<br/>4 supported roles"]
        HEURISTICS["scoring-heuristics.md<br/>Common scoring rules"]
        ACTIVITY["activity-framework.md<br/>7 activity categories<br/>+ title mismatch table"]
        HYGIENE["hygiene-checks.md<br/>Inconsistency patterns"]

        subgraph CRITERIA["role-criteria/"]
            PM["product-management.md<br/>5 dimensions, weighted"]
            AIPM["ai-product-management.md<br/>6 dimensions, weighted"]
            ENG["engineering.md<br/>5 dimensions, weighted"]
            BA["business-analysis.md<br/>5 dimensions, weighted"]
        end
    end

    SKILL -->|"Stage 1: Which role?"| ROLES
    ROLES -->|"Route to criteria"| CRITERIA
    SKILL -->|"Stage 1: Scoring rules"| HEURISTICS
    SKILL -->|"Stage 2: Decompose work"| ACTIVITY
    SKILL -->|"Stage 3: Screen check rules"| HEURISTICS
    SKILL -->|"Stage 4: Score dimensions"| CRITERIA
    SKILL -->|"Stage 4: Calculate score"| HEURISTICS
    SKILL -->|"Section 8: Check hygiene"| HYGIENE
```

## Scoring Calculation Flow

```mermaid
flowchart TD
    subgraph SCREEN["Screen Check Path"]
        HG["Extract hard gates from JD"]
        CHECK["Check each gate against<br/>candidate evidence"]
        VERDICT["Produce screen verdict:<br/>Likely Passes Screen /<br/>Borderline / Likely Filtered Out"]
        HG --> CHECK --> VERDICT
    end

    subgraph DIMENSIONAL["Dimensional Scoring Path"]
        DIM["Score each dimension<br/>(0-100 per dimension)"]
        WEIGHT["Apply role-specific weights<br/>(from role-criteria file)"]
        AVG["Calculate weighted average"]
        GAP{"Any dimension<br/>below 20?"}
        PENALTY1["-10 points<br/>(one critical gap)"]
        PENALTY2["-20 points<br/>(two+ critical gaps)"]
        CORR{"3+ dimensions<br/>corroborated in<br/>both documents?"}
        BONUS["+3 points"]
        OVERRIDE{"Does math<br/>match reality?"}
        ADJUST["Manual override<br/>(must explain why)"]
        FITSCORE["Fit Score (0-100)"]

        DIM --> WEIGHT --> AVG
        AVG --> GAP
        GAP -->|"Yes, one"| PENALTY1 --> CORR
        GAP -->|"Yes, two+"| PENALTY2 --> CORR
        GAP -->|"No"| CORR
        CORR -->|"Yes"| BONUS --> OVERRIDE
        CORR -->|"No"| OVERRIDE
        OVERRIDE -->|"No, adjust"| ADJUST --> FITSCORE
        OVERRIDE -->|"Yes"| FITSCORE
    end

    FINAL["Final Output<br/>(10 sections, O0-O9)"]

    VERDICT --> FINAL
    FITSCORE --> FINAL
```

## File Structure

```
job-fit-analyzer/
├── job-fit-analyzer/                # THE SKILL (upload this folder as ZIP)
│   ├── SKILL.md                     # Main engine. 5-stage analysis flow.
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
│   └── sample-output.md            # Full 10-section analysis output
├── ARCHITECTURE.md                  # This file
├── CLAUDE.md                        # Writing style rules
├── README.md                        # Project overview and setup
├── LICENSE                          # MIT
├── plan.md                          # Original project plan
└── .gitignore
```

## Key Design Decisions

**Three-level loading.** SKILL.md metadata (name + description) loads at session start. SKILL.md body loads when the skill triggers. Reference files load only when needed during analysis. This keeps context usage efficient.

**Role routing.** Stage 1 identifies the role type, then loads only the relevant criteria file. A PM analysis never loads engineering criteria. This keeps each analysis focused and prevents cross-contamination between role evaluation patterns.

**Scoring separation.** The scoring heuristics (common rules) and role criteria (specific dimensions) are in separate files. Common rules change rarely. Role criteria evolve as we get more calibration data. Keeping them apart means you can update PM scoring without touching the shared rules.

**Resume quality is decoupled from fit.** The fit score comes from Stage 4 (dimension scoring). The resume narrative assessment is a separate output in Stage 5. A bad resume doesn't lower the fit score. This was a deliberate product decision to evaluate the person, not just their document.

**Two-layer evaluation.** Screen check runs before dimensional scoring, mirroring how hiring actually works. Hard gate requirements (specific tools, platforms, domains, certifications) are evaluated as Pass/Partial/Fail. The screen verdict tells candidates whether they'd survive initial filtering. The fit score then shows how they'd perform if screened in. This prevents the tool from giving false hope by producing a high fit score for candidates who'd be auto-rejected on a specific missing requirement. No consumer job-matching tool does this - they all produce single composite scores that can mask critical gaps.
