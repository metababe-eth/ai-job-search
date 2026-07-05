# Search Queries for Job Scraper

<!-- SETUP: Customize these queries based on your skills, target roles, and location -->

## Search Sites

Primary (US job market):
- **linkedin.com/jobs** - via the built-in `linkedin-search` CLI skill (preferred: structured results, recency and remote filters, no auth)
- **indeed.com** - largest US job board (via WebSearch `site:` queries)
- **builtin.com** - tech roles by metro (Built In SF/NYC/Austin/etc.)
- **wellfound.com** - startup roles (formerly AngelList Talent)
- **dice.com** - tech/IT contract and full-time roles

Secondary (company career pages via Google):
- Direct Google searches with `site:` filters for known target companies (many use `boards.greenhouse.io` or `jobs.lever.co`)

## LinkedIn CLI Queries

Run one search per role title / key skill (see the job-scraper SKILL.md for the command). Combine with your location or "Remote":

```
-q "[YOUR_PRIMARY_JOB_TITLE]" -l "[YOUR_CITY], [YOUR_STATE], United States" --jobage 14
-q "[YOUR_KEY_SKILL]" -l "[YOUR_CITY], [YOUR_STATE], United States" --jobage 14
-q "[YOUR_PRIMARY_JOB_TITLE]" -l "Remote" --remote remote --jobage 14
```

## WebSearch Query Categories

Queries are grouped by priority. Each query should be combined with your location terms (e.g. "[YOUR_CITY]", "[YOUR_METRO_AREA]", "remote") where the site supports it.

### Priority 1: [YOUR_PRIMARY_ROLE_TYPE]

These match your strongest and most desired career direction.

```
site:indeed.com "[YOUR_PRIMARY_JOB_TITLE]" [YOUR_CITY]
site:indeed.com "[YOUR_KEY_SKILL]" [YOUR_CITY]
site:linkedin.com/jobs "[YOUR_PRIMARY_JOB_TITLE]" [YOUR_STATE]
```

### Priority 2: [YOUR_DOMAIN_EXPERTISE]

These match your domain expertise.

```
site:indeed.com [YOUR_DOMAIN_KEYWORD_1] [YOUR_CITY] OR [YOUR_METRO_AREA]
site:builtin.com [YOUR_DOMAIN_KEYWORD_2] [YOUR_CITY]
site:linkedin.com/jobs [YOUR_DOMAIN_KEYWORD_1] [YOUR_CITY] [YOUR_STATE]
```

### Priority 3: [YOUR_ADJACENT_ROLE_TYPE]

Adjacent roles you could pivot into.

```
site:indeed.com "[YOUR_ADJACENT_TITLE_1]" [YOUR_KEY_SKILL] [YOUR_CITY]
site:wellfound.com "[YOUR_ADJACENT_TITLE_2]" [YOUR_KEY_SKILL]
```

### Priority 4: Broader Technical / Consulting

Wider net for general technical roles.

```
site:indeed.com [YOUR_KEY_SKILL] developer [YOUR_CITY]
site:linkedin.com/jobs "[YOUR_KEY_SKILL] developer" [YOUR_CITY]
site:dice.com "technical consultant" [YOUR_DOMAIN] [YOUR_CITY]
```

## Location Filter

When evaluating results, verify the job location is within reasonable commute distance from your home, or explicitly remote. Define acceptable areas:
- [YOUR_CITY] and surrounding areas
- [ACCEPTABLE_AREA_1]
- [ACCEPTABLE_AREA_2]
- [BORDERLINE_AREA] (borderline - ~X min by car/transit)
- [TOO_FAR_AREA] (too far)
- Remote: [YES/NO/HYBRID_PREFERENCE]

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
