# Sample Analysis Output

> Example output from Job Fit Analyzer. The candidate is a PM with 9+ years in banking (risk and regulatory reporting) applying for a Senior AI PM role at a Series B fintech startup.

---

## Dimension Scores

Using AI/ML Product Management criteria from `role-criteria/ai-product-management.md`:

| Dimension | Weight | Score | Level | Key Evidence |
|---|---|---|---|---|
| Shipped AI/ML Product Experience | 25% | 25 | Weak | Worked with vendor ML analytics platforms. Contributed to an NLP assessment product 10+ years ago. No evidence of owning an AI product end-to-end. |
| Technical Fluency for AI | 20% | 35 | Weak | Worked with data teams and understood system dependencies. No evidence of discussing model constraints, evals, or training approaches. |
| Eval and Quality Framework Thinking | 15% | 45 | Partial | Built self-serve dashboards with operational metrics. Has experimentation mindset from reporting optimization. But no experience with probabilistic quality thresholds or model evaluation. |
| Product Ownership and Shipping | 15% | 82 | Strong | Owned risk reporting platform as Product Owner. Shipped self-serve dashboards, drove adoption, measured outcomes. Clear end-to-end ownership. |
| Breadth of Domain Experience | 15% | 50 | Partial | Deep in one domain (banking risk). Some breadth from edtech (UpGrad) and assessment products (Aspiring Minds). But career is concentrated in financial services. |
| Stakeholder Alignment | 10% | 90 | Strong | Every role shows cross-functional alignment. Resolved design decisions without authority across risk, tech, ops, and governance teams. This is the candidate's superpower. |

**Weighted average:** 46.3
**Critical gap penalty:** -10 (Shipped AI/ML Product scores below 20 threshold after rounding)
**Corroboration bonus:** +3 (4 dimensions have evidence in both documents)
**Override:** +5 (Regulatory domain expertise is specifically called for in this JD. This rare combination of risk domain knowledge + product skills is genuinely valuable for an AI risk assessment platform.)

---

## 1. Fit Score and Headline

**Score: 44/100**

A strong product operator who knows regulated financial systems inside out. But the AI gap is real. This candidate has never shipped an AI product, never written evals, and never worked directly with ML engineers. For a role that puts "AI platform" in the title, that's a hard gap to overcome without a very compelling interview.

## 2. Requirements Map

| Requirement | Evidence From Candidate | Confidence | Source |
|---|---|---|---|
| 5+ years PM in fintech/financial services | 9+ years at BMO. Formal PM title for 2.5 years, but PM-equivalent work for 6+ years when you count the Solutions Architect and Delivery Lead roles. | Strong Match | Both |
| Experience with ML/AI products or data platforms | Worked alongside vendor ML analytics platforms in the FRTB program. Contributed to an NLP assessment product at Aspiring Minds. But this was exposure, not ownership. Never defined model requirements or evaluation criteria. | Gap | LinkedIn |
| Understanding of regulatory environments | This is where the candidate shines. 6+ years inside FRTB regulatory reporting. Broke down complex regulatory requirements into specs that dev teams could build against. Balanced compliance, feasibility, and usability in solution design. | Strong Match | Both |
| Work with ML engineers and data scientists | Partnered with engineering and data teams across multiple programs. Led working sessions with business, data, and engineering stakeholders. But no specific mention of ML engineers, researchers, or data scientists. | Partial Match | Both |
| Define and track product metrics (B2B) | Cut manual reporting requests by about 60% with self-serve dashboards. Raised agile maturity from 3.6 to 4.1. These are real metrics but they're operational, not product-level. No retention curves, adoption funnels, or model performance metrics. | Partial Match | Resume |
| Stakeholder management across technical and non-technical | Strongest signal in the profile. Every role shows this. Risk teams, technology teams, operations, governance, vendors. Resolved key design decisions without positional authority. | Strong Match | Both |
| User research with risk analysts | Gathered requirements from business stakeholders. Designed dashboards based on workflow needs. But no evidence of formal user research methods like interviews, usability testing, or surveys. | Partial Match | Resume |

## 3. Adjacent Work Recognition

**"Solutions Architect" at BMO (2021-2024) = Product Manager**
Title says architect. Work says PM. This person investigated recurring issues by mapping end-to-end workflows across systems. They led cross-team sessions to align business, data, and engineering stakeholders on problem definitions. They broke down regulatory requirements into use cases with acceptance criteria. They proposed solution approaches that balanced multiple constraints.

That's problem framing, stakeholder alignment, requirements definition, and solution scoping. Classic PM work.

This matters because it extends their effective PM experience from 2.5 years to 5.5+ years. Without recognizing this, they don't meet the "5+ years PM" bar. With it, they clear it comfortably.

Evidence strength: Strong. Multiple specific examples across both documents.

**"Business Analyst" at BMO (2017-2019) = Data Product Thinking**
Analyzed source data and database structures using SQL. Partnered with engineers to define reporting logic. Made sure dashboards reflected business decision needs rather than raw system outputs.

That last part is the key. Translating raw data into tools people actually use to make decisions is data product thinking.

This matters for the "data-intensive platforms" requirement. Shows the candidate can bridge data and business needs, even if they did it from a BA chair.

Evidence strength: Moderate. The work is relevant but described in BA language.

