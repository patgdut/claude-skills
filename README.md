# Claude Skills

A collection of Claude Code plugins that extend Claude's capabilities with custom commands and skills.

## Plugins

### [enhance-plugin](plugins/enhance-plugin/)

Prompt enhancement plugin that transforms vague user prompts into clear, structured, and actionable specifications.

**Usage:**
```
/enhance Build a todo API and make it good
```

### [example-plugin](plugins/example-plugin/)

A comprehensive example plugin demonstrating all Claude Code extension options including commands, skills, and MCP servers.

## Project Structure

```
claude-skills/
├── plugins/
│   ├── enhance-plugin/       # Prompt enhancement plugin
│   │   ├── .claude-plugin/
│   │   │   └── plugin.json
│   │   ├── commands/
│   │   │   └── enhance.md
│   │   └── skills/
│   │       └── enhance/
│   └── example-plugin/       # Example/template plugin
│       ├── .claude-plugin/
│       │   └── plugin.json
│       ├── .mcp.json
│       ├── commands/
│       └── skills/
└── enhance/                  # Legacy (migrated to plugins/enhance-plugin)
```

## Plugin Anatomy

Each plugin follows this structure:

```
plugin-name/
├── .claude-plugin/
│   └── plugin.json           # Plugin metadata (required)
├── .mcp.json                 # MCP server configuration (optional)
├── commands/
│   └── command-name.md       # Slash commands (user-invoked)
└── skills/
    └── skill-name/
        └── SKILL.md          # Skills (model-invoked)
```

### Commands vs Skills

| Feature | Commands | Skills |
|---------|----------|--------|
| Invocation | User types `/command-name` | Model auto-triggers based on context |
| Location | `commands/*.md` | `skills/*/SKILL.md` |
| Use case | Explicit user actions | Contextual assistance |

## Installation

To use these plugins with Claude Code, add them to your project or global settings.

## License

MIT
