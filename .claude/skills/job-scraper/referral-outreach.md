# Referral Outreach Drafts

Referenced by `SKILL.md` Step 4.5. For every high/medium-fit job found by `/scrape`, draft
two short LinkedIn messages for the user to send when reaching out:

- **A. Recruiter / talent message** - the referral ask.
- **B. Peer / team message** - the warm-intro or advice ask.

Drafts only: `/scrape` never sends messages, never fetches LinkedIn people-search pages, and
never invents a recipient. Names stay as `[Name]` until the user personalizes them.

## Output location and shape

One file per run: `job_scraper/outreach/YYYY-MM-DD_referral_outreach.md` (run date). Organize
by the Step 5 table number - one section per high/medium job, in the same order as the table,
each with the posting URL, both people-search links, and the two drafts:

```
## <n>. <Company> - <Role title> (<fit> fit)
- Posting: <url>
- Find contacts: [recruiters/TA](<link>) | [peers](<link>)

**A. To recruiter / talent:**
> <message>

**B. To peer / team member:**
> <message>
```

## Message anatomy (both variants)

1. Greeting: `Hi [Name],`
2. One-line introduction: final-year B.Tech IT student, Java/Spring Boot + Python backend
   developer (adapt the specialty to the role).
3. Specific reference: the exact role title and company from the posting. Add the location
   only when it helps - for NCR roles: "I'm based in Greater Noida, so on-site in <city>
   works well for me"; for remote roles: "remote works well from Greater Noida".
4. One proof point matched to the role's stack (mapping below). One, not three.
5. The ask. Recruiter: a referral or a pointer to the hiring team. Peer: a short chat about
   the team, or advice on the process.
6. One-sentence close. Confident, no begging.

Target 60-90 words. LinkedIn caps connection-request notes at 300 characters, so to
cold-connect send only sentences 1-2 plus the ask, trimmed to the cap, and the full message
in the first DM after acceptance.

## Proof-point mapping (pick the one matching the role)

| Role type | Proof point |
|-----------|-------------|
| Java / Spring Boot / backend | four merged pull requests in Apache Wayang (Java, Apache Software Foundation) and MatchIQ, a Spring Boot + PostgreSQL ATS platform built with LLM-based matching |
| Python | MatchIQ's FastAPI + pgvector matching service, and Synthetic Media Detector (a Python ML inference service, Dockerized) |
| Full-stack | Discipify, a live full-stack productivity app (Spring Boot + React), plus MatchIQ's REST APIs |
| AI-integrated | MatchIQ, an AI-native ATS built with LLM/RAG matching on pgvector |
| General SWE / intern | four merged Apache Wayang PRs, 450+ DSA problems solved, and two production projects built end to end |

## Rules

- `../job-application-assistant/03-writing-style.md` applies in full: no em-dashes, no
  cliches ("passionate about", "great fit", "hit the ground running"), no apologetic
  phrasing, every claim backed by a profile fact.
- Only profile facts (CLAUDE.md and the candidate profile files). Never claim company
  familiarity ("I admire your work in ...") unless independently verified; never invent a
  person, a referral, or an introduction.
- One message per contact type per job. Vary wording and proof points per posting; never
  reuse an identical message across jobs.
- The skill drafts, the user sends. Nothing here is auto-sent.
