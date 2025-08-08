# Guidelines for AI Assistants

Leverage the full power of Nuxt UI in your AI-powered workflow. These guidelines are designed to help AI coding assistants like Cursor, Windsurf, Claude Code, and others understand the best practices for working with the Nuxt UI component library.

## Available Rule Sets

We provide two versions of Nuxt UI rules to fit different needs:

### 📚 Complete Rules (`nuxt-ui.md`) - **Recommended**

- **~600 lines** - Comprehensive documentation and examples
- **Detailed breaking changes** - Full v2 → v3 migration guide
- **Advanced patterns** - Theming, performance, accessibility, TypeScript
- **Best for most projects and learning**

### 📋 Minimal Rules (`nuxt-ui-minimal.md`)

- **~140 lines** - Optimized for AI assistants with token limits
- **Essential changes only** - Core breaking changes and patterns
- **Quick reference** - Most common pitfalls to avoid
- **For AI assistants with limited context**

## Getting Started

**Recommended** → Use the [complete rules](https://github.com/hugorcd/nuxt-ui-rules/blob/main/rules/nuxt-ui.md?plain=1)

**For AI assistants with limited context** → Use the [minimal rules](https://github.com/hugorcd/nuxt-ui-rules/blob/main/rules/nuxt-ui-minimal.md?plain=1)

## Using with Cursor

**Option 1 - Via Settings Interface (Recommended)** 🎯

1. Open Cursor Settings (`Cmd/Ctrl + ,`)
2. Navigate to **"Rules for AI"** tab
3. Copy and paste your chosen rule content:
   - **Complete**: Copy from [nuxt-ui.md](https://github.com/hugorcd/nuxt-ui-rules/blob/main/rules/nuxt-ui.md?plain=1)
   - **Minimal**: Copy from [nuxt-ui-minimal.md](https://github.com/hugorcd/nuxt-ui-rules/blob/main/rules/nuxt-ui-minimal.md?plain=1)

**Option 2 - Via File Configuration**

1. Create `.cursor/rules/nuxt-ui.mdc` in your project root
2. Copy your chosen rule content into this file

## Using with Claude Code

### On-Demand Context

Place your chosen rule file in your project directory, for instance, `rules/nuxt-ui.md`. Then, anytime you need Claude to understand Nuxt UI best practices, simply `@`-mention the file path in your prompt to load it into the current session's context.

## Sync with your repo

Add `.github/workflows/sync-ai-rules.yml` with the following content:

```yml
name: Sync AI Rules
on:
  schedule:
    - cron: '0 0 1 * *' # Monthly
  workflow_dispatch:
jobs:
  sync:
    runs-on: ubuntu-latest
    permissions:
      contents: write
      pull-requests: write
    steps:
      - uses: actions/checkout@v4
      - name: Download remote file
        run: |
          curl -sL https://raw.githubusercontent.com/HugoRCD/nuxt-ui-rules/refs/heads/main/rules/nuxt-ui.md --output nuxt-ui.md
      - name: Compare and commit if changed
        run: |
          if ! cmp -s nuxt-ui.md .prompts/nuxt-ui.md; then
            mv nuxt-ui.md .prompts/nuxt-ui.md
            git config user.name "${{ github.actor }}"
            git config user.email "${{ github.actor }}@users.noreply.github.com"
            git add .cursor/rules/nuxt-ui.md
            git commit -m "chore(ci): synced nuxt-ui.md"
            git push
          else
            echo "No changes detected."
          fi
```

This will check if there are any changes in source rules file and if found will update in your repo.
