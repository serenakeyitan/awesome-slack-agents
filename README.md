# 🤖 awesome-slack-agents

<p align="center">
  <img src="https://img.shields.io/badge/agents-22%20curated-blueviolet?style=for-the-badge" />
  <img src="https://img.shields.io/badge/sources-Twitter%20%7C%20Reddit%20%7C%20GitHub-orange?style=for-the-badge" />
  <img src="https://img.shields.io/badge/license-CC0-lightgrey?style=for-the-badge" />
  <img src="https://awesome.re/badge-flat2.svg" />
</p>

<p align="center">
  <b>The best AI agents for Slack — curated from what's actually going viral in the community.</b><br/>
  Every entry came from a real tweet, Reddit post, or HN thread. Every entry tells you exactly which daily Slack workflow it replaces.
</p>

> Built as part of my work on [first-tree](https://github.com/unispark-inc/first-tree) — shared context infrastructure for agent teams.

---

## 💡 Why this exists

Most "best Slack bots" lists are vendor SEO. This one is different:

- **Source-linked** — every entry traces back to a viral tweet, HN post, or Reddit thread
- **Workflow-first** — organized by what you're *doing* in Slack, not by tool name
- **Plain English** — written for people who haven't set up a Slack agent before

Pick your situation:

| I want to… | Go to |
|---|---|
| Stop reading 200 unread messages every morning | [📋 Summaries & Digests](#-summaries--daily-digests) |
| Handle incidents without switching apps | [🚨 Incident Response](#-incident-response) |
| Automate standups so nobody forgets | [🤝 Standups & Async Updates](#-standups--async-updates) |
| Get PRs reviewed and triaged automatically | [🔍 Code Review & PR Triage](#-code-review--pr-triage) |
| Answer team questions from docs automatically | [🧠 Knowledge & Q&A](#-knowledge--qa) |
| Connect Slack to every tool (Jira, GitHub, Gmail…) | [🔌 Connect Slack to Everything](#-connect-slack-to-everything) |
| Run a full AI assistant from my own server | [🏠 Self-Hosted AI in Slack](#-self-hosted-ai-in-slack) |
| Have an AI coding agent I can message from Slack | [💻 Coding Agents via Slack](#-coding-agents-via-slack) |

---

## 📋 Summaries & Daily Digests

> **The situation:** You open Slack and there are 200 unread messages. You need to know what actually matters in 2 minutes, not 20.

---

### 🔵 open-source-slack-ai — summarize any thread or channel, free

![Stars](https://img.shields.io/github/stars/meetbryce/open-source-slack-ai?style=flat-square&label=⭐) &nbsp; Built at a hackathon in 3 days

**What it does:** Summarize any Slack thread or channel on demand. Free alternative to Slack AI's paid tier.

```
Type /summarize in any channel → clean summary of the last 24h
Highlight any thread → ask for a /tldr
```

**Onboarding (5 min):**
```bash
git clone https://github.com/meetbryce/open-source-slack-ai
pip install -r requirements.txt
# Add SLACK_BOT_TOKEN + OPENAI_API_KEY to .env
python app.py
```
Then add the bot to your Slack workspace via the app manifest in the repo.

🔗 https://github.com/meetbryce/open-source-slack-ai  
📣 [How & Why I Built It In 3 Days](https://bryceyork.com/free-open-source-slack-ai/)

---

### 🔵 slack-summarizer — daily channel digest, auto-posted every morning

![Stars](https://img.shields.io/github/stars/masuidrive/slack-summarizer?style=flat-square&label=⭐) &nbsp; 104 forks

**What it does:** Runs on a cron schedule. Reads a busy channel. Posts a clean AI-written summary to any channel you choose. Set it once, it runs every morning.

Good for: `#engineering`, `#support`, `#general` — any channel people skim instead of read.

**Onboarding (10 min):**
```bash
git clone https://github.com/masuidrive/slack-summarizer
cp .env.example .env
# Fill in: SLACK_BOT_TOKEN, SLACK_USER_TOKEN, OPENAI_API_KEY, CHANNEL_ID
# Add to cron: 0 9 * * 1-5 python summarize.py
```

🔗 https://github.com/masuidrive/slack-summarizer

---

### 🔵 LlamaBot — Slack bot that learns from your conversations

![Stars](https://img.shields.io/github/stars/run-llama/llamabot?style=flat-square&label=⭐) &nbsp; By the LlamaIndex team

**What it does:** Listens to your Slack workspace, stores conversations in a vector database (Qdrant), and answers questions about what was discussed — with memory across restarts.

Ask it: *"What did the team decide about the API design last week?"* — it will know.

🔗 https://github.com/run-llama/llamabot

---

## 🚨 Incident Response

> **The situation:** Something breaks. Your on-call gets paged. You want the bot to investigate, post findings, and propose a fix in Slack — before the human opens their laptop.

---

### 🔴 incidentbot — full incident lifecycle in Slack

![Stars](https://img.shields.io/github/stars/incidentbot/incidentbot?style=flat-square&label=⭐) &nbsp; Updated May 2026 · Used by DevOps teams worldwide

**What it does:** Someone types `/incident start` in Slack. The bot creates a dedicated incident channel, assigns roles, tracks the timeline, and integrates with PagerDuty + Jira + Statuspage + Zoom. When resolved, it drafts the postmortem automatically.

```
/incident start → auto-creates #incident-2026-05-21-api-down
                → assigns IC, Comms Lead, Tech Lead roles
                → starts timeline tracking
                → posts status updates to Statuspage
/incident resolve → generates postmortem draft
```

**Onboarding:**
```bash
git clone https://github.com/incidentbot/incidentbot
cp config.example.yaml config.yaml
# Configure: slack_token, pagerduty_token, jira_url, statuspage_id
docker-compose up
```

🔗 https://github.com/incidentbot/incidentbot · https://incidentbot.io  
📣 Most-cited open-source incident bot in r/devops and SRE communities

---

### 🔴 openai/openai-security-bots — 3 bots from OpenAI's own security team

![Stars](https://img.shields.io/github/stars/openai/openai-security-bots?style=flat-square&label=⭐) &nbsp; Released by OpenAI internally, then open-sourced

**What it does:** Three production Slack bots OpenAI actually runs internally:

| Bot | What it does |
|-----|-------------|
| **Incident Response Bot** | Chats with users in an incident thread, tracks status, auto-summarizes |
| **Triage Bot** | Routes inbound security requests to the right sub-team |
| **SDLC Bot** | Reviews new projects and decides if they need a security review |

These aren't demos — they're the actual bots running at OpenAI.

🔗 https://github.com/openai/openai-security-bots

---

## 🤝 Standups & Async Updates

> **The situation:** Remote team. Standups are either skipped or take 30 minutes. You want updates to happen automatically.

---

### 🟢 HowsThisGoing — AI standup bot, connects to GitHub + Linear

**What it does:** Connects to GitHub, Linear, HubSpot, and Notion. Reads what your team actually *did* (commits, tickets closed) and generates the standup summary for them. Setup in under 30 seconds.

> *"AI project manager for Slack that provides instant insights on team progress, blockers, and milestones. GitHub-aware — reads your commits and PRs."*

📣 [BetaList launch tweet](https://twitter.com/BetaList/status/1827485288811393526) (August 2024)  
🔗 https://howsthisgoing.app

---

### 🟢 Cursor Automations — cron digest agent (engineer's personal async assistant)

**What it does:** A scheduled AI agent that runs every 2 hours, reads your Slack mentions + GitHub PRs + Jira issues, deduplicates across all sources, and posts a clean priority list to a private Slack channel.

Real usage from Rippling:
> *"I dump meeting notes, action items, TODOs, and Loom links into a Slack channel throughout the day. A cron agent reads everything alongside my GitHub PRs, Jira issues, and Slack mentions, deduplicates across sources, and posts a clean dashboard."*
> — Abhishek Singh, Rippling

**Workflow triggers available:** Slack message → Linear issue · GitHub PR → review · PagerDuty alert → investigation

📣 [Cursor Automations launch — March 5, 2026](https://cursor.com/blog/automations)

---

## 🔍 Code Review & PR Triage

> **The situation:** PRs pile up. Engineers don't know which ones are urgent. You want the bot to read every PR, flag the risky ones, and ping the right reviewer in Slack — automatically.

---

### 🟡 innogames/slack-bot — start Jenkins jobs, watch PRs, all from Slack

![Stars](https://img.shields.io/github/stars/innogames/slack-bot?style=flat-square&label=⭐) &nbsp; Updated May 2026 · In production at InnoGames

**What it does:** Start Jenkins builds, watch GitHub/GitLab PRs, watch Jira tickets — all from Slack. When a PR is approved or a build finishes, it pings you in Slack. ChatGPT/DALL-E support added.

```
@bot watch pull request → notifies you when it merges
@bot start job backend-deploy → triggers Jenkins job
@bot tell me about jira ABC-123 → posts ticket summary
```

**Onboarding:**
```bash
git clone https://github.com/innogames/slack-bot
cp config.example.yaml config.yaml
# Fill in: slack.token, jenkins.host, github.access_token
go run cmd/bot/main.go
```

🔗 https://github.com/innogames/slack-bot

---

### 🟡 Kilo for Slack — mention @Kilo in a thread, it ships a PR

**What it does:** Mention `@Kilo` in any Slack thread about a bug or feature. It reads the thread, accesses your GitHub repo, implements the fix, and pushes a pull request — without leaving Slack.

> *"A developer can type '@Kilo based on this thread, can you implement the fix for the null pointer exception' and the bot pushes a PR."*

Backed by GitLab's cofounder. $8M seed.

📣 [VentureBeat — January 2026](https://venturebeat.com/technology/kilo-launches-ai-powered-slack-bot-that-ships-code-from-a-chat-message)  
🔗 https://kilo.ai/slack

---

## 🧠 Knowledge & Q&A

> **The situation:** Someone asks in Slack "where's the API docs?" or "what's our refund policy?" and a human has to stop working to answer. You want a bot that knows everything and answers instantly.

---

### 🟣 Archer (ArcadeAI/SlackAgent) — agentic assistant that acts *as* you

![Stars](https://img.shields.io/github/stars/ArcadeAI/SlackAgent?style=flat-square&label=⭐) &nbsp; Self-hosted, runs free on Modal

**What it does:** An agentic Slack assistant that works as *you* — with access to your own GitHub, email, and calendar via OAuth. Can review and summarize PRs, draft and send emails, find calendar availability and schedule meetings, and crawl websites for research — all inside Slack.

Every team member gets their own authenticated session. Self-hosted on Modal (free tier available).

**Onboarding:**
```bash
git clone https://github.com/ArcadeAI/SlackAgent
pip install -r requirements.txt
# Configure: SLACK_BOT_TOKEN, ARCADE_API_KEY, MODAL_TOKEN
modal deploy archer.py
# Add bot to workspace → each user connects their own Google/GitHub via OAuth
```

🔗 https://github.com/ArcadeAI/SlackAgent  
📣 [Full walkthrough — partee.io (March 2025)](https://partee.io/2025/03/05/slack-agent/)

---

### 🟣 WandBot — RAG bot that answers questions about your docs

![Stars](https://img.shields.io/github/stars/wandb/wandbot?style=flat-square&label=⭐) &nbsp; Production bot — used live in W&B's Slack and Discord

**What it does:** RAG-based support bot. Point it at your documentation, and it answers questions in Slack with citations. Used in production by Weights & Biases to handle developer support across Slack, Discord, ChatGPT, and Zendesk.

Good model for any team that wants a "ask about our docs" bot in Slack.

🔗 https://github.com/wandb/wandbot

---

### 🟣 Claude Cookbook — Slack data analyst bot

**What it does:** Official Anthropic recipe for building a Slack bot that answers data questions. Ask it *"how many signups did we get this week?"* — it queries your database and posts the answer in Slack.

📣 [Claude Platform Cookbook](https://platform.claude.com/cookbook/managed-agents-slack-data-bot)

---

## 🔌 Connect Slack to Everything

> **The situation:** Your Slack agent needs to *do* things — create Jira tickets, push commits, send emails — not just chat. You need the integration layer.

---

### 🔌 Composio — 1,000+ tool integrations for AI agents

![Stars](https://img.shields.io/github/stars/ComposioHQ/composio?style=flat-square&label=⭐&color=green) &nbsp; 4,578 forks

**What it does:** One library. Your agent gets authenticated read/write access to Slack, GitHub, Gmail, Jira, Linear, Notion, Salesforce, and 990+ more. Stop writing OAuth flows for every tool.

```python
from composio_langchain import ComposioToolSet
tools = ComposioToolSet().get_tools(["SLACK", "GITHUB", "GMAIL", "LINEAR"])
# your agent can now read/write all of those — authenticated, no extra setup
```

> *"Composio is a cool production-ready toolset for AI agents — includes 100+ tools including GitHub, Slack, Salesforce, and more."*
> — [@llama_index on Twitter](https://x.com/llama_index/status/1820224063174053984)

🔗 https://github.com/ComposioHQ/composio

---

### 🔌 agent-slack (stablyai) — CLI that lets any AI agent use Slack

![Stars](https://img.shields.io/github/stars/stablyai/agent-slack?style=flat-square&label=⭐) &nbsp; 99 upvotes on HN · 35 comments

**What it does:** CLI tool for AI agents to interact with Slack. Paste in a Slack URL and it reads the channel or thread. Downloads files and snippets. Reads Canvases as markdown. Zero-config auth if you have Slack Desktop installed.

> *"We don't have access to the Slack MCP and couldn't find anything out there that worked for us."*

📣 [Show HN — 99 points](https://news.ycombinator.com/item?id=46905745)  
🔗 https://github.com/stablyai/agent-slack

---

### 🔌 n8n — visual workflow builder, 1,000+ Slack templates

**What it does:** No-code visual builder. Connect Slack to anything with drag-and-drop. Nodes for every trigger and action: *"when Slack message matches keyword → create Jira ticket + reply in thread."* AI nodes available for reasoning steps.

Viral workflow: monitoring Reddit for trending topics → GPT-4 summary → posted to Slack (389 upvotes on Reddit).

**Onboarding (2 min with Docker):**
```bash
docker run -it --rm \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
# Open http://localhost:5678 → add Slack credentials → import a template
```

🔗 https://n8n.io/integrations/slack/ · 280+ free templates: https://github.com/enescingoz/awesome-n8n-templates

---

## 🏠 Self-Hosted AI in Slack

> **The situation:** You want a full AI assistant in Slack that you control — your server, your model, your data.

---

### 🏠 OpenClaw — AI agent for Slack, Discord, WhatsApp + 50 more

![Stars](https://img.shields.io/badge/⭐-373%2C759-yellow?style=flat-square) &nbsp; Fastest-growing GitHub repo in history

**What it does:** Run any LLM (Claude, GPT-4, DeepSeek, Gemini) from your own machine and connect it to every messaging app you use. Your agent lives in Slack DMs, responds in Discord, and replies to WhatsApp — same brain, same context, everywhere.

**The viral moment:** January 2026 — went from 9k to 149k GitHub stars in one week. The reason: first tool that lets AI come *to you* instead of you going to AI.

**Onboarding:**
```bash
git clone https://github.com/openclaw/openclaw
cp .env.example .env
# Add your LLM API key + Slack bot token
docker-compose up
# In Slack: add app → DM it → it replies with your LLM
```

🔗 https://github.com/openclaw/openclaw  
📣 [KDNuggets — "OpenClaw: The Free AI Agent Tool Going Viral in 2026"](https://www.kdnuggets.com/openclaw-explained-the-free-ai-agent-tool-going-viral-already-in-2026)  
📣 [SimilarLabs — "60K Stars in 72 Hours"](https://similarlabs.com/blog/openclaw-ai-agent-trend-2026)

---

### 🏠 nanobot (HKUDS) — tiny, readable, fully hackable

![Stars](https://img.shields.io/badge/⭐-42%2C948-yellow?style=flat-square) &nbsp; By HKU Data Intelligence Lab · Feb 2026

**What it does:** Same idea as OpenClaw — self-hosted AI agent across Slack, Discord, Telegram, WhatsApp, Teams, DingTalk, Feishu — but ~4,000 lines of code vs OpenClaw's 430,000. You can actually read the whole thing.

Good for: teams who want to fork and customize without drowning in code.

🔗 https://github.com/HKUDS/nanobot  
📣 [Medium — widely shared in ML community](https://medium.com/data-science-in-your-pocket/what-is-nanobot-ultra-lightweight-ai-agent-framework-c43ad6c40b11)

---

### 🏠 doppel-bot (Modal) — train a bot on your own Slack messages

![Stars](https://img.shields.io/github/stars/modal-labs/doppel-bot?style=flat-square&label=⭐) &nbsp; By the Modal team

**What it does:** Trains a language model on *your* Slack message history. Other people in your workspace can ask it questions and it replies as you — your vocabulary, your opinions, your style.

Good for: async teams, persistent knowledge, "ask what X would say about Y."

🔗 https://github.com/modal-labs/doppel-bot

---

## 💻 Coding Agents via Slack

> **The situation:** You want to send a task to a coding agent from Slack ("fix the login bug") and get back a PR — without touching the terminal.

---

### 💻 sleepless-agent — 24/7 Claude Code queue, via Slack

![Stars](https://img.shields.io/github/stars/context-machine-lab/sleepless-agent?style=flat-square&label=⭐) &nbsp; Oct 2025

**What it does:** A daemon that keeps Claude Code Pro running 24/7 via Slack. You drop tasks into Slack — it picks them up, creates isolated workspaces, writes code, commits, opens PRs. Handles day/night usage thresholds to maximize your subscription.

```
Send to Slack: "refactor auth.ts to use JWT instead of sessions"
→ agent picks it up, writes the code, opens a PR, replies with the link
```

🔗 https://github.com/context-machine-lab/sleepless-agent

---

### 💻 claude-code-slack-bot (mpociot) — send Claude Code tasks from Slack DMs

![Stars](https://img.shields.io/github/stars/mpociot/claude-code-slack-bot?style=flat-square&label=⭐) &nbsp; Jun 2025 · 71 forks

**What it does:** Bridges Slack to your local Claude Code. DM the bot or @mention it in a channel with a coding task. Claude Code executes it locally on your machine and posts the result back in Slack.

```bash
git clone https://github.com/mpociot/claude-code-slack-bot
npm install
# Set SLACK_BOT_TOKEN + CLAUDE_API_KEY in .env
node index.js
# In Slack: DM the bot with "add error handling to api/routes/users.js"
```

🔗 https://github.com/mpociot/claude-code-slack-bot  
📣 [Building an agentic Slackbot with Claude Code — Medium](https://medium.com/@dotdc/building-an-agentic-slackbot-with-claude-code-eba0e472d8f4)

---

### 💻 cc-connect (chenhg5) — chat with Claude Code / Cursor from your phone via Slack

![Stars](https://img.shields.io/badge/⭐-10%2C059-yellow?style=flat-square) &nbsp; Feb 2026 · 920 forks

**What it does:** Bridges local AI coding agents (Claude Code, Cursor, Gemini CLI, Codex) to Slack, Telegram, Discord, WeChat Work, DingTalk, and more. No public IP required. You run it on your dev machine, then message your coding agent from your phone via Slack.

Full web admin UI included to monitor agent sessions.

🔗 https://github.com/chenhg5/cc-connect

---

### 💻 Sniptail — "implement this" from Slack, agent opens a PR

**What it does:** An omnichannel bot that turns Slack "implement this" requests into real code changes. Gathers context from multiple repos, runs a coding agent, opens a PR, posts the result back in Slack.

> *"Turn Slack into a team interface for AI coding agents."*

📣 [Show HN — Feb 2026](https://news.ycombinator.com/item?id=47066016)  
🔗 https://github.com/Justkog/sniptail

---

## 📚 Tutorials & Onboarding Guides

If you want to build your own from scratch:

| Guide | What you'll build | Stack |
|---|---|---|
| [Claude Cookbook — Slack data analyst](https://platform.claude.com/cookbook/managed-agents-slack-data-bot) | Bot that answers data questions in Slack | Claude · Python |
| [Vercel guide — AI agent for Slack](https://vercel.com/kb/guide/how-to-build-an-ai-agent-for-slack-with-chat-sdk-and-ai-sdk) | Streaming agent with tool use | AI SDK · Next.js |
| [Cloudflare guide — multi-tenant Slack agent](https://developers.cloudflare.com/agents/guides/slack-agent/) | Agent on Cloudflare Workers | Workers · Durable Objects |
| [partee.io — Archer walkthrough](https://partee.io/2025/03/05/slack-agent/) | Agentic assistant with OAuth per user | LangGraph · Arcade · Modal |
| [Medium — DevOps bot from scratch](https://kymidd.medium.com/lets-do-devops-building-a-slack-bot-with-ai-capabilities-from-scratch-ca4c8f9ca78b) | DevOps Slack bot with Claude Sonnet | Python · Bolt |
| [Medium — Claude Code Slackbot](https://medium.com/@dotdc/building-an-agentic-slackbot-with-claude-code-eba0e472d8f4) | Coding agent reachable from Slack | Claude Code · Python |

---

## 🧪 Reliability Notes

Things that break or need watching before you commit to any of these:

| Issue | Which tools | What to know |
|---|---|---|
| Slack token expiry | All | Bot tokens expire if app is inactive >90 days on free workspaces. Use socket mode or set up token refresh. |
| Rate limits | open-source-slack-ai, summarizers | Slack API: 1 message/sec per channel. OpenAI API: watch costs on GPT-4 for large channels. |
| Context window on long channels | All summarizers | Channels with 1k+ messages will truncate. Most tools default to last 100 messages — adjust the window in config. |
| Docker required | OpenClaw, nanobot, incidentbot | All three need Docker. If you're on a shared server without Docker, use the Python installs directly. |
| Slack's Bolt version mismatch | Bolt-based projects | `bolt-python` breaks on major versions. Pin `slack-bolt==1.x.x` in requirements.txt. |
| Cursor Automations (cloud) | Cursor | Requires Cursor Pro/Business. Not self-hostable. |

---

## Contributing

Found something going viral — a tweet, a Reddit thread, a GitHub project getting shared — that belongs here?

**Rules:**
1. Must have a **real source** (tweet/post/HN/PH link with engagement). No source = no merge.
2. Must fit a **real Slack workflow** (not a generic chatbot, not a "coming soon" tool).
3. Must include **onboarding steps** — at minimum a `git clone` and the 3 env vars needed.
4. **Plain language** — write it so someone who has never set up a Slack bot understands it.

```markdown
### Name

**What it does:** one sentence

**The situation it fits:** describe the daily Slack problem this solves

**Onboarding:**
```bash
# the actual commands
```

🔗 Repo link  
📣 Source: [description](viral-link)
```

---

*Built as part of my work on [first-tree](https://github.com/unispark-inc/first-tree) — shared context infrastructure for agent teams.*
