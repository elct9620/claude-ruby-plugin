# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Claude Code plugin for Ruby that provides Ruby documentation access and development tools. It's designed to be installed via the [claudekit](https://github.com/elct9620/claudekit) marketplace.

## Architecture

### Markdown-as-Prompts Philosophy

This plugin is heavily based on **markdown files as AI agent prompts**. The `commands/` and `skills/` directories contain markdown files with YAML frontmatter that define:
- Instructions and procedures for the AI agent
- Tool permissions (`allowed-tools`)
- Parameter definitions and argument hints

These markdown files are **executable features**, not documentation. They define the actual behavior of commands and skills.

### Plugin Structure

The plugin follows the Claude Code plugin architecture:

- **Commands** (`commands/`): Slash commands that expand into prompts (markdown-based features)
  - `/info <query>`: Executes the `ruby:ri` skill to look up Ruby documentation

- **Skills** (`skills/`): Reusable procedures that can be invoked by commands or directly (markdown-based features)
  - `ruby:ri`: Accesses Ruby documentation using the `ri` command for classes, modules, and methods

- **Plugin Configuration** (`.claude-plugin/plugin.json`): Plugin metadata including name, description, version, and author

### Documentation Standards

README files must follow the rubric defined in `docs/rubrics/readme.md`:
- Structure: Plugin Name → Purpose → Installation → Commands → Skills → (optional sections)
- Use markdown tables for listing commands/skills/agents/hooks
- Only include applicable sections (omit unused sections like Agents or Hooks)
- Installation section is fixed (uses claudekit marketplace instructions)

## Key Commands

### Using the ri Skill

The `ruby:ri` skill is the core functionality. When using it:

```bash
# Direct lookup
ri Array#push

# Search for methods (use quotes for special characters)
ri '.find' | wc -l
ri 'String#blank?'

# Filter results
ri '.find' | grep 'Enumerable'

# List names under namespace
ri --list 'MyModule::Application'

# Preview documentation
ri 'String#upcase' | head -n 10
```

### Project Documentation

For custom Ruby projects, generate and view documentation:

```bash
# Generate documentation
rdoc --format=ri --output=ri_doc .

# View generated docs
ri -d ./ri_doc 'MyClass'
```

## Version Management

This project uses Release Please for automated versioning:
- Pushes to `main` trigger release automation via `.github/workflows/release-please.yml`
- Version is managed in two places:
  - `.release-please-manifest.json` (source of truth)
  - `.claude-plugin/plugin.json` (synced automatically)
- Use conventional commits for changelog generation

## Commit Conventions

**IMPORTANT**: Because `commands/` and `skills/` contain markdown files that are executable features (AI agent prompts), changes to these files should use:

- `feat:` - When adding new commands/skills or enhancing existing ones
- `refactor:` - When restructuring command/skill prompts without changing behavior
- `fix:` - When fixing bugs in command/skill behavior

**Do NOT use** `docs:` for changes to `commands/` or `skills/` markdown files. These are features, not documentation.

Use `docs:` only for:
- README.md changes
- Rubric documentation in `docs/rubrics/`
- This CLAUDE.md file

## Development Principles

When modifying this plugin:
- Follow the plugin README rubric in `docs/rubrics/readme.md`
- Maintain consistency between README.md structure and the rubric
- Keep skill instructions focused on `ri` command usage patterns
- Avoid checking source code or using `ruby -e` for documentation lookups
- Remember: markdown files in `commands/` and `skills/` are executable features, not documentation
