Ruby Plugin
===

## Purpose

Provides helpful Ruby extensions for various scenarios, enabling Claude Code to access Ruby documentation and development tools efficiently.

## Installation

Use [claudekit](https://github.com/elct9620/claudekit) marketplace which maintains by Aotokitsuruya.

Add following config to your marketplace configuration file:

```json
{
  "plugins": [
    {
      "name": "ruby",
      "source": {
        "source": "github",
        "repo": "elct9620/claude-ruby-plugin"
      }
    }
  ]
}
```

## Commands

| Command | Description |
|---------|-------------|
| `/info <query>` | Look up Ruby documentation using the `ri` skill for classes, modules, and methods |

## Skills

| Skill | Description |
|-------|-------------|
| `ruby:ri` | Access Ruby documentation using the `ri` command to look up classes, modules, and methods without checking source code |
