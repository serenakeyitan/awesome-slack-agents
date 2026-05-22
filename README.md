# awesome-slack-agents

> *check out my recent work at [first-tree](https://github.com/unispark-inc/first-tree) — shared context infrastructure for agent teams.*

![Awesome](https://awesome.re/badge.svg)
![License: CC0](https://img.shields.io/badge/License-CC0-lightgrey.svg)

**A curated list of the best AI agents to run in your Slack or Discord — sourced from what's actually going viral on Twitter and Reddit.**

Every entry links back to the original tweet, thread, or post that made it spread. No vendor blog posts. No affiliate lists. Just things real builders are shipping and talking about.

---

## Table of Contents

### Agents (Install & Run)
- [OpenClaw — AI agent for Slack, Discord, WhatsApp + 20 others](#openclaw)
- [Vercel Community Agent — AI-powered Slack community manager](#vercel-community-agent)
- [Vercel AI SDK Slackbot — streaming LLM replies in threads](#vercel-ai-sdk-slackbot)
- [Bolt Python AI Chatbot — Slack app powered by Claude + OpenAI](#bolt-python-ai-chatbot)
- [Bolt Python Assistant Template — agent with side panel + suggested prompts](#bolt-python-assistant-template)
- [Tempo AI Agent — autonomous engineering team agent in Slack](#tempo-ai-agent)

### Frameworks (Build Your Own)
- [Slack Bolt (Python / JS) — official event-driven framework](#slack-bolt)
- [Vercel AI SDK + Slack Adapter — streaming agents on Vercel](#vercel-ai-sdk--slack-adapter)
- [Composio — connect any agent to Slack, Gmail, GitHub in one line](#composio)

### Practices & Architecture
- [Slack as Agentic OS — MCP client built into Slackbot (Salesforce)](#slack-as-agentic-os)
- [Multi-agent channel architecture — DMs as agent-to-agent protocol](#multi-agent-channel-architecture)
- [Integrating agentic stacks into Slack — enterprise orchestration guide](#integrating-agentic-stacks-into-slack)

---

## Agents (Install & Run)

---

### OpenClaw

> Your own personal AI assistant. Runs locally. Connects to Slack, Discord, WhatsApp, Telegram, iMessage, Teams, and 20+ more.

**300,000+ GitHub stars.** Went from a weekend side project to the fastest-growing GitHub repo in history — 60k stars in 72 hours in January 2026. MIT license. Connect any LLM (Claude, GPT, DeepSeek, Gemini) and control it from any chat platform.

**Slack setup:** Add as a workspace app, send it messages in DMs or channels. It reads context, calls your LLM, replies in thread.

```bash
git clone https://github.com/openclaw/openclaw
# configure your LLM key + Slack token in .env
docker-compose up
```

🔗 **Repo:** https://github.com/openclaw/openclaw  
📣 **Source:** [The viral moment — 60k stars in 72 hours (SimilarLabs writeup)](https://similarlabs.com/blog/openclaw-ai-agent-trend-2026)

---

### Vercel Community Agent

> Open-source AI-powered Slack community management bot with a built-in Next.js admin panel.

Built by the Vercel team. Uses AI SDK, Chat SDK, and Vercel Workflow. Handles community Q&A, moderation signals, and admin review in one package. The admin panel is the part most community bots miss.

**Stack:** Next.js · AI SDK · Vercel Workflow · Bolt for JS  
**Deploy:** One-click to Vercel

🔗 **Repo:** https://github.com/vercel-labs/community-agent-template  
📣 **Source:** [@aurorascharff tweet — "built the Community Agent Template...it's up on Vercel templates" (45 likes)](https://twitter.com/aurorascharff)

---

### Vercel AI SDK Slackbot

> An AI-powered Slack chatbot that streams LLM responses directly into threads.

Minimal, clean starting point. Handles app mentions and DMs. Streams tokens so replies feel fast. Good base if you want to add tools on top.

**Stack:** AI SDK · Bolt for JS · Vercel  
**Deploy:** One-click to Vercel

🔗 **Repo:** https://github.com/vercel-labs/ai-sdk-slackbot  
🔗 **Template:** https://vercel.com/templates/other/ai-sdk-slackbot

---

### Bolt Python AI Chatbot

> Bring AI into your workspace — chatbot powered by Anthropic and OpenAI, official Slack sample.

Official Slack sample repo. Supports both Claude and GPT. Good for teams that want a maintained, supported starting point rather than a community fork.

**Stack:** Python · Bolt · Anthropic SDK · OpenAI SDK

🔗 **Repo:** https://github.com/slack-samples/bolt-python-ai-chatbot

---

### Bolt Python Assistant Template

> Agent with Slack's native Assistant side panel + suggested prompts.

Uses Slack's newer Assistant API — the side panel that slides in from the right. Lets you show suggested prompts, stream responses, and handle multi-turn context in a cleaner UX than @mentions in a channel.

🔗 **Repo:** https://github.com/slack-samples/bolt-python-assistant-template

---

### Tempo AI Agent

> Autonomous engineering team agent that lives in Slack — plans, codes, reviews, ships.

Not a chatbot. Tempo's agent receives Slack messages, breaks them into tasks, writes code, opens PRs, and updates you in thread. Real async engineering work through Slack.

📣 **Source:** [@jevgenijs tweet — "Our AI agent in Slack has been a game changer... huge kudos to the Tempo team" (8 likes)](https://twitter.com/jevgenijs)  
📣 **Source:** [@jpegmogul — "when @patrickc described AI-native orgs to @sama, he pointed to Tempo" (13 likes)](https://twitter.com/jpegmogul)  
🔗 **Product:** https://www.tempolabs.ai

---

## Frameworks (Build Your Own)

---

### Slack Bolt

> The official Slack framework for building event-driven agents in Python or JavaScript.

The standard starting point. Handles OAuth, event subscriptions, slash commands, modals, and the Assistant API. Every serious Slack agent is built on this or wraps it.

**Python:** https://github.com/slackapi/bolt-python  
**JS/TS:** https://github.com/slackapi/bolt-js

---

### Vercel AI SDK + Slack Adapter

> Build streaming agents with tool use, deploy on Vercel, wire to Slack in a few lines.

The Vercel Slack Adapter handles Bolt plumbing so you can focus on agent logic. Pairs with the AI SDK's tool-calling and streaming primitives. The lead-agent template shows the full pattern: inbound Slack message → agent reasons → calls tools → replies in thread.

🔗 **Lead Agent (full example):** https://github.com/vercel-labs/lead-agent  
🔗 **Slack Agent Template (Nitro):** https://github.com/vercel-partner-solutions/slack-agent-template

---

### Composio

> Connect any AI agent to Slack, Gmail, GitHub, Linear, and 100+ tools in one line of code.

Stop writing five different SDK integrations. Composio gives your agent authenticated read/write access to every tool without managing OAuth yourself. Works with LangChain, LlamaIndex, raw OpenAI/Anthropic calls.

```python
from composio_langchain import ComposioToolSet
tools = ComposioToolSet().get_tools(["SLACK", "GITHUB", "GMAIL"])
```

📣 **Source:** [@so_sthbryan tweet — "Stop writing five different SDK integrations...Composio mounts Slack, Gmail, GitHub, Linear"](https://twitter.com/so_sthbryan)  
🔗 **Repo:** https://github.com/ComposioHQ/composio

---

## Practices & Architecture

---

### Slack as Agentic OS

> Salesforce shipped ~30 new AI capabilities for Slack — headline: MCP client built directly into Slackbot.

Slack is now a two-way orchestration hub. Slackbot as MCP client reaches out to external tools. External AI clients can pull data *from* Slack via the MCP server. This changes what "a Slack agent" can mean — instead of one bot per tool, agents share context through MCP.

📣 **Source:** [Salesforce blog — "Architect the Future UI: Slack as Your Agentic Surface"](https://www.salesforce.com/blog/slack-agentic-enterprise-architecture/)  
📣 **Source:** [Slack official — "Best Agentic AI Platforms for 2026"](https://slack.com/blog/productivity/best-agentic-ai-platforms-for-2026-what-they-are-and-how-to-choose-one)  
📣 **Source:** [AI Automation Global — "Slack Becomes an Agentic OS: 30 AI Features + MCP"](https://aiautomationglobal.com/blog/slack-ai-agentic-os-mcp-30-features-2026)

---

### Multi-Agent Channel Architecture

> How to structure Slack channels and DMs so multiple agents don't collide.

Core principle: **DMs as agent-to-agent protocol.** Agent logic stays platform-agnostic (reasoning layer independent of Slack). Platform-specific code = thin adapter that handles Block Kit formatting and thread management. All agents share the same knowledge base regardless of which channel they're in.

Key patterns:
- `#agent-ops` — one channel for agent status/errors, not scattered across product channels
- `#agent-debug` — separate trace/log channel agents write to when something breaks
- Use threads, not new messages — agents replying in-thread keep context scoped
- One agent, one job — Swiss Army knife bots become impossible to debug

📣 **Source:** [MindStudio — "Multi-Channel AI Agent Deployment: Slack, Teams & Beyond"](https://www.mindstudio.ai/blog/multi-channel-ai-agent-deployment-slack-teams)

---

### Integrating Agentic Stacks into Slack

> Enterprise guide: how to pack your full agentic stack (RAG, tools, memory) into a Slack deployment.

Covers the hard parts: auth context across turns, handling rate limits gracefully, routing messages to the right agent when you have more than one, and keeping Slack UX clean when the agent is doing slow async work.

📣 **Source:** [earezki.com — "Integrating Agentic Stacks into Slack: Enterprise AI Orchestration" (2026-05-20)](https://earezki.com/ai-news/2026-05-20-pack-your-agentic-stack-in-slack/)

---

## Contributing

Add an entry via PR. Requirements:

1. **Real thing** — must be a working repo, not a concept or vendor pitch
2. **Source link required** — cite the tweet, Reddit post, or blog that made it spread. No source = PR closed.
3. **Format:**

```markdown
### Name
> One-line description

What it does, why it's worth using, honest note on limits.

📣 **Source:** [description of the original post](https://link-to-tweet-or-post)  
🔗 **Repo/Link:** https://github.com/...
```

---

*Built as part of my work on [first-tree](https://github.com/unispark-inc/first-tree) — shared context infrastructure for agent teams.*
