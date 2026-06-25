# awesome-agent-skills

The single best **outcome-producing skill per function**, hand-picked from the [OpenClaw skill marketplace](https://clawskills.sh/). Each one produces a finished deliverable your team can use — a report, audit, or summary — not a raw connector that just returns API data.

Not Slack-bound. Install into a Slack bot, a mobile assistant, Claude Code, or any agent that loads a skill.

## How these were chosen

Read across the [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) marketplace (5,000+ community skills), kept only skills with **1,000+ installs** that produce a finished deliverable, and verified each against the security signals on its clawskills.sh page (skills flagged Suspicious were dropped in favor of clean alternatives).

## Growth & analytics

| Function          | Skill                                                                       | Produces                       | Installs |
| ----------------- | --------------------------------------------------------------------------- | ------------------------------ | -------- |
| Analytics audit   | [check-analytics](https://clawskills.sh/skills/jeftekhari-check-analytics)  | Google Analytics audit report  | 2.3k     |
| Data report       | [csv-pipeline](https://clawskills.sh/skills/gitgoodordietrying-csv-pipeline)| CSV/JSON data report           | 3.4k     |

## Marketing

| Function   | Skill                                                                                 | Produces               | Installs |
| ---------- | ------------------------------------------------------------------------------------- | ---------------------- | -------- |
| SEO audit  | [on-page-seo-auditor](https://clawskills.sh/skills/aaron-he-zhu-on-page-seo-auditor)  | Scored SEO audit report| 1.9k     |

## Dev

| Function          | Skill                                                                          | Produces                    | Installs |
| ----------------- | ------------------------------------------------------------------------------ | --------------------------- | -------- |
| Code security     | [senior-security](https://clawskills.sh/skills/alirezarezvani-senior-security) | Security findings report    | 1.9k     |
| Repo summary      | [git-summary](https://clawskills.sh/skills/zweack-git-summary)                 | Git repository summary       | 2.8k     |
| Cost report       | [session-cost](https://clawskills.sh/skills/khaney64-session-cost)             | Token usage and cost report  | 1.7k     |

## Product & research

| Function           | Skill                                                                          | Produces                          | Installs |
| ------------------ | ------------------------------------------------------------------------------ | --------------------------------- | -------- |
| Investment review  | [stock-evaluator](https://clawskills.sh/skills/demandgap-stock-evaluator)      | Stock evaluation dashboard         | 4.3k     |

## Meetings & comms

| Function           | Skill                                                                          | Produces                      | Installs |
| ------------------ | ------------------------------------------------------------------------------ | ----------------------------- | -------- |
| Meeting follow-up  | [meeting-to-action](https://clawskills.sh/skills/codedao12-meeting-to-action)  | Action items and recap email   | 1.4k     |

## What didn't make the cut

| Excluded                                     | Why                                              |
| -------------------------------------------- | ------------------------------------------------ |
| Skills under 1,000 installs                  | Quality bar                                      |
| Skills flagged Suspicious on security scan   | Dropped for clean alternatives                   |
| Raw MCP servers and connectors               | Give access, not a finished deliverable          |
| Anthropic official skills (pptx, docx, pdf)  | Excellent, but not from the OpenClaw marketplace |
| Template and framework libraries             | Ship blank frameworks, not produced output       |

## Install

| Method        | Command                                |
| ------------- | -------------------------------------- |
| OpenClaw CLI  | `openclaw skills install <skill-name>` |
| ClawHub       | `npx clawhub install <skill-name>`     |

Any agent that loads the skill picks it up when a request matches. Check the security status on the skill's clawskills.sh page before installing — statuses can change as skills are re-scanned.

## Contributing

PRs welcome. Include a skill only if it: has 1,000+ installs, is on the OpenClaw / ClawHub marketplace, produces a finished deliverable, and is not flagged Suspicious. For each entry give: function, skill name, what it produces (a few words), clawskills.sh link, installs.

---

Curated by [first-tree](https://github.com/serenakeyitan/first-tree). Picks sourced from the OpenClaw marketplace, filtered to 1,000+ installs, and verified live.
