# awesome-slack-agents

> *Built as part of my work on [first-tree](https://github.com/unispark-inc/first-tree) — shared context infrastructure for agent teams.*

![Awesome](https://awesome.re/badge.svg)
![License: CC0](https://img.shields.io/badge/License-CC0-lightgrey.svg)

**The best AI agents to run in your Slack — curated from what's actually going viral in the community.**

Every entry here came from a real tweet, Reddit post, or GitHub project that people are sharing. Not from vendor blogs. Each entry tells you in plain language: **what workflow it fits**, **what problem it solves**, and **where the community discovered it**.

---

## How to use this list

Each entry answers three questions:

- 📌 **When do you need this?** — the Slack workflow it fits
- 🎯 **What does it do?** — one sentence, plain English
- 📣 **Where did it go viral?** — the tweet or post that made it spread

---

## Table of Contents

**By what you're trying to do:**

- [Get a daily digest without reading everything](#-daily-digest--summaries)
- [Handle incidents without leaving Slack](#-incident-response)
- [Automate standups and team updates](#-standups--async-updates)
- [Code review and PR triage in Slack](#-code-review--pr-triage)
- [Answer team questions from your knowledge base](#-knowledge--qa)
- [Connect Slack to every other tool you use](#-connecting-slack-to-other-tools)
- [Run a full AI assistant in Slack from your own server](#-self-hosted-ai-assistants-in-slack)

---

## 📋 Daily Digest & Summaries

> **When:** You wake up and your Slack has 200 unread messages across 10 channels. You need to know what matters in 2 minutes.

---

### open-source-slack-ai

📌 **Fits when:** You want Slack AI's thread/channel summaries but don't want to pay Slack's premium tier.

🎯 **What it does:** Summarize any Slack thread or channel on demand. You install it yourself, it reads your workspace, and gives you a summary whenever you ask.

```
/summarize → summary of the last 24h in any channel
/tldr → summarize any thread
```

No subscription. No Slack AI Pro required. Runs on your own server.

🔗 **Repo:** https://github.com/meetbryce/open-source-slack-ai  
📣 **Source:** Surfaced on Reddit r/selfhosted as a free alternative to Slack's paid AI features

---

### slack-summarizer (masuidrive)

📌 **Fits when:** You have a busy public channel and need a daily digest automatically posted every morning.

🎯 **What it does:** Runs on a schedule. Reads your public Slack channels. Posts a clean AI-written summary to a channel of your choice. Set it once, it runs every day.

Good for: `#general`, `#engineering`, `#support` — any high-volume channel where people miss things.

🔗 **Repo:** https://github.com/masuidrive/slack-summarizer  
📣 **Source:** https://github.com/masuidrive/slack-summarizer (1k+ stars, widely shared in the self-hosting community)

---

### Cursor Automations — Slack digest agent

📌 **Fits when:** You're an engineer and want a personal async assistant that reads your Slack messages, GitHub PRs, and Jira tickets and gives you a clean to-do list every 2 hours.

🎯 **What it does:** A cron agent that runs every 2 hours, reads your Slack mentions + GitHub PRs + Jira issues, deduplicates across sources, and posts a clean dashboard to a private Slack channel.

> *"I dump meeting notes, action items, TODOs, and Loom links into a Slack channel throughout the day. A cron agent runs every 2 hours, reads everything alongside my GitHub PRs, Jira issues, and Slack mentions, deduplicates across sources, and posts a clean dashboard."*
> — Abhishek Singh, Rippling

📣 **Source:** [Cursor Automations launch post — March 5, 2026](https://cursor.com/blog/automations)  
📣 **Source:** [Cursor changelog — real-world usage at Rippling](https://cursor.com/changelog/03-05-26)

---

## 🚨 Incident Response

> **When:** Something breaks at 2am. Your on-call engineer gets paged. You want the bot to investigate, post a summary, and propose a fix in Slack — before the human even opens their laptop.

---

### incidentbot

📌 **Fits when:** Your team handles incidents in Slack and you want a structured framework — not a homemade bot you have to maintain.

🎯 **What it does:** Full incident lifecycle in Slack. Someone types `/incident start`. The bot creates a dedicated incident channel, assigns roles, tracks timeline, integrates with PagerDuty + Jira + Statuspage + Zoom, and posts updates. When it's resolved, it generates a postmortem draft.

Works with: PagerDuty · Jira · GitLab · Statuspage · Confluence · Zoom

🔗 **Repo:** https://github.com/incidentbot/incidentbot  
📣 **Source:** Widely referenced in DevOps and SRE communities as the go-to open-source incident bot

---

### Cursor Automations — incident triage agent

📌 **Fits when:** A PagerDuty alert fires and you want the agent to investigate the logs, find the recent code change that caused it, and post a proposed fix in Slack *before* the on-call engineer picks up their phone.

🎯 **What it does:** Triggered by PagerDuty incident → agent reads Datadog logs + git history → posts findings + proposed fix PR to a Slack channel.

> *"When triggered by a PagerDuty incident, the automation kicks off an agent that uses the Datadog MCP to investigate logs and looks at the codebase for recent changes. It then sends a message to the on-call engineers in Slack with a PR containing the proposed fix."*

📣 **Source:** [Cursor Automations launch — March 2026](https://cursor.com/blog/automations)  
📣 **Also covered:** [Help Net Security — "Cursor Automations turns code review and ops into background tasks"](https://www.helpnetsecurity.com/2026/03/06/cursor-automations-turns-code-review-and-ops-into-background-tasks/)

---

## 🤝 Standups & Async Updates

> **When:** Your team is remote, standups are painful, and half the team forgets to post updates. You want a bot that collects updates on a schedule and formats them so everyone's on the same page.

---

### slack-standup-bot (colestrode)

📌 **Fits when:** You want a dead-simple standup bot that asks your team questions on a schedule and collects their answers in one thread.

🎯 **What it does:** Pings each team member at a set time, asks what they did, what they're doing today, any blockers. Collects all responses into a clean summary thread in the standup channel. No AI required — just structure.

Simple. Runs on Node. Easy to self-host.

🔗 **Repo:** https://github.com/colestrode/slack-standup-bot  
📣 **Source:** One of the most-forked Slack bots for async team rituals

---

### Cursor Automations — standup summarizer

📌 **Fits when:** You want AI to pull standup data from multiple sources (GitHub, Jira, Slack threads) and write the standup summary for you, so no one has to manually type one.

🎯 **What it does:** Scheduled agent reads yesterday's GitHub commits + completed Jira tickets + Slack messages → writes and posts a formatted team update to `#standup`.

📣 **Source:** [Cursor Automations](https://cursor.com/blog/automations)

---

## 🔍 Code Review & PR Triage

> **When:** PRs pile up. Engineers don't know which ones need urgent attention. You want a bot that reads every new PR, classifies it by risk, and pings the right reviewer in Slack.

---

### Cursor Automations — PR risk classifier

📌 **Fits when:** Your team merges multiple PRs a day and reviewers are overwhelmed. You want risky PRs flagged automatically.

🎯 **What it does:** On every new PR, an agent reads the diff, classifies risk (blast radius, complexity, infrastructure impact), auto-approves low-risk PRs, and assigns reviewers to high-risk ones. Posts a summary to Slack.

> *"On every PR open or push, this automation classifies risk based on blast radius, complexity, and infrastructure impact. Low-risk PRs get auto-approved. Higher-risk PRs get up to two reviewers assigned based on contribution history."*

📣 **Source:** [Cursor Automations — March 2026](https://cursor.com/blog/automations)

---

### GitHub Issue Prioritization Agent (Postman)

📌 **Fits when:** Bug reports land in a Slack channel and you want the agent to check for duplicates, create a Linear/Jira issue, and reply in-thread with a root cause summary.

🎯 **What it does:** Triggered by a Slack message → checks for duplicate issues → creates a ticket → investigates root cause in the codebase → replies in the original Slack thread with a summary.

📣 **Source:** [Postman Agent Templates — GitHub Issue Prioritization](https://www.postman.com/templates/agents/github-issue-prioritization-agent/)

---

## 🧠 Knowledge & Q&A

> **When:** Someone asks in Slack "where's the onboarding doc?" or "what's our pricing?" and a human has to stop what they're doing to answer. You want a bot that knows your company's knowledge base and answers instantly.

---

### Vercel Community Agent Template

📌 **Fits when:** You run a developer community in Slack and need a bot that answers questions from your docs, routes unanswered questions to humans, and gives admins a panel to review what the bot said.

🎯 **What it does:** AI-powered community Q&A bot with a built-in Next.js admin panel. The bot answers questions from your knowledge base. Anything it can't answer gets flagged in the admin panel for a human to follow up. You see what the bot answered and can correct it.

Stack: Next.js · Vercel AI SDK · Slack Bolt

🔗 **Repo:** https://github.com/vercel-labs/community-agent-template  
📣 **Source:** [@aurorascharff on Twitter — "built the Community Agent Template...45 likes, widely shared in the Vercel community](https://twitter.com/aurorascharff)

---

### Vercel Knowledge Agent

📌 **Fits when:** You have a growing knowledge base (Notion, files, docs) and want an agent that stays up to date with it and answers Slack questions from it.

🎯 **What it does:** Connects to your file system or knowledge source, indexes it, and answers Slack questions with citations. Auto-updates when files change.

🔗 **Repo:** https://github.com/vercel-labs/knowledge-agent-template

---

### Composio Slack Summariser

📌 **Fits when:** A long Slack thread needs summarizing and you want one command to do it, with the summary posted back in the thread.

🎯 **What it does:** One-command Slack thread summarizer built on Composio. Reads the thread, returns a clean summary, posts it back.

🔗 **Repo:** https://github.com/ComposioHQ/slack-summariser

---

## 🔌 Connecting Slack to Other Tools

> **When:** You need your Slack agent to actually *do* things — create a Jira ticket, send an email, push a GitHub commit — not just talk. You need the plumbing that connects agents to every other tool.

---

### Composio

📌 **Fits when:** You're building a Slack agent and don't want to write five different OAuth integrations for Gmail, Jira, GitHub, Linear, Notion.

🎯 **What it does:** One library that gives your agent authenticated read/write access to 100+ tools. Your agent gets a list of tools it can call. You stop writing integrations.

```python
from composio_langchain import ComposioToolSet
tools = ComposioToolSet().get_tools(["SLACK", "GITHUB", "GMAIL", "LINEAR"])
# now your agent can read/write all of those
```

Works with: LangChain · LlamaIndex · raw Claude/OpenAI calls

🔗 **Repo:** https://github.com/ComposioHQ/composio  
📣 **Source:** Viral tweet — *"stop writing five different SDK integrations for your AI agent — Composio mounts Slack, Gmail, GitHub, Linear in one line"* (widely shared in the agent-building community)

---

### n8n — Slack workflow automation

📌 **Fits when:** You want to connect Slack to anything (Reddit monitoring, CRM updates, support tickets, content pipelines) without writing code.

🎯 **What it does:** Visual workflow builder. Drag nodes together: "when a Slack message matches a keyword → create Jira ticket + reply in thread." No code required for most flows. AI nodes available for the reasoning parts.

> An n8n social media workflow went viral on Reddit with 389 upvotes — a four-stage architecture for monitoring Reddit trends and sending AI-summarized reports to Slack.

🔗 **Templates:** https://n8n.io/integrations/slack/  
🔗 **280+ free templates:** https://github.com/enescingoz/awesome-n8n-templates  
📣 **Source:** [Reddit viral post — n8n + GPT-4 + Slack trend analysis, 389 upvotes](https://n8n.io/workflows/4373-automate-reddit-trend-analysis-with-gpt-4-and-slackgmail-distribution/)

---

## 🏠 Self-Hosted AI Assistants in Slack

> **When:** You want a full AI assistant that lives in your Slack, runs on your own server (or laptop), and you control the model, the data, and the cost.

---

### OpenClaw

📌 **Fits when:** You want one AI agent that follows you across Slack, Discord, WhatsApp, Telegram, and iMessage — all from the same self-hosted instance.

🎯 **What it does:** Run any LLM (Claude, GPT-4, DeepSeek, Gemini) from your own machine and connect it to every messaging app you use. Your agent lives in Slack DMs, answers in Discord channels, and replies to WhatsApp messages — all the same brain, all the same context.

**The viral moment:** In January 2026, it went from 9k to 149k GitHub stars in one week. The reason: it was the first tool that let AI come to you, instead of you going to AI.

🔗 **Repo:** https://github.com/openclaw/openclaw  
📣 **Source:** [SimilarLabs — "OpenClaw: Why 2026's Hottest AI Agent Project Got 60K Stars in 72 Hours"](https://similarlabs.com/blog/openclaw-ai-agent-trend-2026)  
📣 **Source:** [KDNuggets — "OpenClaw Explained: The Free AI Agent Tool Going Viral in 2026"](https://www.kdnuggets.com/openclaw-explained-the-free-ai-agent-tool-going-viral-already-in-2026)

---

### nanobot (HKUDS)

📌 **Fits when:** You want a lightweight, hackable AI agent for Slack that you can actually read the full source code of — only ~4,000 lines.

🎯 **What it does:** Minimal open-source AI agent. Connects to Slack, Discord, Telegram, WhatsApp, Teams, and 10+ more. Works with 20+ LLM providers. Small enough to understand and modify. Built by the HKU Data Intelligence Lab team.

What makes it different from OpenClaw: smaller, more readable, easier to fork and customize.

🔗 **Repo:** https://github.com/HKUDS/nanobot  
📣 **Source:** [Medium — "NanoBot: Ultra-Lightweight AI Agent Framework" — widely shared in the ML community](https://medium.com/data-science-in-your-pocket/what-is-nanobot-ultra-lightweight-ai-agent-framework-c43ad6c40b11)

---

### Bolt Python AI Chatbot (official Slack sample)

📌 **Fits when:** You want to build a custom Slack AI bot from scratch with a supported, official starting point from Slack.

🎯 **What it does:** Official Slack sample repo that wires up both Claude and GPT-4 to a Slack app. Handles app mentions, DMs, and streaming responses. The cleanest starting point if you're building something custom.

🔗 **Repo:** https://github.com/slack-samples/bolt-python-ai-chatbot

---

## Contributing

Add something you found going viral — a tweet, a Reddit post, a GitHub project getting shared around.

Rules:
1. **Must have a real source** — link to the tweet/post/thread that made it spread. No source = no merge.
2. **Must fit a real Slack workflow** — explain which kind of team would use it and when.
3. **Plain language** — write it so someone who has never set up a Slack bot can understand what it does.

Format:
```markdown
### Name

📌 **Fits when:** [the workflow / situation]

🎯 **What it does:** [one sentence, plain English]

[2-3 lines of context — what makes it worth using]

🔗 **Repo:** https://github.com/...
📣 **Source:** [description](https://link-to-tweet-or-post)
```

---

*Built as part of my work on [first-tree](https://github.com/unispark-inc/first-tree) — shared context infrastructure for agent teams.*
