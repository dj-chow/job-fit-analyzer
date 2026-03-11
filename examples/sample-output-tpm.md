# Sample Analysis Output: Technical Program Manager (Unsupported Role)

> Sample output from Job Fit Analyzer. Uses a two-layer model: a screen check for hard gate needs, then a weighted fit score across role areas. The person is a PM with 9+ years in banking (risk and regulatory reporting) applying for a Technical Program Manager, Generative AI role at a major Canadian bank's AI research division. This role is NOT one of the four supported types, so the tool created custom scoring dimensions from the JD and shared rules. This output has 10 parts.

\---

## 0\. Screen Check

This JD does not use "required" or "must have" language for any specific tool, platform, or certification. However, three items function as practical screening filters given the role sits inside the bank's AI research arm.

| # | Hard Gate Requirement | Evidence | Verdict |
|---|---|---|---|
| 1 | Gen-AI technical fluency (understanding of generative AI capabilities, limitations, implementation strategies) | LinkedIn lists an internal AI awareness certification (not hands-on). Worked at TalentScope on an NLP-based assessment product (2012-2015), but that is 11 years old and pre-dates the GenAI era. No evidence of working with LLMs, prompt engineering, fine-tuning, RAG, or AI deployment pipelines. | Partial |
| 2 | Hands-on experience building internal tools with Gen-AI powered IDE and low-code environments | Resume lists Power Apps under tools (low-code, but not GenAI-powered). No mention of Cursor, Copilot, Replit Agent, or any GenAI-powered IDE. No shipped GenAI-powered internal tool in either document. | Fail |
| 3 | Title match to role family (Program Manager / TPM / Delivery Manager) | Titles held: Agile Delivery Lead, Solution Architect, Product Owner, Lead Business Analyst, Product Manager, Product Consultant, Co-Founder. None of these are "Program Manager," "TPM," or "Delivery Manager." "Agile Delivery Lead" is the closest but reads as an agile facilitation role, not a standard program management title. ATS keyword searches for "Program Manager" or "TPM" would not return this profile. | Partial |

**Screen Verdict: Borderline**

This person is on the edge. Passing the screen depends on the recruiter, the applicant pool, and how well the application frames nearby experience. One Fail on GenAI tooling, two Partials on AI fluency and title match. A recruiter who reads past the title will see strong program-level delivery work at a major bank. One who relies on keyword filters or expects explicit GenAI experience will pass.

\---

## Dimension Scores

> Note: Technical Program Manager is not a supported role. These dimensions were built from the JD and shared scoring rules. Scores are less exact than for supported roles.

| Dimension | Weight | Score | Level | Key Evidence |
|---|---|---|---|---|
| Program/Delivery Management | 25% | 78 | Solid | Currently leads delivery across a 10-squad regulatory program. Increased throughput ~25% (50 to 63 items/sprint). Managed a $20M+ multi-year program coordinating six delivery teams. Delivered a risk governance platform from failed pilot to 250+ users. Strong and recent, but the resume never uses "program management" language. |
| Cross-functional Alignment | 25% | 82 | Strong | Created Design Authority sessions resolving 10 critical trade-offs across risk, front office, and technology on a $20M+ program. Drove decisions without direct authority (confirmed on both documents). Aligned risk, operations, and technology teams on shared workflows. Change management certification adds credibility. |
| AI/ML Technical Fluency | 20% | 25 | Weak | Internal AI awareness certification. NLP-based assessment work at TalentScope is 11 years old and pre-dates modern GenAI. No evidence of working with LLMs, prompt engineering, model evaluation, or AI deployment. This is the biggest gap and it sits at the center of what this AI lab does. |
| Strategic Communication | 15% | 72 | Solid | Presented program strategy to leadership at LearnPath. Socialized recommendations with program leadership at Meridian Bank. Designed executive reporting dashboards. Change management certified. Good proof of leadership-facing communication, but no evidence of C-suite or board-level reporting. |
| Technical Versatility | 15% | 38 | Weak | Lists Power Apps, SQL, Kibana, AWS Foundational, Clarity. Built a data warehouse from scratch. No evidence of building with GenAI-powered IDEs. No AI-assisted tooling. The JD specifically asks for this and the gap is clear. |

**Weighted average:** 61.50
**Critical gap penalty:** None (no dimension below 20)
**Corroboration bonus:** +3 (3 dimensions backed by both documents)
**Override:** -3.5 (Two of five dimensions are specifically about generative AI. These are the defining features of a role inside an AI research lab. Scoring 25 and 38 on the traits that make this role different from a regular TPM means the math overstates the practical fit.)

\---

## 1\. Fit Score and Headline

