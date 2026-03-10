# Supported Roles

This tool launches with 4 well-calibrated roles. Each has specific scoring criteria, weighted dimensions, and calibration examples.

For roles not listed here, the tool falls back to the common heuristics in `scoring-heuristics.md` and adapts based on JD analysis. Results for unsupported roles will be less precisely calibrated.

## Launch Roles

### 1. Product Management
Covers: Product Manager, Senior PM, Group PM, Product Owner, Director of Product.
Does NOT cover: Technical PM (use Engineering or AI PM criteria depending on context), Growth PM (use PM criteria but weight Growth/Optimization activities higher).
Criteria file: `role-criteria/product-management.md`

### 2. AI / ML Product Management
Covers: AI PM, ML PM, AI Product Manager, Product Manager for AI/ML platforms.
This is a distinct role from traditional PM. It requires different evaluation criteria, different signals, and different calibration.
Criteria file: `role-criteria/ai-product-management.md`

### 3. Software Engineering
Covers: Software Engineer, Senior Engineer, Staff Engineer, Backend/Frontend/Full-stack Engineer, Engineering Manager (technical track).
Does NOT cover: DevOps/SRE (adjacent but different priorities), QA/Test Engineering, Security Engineering.
Criteria file: `role-criteria/engineering.md`

### 4. Business Analysis / BSA
Covers: Business Analyst, Business Systems Analyst (BSA), Senior BA, Lead BA, Requirements Analyst, Systems Analyst.
Does NOT cover: Product Analyst (closer to PM criteria), Data Analyst (planned future role).
Criteria file: `role-criteria/business-analysis.md`

## Unsupported Roles (Planned)

These roles are on the roadmap. Community contributions welcome. See CONTRIBUTING.md for how to add a new role.

- Data Science / Analytics
- Design (UX/UI, Product Design)
- Marketing (Growth, Product Marketing, Demand Gen)
- Sales (AE, SDR/BDR, Sales Engineering)
- Operations (Program Management, Business Operations)
- Finance (FP&A, Corporate Development)

## How to Determine Which Role Applies

1. Read the job title and description
2. If the JD mentions AI/ML products, model development, or eval frameworks, use **AI PM** criteria even if the title just says "Product Manager"
3. If the JD is ambiguous between two roles, state the ambiguity and evaluate against both. Present both scores with an explanation
4. If the role doesn't match any supported role, say so clearly. Use the common heuristics and flag that calibration is less precise
