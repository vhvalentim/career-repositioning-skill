---
name: career-repositioning
description: Generic professional repositioning workflow for any user. Covers CV optimization, job search across major platforms, ATS-style scoring, document generation, and Git-safe publishing.
category: productivity
public: true
---

# Career Repositioning Workflow

End-to-end, user-agnostic workflow for job search and career transition.

## When to Use
- User wants to search jobs systematically.
- Need to score/map jobs against a candidate profile.
- Generate professional documents without exposing credentials.

## Prerequisites
- A candidate profile source the user provides (skills, experience, location).
- Internet access for job searches.
- Optional: weasyprint/pandoc/reportlab for PDF generation.

## Workflow

### 1. Profile intake
- Gather role target, seniority, location, must-have skills, nice-to-have skills, salary band.
- Store profile in a single local file, e.g. `PROFILE.md`.
- Do NOT hardcode personal data into the skill docs or templates.

### 2. Job search
Recommended channels:
- LinkedIn public search: `https://www.linkedin.com/jobs/search/?keywords={query}&location={city}&f_E=3,4&sortBy=DD`
- APinfo for IT/BI/data adjacent roles
- InfoJobs/Gupy/Catho/Vagas/Indeed as fallbacks

Rules:
- Prefer public listings; rely on `web_search`/`web_extract` where available.
- If bot-detected or subscription-limited: provide manual-search-link tables and reuse previous cached listings when available.
- Never fabricate URLs. Every vaga MUST point to a real job page, not a generic search page.
- Respect rate limits; avoid tight scraping bursts.

### 3. Scoring
Use a 100-point model:
- Skills Match: 40%
- Seniority Match: 30%
- Relevance: 20%
- Recency: 10%

Classify:
- 95-100: apply immediately, personalize
- 85-94: apply same day
- 75-84: apply within 2 days
- 65-74: evaluate personalization worth
- <65: skip or archive

### 4. Document generation
Generate:
- optimized CV
- job map with scored listings and direct links
- repositioning plan with weekly milestones
- consolidated document combining CV + map + plan
- compatibility chart HTML/PDF when useful

Storage:
- Use `~/Downloads` or repo docs folder.
- Keep both `.md` and `.pdf` where possible.

### 5. Git publication (safe)
If publishing outputs to Git:
- Sanitize first: redact personal emails, phones, CPF/RG, addresses, internal project keys, credentials/tokens.
- Use `.gitignore` for intermediate files and data dumps.
- Use meaningful commits:
  - `chore: initialize career-repositioning skill`
  - `docs: add generic profile template`
  - `feat: add job-scoring methodology`
  - `chore: add PDF generation snippets`
- If credentials/secrets were committed in history, purge with `git filter-repo` or BFG, then rotate.

## Security rules
- Never commit raw user data, resumes with real PII, or platform credentials.
- If generating from an existing personal toolkit, generalize first.
- License: MIT or CC-BY is recommended for open reuse.

## Templates path convention
- `TEMPLATE_PROFILE.md`
- `TEMPLATE_CV.md`
- `TEMPLATE_JOB_MAP.md`
- `TEMPLATE_PLAN.md`
- `TEMPLATE_CONSOLIDATED.md`

## Maintenance
- Keep platform-specific URL patterns updated.
- Document any new channels as they become public/reliable.
