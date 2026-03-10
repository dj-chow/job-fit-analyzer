# Sample Analysis Output

> Sample output from Job Fit Analyzer. Uses a two-layer model: a screen check for hard gate needs, then a weighted fit score across role areas. The person is a PM with 9+ years in banking (risk and regulatory reporting) applying for a Senior AI PM role at a Series B fintech startup. This output has 10 parts.

---

## 0. Screen Check

Before scoring areas, the tool checks if the person clears the hard gate needs for this role. These are the must-have items that a recruiter or hiring manager would screen for in 30 seconds.

| Hard Gate | What the JD Asks For | Candidate Evidence | Verdict |
|---|---|---|---|
| ML/AI product experience | "Experience working with ML/AI products or data-intensive platforms" | Worked with vendor ML analytics platforms at BMO. Helped with an NLP product at Aspiring Minds, but that was 10+ years ago and in a consulting role. This is exposure, not ownership. No signs of defining model needs, running evals, or owning an AI product. | **Fail** |
| Work with ML engineers and data scientists | "Demonstrated ability to work with technical teams (ML engineers, data scientists)" | Worked with eng and data teams across many programs. Led sessions with business, data, and eng groups. But no direct mention of working with ML engineers, ML researchers, or data scientists. The tech teamwork is real, but the ML flavor is missing. | **Partial** |

**Screen verdict: Borderline**

One Fail and one Partial. The ML/AI gate is a clear miss, though there is thin nearby proof (vendor ML platforms, early NLP work). The tech teamwork gate is close but lacks ML-based proof points. A recruiter who follows the JD strictly would likely pass on this person. But a hiring manager who values the regulatory domain might still do a phone screen to test AI fluency in person.

This screening risk carries into the fit score below.

---

## Dimension Scores

Using AI/ML Product Management criteria from `role-criteria/ai-product-management.md`:

| Dimension | Weight | Score | Level | Key Evidence |
|---|---|---|---|---|
| Shipped AI/ML Product Experience | 25% | 25 | Weak | Worked with vendor ML analytics platforms. Helped with an NLP product 10+ years ago. No signs of owning an AI product end-to-end. |
| Technical Fluency for AI | 20% | 35 | Weak | Worked with data teams and knew system links. No signs of talking about model limits, evals, or training methods. |
| Eval and Quality Framework Thinking | 15% | 45 | Partial | Built self-serve dashboards with ops metrics. Has a testing mindset from reporting work. But no work with model quality thresholds or model review. |
| Product Ownership and Shipping | 15% | 82 | Strong | Owned risk reporting platform as Product Owner. Shipped self-serve dashboards, drove adoption, tracked results. Clear end-to-end ownership. |
| Breadth of Domain Experience | 15% | 50 | Partial | Deep in one domain (banking risk). Some breadth from edtech (UpGrad) and test products (Aspiring Minds). But career is mostly in financial services. |
| Stakeholder Alignment | 10% | 90 | Strong | Every role shows cross-team alignment. Resolved design calls without authority across risk, tech, ops, and governance teams. This is the person's superpower. |

**Weighted average:** 46.3
**Critical gap penalty:** -10 (Shipped AI/ML Product scores below 20 threshold after rounding)
**Corroboration bonus:** +3 (4 areas have proof in both docs)
**Override:** +5 (Regulatory domain expertise is called for in this JD. This rare mix of risk domain knowledge + product skills is truly useful for an AI risk platform.)

---

## 1. Fit Score and Headline

**Score: 44/100**
**Screen: Borderline** (1 Fail, 1 Partial on hard gates)

A strong product operator who knows regulated systems inside out, but flagged at screening for lack of direct AI/ML work. The person has never shipped an AI product, never written evals, and never worked directly with ML engineers. For a role with "AI platform" in the title, that's a hard gap to beat without a very strong interview. The screening risk means this app likely gets filtered out before a human reads the full profile.

## 2. Requirements Map

