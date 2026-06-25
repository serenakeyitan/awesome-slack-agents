# awesome-agent-skills

> A curated, **honestly-filtered** list of agent **skills that produce a finished deliverable** — a report, brief, deck, audit, or spreadsheet — not raw connectors that just hand back API data.

A *skill* here is the [`SKILL.md`](https://www.anthropic.com/news/skills) wrapper layer: you drop it into an agent, and the agent comes back with a **finished thing a human can use**. A GA4 skill returns a growth *report*, not a JSON blob. An SEO skill returns an *audit*, not a list of backlinks.

These are **not Slack-bound.** Install them into a Slack bot, a mobile assistant, Claude Code, or any agent that reads `SKILL.md`. The use case is the deliverable, not the surface.

**What this list is not:** raw [MCP servers](https://modelcontextprotocol.io/) (those give an agent *access*, not an *outcome*), template libraries you fill in yourself, or process scaffolds. Every entry below was checked to confirm it ships a real, finished output and that its source actually exists.

---

## The honest headline

This category is **thin**. We mined the major skill collections (Anthropic official, the big community lists) and verified every candidate's source by hand. After deduping and dropping anything that's really a *template* or a *raw connector*, only a couple dozen skills clear the bar. We'd rather show you ~20 real ones than 200 padded ones.

Where a use case has **no good existing skill**, we say so plainly (see [Honest gaps](#honest-gaps)) instead of inventing one.

Legend: ⭐ = stars of the **host** repo (a skill often lives inside a large repo, so stars reflect the repo, not the skill). 🏛️ = Anthropic official. ⚠️ = caveat worth reading before you rely on it.

---

## Growth, analytics & experimentation

| Skill | Produces | Source |
|---|---|---|
| **analytics-strategy** | A tracking-plan doc: North Star metric, KPI hierarchy, event catalog, naming conventions, measurement governance | [rampstackco/claude-skills](https://github.com/rampstackco/claude-skills/tree/main/skills/analytics-strategy) · 373⭐ |
| **cro-optimization** | A CRO test-plan doc + ICE-scored hypothesis list with decision criteria and segment-level results analysis | [rampstackco/claude-skills](https://github.com/rampstackco/claude-skills/tree/main/skills/cro-optimization) · 373⭐ |
| **experiment-design** | An experiment design (A/B, multivariate, holdout): hypothesis, sample size, guardrail metrics, analysis plan | [rampstackco/claude-skills](https://github.com/rampstackco/claude-skills/tree/main/skills/experiment-design) · 373⭐ |
| **performance-report** | An executive marketing-performance report: KPI dashboard by channel, trend analysis, wins/misses, impact×effort recommendations | [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins/tree/main/marketing/skills/performance-report) · 🏛️ 21.9k⭐ |

## Marketing & content

| Skill | Produces | Source |
|---|---|---|
| **competitive-brief** | A competitive brief: feature-comparison matrix, positioning analysis, messaging review, strategic recommendations | [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins/tree/main/marketing/skills/competitive-brief) · 🏛️ 21.9k⭐ |
| **campaign-plan** | A campaign brief: objectives, audience, messaging, channel strategy, content calendar, budget, risks | [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins/tree/main/marketing/skills/campaign-plan) · 🏛️ 21.9k⭐ |
| **email-sequence** | A ready-to-send multi-touch email sequence with per-step intent and copy | [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins/tree/main/marketing/skills/email-sequence) · 🏛️ 21.9k⭐ |
| **brand-review** | A brand-consistency review across copy and assets, with specific fixes | [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins/tree/main/marketing/skills/brand-review) · 🏛️ 21.9k⭐ |

## SEO

| Skill | Produces | Source |
|---|---|---|
| **seo-audit-orchestration** | A full SEO audit suite (technical, on-page, content-gap, keyword-gap, backlink) as a consolidated report | [rampstackco/claude-skills](https://github.com/rampstackco/claude-skills/tree/main/skills/seo-audit-orchestration) · 373⭐ ⚠️ needs Ahrefs MCP |
| **seo-audit** (marketing) | A standalone SEO audit report: technical issues, on-page gaps, content/keyword opportunities | [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins/tree/main/marketing/skills/seo-audit) · 🏛️ 21.9k⭐ |

## Product & research

| Skill | Produces | Source |
|---|---|---|
| **pm-spec-writing** | A specific, actionable dev brief / spec written from a vague idea or feature request | [rampstackco/claude-skills](https://github.com/rampstackco/claude-skills/tree/main/skills/pm-spec-writing) · 373⭐ |
| **roadmap-planning** | A multi-quarter roadmap sequenced from a backlog, with dependencies and themes | [rampstackco/claude-skills](https://github.com/rampstackco/claude-skills/tree/main/skills/roadmap-planning) · 373⭐ |
| **user-feedback-aggregation** | A synthesized feedback brief: themes, severity, representative quotes, prioritized actions, across support/NPS/sales/social | [rampstackco/claude-skills](https://github.com/rampstackco/claude-skills/tree/main/skills/user-feedback-aggregation) · 373⭐ |
| **deep-research** | A cited research report from autonomous multi-step investigation (market/competitive/literature) | [sanjay3290/ai-skills](https://github.com/sanjay3290/ai-skills/tree/main/skills/deep-research) · 327⭐ ⚠️ wraps Gemini Deep Research paid API; needs your own key |
| **academic-research-skills** | A full research-to-publication pipeline: formatted paper (PDF/DOCX), literature review, peer-review report, citation validation | [Imbad0202/academic-research-skills](https://github.com/Imbad0202/academic-research-skills) · 34.4k⭐ |

## Engineering — code, PR & security

| Skill | Produces | Source |
|---|---|---|
| **code-review** | A confidence-scored PR review report + high-confidence line-by-line comments posted to the PR | [anthropics/claude-code](https://github.com/anthropics/claude-code/tree/main/plugins/code-review) · 🏛️ 134k⭐ |
| **pr-review-toolkit** | A multi-agent PR review report across 6 lenses: comment accuracy, test coverage, error handling, type design, quality, simplification | [anthropics/claude-code](https://github.com/anthropics/claude-code/tree/main/plugins/pr-review-toolkit) · 🏛️ 134k⭐ |
| **security-guidance** | A security audit report: pattern warnings, diff review for high-severity findings, multi-file data-flow analysis (IDOR, auth bypass, SSRF, injection, XSS) | [anthropics/claude-code](https://github.com/anthropics/claude-code/tree/main/plugins/security-guidance) · 🏛️ 134k⭐ |
| **after-action-report** | A structured postmortem / retrospective: timeline, root-cause analysis, contributing factors, action items | [rampstackco/claude-skills](https://github.com/rampstackco/claude-skills/tree/main/skills/after-action-report) · 373⭐ |

## Documents & decks (the reliable core)

These are the Anthropic-official office-doc engines — the most dependable outcome-producers in the ecosystem. Any of the report-style skills above can hand off to these to render a final file.

| Skill | Produces | Source |
|---|---|---|
| **pptx** | A finished, editable PowerPoint deck: layouts, charts, speaker notes | [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/pptx) · 🏛️ 155k⭐ |
| **docx** | A polished Word document: TOC, tables, headers/footers, tracked changes, comments | [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/docx) · 🏛️ 155k⭐ |
| **xlsx** | A spreadsheet / financial model with formulas, formatting, and zero formula errors | [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/xlsx) · 🏛️ 155k⭐ |
| **pdf** | PDF documents: create, merge, split, fill forms, OCR | [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/pdf) · 🏛️ 155k⭐ |
| **canvas-design** | Finished poster/visual designs as PNG and PDF | [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/canvas-design) · 🏛️ 155k⭐ |

---

## Honest gaps

Use cases people clearly want, where we could **not** find a real, mainstream, outcome-producing skill (as of this writing). If you know one that genuinely ships a finished deliverable, [open a PR](#contributing).

- **Pitch / investor deck (the *narrative*, not just the file).** `pptx` renders the slides; nothing mainstream writes the story + financial summary for you.
- **Meeting → action-item brief.** Plenty of transcript *tools*; no clean skill that returns an owner/due/decision brief.
- **Researched, personalized sales outreach.** `email-sequence` writes the copy; none does the per-prospect research that makes outreach land.
- **Live KPI dashboard report (data → narrative report).** `analytics-strategy` plans the tracking; nothing portable turns *live* GA4/Amplitude data into a written growth report. (Custom builds exist but are hard-wired to one property.)

---

## What didn't make the cut (and why)

Being explicit keeps the list trustworthy:

- **Template / framework libraries** (e.g. large "PM skills" packs). They ship blank frameworks you fill in — not a finished deliverable the agent produces. Great starting points, wrong category for this list.
- **Raw MCP servers / connectors.** They give an agent *access* to GA4, Slack, GitHub, Ahrefs, etc. — necessary plumbing, but the *outcome* is yours to build. A skill is what turns that access into a report.
- **Process scaffolds and "guidance" skills** (design philosophy, how-to-build-an-MCP). Useful, but they don't return a deliverable.
- **Personal / hard-wired skills.** Skills hard-coded to one team's analytics property or repo set. Real and working, but not reusable by others.

---

## How to use a skill in any agent

A skill is a folder with a `SKILL.md` (a short spec the agent reads) plus any supporting scripts. To use one:

1. **Claude Code / Claude app** — drop the skill folder into your skills directory, or install the plugin it ships in. The agent auto-loads it when a request matches.
2. **A Slack bot or mobile assistant** — if your agent runtime supports skills, point it at the skill folder; it loads the same `SKILL.md`.
3. **Skills that wrap an MCP** (e.g. the SEO suite wraps Ahrefs) need that MCP connected first — the ⚠️ notes call this out.

New to the format? See Anthropic's [Agent Skills announcement](https://www.anthropic.com/news/skills) and the [anthropics/skills](https://github.com/anthropics/skills) repo for canonical examples.

---

## Contributing

PRs welcome — but the bar is strict, because the value of this list is its filter:

✅ **Include** if the skill: (1) is a real `SKILL.md`-style skill (link to it), (2) **produces a finished deliverable** — report, brief, deck, audit, spreadsheet — not raw data, (3) is reusable by anyone (not hard-wired to one account), (4) actually exists (we verify the source).

❌ **Don't** submit raw MCP servers, blank template packs, or "guidance" skills.

For each entry give: **name · what finished thing it produces · link to the skill · host-repo stars · any caveat (paid API, required MCP, etc.).**

---

*Curated by [first-tree](https://github.com/serenakeyitan/first-tree). Every entry's source was verified by hand. Found a dead link or a skill that's really a template? Open an issue — keeping the filter honest is the whole point.*
