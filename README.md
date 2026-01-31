# rice-opencode

Personal [OpenCode](https://opencode.ai) configuration — a complete AI-assisted development environment with specialized agents, MCP servers, and document generation tools.

## Overview

This repository contains a fully-featured OpenCode-AI configuration designed for professional software development workflows. It provides specialized AI agents for different tasks, integrated MCP servers for external knowledge sources, and a custom document generation plugin.

## Features

### Specialized Agents

| Agent | Model | Purpose |
|-------|-------|---------|
| `explore` | Gemini 3 Flash | Fast codebase navigation and file discovery |
| `docs-first-coder` | Claude Opus 4.5 | Documentation-verified coding with live API research |
| `code-checker` | Gemini 3 Flash | Code review, smells detection, and verification |
| `esp32-tdd-coder` | Claude Opus 4.5 | ESP32 embedded development with strict TDD |
| `esp32-tdd-test-writer` | GLM-4.7 | ESP32 unit test generation from specifications |
| `document-writer` | Kimi K2 Thinking | Academic papers, reports, and PDF generation |

### MCP Server Integrations

- **GitHub Copilot** — Code search and repository intelligence
- **DeepWiki** — Repository documentation and structure analysis
- **Context7** — Library documentation queries
- **Brave Search** — Web search via Brave API
- **DuckDuckGo Search** — Alternative web search

### Document Generation Plugin

Custom TypeScript plugin for creating professional documents:

- **IEEE Papers** — Two-column conference and journal formats
- **School Reports** — SIT/UofG branded reports with logos
- **Styled PDFs** — Professional documents with Eisvogel template
- **Format Conversion** — Pandoc-powered format conversion

## Repository Structure

```
├── agents/                 # Agent prompt definitions
│   ├── builder-prompt.md   # Core builder methodology
│   ├── code-checker.md     # Code verification agent
│   ├── docs-first-coder.md # Documentation-first coding
│   ├── document-writer.md  # Document generation agent
│   ├── esp32-tdd-coder.md  # ESP32 TDD practitioner
│   ├── esp32-tdd-test-writer.md
│   └── explore.md          # File system navigator
├── plugins/                # OpenCode plugin source (TypeScript)
│   └── docs.ts            # Document generation plugin
├── src/                    # Supporting modules
├── pandoc/                 # LaTeX templates and assets
│   ├── assets/            # Logo images (SIT, UofG)
│   └── templates/         # LaTeX templates
├── opencode.json          # Main OpenCode configuration
└── builder-prompt.txt     # Condensed builder prompt
```

## Installation

1. **Clone or copy** to your OpenCode configuration directory:
   ```bash
   # Global config
   cp -r rice-opencode ~/.config/opencode/
   
   # Or project-local
   cp rice-opencode/opencode.json ./
   ```

2. **Install dependencies:**
   ```bash
   bun install
   # or
   npm install
   ```

3. **Create `.env` with API keys:**
   ```bash
   GITHUB_PAT=your_github_pat
   BRAVE_API_KEY=your_brave_key
   CONTEXT7_API_KEY=your_context7_key
   ```

4. **Install LaTeX** (for document generation):
   ```bash
   # Ubuntu/Debian
   sudo apt install texlive-full
   
   # macOS
   brew install --cask mactex
   ```

## Usage

### Using Agents

Agents are invoked automatically by OpenCode based on task context, or you can reference them explicitly:

```
@explore find all configuration files in this project
@docs-first-coder implement a React hook following current React docs
@code-checker review the auth module
@document-writer create an IEEE paper from paper.md
```

### Document Generation

Available tools when working with documents:

- `docs_convert` — Convert between formats (markdown, PDF, docx, etc.)
- `docs_create` — Create documents using presets
- `docs_create_ieee_paper` — IEEE conference/journal papers
- `docs_create_styled_pdf` — Professional styled PDFs
- `docs_templates_list` — List installed templates
- `docs_templates_install` — Install templates and CSL styles
- `docs_presets_list` / `docs_presets_show` — Manage document presets

**Presets:**
- `school-report` — SIT/UofG reports (`--logo sit|uofg|both`)
- `ieee-conference` — IEEE two-column conference papers
- `ieee-journal` — IEEE journal format
- `eisvogel` — General professional documents

## Configuration Notes

- `opencode.json` uses `{env:VAR}` syntax for secrets — safe to commit
- Agent prompts in `agents/` are referenced via `{file:path}` syntax
- Actual API keys should be in `.env` (gitignored)

## Requirements

- [OpenCode](https://opencode.ai) AI CLI
- Node.js / Bun runtime
- LaTeX installation (for document generation)
- API keys for enabled MCP servers

## License

Personal configuration — use as reference for your own setup.