| Requirement | Evidence From Candidate | Confidence | Source |
|---|---|---|---|
| 5+ years PM in fintech/financial services | 9+ years at BMO. Formal PM title for 2.5 years, but PM-level work for 6+ years when you count the Solutions Architect and Delivery Lead roles. | Strong Match | Both |
| Experience with ML/AI products or data platforms | Worked alongside vendor ML analytics platforms in the FRTB program. Helped with an NLP product at Aspiring Minds. But this was exposure, not ownership. Never defined model needs or eval criteria. | Gap | LinkedIn |
| Understanding of regulatory environments | This is where the person shines. 6+ years inside FRTB regulatory reporting. Broke down complex rules into specs that dev teams could build against. Balanced compliance, feasibility, and usability in solution design. | Strong Match | Both |
| Work with ML engineers and data scientists | Worked with eng and data teams across many programs. Led sessions with business, data, and eng groups. But no direct mention of ML engineers, researchers, or data scientists. | Partial Match | Both |
| Define and track product metrics (B2B) | Cut manual reporting requests by about 60% with self-serve dashboards. Raised agile maturity from 3.6 to 4.1. These are real numbers but they're ops-level, not product-level. No retention curves, adoption funnels, or model performance metrics. | Partial Match | Resume |
| Stakeholder management across technical and non-technical | Strongest signal in the profile. Every role shows this. Risk teams, tech teams, ops, governance, vendors. Resolved key design calls without position power. | Strong Match | Both |
| User research with risk analysts | Gathered needs from business groups. Designed dashboards based on workflow needs. But no signs of formal user research methods like interviews, usability testing, or surveys. | Partial Match | Resume |

## 3. Adjacent Work Recognition

**"Solutions Architect" at BMO (2021-2024) = Product Manager**
Title says architect. Work says PM. This person looked into repeat issues by mapping end-to-end flows across systems. They led cross-team sessions to align business, data, and eng groups on problem scope. They broke down regulatory needs into use cases with acceptance criteria. They proposed fixes that balanced many constraints.

That's problem framing, team alignment, requirements work, and solution scoping. Classic PM work.

This matters because it extends their real PM time from 2.5 years to 5.5+ years. Without seeing this, they don't meet the "5+ years PM" bar. With it, they clear it well.

Proof strength: Strong. Many specific cases across both docs.

**"Business Analyst" at BMO (2017-2019) = Data Product Thinking**
Looked at source data and database structures using SQL. Worked with engineers to define reporting logic. Made sure dashboards showed what people needed to make calls, not just raw system outputs.

That last part is the key. Turning raw data into tools people actually use to decide things is data product thinking.

This matters for the "data platforms" need. Shows the person can bridge data and business needs, even if they did it from a BA seat.

Proof strength: Moderate. The work fits but is written in BA terms.

**Product Consultant at Aspiring Minds = Early AI Exposure**
Ran stats work linking test results with job outcomes. Led proof-of-concept studies for big clients on NLP-based test products.

This gives a thin link to ML product work. But it was 10+ years ago and in a consulting role. Not ownership.

Proof strength: Weak. Too old and too small to carry much weight.

## 4. What the Hiring Manager Is Thinking

"Nine years at one bank. Okay, loyal or stuck? Let me scan. Product Owner, Solutions Architect, Delivery Lead. None of these scream AI PM. The regulatory angle is notable though. We need someone who gets compliance and we've been struggling to find that.

But wait. I need this person talking to our ML team about model review and deploy plans. I'm not seeing any of that. The NLP thing from Aspiring Minds is too old to count.

The 60% cut in manual reporting is a solid number. Shows they can ship and measure. But our world is different. We ship models, not dashboards.

Putting this in the 'no' pile for now. Unless our recruiter tells me this person can truly talk about AI with fluency. Then maybe a phone screen. But I'd need to hear it myself."

## 5. Biggest Weakness + Flip Strategy

**The weakness:** Zero shipped AI products. The role title says "AI Platform" and the person has never owned an AI product, written model evals, or worked directly with ML engineers. In a market where nearly all AI PM jobs ask for prior hands-on AI PM work, this is a deal-breaker level gap.

**Flip strategy:**
Don't pretend the gap doesn't exist. Own it and reframe it.

The angle: "Most AI PMs come from the tech side and learn compliance on the job. I come from the other way. I've spent 9 years watching ML model outputs flow through risk reporting systems. I know what happens when model governance fails, because I've seen the regulatory fallout. Your AI risk platform needs someone who knows both sides of that picture."

**Interview response:** "I haven't built an AI product from scratch, and I won't pretend I have. But I've spent the last 6 years working inside a regulatory reporting program where vendor ML analytics platforms were core to our flow. I've seen how model risk, regulatory needs, and product usability clash in practice. That domain knowledge is the hard part. The AI product skills I can build. The regulatory instinct took 9 years."

To make this flip work, the person should also show they're building AI fluency now. A side project using Claude or a small AI tool they've built would go a long way.

## 6. Top 3 Strongest Stories

**1. Self-serve risk reporting platform (Product Owner, BMO)**
Cut manual executive reporting requests by about 60%. Rebuilt messy risk governance flows into self-serve dashboards. Defined the MVP backlog, aligned three teams (risk, ops, tech), and drove adoption through onboarding and change management.

Why it lands: End-to-end product ownership in a regulated financial setting. Same context as the target role. The 60% number sticks.

The hook: "Replaced a process where analysts hand-built reports for executives, with a platform where executives could get answers themselves."

