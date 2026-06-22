# awesome-slack-skills

Skills for the AI agent already running in your Slack. Not another agent to install — capabilities you give the one you have.

All entries are Slack-native MCP servers or CLIs. All under 5,000 stars. Every entry came from a real community post.

> Curated by the [first-tree](https://github.com/unispark-inc/first-tree?ref=awesome-slack-agents) team.

> use [first-tree 🌳](https://first-tree.ai/?utm_source=github&utm_medium=readme&utm_campaign=awesome-slack-agents-site) for **free!!!** — the most efficient way to **loopmaxx your engineering work** :D

---

| | Repo | Replaces |
|---|---|---|
| 1 | [korotovsky/slack-mcp-server](#1-korotskyslack-mcp-server--full-readwrite-no-bot-registration) | Registering a Slack App just to read/write channels |
| 2 | [stablyai/agent-slack](#2-stablyaiagent-slack--read-any-thread-by-url-zero-config) | Manually copying Slack threads into your agent |
| 3 | [rusq/slackdump](#3-rusqslackdump--archive-your-workspace-without-admin-rights) | Asking an admin to export your workspace |
| 4 | [slackapi/slack-mcp-plugin](#4-slackapislack-mcp-plugin--official-slack-mcp) | Third-party MCPs when you want the official one |
| 5 | [piekstra/slack-mcp-server](#5-piekstraslack-mcp-server--block-kit-messages) | Plain-text agent messages that look like bot output |
| 6 | [jtalk22/slack-mcp-server](#6-jtalk22slack-mcp-server--21-tools--workflow-profiles) | Writing oncall/triage/sprint workflows from scratch |
| 7 | [dvcrn/slack-thread-summarizer](#7-dvcrntslack-thread-summarizer--mention--summary) | Reading 80-message threads to find the decision |
| 8 | [arifszn/reminder-mcp](#8-arifsznreminder-mcp--cron-reminders-that-survive-restarts) | Slack reminders that vanish after a server restart |
| 9 | [ubie-oss/slack-mcp-server](#9-ubie-ossslack-mcp-server--production-grade-typescript-base) | Forking an unmaintained weekend-project MCP |
| 10 | [redhat-community-ai-tools/slack-mcp](#10-redhat-community-ai-toolsslack-mcp--read-only-mode) | Giving write access to an agent that only needs to read |

---

## 1. `korotovsky/slack-mcp-server` — full read/write, no bot registration

![Stars](https://img.shields.io/github/stars/korotovsky/slack-mcp-server?style=flat-square)

Read messages, post replies, upload files, manage reactions — using your existing Slack session token instead of registering a bot app. No admin approval. No app manifest. ~30,000 engineers/month use it this way.

Every other Slack MCP requires creating a Slack App and waiting for admin approval. This one uses `xoxc` + `xoxd` browser tokens, the same ones your desktop client uses.

```json
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

Get your tokens: Slack desktop → Help → Troubleshooting → Copy support link → extract from cookies in DevTools.

Tokens expire on logout. Re-extract after each logout.

🔗 https://github.com/korotovsky/slack-mcp-server  
*[Show HN](https://news.ycombinator.com/item?id=47166047)*

---

## 2. `stablyai/agent-slack` — read any thread by URL, zero config

![Stars](https://img.shields.io/github/stars/stablyai/agent-slack?style=flat-square)

Paste a Slack URL, get the thread. Downloads files and snippets. Reads Canvases as markdown. Auth is automatic if Slack Desktop is installed — no token setup.

Ships with a `SKILL.md` that works with Claude Code, Cursor, and Windsurf out of the box.

```bash
pip install agent-slack
agent-slack read https://yourworkspace.slack.com/archives/C1234/p1234567890
```

🔗 https://github.com/stablyai/agent-slack  
*[Show HN — 99 upvotes](https://news.ycombinator.com/item?id=46905745)*

---

## 3. `rusq/slackdump` — archive your workspace without admin rights

![Stars](https://img.shields.io/github/stars/rusq/slackdump?style=flat-square)

Export any channel, DM, or file into JSON/HTML/text without workspace admin privileges. Built-in MCP mode so your agent can query the archive directly.

Slack's official export requires admin. This doesn't. Works on free workspaces.

```bash
brew install rusq/brews/slackdump
slackdump -auth-flow browser      # authenticate via browser
slackdump -o ./export C1234567890 # export a channel
slackdump mcp                     # start MCP server over the archive
```

🔗 https://github.com/rusq/slackdump

---

## 4. `slackapi/slack-mcp-plugin` — official Slack MCP

![Stars](https://img.shields.io/github/stars/slackapi/slack-mcp-plugin?style=flat-square)

Search messages, list channels, post messages, manage threads. Built by the Slack team. 56 stars — almost nobody knows it exists yet.

```json
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

---

## 5. `piekstra/slack-mcp-server` — Block Kit messages

![Stars](https://img.shields.io/github/stars/piekstra/slack-mcp-server?style=flat-square)

The only Slack MCP with full Block Kit support. Every other MCP sends plain text. This one lets your agent compose rich messages with buttons, sections, images, and action menus.

```bash
git clone https://github.com/piekstra/slack-mcp-server
pip install -r requirements.txt
```

```json
{
  "mcpServers": {
    "slack": {
      "command": "python",
      "args": ["-m", "slack_mcp_server"],
      "env": { "SLACK_BOT_TOKEN": "xoxb-...", "SLACK_SIGNING_SECRET": "..." }
    }
  }
}
```

🔗 https://github.com/piekstra/slack-mcp-server

---

## 6. `jtalk22/slack-mcp-server` — 21 tools + workflow profiles

![Stars](https://img.shields.io/github/stars/jtalk22/slack-mcp-server?style=flat-square)

21 tools covering channels, users, threads, reactions, files, and user groups. The only MCP with built-in workflow profiles: `oncall-handoff`, `support-triage`, `sprint-tracker`.

```bash
git clone https://github.com/jtalk22/slack-mcp-server
npm install
# SLACK_BOT_TOKEN + SLACK_SIGNING_SECRET in .env
npm start
```

🔗 https://github.com/jtalk22/slack-mcp-server

---

## 7. `dvcrn/slack-thread-summarizer` — @mention → summary

![Stars](https://img.shields.io/github/stars/dvcrn/slack-thread-summarizer?style=flat-square)

@mention it in any thread. It reads the whole thread and posts a summary as a reply. No slash command. No config beyond a bot token and an OpenAI key.

```bash
git clone https://github.com/dvcrn/slack-thread-summarizer
pip install -r requirements.txt
# SLACK_BOT_TOKEN + SLACK_APP_TOKEN + OPENAI_API_KEY in .env
python app.py
```

🔗 https://github.com/dvcrn/slack-thread-summarizer

---

## 8. `arifszn/reminder-mcp` — cron reminders that survive restarts

![Stars](https://img.shields.io/github/stars/arifszn/reminder-mcp?style=flat-square)

Persistent cron-based Slack reminders stored in SQLite. Set a 9am Monday reminder in January, it still fires in June. Most reminder bots lose their schedule on restart.

```bash
git clone https://github.com/arifszn/reminder-mcp
npm install
# SLACK_BOT_TOKEN + SLACK_CHANNEL_ID in .env
```

Your agent calls `set_reminder(cron, message, channel)`.

🔗 https://github.com/arifszn/reminder-mcp

---

## 9. `ubie-oss/slack-mcp-server` — production-grade TypeScript base

![Stars](https://img.shields.io/github/stars/ubie-oss/slack-mcp-server?style=flat-square)

Zod-validated inputs, full test suite, clean architecture. Built by a Japanese health-tech company running it in production. The right base if you're building a custom Slack skill and don't want to inherit a weekend project.

```bash
git clone https://github.com/ubie-oss/slack-mcp-server
npm install && npm run build && npm test
```

🔗 https://github.com/ubie-oss/slack-mcp-server

---

## 10. `redhat-community-ai-tools/slack-mcp` — read-only mode

![Stars](https://img.shields.io/github/stars/redhat-community-ai-tools/slack-mcp?style=flat-square)

Read channels, threads, and users. Cannot post or delete anything. Use this when your agent only needs to read Slack — for RAG pipelines, auditing, or any context where write access is a liability.

```json
{
  "mcpServers": {
    "slack-readonly": {
      "command": "uvx",
      "args": ["redhat-slack-mcp"],
      "env": { "SLACK_BOT_TOKEN": "xoxb-...", "SLACK_TEAM_ID": "T..." }
    }
  }
}
```

🔗 https://github.com/redhat-community-ai-tools/slack-mcp

---

## Contributing

Must be Slack-native (not a generic agent with Slack support). Must have a community source — HN post, Reddit thread, or GitHub signal. Must be under 5,000 stars. One entry per PR.

```markdown
## N. `owner/repo` — tagline

![Stars](https://img.shields.io/github/stars/owner/repo?style=flat-square)

One sentence on what capability it adds. One sentence on what makes it different.

```bash
# install + config
```

🔗 https://github.com/owner/repo  
*[source](link)*
```

---

*Maintained as part of [first-tree](https://github.com/unispark-inc/first-tree?ref=awesome-slack-agents) — shared context infrastructure for agent teams.*