**Score: 61/100**
**Screen: Borderline** (1 Fail, 2 Partials on hard gates)

Screening is a coin flip. The missing TPM title, absent GenAI hands-on experience, and lack of AI tooling could filter this person out before anyone reads the full profile. If screened in, this is a strong delivery operator who has run multi-team programs in regulated financial services for years. The AI dimension is the real gap, and it matters more here than in most TPM roles because this seat lives inside an AI research lab.

## 2\. Requirements Map

| Requirement | Evidence From Candidate | Confidence | Source |
|---|---|---|---|
| Cross-functional alignment across engineering, product, data science, and senior stakeholders | Created Design Authority sessions across risk, front office, and technology. Resolved 10 critical trade-offs on a $20M+ program. Coordinated delivery across 10 squads spanning engineering teams, business stakeholders, and vendor systems. | Strong Match | Both |
| End-to-end program delivery across multiple AI product workstreams | Managed a $20M+ multi-year regulatory program through multiple phases. Delivered a risk platform from pilot to 250+ users. Led a learning program from business case to 5,000+ learners. Programs were regulatory/data platforms, not AI product workstreams. The delivery pattern is strong but the AI product context is absent. | Partial Match | Both |
| Strategic communication to leadership including risk assessments | Presented program strategy to leadership. Designed executive reporting dashboards. Socialized recommendations with program leadership. Change management certified. Good proof of leadership-facing communication, but no evidence of C-suite briefings or board-level reporting. | Partial Match | Both |
| Primary point of contact for program decisions | Served as the decision-maker on a risk governance platform as Product Owner. Unblocked three years of stalled decisions on a regulatory program. Currently the delivery lead for a 10-squad program. Pattern of being the go-to person for decisions is consistent across roles. | Strong Match | Both |
| GenAI technical fluency (capabilities, limitations, implementation strategies) | Internal AI awareness certification. NLP-based assessment product work at TalentScope, 11 years ago. No evidence of working with LLMs, GenAI architectures, or modern AI implementation strategies. | Gap | LinkedIn |
| Build AI-powered internal productivity tools and dashboards | Built self-serve dashboards and a KPI data warehouse. Lists Power Apps. None of these involved AI or GenAI. No evidence of building with AI-powered IDEs or shipping AI-powered tools. | Gap | Resume |
| Working with data scientists and ML engineering teams | No direct evidence of working alongside data science or ML teams. Worked with risk analysts, front office traders, and engineering teams. The closest is the TalentScope NLP work, which is too old to count. | Gap | Neither |

## 3\. Adjacent Work Recognition

**"Solutions Architect" at Meridian Bank (2021-2024) = Program Management**

Title says architect. Work says program manager. This person ran cross-functional alignment across a $20M+ regulatory program. Created Design Authority sessions. Resolved 10 critical trade-offs across risk, front office, and technology. Mapped front office workflows and translated them into specs for six delivery teams. This is program management and stakeholder alignment work, not architecture.

Why it matters: The TPM role coordinates multiple teams and drives decisions without authority. This person did exactly that for three years at a major bank.

Proof strength: Strong. Both documents describe the same work with consistent details.

**"Product Owner" at Meridian Bank (2019-2021) = Program Delivery and Change Management**

Title says product owner. Work went well beyond backlog grooming. Inherited a failed pilot and turned it into a 250+ user platform. Ran persona-based discovery, found the real blocker (executives resisted transparency), redesigned the approach, and drove adoption. Led onboarding, training, and change management. Shipped MVP with a two-person team, then scaled.

Why it matters: The TPM will need to drive adoption of AI tools across teams that may resist. This person has done adoption work in a resistant, politically sensitive environment.

Proof strength: Strong. Metrics and outcomes confirmed in both documents.

**"Agile Delivery Lead" at Meridian Bank (2024-Present) = Portfolio-level Program Coordination**

Title says delivery lead. Scope says program coordinator. Restructured planning and dependency management across a 10-squad program spanning market risk and counterparty credit risk platforms. Managed cross-team dependencies and sequencing across multiple workstreams. Improved delivery predictability, raising agile maturity from 3.6 to 4.1.

Why it matters: Direct match to "manage the lifecycle of multiple workstreams" and "coordinate strategic alignment between multiple engineering teams."

Proof strength: Strong. Both documents describe the same scope. LinkedIn adds richer context about platform scope.

## 4\. What the Hiring Manager Is Thinking

"First thing: no TPM or Program Manager title anywhere. I searched for 'Program Manager' and this resume did not come up. If the recruiter passed this through, it was either a manual referral or someone read it closely. Most ATSs would not flag this profile for my role."

