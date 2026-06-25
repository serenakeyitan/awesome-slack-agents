# awesome-agent-skills

The single best **outcome-producing skill per function**, hand-picked from the [OpenClaw skill marketplace](https://clawskills.sh/). Each one produces a finished deliverable your team can use — a report, brief, audit, or doc — not a raw connector that just returns API data.

Not Slack-bound. Install into a Slack bot, a mobile assistant, Claude Code, or any agent that loads a skill.

## How these were chosen

Read across the [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) marketplace (5,000+ community skills), picked the best deliverable-producing skill per function, then checked each against the two security signals clawskills.sh publishes per skill: **VirusTotal** and **OpenClaw** status.

| Security bar | Rule |
|---|---|
| Both `Benign` | Listed, clean |
| One `Suspicious` | Listed with a warning — review before installing |
| Both `Suspicious` | Excluded |

`OK` = Benign on both. `Warn` = Suspicious on one signal.

## Growth & analytics

| Function | Skill | Produces | Security | Installs |
|---|---|---|---|---|
| Analytics audit | [check-analytics](https://clawskills.sh/skills/jeftekhari-check-analytics) | Google Analytics audit report | OK | 2.3k |
| Data reports | [csv-pipeline](https://clawskills.sh/skills/gitgoodordietrying-csv-pipeline) | CSV/JSON data report | OK | 3.4k |

## Marketing

| Function | Skill | Produces | Security | Installs |
|---|---|---|---|---|
| Marketing report | [performance-reporter](https://clawskills.sh/skills/aaron-he-zhu-performance-reporter) | Client-ready SEO performance report | Warn (OpenClaw) | 1.5k |

## Dev

| Function | Skill | Produces | Security | Installs |
|---|---|---|---|---|
| Security review | [code-security-audit](https://clawskills.sh/skills/wisdomsword-code-security-audit) | Code security audit report | OK | new |
| Release notes | [sovereign-changelog-maker](https://clawskills.sh/skills/ryudi84-sovereign-changelog-maker) | Changelog from git history | OK | 310 |
| Plan review | [cross-model-review](https://clawskills.sh/skills/don-gbot-cross-model-review) | Reviewed plan with rubric scores | OK | 431 |

## Product & research

| Function | Skill | Produces | Security | Installs |
|---|---|---|---|---|
| Research report | [super-research](https://clawskills.sh/skills/heldinhow-super-research) | Cited research synthesis | OK | 509 |

## Documents

| Function | Skill | Produces | Security | Installs |
|---|---|---|---|---|
| Word docs | [docx](https://clawskills.sh/skills/seanphan-docx) | Word document with redlines | OK | new |

## Meetings & comms

| Function | Skill | Produces | Security | Installs |
|---|---|---|---|---|
| Meeting follow-up | [meeting-to-action](https://clawskills.sh/skills/codedao12-meeting-to-action) | Action items, owners, recap email | OK | 1.4k |

## What didn't make the cut

| Excluded | Why |
|---|---|
| Raw MCP servers / connectors | Give an agent access, not a finished deliverable |
| Skills flagged `Suspicious` on both signals | Failed the security bar |
| Anthropic official skills (pptx, docx, pdf) | Excellent, but not from the OpenClaw marketplace |
| Template / framework libraries | Ship blank frameworks, not produced output |

## Install

| Method | Command |
|---|---|
| OpenClaw CLI | `openclaw skills install <skill-name>` |
| ClawHub | `npx clawhub install <skill-name>` |

Any agent that loads the skill picks it up when a request matches. Always check the security status on the skill's clawskills.sh page before installing — statuses can change as skills are re-scanned.

## Contributing

PRs welcome. Include a skill only if it: (1) is on the OpenClaw / ClawHub marketplace, (2) produces a finished deliverable, (3) covers a new function or cleanly replaces a current pick, (4) is not flagged `Suspicious` on both signals.

For each entry give: function, skill name, what it produces (a few words), clawskills.sh link, VirusTotal + OpenClaw status, installs.

---

Curated by [first-tree](https://github.com/serenakeyitan/first-tree). Picks sourced from the OpenClaw marketplace and verified live against each skill's published security status.
