---
framework_version: 1.0.0
---

# Interview Preparation Guide

## STAR Format

Structure answers as: **Situation** (context), **Task** (your responsibility), **Action** (what you did), **Result** (outcome).

Keep answers to 1-2 minutes. Be specific. End with what you learned or would do differently.

## STAR Candidates (Complete Manually)

<!-- Added by /setup from CV and project evidence. Fill in situation/task/action/result before using them in interviews. -->

### Apache Wayang - non-deterministic JVM crash hunt (debugging, persistence)
**Source:** CV - Apache Wayang PR #781 (merged)
**What happened:** `TensorflowModelTest` failed intermittently with a SIGABRT during Maven teardown ("forked VM terminated without properly saying goodbye"). Traced it to unclosed EagerSession/Tensor resources racing garbage collection at JVM shutdown; fixed with try-with-resources and removed eager operations.
**Why it matters:** "hardest bug" questions, debugging methodology, working in unfamiliar codebases.
**S/T/A/R stub:**
- Situation:
- Task:
- Action:
- Result:

### Apache Wayang - JDBC connection lifecycle fix (root-cause analysis, quality bar)
**Source:** CV - Apache Wayang PR #809 (merged)
**What happened:** Found `GenericJdbcExecutor`'s connection initialization silently commented out, leaving a null connection; restored the lifecycle against the current API and added 4 regression tests with all CI checks passing.
**Why it matters:** "tell me about a bug you found", code-quality and testing-discipline questions.
**S/T/A/R stub:**
- Situation:
- Task:
- Action:
- Result:

### Apache Wayang - landing changes through review (communication, feedback)
**Source:** CV - Apache Wayang PRs #722, #809, #837
**What happened:** Iterated through multiple rounds of maintainer review to land documentation and bug fixes in an Apache project, adjusting the approach each round.
**Why it matters:** teamwork/feedback questions, remote collaboration, handling criticism.
**S/T/A/R stub:**
- Situation:
- Task:
- Action:
- Result:

### MatchIQ - designing a multi-tier AI platform (system design, ownership)
**Source:** CV - MatchIQ project
**What happened:** Built a Spring Boot + FastAPI + React system with PDF ingestion, embeddings, pgvector similarity search, multi-provider LLM fallback chains, and JWT-secured role-based access across three user types.
**Why it matters:** architecture questions, full-stack ownership, AI integration judgment.
**S/T/A/R stub:**
- Situation:
- Task:
- Action:
- Result:

### Discipify - zero to live deployment (initiative, shipping)
**Source:** CV - Discipify project (live at focusforge-frontend.vercel.app)
**What happened:** Designed 10+ REST APIs, optimized database access through indexing, built an admin dashboard, and shipped a live deployment solo.
**Why it matters:** "initiative" and "something you shipped" questions, prioritization.
**S/T/A/R stub:**
- Situation:
- Task:
- Action:
- Result:

### 450+ DSA problems solved (consistency, fundamentals)
**Source:** CV - achievements
**What happened:** Solved 450+ problems (200+ Medium, 70+ Hard) across LeetCode and GeeksforGeeks while studying full-time.
**Why it matters:** consistency/discipline questions, stamina for technical screens.
**S/T/A/R stub:**
- Situation:
- Task:
- Action:
- Result:

## Common Tough Questions

### "You don't have professional experience yet - why should we hire you?"
> Bridge: merged Apache Wayang PRs went through the same CI and maintainer-review discipline as professional work, and production-style systems were built and deployed solo (one live). The gap between that and a first job is team context, not capability. Anchor with PR #781/#809 and the Discipify live deployment; close with eagerness to learn inside a team with code review.

### "Why did you leave [previous company]?"
> Not applicable (no employment history yet) - drop this question in practice.

### "You don't have [specific skill/experience]."
> [PREPARE YOUR ANSWER - acknowledge the gap, bridge to adjacent experience, show willingness to learn]

### "Where do you see yourself in 5 years?"
> [PREPARE YOUR ANSWER - show ambition aligned with the role's growth path]

### "What's your biggest weakness?"
> [PREPARE YOUR ANSWER - genuine weakness with concrete mitigation strategy]

### "Why this company specifically?"
> Customize per company. Must reference: specific projects, company values, market position, or team structure. Never give a generic answer.

## Questions You Should Ask Interviewers

### About the Role
- "What does a typical week look like in this role?"
- "What would success look like in the first 6 months?"
- "What's the biggest challenge the team is facing right now?"

### About the Team
- "How big is the team, and how do you divide work?"
- "What does the development/project lifecycle look like, from idea to production?"
- "How do you onboard new team members?"

### About Tech & Growth
- "What's your current tech stack for [relevant area]?"
- "Is there room to grow into more architectural or strategic decisions?"
- "How does the team stay current with new tools and methods?"

### About Culture (use these to prevent disappointment)
- "How would you describe the team culture?"
- "What does professional development look like here?"
- "Is there flexibility for remote/hybrid work?"
- "What's the balance between development/new projects and maintenance work?"
- "How would you describe the leadership style in this team?"
- "What do people who thrive here have in common?"

## Phone/Video Interview Tips
- Have STAR examples written out (use this file)
- Keep a glass of water nearby
- Smile when speaking (it changes your tone)
- Ask for clarification if a question is vague
- It's OK to take 5 seconds to think before answering
- End with: "Is there anything else you'd like to know about my background?"

## After the Application (Best Practice)

### Follow-Up Etiquette
- **Don't call to "stand out"** or to learn more about the role post-submission - this risks a negative impression
- If the employer specified a timeline, respect it and wait
- If no timeline was given and significant time has passed (2+ weeks), a brief call to ask about status is acceptable
- If you have genuinely new, relevant information to share, a short follow-up is fine

### Thank-You Notes
- When you receive any update (interview invitation, rejection, or status update), send a brief thank-you message
- Express appreciation for their time and the process
- Keep it short (2-3 sentences)

## Roleplay Guidelines
When the user asks for interview practice:
1. Ask which role/company to simulate
2. Start with easy warm-up questions ("Tell me about yourself")
3. Progress to role-specific technical questions
4. Include 1-2 behavioral questions using the competencies from the job posting
5. End with a tough question or curveball
6. After each answer, give brief feedback: what worked, what to sharpen
7. Suggest which STAR example would work best for each question
