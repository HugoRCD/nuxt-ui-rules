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

To integrate these guidelines with Cursor, follow these steps:

1.  Create a new file named `nuxt-ui.mdc` inside the `.cursor/rules/` directory of your project.

2.  Copy the complete content from your chosen rule file:
    - **Complete**: Copy everything from [nuxt-ui.md](https://github.com/hugorcd/nuxt-ui-rules/blob/main/rules/nuxt-ui.md?plain=1)
    - **Minimal**: Copy everything from [nuxt-ui-minimal.md](https://github.com/hugorcd/nuxt-ui-rules/blob/main/rules/nuxt-ui-minimal.md?plain=1)

## Using with Claude Code

### On-Demand Context

Place your chosen rule file in your project directory, for instance, `rules/nuxt-ui.md`. Then, anytime you need Claude to understand Nuxt UI best practices, simply `@`-mention the file path in your prompt to load it into the current session's context.
