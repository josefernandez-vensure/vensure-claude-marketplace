# vensure-claude-marketplace

Curated Claude Code plugin marketplace with productivity tools, skills, and workflows.

## Available Plugins

| Plugin | Description | Version |
|--------|-------------|---------|
| [dev-assist](plugins/dev-assist/) | Development assistance tools including agents, commands, hooks, MCP, and LSP | 1.0.0 |

## Installation

### Claude Code CLI (Recommended)

#### 1. Add the Marketplace

```shell
/plugin marketplace add Vensure-Devops-QA/vensure-claude-marketplace
```

#### 2. Install a Plugin

```shell
/plugin install dev-assist@vensure-claude-marketplace
```

#### Installation Scope Options

You can specify where the plugin is installed:

```shell
# User scope (default) - available across all projects
/plugin install dev-assist@vensure-claude-marketplace --scope user

# Project scope - shared with team via version control
/plugin install dev-assist@vensure-claude-marketplace --scope project

# Local scope - project-specific, gitignored
/plugin install dev-assist@vensure-claude-marketplace --scope local
```

#### Browse Available Plugins

```shell
/plugin
```

Opens an interactive menu to browse and discover plugins.

---

### Manual Installation

If you prefer to install plugins manually:

#### 1. Clone the Repository

```shell
git clone https://github.com/Vensure-Devops-QA/vensure-claude-marketplace.git
```

#### 2. Copy Plugin Components

Copy the desired components from `plugins/<plugin-name>/` to your project's `.claude/` directory:

```
your-project/
└── .claude/
    ├── commands/          # Copy from plugins/dev-assist/commands/
    ├── agents/            # Copy from plugins/dev-assist/agents/
    ├── skills/            # Copy from plugins/dev-assist/skills/
    └── settings.json      # Configure hooks, MCP, LSP
```

#### 3. Configure Hooks

Add hook configurations to your `.claude/settings.json`:

```json
{
  "hooks": {
    "Bash": {
      "hooks": [
        {
          "matcher": "",
          "hooks": [
            {
              "type": "command",
              "command": ".claude/hooks/bash-worktree-fix.sh $CLAUDE_TOOL_INPUT"
            }
          ]
        }
      ]
    }
  }
}
```

#### 4. Configure LSP (Optional)

Add LSP server configurations to your project or user settings as needed for TypeScript and C# support.

#### 5. Configure MCP Servers (Optional)

Add MCP server configurations to your `.claude/settings.json` or user settings.

---

## Plugin Structure

Each plugin follows this structure:

```
plugins/<plugin-name>/
├── plugin.json           # Plugin manifest (required)
├── commands/             # Slash commands
├── agents/               # Agent definitions
├── skills/               # Agent skills
├── hooks/                # Event handlers
├── mcp/                  # MCP server configs
└── lsp/                  # LSP server configs
```

## Marketplace Structure

```
.claude-plugin/
├── marketplace.json      # Marketplace metadata
├── plugins.json          # Plugin registry
└── plugin.schema.json    # Plugin manifest schema
```

## Contributing

To add a new plugin to this marketplace:

1. Create a new directory under `plugins/`
2. Add a `plugin.json` manifest following the schema in `.claude-plugin/plugin.schema.json`
3. Add your components (commands, agents, skills, hooks, etc.)
4. Update `.claude-plugin/plugins.json` to register your plugin
5. Update `.claude-plugin/marketplace.json` to include your plugin
6. Submit a pull request

## License

MIT