"The person calls themselves a Product Manager on LinkedIn. That is a different job. I need a TPM who coordinates teams. I do not need someone who owns a product backlog. But wait, the current role is 'Agile Delivery Lead' managing 10 squads. That is closer. Still, the title does not match what I posted."

"If I keep reading, the work is interesting. Nine years at a top bank. They have run a $20M+ regulatory program, coordinated six delivery teams, and resolved cross-functional trade-offs. That is TPM-shaped work. The 250+ user platform story shows they can ship and drive adoption. I like that."

"But this is an AI lab. I need someone who can sit in a room with ML engineers and discuss model performance, GenAI limitations, and deployment trade-offs. I see an internal AI cert and NLP work from 2012. That is not enough. My team lives in the GenAI space. Everyone here builds with Copilot, talks about RAG pipelines, and debates fine-tuning vs. prompt engineering. This person would be lost in those conversations."

"Bottom line: strong program operator, wrong domain. If I had an open TPM role in my regulatory technology group, this person would be a strong candidate. For an AI-focused role at the lab, the domain gap is too big unless they can prove they have been building with GenAI tools on the side."

## 5\. Biggest Weakness + Flip Strategy

**The weakness:** No hands-on generative AI experience. This role sits inside an AI research lab. The hiring manager expects someone who can discuss model capabilities, limitations, and implementation trade-offs with data scientists and ML engineers. The candidate's AI exposure is limited to an awareness-level internal certification and decade-old NLP work. That is not enough for an AI lab.

**Flip strategy:**

The candidate cannot fake AI depth. But they can reframe the gap and start closing it before applying.

In a cover letter, do not ignore the gap. Name it and pivot. "I have not built ML models, and that is not what you need a TPM to do. What you need is someone who can take what your AI teams are building, coordinate across engineering and product, and make sure it ships on time and gets adopted. I have done exactly that for regulatory programs at a major bank. My Design Authority sessions resolved three years of stalled decisions across six delivery teams. I am now applying that same approach to GenAI, starting with [specific project built with AI tools]."

Proof that partly covers it: the TalentScope NLP product work shows past comfort with AI-adjacent products. The risk governance platform shows the ability to build internal tools and drive adoption among resistant stakeholders. The Design Authority sessions show the person can facilitate technical trade-off conversations between teams with different priorities.

**Interview answer:** "My value is not AI depth. It is making programs deliver. I unblocked three years of stalled decisions on a $20M regulatory program by creating Design Authority sessions that forced trade-offs into the open. I have started building with GenAI tools to understand the space from the inside. But what I bring is the ability to coordinate complex, multi-team programs and make them ship. That is what a TPM does, regardless of the domain."

(This answer only works if the candidate actually starts building with GenAI tools before the interview.)

## 6\. Top 3 Strongest Stories

**1. Unblocking three years of stalled decisions on a $20M+ program**

Product decisions on a regulatory program had been stuck for three years. The candidate created cross-functional Design Authority sessions that brought risk, front office, and technology teams together. Resolved 10 critical trade-offs that had blocked progress.

Why it works: TPMs at the AI lab coordinate multiple engineering teams, product managers, and data scientists. Driving decisions across teams without direct authority is the core TPM skill. This story proves it at scale, in a regulated environment.

The hook: Three years stuck, ten trade-offs resolved, no direct authority. The duration of the stall and the specificity of the outcome make this memorable.

**2. Turning a failed pilot into a 250+ user platform**

Inherited a risk reporting pilot that executives resisted because it surfaced issues they would have to defend. Ran persona-based discovery, found the real adoption blocker, redesigned the approach with transparent risk thresholds, and grew it to 250+ users. Cut executive reporting requests by 60% and freed about $200K per year.

Why it works: The TPM will need to drive adoption of AI tools across teams. This story shows the candidate can diagnose why people resist a new tool, redesign the approach, and get real usage.

The hook: A tool executives avoided became one used by 250+ people. The reason they avoided it (accountability) is a sharp insight that sticks.

**3. Managing a 10-squad delivery program and increasing throughput 25%**

Restructured planning and dependency management across a 10-squad regulatory program. Product throughput increased from 50 to 63 items per sprint. Unplanned work dropped. Earned the portfolio's highest agile maturity rating.

Why it works: This is the core TPM function. Coordinating multiple teams, managing dependencies, and making delivery predictable. Ten squads is real scale.

The hook: The throughput numbers (50 to 63) are concrete. "Highest agile maturity rating in the portfolio" is a verifiable comparison point.

## 7\. Score Improvement Roadmap

**Action 1: Build and ship an internal tool using a GenAI-powered IDE**

