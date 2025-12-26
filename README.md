# Telegram Assistant Skill

A Claude Code skill for automating Telegram workflows: digests, channel posting, and style-matched drafts.

## Features

- **Digest Workflow**: Summarize unread messages across all chats with priority classification
- **Style Extraction**: Analyze channel posts to capture writing style patterns
- **Post Workflow**: Draft posts matching your authentic voice, saved as drafts for review

## Requirements

- [Claude Code](https://claude.ai/claude-code) or compatible agent
- [telegram-mcp](https://github.com/chigwell/telegram-mcp) server configured
- Telegram API credentials from https://my.telegram.org

## Installation

1. Clone this repo:
```bash
git clone https://github.com/BayramAnnakov/telegram-assistant-skill.git
```

2. Symlink to Claude skills directory:
```bash
ln -s /path/to/telegram-assistant-skill ~/.claude/skills/telegram-assistant
```

3. Restart Claude Code

4. Verify the skill is detected:
```
Ask Claude: "use the telegram-assistant skill to show my unread messages"
```

## Usage

### Digest Workflow
Triggers: "telegram digest", "unread messages", "morning summary"

```
"Show me a digest of my unread Telegram messages"
"Summarize what I missed in Telegram today"
```

### Style Extraction
Triggers: "analyze writing style", "extract style from channel"

```
"Analyze the writing style of my ProductsAndStartups channel"
"Extract style patterns from @cryptoEssay"
```

### Post Workflow
Triggers: "post to channel", "draft telegram post", "write for channel"

```
"Draft a post about MCP for my channel using my style"
"Write a channel post about AI agents"
```

## Safety

This skill follows a **draft-first** policy:
- Never sends messages directly via `send_message`
- Always uses `save_draft` so you can review in Telegram before sending
- Drafts appear in the chat input field in your Telegram app

## Dependencies

This skill works best with the following PRs merged into telegram-mcp:
- [PR #45](https://github.com/chigwell/telegram-mcp/pull/45): Draft management tools (save_draft, get_drafts, clear_draft)
- [PR #46](https://github.com/chigwell/telegram-mcp/pull/46): Fix unread detection (unread_mark flag)

Until merged, you can use the fork with these features.

## File Structure

```
telegram-assistant/
├── SKILL.md              # Main skill file (AgentSkills.io compliant)
├── README.md             # This file
├── LICENSE               # MIT License
└── references/
    ├── setup.md          # Installation guide for telegram-mcp
    └── style-guide.md    # Generated style guide (per-channel)
```

## AgentSkills.io Compliance

This skill follows the [AgentSkills.io](https://agentskills.io) open standard:
- Valid YAML frontmatter with required fields
- Trigger-based activation (not slash commands)
- Clear workflow documentation

## License

MIT

## Author

Bayram Annakov ([@BayramAnnakov](https://t.me/BayramAnnakov))

---

Co-created with Claude using the telegram-assistant skill itself.
