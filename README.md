# awesome-agent-skills

> The single **best outcome-producing skill per function**, hand-picked from the [OpenClaw skill marketplace](https://clawskills.sh/) — skills that produce a *finished deliverable* (a report, brief, audit, deck), not raw connectors that just hand back API data.

A *skill* here is the `SKILL.md` wrapper layer: you drop it into an agent, and the agent comes back with a **finished thing a human can use**. A GA skill returns an *audit report*, not a JSON blob. A research skill returns a *cited synthesis*, not a list of links.

These are **not Slack-bound.** Install them into a Slack bot, a mobile assistant, Claude Code, or any agent that loads a skill. The use case is the deliverable, not the surface.

**One per function.** For each function below we picked the *single best* skill — not a long list. Every pick was fetched live, confirmed to produce a real deliverable, and checked against its [clawskills.sh](https://clawskills.sh/) security status.

---

## How these were chosen

We read the [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) marketplace (5,000+ community skills, sourced from [ClawHub](https://clawskills.sh/)), and for each function picked the one skill that best **produces a finished deliverable**. Then we verified every winner against two signals clawskills.sh publishes per skill:

- 🛡️ **VirusTotal** scan result
- 🔍 **OpenClaw** security status (`Benign` / `Suspicious`)

**Security bar:** we prefer skills that are **`Benign` on both**. A skill flagged `Suspicious` on *one* signal is still listed but carries a ⚠️ — read it before installing. Skills flagged `Suspicious` on **both** were **excluded** entirely.

Legend: ⬇️ = downloads on clawskills.sh · ✅ = Benign on both VirusTotal + OpenClaw · ⚠️ = flagged Suspicious on one signal (use with caution).

---

## The picks — one per function

### 📊 Google Analytics / Analytics audit
**[check-analytics](https://clawskills.sh/skills/jeftekhari-check-analytics)** ✅ · ⬇️ 2.3k
Audits an existing Google Analytics setup by scanning the codebase for tracking code, measurement IDs, and config issues — produces a **severity-ranked Markdown GA audit report** (Critical / Warning / Suggestion) with a detected-providers list, event-coverage table, and remediation steps.
*Scope: static codebase audit of the GA implementation, not live GA4 traffic analytics.*

### 🗂️ Data & reporting
**[csv-pipeline](https://clawskills.sh/skills/gitgoodordietrying-csv-pipeline)** ✅ · ⬇️ 3.4k
Processes, transforms, analyzes, and reports on CSV/JSON using Python 3 + standard shell utilities — produces **aggregated results and a formatted Markdown report**, no external dependencies.
*Picked over the more-downloaded `data-analyst` (16.3k ⬇️) because that one is flagged ⚠️ Suspicious by OpenClaw; csv-pipeline is clean on both signals.*

### 📣 Marketing & sales
**[performance-reporter](https://clawskills.sh/skills/aaron-he-zhu-performance-reporter)** ⚠️ *(OpenClaw: Suspicious)* · ⬇️ 1.5k
Generates **client-ready SEO / performance reports** — executive summary with metrics table, ROI calculation, traffic / keyword / backlink / AI-visibility trend analyses, and tiered (immediate / short / long-term) recommendations, audience-tuned for execs, clients, and technical teams.
⚠️ *VirusTotal: Benign, but OpenClaw flags it Suspicious — review before installing.*

### 🔬 Research / product
**[super-research](https://clawskills.sh/skills/heldinhow-super-research)** ✅ · ⬇️ 509
Classifies a query, searches across web / news / GitHub / scholarly sources, assesses source quality, and compiles a **cited literature-review / synthesis report** — a finished research document, not raw search results.

### 📄 Documents & decks
**[docx](https://clawskills.sh/skills/seanphan-docx)** ✅ · ⬇️ new
Creates and edits real **Word documents (.docx)** via docx-js / Python OOXML / pandoc — tracked changes, comments, format-preserving redlines, text extraction (e.g. a redlined `contract.docx` ready to open in Word).

### 🗣️ Meetings / comms / knowledge
**[meeting-to-action](https://clawskills.sh/skills/codedao12-meeting-to-action)** ✅ · ⬇️ 1.4k
Turns a meeting transcript or notes into a **structured follow-up package** — a summary, an action-item table (each with owner + due date), an open-questions / risks list, and a draft recap email. Draft-only (won't write to external systems on its own).

---

## Honest gaps

A function where the marketplace's best option failed our bar, so we list it as a gap rather than recommend something risky:

- **Dev / Code / PR review.** The strongest outcome-producing code-review skill we found ([astrai-code-review](https://clawskills.sh/skills/beee003-astrai-code-review)) is flagged **Suspicious on *both* VirusTotal and OpenClaw**, has only ~447 downloads, and requires an external API key. It failed the security bar, so we left this slot open. If you know a clean OpenClaw code-review skill that ships a real review report, [open a PR](#contributing).

---

## What didn't make the cut (and why)

Being explicit keeps the list trustworthy:

- **Raw MCP servers / connectors.** They give an agent *access* (to GA4, a database, GitHub, etc.) — necessary plumbing, but the *outcome* is yours to build. A skill is what turns access into a report.
- **Skills flagged `Suspicious` on both security signals.** Excluded regardless of how good the description sounds (this cost us the dev slot).
- **Anthropic's official skills** (pptx/docx/pdf/xlsx and friends). Excellent, but they're not from the OpenClaw marketplace — this list is specifically the best the OpenClaw community ecosystem has to offer.
- **Template / framework libraries.** They ship blank frameworks you fill in, not a finished deliverable the agent produces.

---

## How to install a skill

Every skill above installs the same way:

```bash
# OpenClaw CLI
openclaw skills install <skill-name>

# or via ClawHub (for registry-managed skill folders outside a full OpenClaw workspace)
npx clawhub install <skill-name>
```

Then any agent that loads the skill picks it up automatically when a request matches. Skills are portable `SKILL.md` folders — usable in a Slack bot, a mobile assistant, or Claude Code, not just OpenClaw.

**Always check the security status** on the skill's clawskills.sh page before installing, especially for ⚠️-flagged picks. Statuses can change as skills are re-scanned.

---

## Contributing

PRs welcome — but the bar is strict, because the value of this list is its filter:

✅ **Include** if the skill: (1) is on the OpenClaw / ClawHub marketplace (link to its clawskills.sh page), (2) **produces a finished deliverable** — report, brief, audit, deck — not raw data, (3) is the best pick for a function not already covered, **or** a cleaner (better security status / more downloads) replacement for a current pick, (4) is not flagged `Suspicious` on both signals.

For each entry give: **function · skill name · what finished thing it produces · clawskills.sh link · VirusTotal + OpenClaw status · downloads.**

---

*Curated by [first-tree](https://github.com/serenakeyitan/first-tree). Picks sourced from the OpenClaw marketplace and verified live against each skill's published security status. Found a cleaner pick or a dead link? Open an issue — keeping the filter honest is the whole point.*