Pick a real problem from your current work or domain (report generation, dependency tracking, risk summary automation) and build a working tool using Cursor, Copilot, or Replit Agent. Document the build process. Put the code on GitHub. Write about what you built and what you learned about GenAI capabilities and limits.

Why it helps: Covers both the AI/ML Technical Fluency dimension (learn GenAI by using it) and the Technical Versatility dimension (build with GenAI-powered IDEs). This also directly addresses the hard gate Fail on GenAI tooling.

Score impact: Could move AI/ML Technical Fluency from 25 to 40 and Technical Versatility from 38 to 55. Combined weighted impact: roughly +6 points to total score.
Time needed: 2-4 weeks for a meaningful project.

**Action 2: Publish GenAI content showing practical fluency**

Write 2-3 LinkedIn posts or articles about GenAI applied to financial services, internal tooling, or program management. Ground each post in something you built or learned, not just opinions.

Why it helps: Strengthens the AI/ML Technical Fluency dimension and creates searchable content. When the hiring manager checks LinkedIn, GenAI content shifts the narrative from "traditional bank PM" to "someone who understands this space."

Score impact: Could move AI/ML Technical Fluency from 25 to 35 on its own (or from 40 to 50 if combined with Action 1). Adds roughly 2-3 points.
Time needed: 1-2 weeks for 2-3 solid posts.

**Action 3: Reframe your LinkedIn headline and role descriptions to signal TPM work**

Your LinkedIn headline says "Product Manager." Your current role is "Agile Delivery Lead." Neither signals TPM or program management. Update the headline to include "Program Delivery" or "Technical Program Delivery" language. In the current role description, add "program management" and "cross-team coordination" where they honestly apply. You are already doing this work. The problem is that no one can find it.

Why it helps: Addresses the title match screening gap. ATS systems and recruiter searches for "Program Manager" or "TPM" would start finding your profile. This does not change your skills, but it changes whether anyone sees them.

Score impact: Does not change the fit score (title is a visibility problem, not a skills gap). But it directly improves the screen verdict, which matters more than score points for getting an interview.
Time needed: 1-2 hours.

## 8\. Hygiene Check

| What | Resume Says | LinkedIn Says | Risk | Action |
|---|---|---|---|---|
| Solutions Architect title | "Solution Architect" | "Solutions Architect" | Low | Pick one spelling and use it in both places. Small but avoidable. |
| Business Analyst title | "Lead Business Analyst" | "Business Analyst" | Medium | Looks like title inflation. If the official title included "Lead," update LinkedIn. If not, remove "Lead" from the resume. Titles must match. |
| Revenue claim at TalentScope | "$2M+ in enterprise contracts" | "contributed to early client adoption and commercialization" | Low | Not a direct conflict, but LinkedIn does not confirm the $2M figure. Adding it to LinkedIn would strengthen consistency. |

Overall hygiene: Clean with one medium flag. The title difference on the BA role is the most important item to fix. Neither issue is a dealbreaker, but the title difference could raise questions during a background check.

## 9\. Resume Narrative Check

**Rating: Underselling**

The resume is well-structured and outcome-focused for a Product Manager role. But it is not written for a TPM role, and that is a problem when applying to a TPM position.

**No program management language anywhere.** The resume never uses the words "program," "program management," or "cross-team coordination" as primary descriptors. The Agile Delivery Lead section describes program-level work (10-squad, dependency management, throughput metrics) but frames it in agile delivery terms. A TPM hiring manager would miss it in a 7-second scan.

**AI experience is invisible.** The internal AI certification only appears on LinkedIn, not the resume. The NLP work at TalentScope is buried in "Earlier Roles." For a GenAI TPM role, any AI-adjacent experience should be visible in the first few seconds.

**Summary positions as a product builder, not a program leader.** The summary says "I build internal data products." That is a product manager message. For a TPM role, the summary should lead with multi-team program delivery and cross-functional alignment.

**Solutions Architect role hides program management work.** The first bullet talks about expanding risk decomposition from single-layer to multi-layer structures. That reads like architecture. The real TPM story (coordinating a $20M+ program, resolving stalled decisions across six teams) is in the second bullet. For a TPM application, flip the order.

The person behind this resume is stronger than the resume shows for TPM roles. LinkedIn tells a more TPM-aligned story. Phrases like "coordinating delivery across internal engineering teams, business stakeholders, and vendor systems" and "resolving key design decisions without direct authority" are TPM gold. They do not appear on the resume.

\---

*Generated by [Job Fit Analyzer](https://github.com/dj-chow/job-fit-analyzer). A Claude skill that checks job fit by looking at work done, not just titles and keywords.*