**Product Consultant at Aspiring Minds = Early AI Exposure**
Conducted statistical analysis linking assessment performance with job outcomes. Led proof-of-concept studies for enterprise clients on NLP-based assessment products.

This provides a thin thread connecting the candidate to ML product work. But it was 10+ years ago and in a consulting capacity. Not ownership.

Evidence strength: Weak. Too old and too peripheral to carry much weight.

## 4. What the Hiring Manager Is Thinking

"Nine years at one bank. Okay, loyal or stuck? Let me scan. Product Owner, Solutions Architect, Delivery Lead. None of these scream AI PM. The regulatory angle is interesting though. We need someone who gets compliance and we've been struggling to find that.

But wait. I need this person talking to our ML team about model evaluation and deployment strategies. I'm not seeing any of that. The NLP thing from Aspiring Minds is too old to count.

The 60% reduction in manual reporting is a solid number. Shows they can ship and measure. But our world is different. We ship models, not dashboards.

Putting this in the 'no' pile for now. Unless our recruiter tells me this person can actually talk about AI with fluency. Then maybe a phone screen. But I'd need to hear it myself."

## 5. Biggest Weakness + Flip Strategy

**The weakness:** Zero shipped AI products. The role title literally says "AI Platform" and the candidate has never owned an AI product, written model evals, or worked directly with ML engineers. In a market where "almost all AI PM jobs ask for prior hands-on AI PM experience," this is a dealbreaker-level gap.

**Flip strategy:**
Don't pretend the gap doesn't exist. Own it and reframe it.

The angle: "Most AI PMs come from the technical side and learn compliance on the job. I come from the other direction. I've spent 9 years watching ML model outputs flow through risk reporting systems. I know what happens when model governance fails, because I've seen the regulatory consequences. Your AI risk assessment platform needs someone who understands both sides of that equation."

**Interview response:** "I haven't built an AI product from scratch, and I won't pretend otherwise. But I've spent the last 6 years working inside a regulatory reporting program where vendor ML analytics platforms were core to our workflow. I've seen how model risk management, regulatory requirements, and product usability collide in practice. That domain knowledge is the hard part. The AI product skills I can build. The regulatory intuition took 9 years."

To make this flip work, the candidate should also show they're actively building AI fluency. A side project using Claude or a small AI tool they've built would go a long way.

## 6. Top 3 Strongest Stories

**1. Self-serve risk reporting platform (Product Owner, BMO)**
Cut manual executive reporting requests by about 60%. Redesigned fragmented risk governance workflows into self-serve dashboards. Defined the MVP backlog, aligned three teams (risk, ops, technology), and drove adoption through onboarding and change management.

Why it resonates: End-to-end product ownership in a regulated financial environment. Same context as the target role. The 60% number sticks.

The hook: "Replaced a process where analysts manually compiled reports for executives, with a platform where executives could get answers themselves."

**2. Cross-functional alignment on FRTB program (Solutions Architect, BMO)**
Resolved key design decisions across risk, technology, and operations teams within a multi-year regulatory program. Did this without direct authority over any of those teams. Turned undocumented institutional knowledge into specs that dev teams could actually build against.

Why it resonates: The "without direct authority" detail is pure PM signal. The regulatory context maps directly to this role's compliance requirements.

The hook: "Nobody owned the full picture. I made myself the person who did."

**3. NLP assessment product (Aspiring Minds)**
Worked on an NLP-based assessment product supporting multi-million-dollar enterprise contracts. Led proof-of-concept studies linking assessment performance to job outcomes.

Why it resonates: The only direct AI/ML touchpoint. While early-career, it shows the candidate has been in the room where ML products get built and sold.

The hook: Weak. This story needs more specific detail to land. The candidate should reconstruct what they remember about the NLP product decisions and data challenges.

## 7. Hygiene Check

| What | Resume Says | LinkedIn Says | Risk | Action |
|---|---|---|---|---|
| No inconsistencies found | Titles, dates, and company info are consistent across both documents | Same | N/A | Clean check. This is a positive signal. |

The resume and LinkedIn tell the same story at different levels of detail. LinkedIn has richer descriptions. Resume is more concise. No factual conflicts.

## 8. Resume Narrative Assessment

**Rating: Underselling**

The resume is okay but it misrepresents the candidate's actual strength. Three specific problems:

1. **The Solutions Architect role reads like an analyst role.** The resume describes investigation and analysis work. But LinkedIn reveals full product-scope work: stakeholder alignment, requirements decomposition, solution design, and implementation coordination. Reframe this role in PM language. The current framing is costing the candidate 3 years of product experience that hiring managers can't see.

2. **Key metrics are missing.** The Product Owner role has the 60% number, which is good. But the Solutions Architect role (3 years) and Delivery Lead role have almost no quantified outcomes. LinkedIn mentions "raising agile maturity from 3.6 to 4.1." That should be on the resume.

3. **The AI connection is invisible.** The Aspiring Minds work with NLP products and statistical analysis is barely described. For an AI PM role, this needs way more detail. What was the NLP model doing? What were the enterprise client decisions based on? What did the candidate learn about ML products? Every detail here counts.

---

*Generated by [Job Fit Analyzer](https://github.com/dj-chow/job-fit-analyzer). A Claude skill that evaluates job fit by analyzing work activities, not just titles and keywords.*
