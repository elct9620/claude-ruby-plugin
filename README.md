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

This plugin does not provide any commands.

## Agents

This plugin does not provide any agents.

## Skills

| Skill | Description |
|-------|-------------|
| `ruby:ri` | Access Ruby documentation using the `ri` command to look up classes, modules, and methods without checking source code |

## Hooks

This plugin does not provide any hooks.

## Configuration

This plugin does not require any configuration.