**2. Cross-team alignment on FRTB program (Solutions Architect, BMO)**
Resolved key design calls across risk, tech, and ops teams within a multi-year regulatory program. Did this without direct authority over any of those teams. Turned unwritten know-how into specs that dev teams could build against.

Why it lands: The "without direct authority" detail is pure PM signal. The regulatory context maps straight to this role's compliance needs.

The hook: "Nobody owned the full picture. I made myself the person who did."

**3. NLP test product (Aspiring Minds)**
Worked on an NLP-based test product backing multi-million-dollar enterprise deals. Led proof-of-concept studies linking test results to job outcomes.

Why it lands: The only direct AI/ML touch point. While early in their career, it shows the person has been in the room where ML products get built and sold.

The hook: Weak. This story needs more detail to land. The person should recall what they remember about the NLP product calls and data issues.

## 7. Score Improvement Roadmap

Here's what would move the needle for this person applying to AI PM roles.

**Action 1: Build and ship an AI tool in your domain.**
Build something small that uses AI to solve a real problem you know. For example: a Claude tool that reads regulatory docs and pulls out reporting needs on its own. Or an AI helper that aids risk analysts in checking data outputs. Ship it publicly. Get even a few real users.

Why it helps: This directly fixes Area 1 (Shipped AI/ML Product), the weakest score at 25. Going from "has never built AI" to "has built and shipped a working AI tool" changes the whole story. Hiring managers at OpenAI, Google, and Meta keep saying shipped product is the best signal, even small ones.

Score impact: Could move Area 1 from 25 to 50-55, adding roughly 6-8 points to the total score.
Time needed: 2-4 weeks of focused building.

**Action 2: Write and publish an eval framework for AI in risk work.**
Write a public piece (blog post, GitHub repo, or LinkedIn article) that defines how you'd judge an AI-powered credit risk or regulatory reporting product. What does "good" look like? What are the failure modes? How do you measure quality when the output varies? Include specific metrics and thresholds.

Why it helps: Eval-writing is replacing PRDs as the core AI PM artifact. Jake Brill at OpenAI said PMs write the best evals because they know how the product should work. A banking PM who publishes domain-based AI evals shows they think in the new way. This fixes Area 3 (Eval and Quality Framework Thinking), now at 45.

Score impact: Could move Area 3 from 45 to 65-70, adding roughly 3-4 points to the total score.
Time needed: 1-2 weeks.

**Action 3: Build your AI vocab through daily use and public writing.**
Use AI tools daily in your real work. Then write about it. Not "I took an AI course" but "I used Claude to automate our quarterly risk report and here's what I learned about prompt design, output checking, and where AI breaks down in regulated contexts."

Why it helps: Fixes Area 2 (Technical Fluency for AI), now at 35. Hiring managers check if people truly use AI in their work. Public writing about the process shows tech fluency and critical thinking about AI limits, not just hype.

Score impact: Could move Area 2 from 35 to 50-55, adding roughly 3-4 points to the total score.
Time needed: Ongoing. 2-3 LinkedIn posts or articles over 4-6 weeks.

**Combined impact:** If the person does all three, the total score could move from 44 to roughly 56-60. That shifts them from "stretch pick" to "partial fit with real strengths." Paired with regulatory domain expertise and strong stakeholder skills, that might be enough to get a phone screen at the right company.

## 8. Hygiene Check

| What | Resume Says | LinkedIn Says | Risk | Action |
|---|---|---|---|---|
| No issues found | Titles, dates, and company info are the same across both docs | Same | N/A | Clean check. This is a good signal. |

The resume and LinkedIn tell the same story at different levels of detail. LinkedIn has richer notes. Resume is more concise. No factual clashes.

## 9. Resume Narrative Assessment

**Rating: Underselling**

The resume is okay but it hides the person's real strength. Three specific problems:

1. **The Solutions Architect role reads like an analyst role.** The resume talks about looking into issues and doing reviews. But LinkedIn shows full product-scope work: team alignment, breaking down needs, solution design, and shipping. Reframe this role in PM terms. The current framing costs the person 3 years of product work that hiring managers can't see.

2. **Key numbers are missing.** The Product Owner role has the 60% number, which is good. But the Solutions Architect role (3 years) and Delivery Lead role have almost no measured results. LinkedIn mentions "raising agile maturity from 3.6 to 4.1." That should be on the resume.

3. **The AI link is hidden.** The Aspiring Minds work with NLP products and stats is barely described. For an AI PM role, this needs much more detail. What was the NLP model doing? What were the client calls based on? What did the person learn about ML products? Every detail here counts.

---

*Generated by [Job Fit Analyzer](https://github.com/dj-chow/job-fit-analyzer). A Claude skill that checks job fit by looking at work done, not just titles and keywords.*
