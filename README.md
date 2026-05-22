# 🧩 awesome-slack-skills

<p align="center">
  <img src="https://img.shields.io/badge/skills-10%20hidden%20gems-blueviolet?style=for-the-badge" />
  <img src="https://img.shields.io/badge/sources-HN%20%7C%20Reddit%20%7C%20GitHub-orange?style=for-the-badge" />
  <img src="https://img.shields.io/badge/stars-%3C5k%20only-green?style=for-the-badge" />
  <img src="https://img.shields.io/badge/license-CC0-lightgrey?style=for-the-badge" />
  <img src="https://awesome.re/badge-flat2.svg" />
</p>

<p align="center">
  <b>Your Slack agent already exists. These are the skills worth giving it.</b><br/>
  Hidden gems only — under 5,000 stars, all Slack-native, all community-discovered.
</p>

> Curated by the [first-tree](https://github.com/unispark-inc/first-tree?ref=awesome-slack-agents) team — shared context infrastructure for agent teams.

---

## The idea

Most "awesome Slack bots" lists give you a new agent to install. This one doesn't.

Assume you already have an AI agent running in Slack — Claude, GPT-4, whatever you chose. This list gives that agent new **skills**: read a thread, archive a channel, set a cron reminder, format rich messages with Block Kit. Each skill is a Slack-native MCP server or CLI tool. Every entry was found from a real community post — HN, Reddit, or GitHub trending — not a vendor press release.

**What counts as a skill vs. an agent:**
- ❌ Agent — full AI assistant (big, general, needs its own Slack app registration)
- ✅ Skill — one specific Slack capability your existing agent gains by calling an MCP tool

**Signal floor for entries:** GitHub repos ≥ 15 stars OR HN/Reddit post ≥ 30 upvotes. Below floor = clearly labeled.

---

## Skills

| # | Skill | What it gives your agent | Stars |
|---|-------|--------------------------|-------|
| 1 | [Read & write Slack — no bot registration](#1-korotskyslack-mcp-server--read--write-any-channel-no-bot-registration) | Full Slack access via browser session | ~1,600 ⭐ |
| 2 | [Use Slack from a CLI](#2-stablyaiagent-slack--use-slack-from-a-cli-or-any-ai-agent) | Read threads, download files, zero-config auth | ~415 ⭐ |
| 3 | [Archive your whole workspace](#3-rusqslackdump--archive-your-whole-workspace-no-admin-needed) | Export DMs and channels without admin | ~2,600 ⭐ |
| 4 | [Official Slack MCP plugin](#4-slackapislack-mcp-plugin--official-slack-mcp-plugin) | Slack's own MCP, brand new | ~56 ⭐ |
| 5 | [Send rich Block Kit messages](#5-piekstraslack-mcp-server--send-rich-block-kit-messages) | The only MCP with full Block Kit support | ~3 ⭐ |
| 6 | [21 Slack tools in one server](#6-jtalk22slack-mcp-server--21-slack-tools-one-server) | Channels, users, threads, workflows | ~23 ⭐ |
| 7 | [Summarize any thread with a @mention](#7-dvcrntslack-thread-summarizer--summarize-any-thread-with-a-mention) | No command needed — just @mention | ~18 ⭐ |
| 8 | [Cron reminders that survive restarts](#8-arifsznreminder-mcp--cron-reminders-that-survive-server-restarts) | Set-and-forget scheduled Slack pings | ~15 ⭐ |
| 9 | [Production-grade TypeScript MCP](#9-ubie-ossslack-mcp-server--production-grade-typescript-mcp) | Zod-validated, tested, ready to fork | ~110 ⭐ |
| 10 | [Red Hat read-only mode](#10-redhat-community-ai-toolsslack-mcp--red-hat-read-only-mode) | Safe read access for auditing or RAG | ~24 ⭐ |

---

## 1. `korotovsky/slack-mcp-server` — Read & write any channel, no bot registration

![Stars](https://img.shields.io/github/stars/korotovsky/slack-mcp-server?style=flat-square&label=⭐)

**What your agent gains:** Read messages, post replies, upload files, and manage reactions — using your own Slack session token instead of registering a bot. Zero footprint in workspace admin.

**Why it's different:** Every other Slack MCP requires creating a Slack App, going through the admin approval flow, and getting a bot token. This one uses `xoxc` + `xoxd` browser session tokens — the same ones your Slack desktop app uses. No admin. No app manifest. No waiting for approval. ~30,000 engineers/month are using it this way.

**The Slack workflows it fits:**
- Agent reads a `#support` thread → drafts a reply → you approve → agent posts it
- Agent monitors `#incidents` → DMs oncall with a summary when a new incident is created
- Agent scans `#general` → extracts action items → posts a digest to `#agent-ops`

**Onboarding:**
```bash
# 1. Get your session tokens from Slack desktop
#    Open Slack desktop → Help → Troubleshooting → Copy support link
#    Extract xoxc-... and xoxd=... from the cookies in browser DevTools

# 2. Run the MCP server
npx @korotovsky/slack-mcp-server

# 3. Add to Claude Desktop / Cursor / any MCP client
# In your MCP config:
{
  "mcpServers": {
    "slack": {
      "command": "npx",
      "args": ["@korotovsky/slack-mcp-server"],
      "env": {
        "SLACK_MCP_XOXC_TOKEN": "xoxc-...",
        "SLACK_MCP_XOXD_TOKEN": "xoxd=..."
      }
    }
  }
}
```

**Known limitation:** Session tokens expire when you log out of Slack. Re-extract after each logout. Not suitable for fully automated server-side bots (use a bot token approach for those).

🔗 https://github.com/korotovsky/slack-mcp-server  
📣 *source: [Show HN — "Slack MCP Server (no bot registration)"](https://news.ycombinator.com/item?id=47166047) — 30k engineers/month*

---

## 2. `stablyai/agent-slack` — Use Slack from a CLI or any AI agent

![Stars](https://img.shields.io/github/stars/stablyai/agent-slack?style=flat-square&label=⭐)

**What your agent gains:** Read any Slack channel or thread by pasting a URL. Download files and snippets. Read Canvases as markdown. Works with Claude Code, Cursor, and Windsurf via a built-in `SKILL.md`.

**Why it's different:** Auth is zero-config if you have Slack Desktop installed — it reads your existing login session. No token setup, no Slack App registration. Paste a URL, get the thread.

**The Slack workflows it fits:**
- Give your coding agent a Slack thread URL → it reads the bug report → writes the fix
- Agent reads a Canvas with architecture decisions → answers questions about it
- Pull a file someone shared in Slack into your agent's working directory

**Onboarding:**
```bash
pip install agent-slack

# That's it. Auth is automatic if Slack Desktop is installed.
# Test it:
agent-slack read https://yourworkspace.slack.com/archives/C1234/p1234567890

# For Claude Code / Cursor — SKILL.md is included in the repo:
# https://github.com/stablyai/agent-slack/blob/main/SKILL.md
# Drop it into your project root and your agent learns the tool automatically.
```

🔗 https://github.com/stablyai/agent-slack  
📣 *source: [Show HN — "Agent-Slack: CLI for AI agents to use Slack"](https://news.ycombinator.com/item?id=46905745) — 99 upvotes, 35 comments*

---

## 3. `rusq/slackdump` — Archive your whole workspace, no admin needed

![Stars](https://img.shields.io/github/stars/rusq/slackdump?style=flat-square&label=⭐)

**What your agent gains:** Export any channel, DM, or file from Slack into structured JSON/HTML/text — without workspace admin privileges. Built-in read-only MCP mode so your agent can query the archive.

**Why it's different:** Slack's official export requires admin rights. This doesn't. Uses the same browser session token approach as `korotovsky/slack-mcp-server`. Export your own DMs. Export channels you're a member of. Works on free workspaces.

**The Slack workflows it fits:**
- Archive `#engineering-decisions` → feed it to an RAG system → agent answers "why did we choose X?"
- Export your DMs before you leave a company
- Agent reads historical context from the archive without live Slack API calls

**Onboarding:**
```bash
# macOS/Linux
brew install rusq/brews/slackdump
# or download binary from https://github.com/rusq/slackdump/releases

# Run with browser auth (no token needed)
slackdump -auth-flow browser

# Export a channel
slackdump -o ./export C1234567890

# Start built-in MCP server (so your AI agent can query the archive)
slackdump mcp
```

🔗 https://github.com/rusq/slackdump  
📣 *source: [GitHub trending — consistently appears in Slack/Go categories](https://github.com/rusq/slackdump)*

---

## 4. `slackapi/slack-mcp-plugin` — Official Slack MCP plugin

![Stars](https://img.shields.io/github/stars/slackapi/slack-mcp-plugin?style=flat-square&label=⭐)

**What your agent gains:** Slack's own official MCP plugin — search messages, list channels, post messages, manage threads. Built by the Slack team.

**Why it's different:** This is the canonical Slack MCP. Brand new (2025). So new that almost nobody knows it exists yet — 56 stars as of this writing. If Slack is going to maintain one MCP server, it's this one.

**The Slack workflows it fits:**
- Search across all channels for messages matching a query
- List channel members and recent activity
- Post structured messages from your agent

**Onboarding:**
```bash
# Requires a Slack App with appropriate scopes
# See: https://github.com/slackapi/slack-mcp-plugin#setup

npm install @slack/mcp-plugin

# Add to your MCP client config:
{
  "mcpServers": {
    "slack": {
      "command": "npx",
      "args": ["-y", "@slack/mcp-plugin"],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-...",
        "SLACK_TEAM_ID": "T..."
      }
    }
  }
}
```

🔗 https://github.com/slackapi/slack-mcp-plugin  
📣 *source: [Official Slack API GitHub org](https://github.com/slackapi) — published quietly in 2025*

---

## 5. `piekstra/slack-mcp-server` — Send rich Block Kit messages

![Stars](https://img.shields.io/github/stars/piekstra/slack-mcp-server?style=flat-square&label=⭐)

**What your agent gains:** The only Slack MCP that exposes full Block Kit support — rich interactive messages with buttons, dividers, sections, images, and markdown formatting.

**Why it's different:** Every other Slack MCP sends plain text. Block Kit is how Slack's own apps send beautiful structured messages. This is the only MCP that lets your agent compose them.

**The Slack workflows it fits:**
- Agent posts a daily digest with action buttons (✅ Done / ➡️ Snooze)
- Incident notification with structured fields (severity, team, link to runbook)
- PR review request with formatted diff summary and approve/reject buttons

**Onboarding:**
```bash
git clone https://github.com/piekstra/slack-mcp-server
cd slack-mcp-server
pip install -r requirements.txt

# Add to MCP config:
{
  "mcpServers": {
    "slack": {
      "command": "python",
      "args": ["-m", "slack_mcp_server"],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-...",
        "SLACK_SIGNING_SECRET": "..."
      }
    }
  }
}
```

🔗 https://github.com/piekstra/slack-mcp-server  
📣 *source: only MCP server in the Slack MCP ecosystem with Block Kit — surfaced via GitHub search `topic:slack-mcp`*

---

## 6. `jtalk22/slack-mcp-server` — 21 Slack tools, one server

![Stars](https://img.shields.io/github/stars/jtalk22/slack-mcp-server?style=flat-square&label=⭐)

**What your agent gains:** The most complete Slack MCP tool surface — 21 individual tools covering channels, users, threads, reactions, files, user groups, and built-in workflow profiles.

**Why it's different:** Comes with three pre-built workflow profiles your agent can activate:
- `oncall-handoff` — structured shift handoff in Slack
- `support-triage` — incoming support tickets routed by urgency
- `sprint-tracker` — daily Slack pings with sprint velocity data

**The Slack workflows it fits:**
- Oncall engineer hands off to the next shift: agent runs `oncall-handoff`, posts structured summary to `#oncall`
- Support rotation: agent triages new threads in `#support`, assigns to the right person
- Sprint sync: agent reads Linear/Jira, posts a daily velocity update to `#engineering`

**Onboarding:**
```bash
git clone https://github.com/jtalk22/slack-mcp-server
npm install

# Configure .env:
SLACK_BOT_TOKEN=xoxb-...
SLACK_SIGNING_SECRET=...

npm start
# Exposes MCP tools: send_message, get_channel_history, list_users,
#   add_reaction, upload_file, get_thread, create_channel, + 14 more
```

🔗 https://github.com/jtalk22/slack-mcp-server  
📣 *source: surfaced via GitHub search `topic:slack-mcp` — only MCP with built-in workflow profiles*

---

## 7. `dvcrn/slack-thread-summarizer` — Summarize any thread with a @mention

![Stars](https://img.shields.io/github/stars/dvcrn/slack-thread-summarizer?style=flat-square&label=⭐)

**What your agent gains:** @mention it in any Slack thread → it reads the whole thread → posts a clean summary as a reply. No slash commands. No config. Just @mention.

**Why it's different:** Single-purpose. Does one thing. No setup beyond a bot token and an OpenAI key. The interaction model is the simplest possible: it lives in your workspace, you @mention it when you need a summary.

**The Slack workflows it fits:**
- Long `#engineering` debate → @summarize-bot → "Here are the 4 positions discussed and the decision reached"
- Support ticket thread → @summarize-bot → clean handoff summary for the next agent
- Meeting notes in Slack → @summarize-bot → action items extracted automatically

**Onboarding:**
```bash
git clone https://github.com/dvcrn/slack-thread-summarizer
pip install -r requirements.txt

# .env
SLACK_BOT_TOKEN=xoxb-...
SLACK_APP_TOKEN=xapp-...   # for socket mode
OPENAI_API_KEY=sk-...

python app.py
# Invite the bot to any channel → @mention it in a thread
```

🔗 https://github.com/dvcrn/slack-thread-summarizer  
📣 *source: surfaced via GitHub search `topic:slack-bot stars:>10` — single-purpose, zero bloat*

---

## 8. `arifszn/reminder-mcp` — Cron reminders that survive server restarts

![Stars](https://img.shields.io/github/stars/arifszn/reminder-mcp?style=flat-square&label=⭐)

**What your agent gains:** Persistent cron-based Slack reminders. Set a reminder once → it fires even if the server restarts. Reminders are stored in SQLite, not in memory.

**Why it's different:** Most reminder bots lose their schedule on restart. This one persists to SQLite and reloads on boot. Set a 9am Monday reminder in January, it still fires in June.

**The Slack workflows it fits:**
- Weekly standup reminder every Monday at 9am in `#engineering`
- "Did you close your tickets?" ping every Friday at 4pm
- Monthly billing reminder to `#finance`
- Daily oncall reminder: "who's on call this week?"

**Onboarding:**
```bash
git clone https://github.com/arifszn/reminder-mcp
npm install

# .env
SLACK_BOT_TOKEN=xoxb-...
SLACK_CHANNEL_ID=C...

# MCP config — your agent calls set_reminder(cron, message, channel):
{
  "mcpServers": {
    "reminder": {
      "command": "node",
      "args": ["dist/index.js"],
      "cwd": "/path/to/reminder-mcp"
    }
  }
}
```

🔗 https://github.com/arifszn/reminder-mcp  
📣 *source: surfaced via GitHub search `topic:mcp slack reminder` — only persistent-cron reminder MCP*

---

## 9. `ubie-oss/slack-mcp-server` — Production-grade TypeScript MCP

![Stars](https://img.shields.io/github/stars/ubie-oss/slack-mcp-server?style=flat-square&label=⭐)

**What your agent gains:** A TypeScript Slack MCP server with Zod input validation, full test coverage, and clean architecture — ready to fork and extend without fighting untyped spaghetti.

**Why it's different:** Most Slack MCP servers are weekend projects. This one is production-quality: typed schemas for every tool, proper error handling, and a test suite. Built by Ubie (Japanese health-tech company running it in production). The best base for teams building a custom Slack skill.

**The Slack workflows it fits:**
- Starting point for any custom Slack skill your team needs to build
- Teams who need audit logs and proper error handling
- Production deployments where "it crashed and we don't know why" is not acceptable

**Onboarding:**
```bash
git clone https://github.com/ubie-oss/slack-mcp-server
npm install
npm run build

# Add to MCP config:
{
  "mcpServers": {
    "slack": {
      "command": "node",
      "args": ["dist/index.js"],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-...",
        "SLACK_TEAM_ID": "T..."
      }
    }
  }
}

npm test   # full test suite passes out of the box
```

🔗 https://github.com/ubie-oss/slack-mcp-server  
📣 *source: surfaced via GitHub search `topic:slack-mcp language:TypeScript` — highest code quality in category*

---

## 10. `redhat-community-ai-tools/slack-mcp` — Red Hat read-only mode

![Stars](https://img.shields.io/github/stars/redhat-community-ai-tools/slack-mcp?style=flat-square&label=⭐)

**What your agent gains:** Read-only Slack MCP. Your agent can read channels, threads, and users — but cannot post or modify anything. Designed for auditing, RAG pipelines, and safe production use.

**Why it's different:** Write access to Slack is dangerous in production. This server is intentionally read-only — it's impossible for it to post a message or delete anything. Use it when your agent only needs to *read* Slack, not act on it.

**The Slack workflows it fits:**
- RAG: agent reads `#engineering-decisions` history → answers architecture questions
- Monitoring: agent reads `#alerts` → generates a report → posts it via a separate system
- Onboarding: new team member asks agent "what did we decide about X?" → agent reads Slack history

**Onboarding:**
```bash
# Works as a Claude Code plugin out of the box
# Add to claude_desktop_config.json:
{
  "mcpServers": {
    "slack-readonly": {
      "command": "uvx",
      "args": ["redhat-slack-mcp"],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-...",
        "SLACK_TEAM_ID": "T..."
      }
    }
  }
}
```

🔗 https://github.com/redhat-community-ai-tools/slack-mcp  
📣 *source: surfaced via GitHub search — only Slack MCP explicitly designed as read-only*

---

## How to use these with your agent

All 10 skills are MCP servers or CLIs. Your existing agent (Claude, GPT-4, whatever) calls them as tools.

**Quick start with Claude Desktop:**
1. Pick a skill from the list above
2. Add it to `~/Library/Application\ Support/Claude/claude_desktop_config.json`
3. Restart Claude Desktop
4. Your agent can now call those Slack tools in any conversation

**Quick start with Claude Code:**
```bash
# Add to .mcp.json in your project root:
{
  "mcpServers": {
    "slack": {
      "command": "npx",
      "args": ["@korotovsky/slack-mcp-server"],
      "env": { "SLACK_MCP_XOXC_TOKEN": "...", "SLACK_MCP_XOXD_TOKEN": "..." }
    }
  }
}
```

**Stack multiple skills:** you can register multiple MCP servers simultaneously. Your agent picks the right tool for each task.

---

## Contributing

Found a Slack-native MCP server or skill that belongs here?

**Rules:**
1. Must be **Slack-native** — not a generic agent, not a multi-platform tool that happens to support Slack
2. Must have a **community source** (HN post, Reddit thread, GitHub search rank, or tweet with engagement). No source = no merge.
3. Must be **under 5,000 stars** — if it's famous, it doesn't need this list
4. One entry per PR. Use this format:

```markdown
### `owner/repo` — tagline

![Stars](https://img.shields.io/github/stars/owner/repo?style=flat-square&label=⭐)

**What your agent gains:** one sentence

**Why it's different:** one sentence — what does it do that others don't?

**Onboarding:**
```bash
# actual commands
```

🔗 https://github.com/owner/repo  
📣 *source: [description](link)*
```

---

*Maintained as part of [first-tree](https://github.com/unispark-inc/first-tree?ref=awesome-slack-agents) — shared context infrastructure for agent teams.*
