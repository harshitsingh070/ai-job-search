# Search Queries for Job Scraper

<!-- Populated by /setup for Harshit Singh. Re-run /setup --section search to update as priorities evolve. -->

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first. Shipped country-agnostic CLIs include `linkedin-search` and `freehire-search`; Danish demos and any skill you add with `/add-portal` are included the same way. You do **not** need a matching `site:` line below for those CLIs to run.

The `site:` query templates in this file are the **WebSearch fallback** — for portals without a CLI, company career pages, or when a CLI fails.

**Language scope:** Harshit works in Hindi (native) and English (professional working proficiency). Indian tech postings are written in English, so every query below is in English; the Languages table still governs the Language Gate for postings that require a language as a job condition (see `04-job-evaluation.md`).

## Search Sites

Primary:
- **Internshala** - India's largest internship board (`site:internshala.com`)
- **LinkedIn Jobs** - `site:linkedin.com/jobs`; also covered by the `linkedin-search` CLI
- **Naukri** - `site:naukri.com` (fresher and entry-level roles)
- **Wellfound** - `site:wellfound.com` (startup roles, remote-friendly)
- **freehire.me** - aggregator across ~50 ATS platforms; covered by the `freehire-search` CLI

Secondary (company career pages via Google):
- Direct Google searches with `site:` filters for known target companies

## Query Categories

Queries are grouped by priority. Combine each query with location terms (remote / India / specific cities) where the site supports it.

**Organize by function, not job title.** The same underlying work carries different titles across companies (a "Software Engineer Intern" at one employer may be posted as "SDE Intern", "Software Developer Intern", or "Backend Intern" at another).

### Priority 1: Software Engineering Internships (primary direction)

These match the strongest and most desired direction: SWE/SDE internships.

```
site:internshala.com "software developer intern" remote
site:internshala.com "software engineer intern"
site:linkedin.com/jobs "software engineer intern" India remote
site:linkedin.com/jobs "SDE intern" India
site:naukri.com "software engineer intern" India
```

### Priority 2: Backend Engineering (Java, Spring Boot, Python)

Entry-level and internship roles matching the core stack.

```
site:internshala.com "backend developer intern" remote
site:linkedin.com/jobs "Java developer" fresher India
site:linkedin.com/jobs "Spring Boot developer" intern India
site:linkedin.com/jobs "Python developer intern" India remote
site:naukri.com "Java developer" "0-1 years" India
```

### Priority 3: Full-Stack / React

Adjacent roles the profile supports (Spring Boot + React + PostgreSQL).

```
site:internshala.com "full stack developer intern" remote
site:linkedin.com/jobs "full stack developer intern" India
site:wellfound.com "full stack" intern India remote
```

### Priority 4: AI-Integrated Software (broader net)

Wider net for general technical roles combining backend + AI/LLM work.

```
site:internshala.com "AI intern" python remote
site:linkedin.com/jobs "AI engineer intern" India remote
site:linkedin.com/jobs "software intern" LLM India
site:wellfound.com "AI" intern remote India
```

## Location Filter

When evaluating results, verify the job location:
- **Remote (India)**: ideal - primary target
- **Delhi NCR** (Noida, Greater Noida, Delhi, Gurugram): ideal - home region
- **Bengaluru, Hyderabad, Pune, Chennai, Mumbai**: acceptable (relocation possible; location is flexible)
- **Outside India**: skip unless remote-worldwide
- No "too far" tier - location is flexible

## Language Filter

Your working languages and levels are in CLAUDE.md's Languages table. When filtering scraped results, apply `04-job-evaluation.md`'s Language Gate: a posting requiring a language you haven't declared at all is excluded; a posting requiring a higher level than you declared in a language you do work in is not excluded, flag it clearly instead (see `job-scraper/SKILL.md`'s Step 3 "Quick Fit Assessment" for how the flag surfaces in `/scrape` output). Postings simply *written* in a language you don't work in, that don't require it on the job, are fine.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
