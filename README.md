# TZH Claude Code Plugin

<div align="center">

**TZH Claude Code Plugin: Doc-Driven Multi-Agent Toolkit**

[![GitHub - KhaosTian/tzh-plugin](https://img.shields.io/badge/GitHub-KhaosTian%2Ftzh--plugin-blue?logo=github)](https://github.com/KhaosTian/tzh-plugin)



[English](README.md) | [简体中文](README.zh-CN.md)

</div>

---

## Installation

### Step 1: Install Plugin

```bash
# Add TZH plugin marketplace
/plugin marketplace add https://github.com/KhaosTian/tzh-plugin

# Install tzh plugin
/plugin install tzh@tzh-plugin
```

### Step 2: Configure System Prompt

Copy the entire contents of `CLAUDE.example.md` from this repository into your user-level `~/.claude/CLAUDE.md` file.  
This enables:

- The TZH command router (e.g. `/what`, `/do`, `/mission`, `/campaign`)
- The multi-agent system (finder, ruler, planner, coder, inspector, tracker, mapper)
- The documentation-first `/llmdoc` workflow

Done. Now you can use the plugin in Claude Code normally.

### Update Plugin

```bash
/plugin marketplace update https://github.com/KhaosTian/tzh-plugin
```

## About

TZH Claude Code Plugin is a documentation-driven, multi-agent toolkit designed by **KhaosTian** for internal and personal projects.  
It turns Claude Code into a disciplined engineering assistant that:

- Follows `/llmdoc` as the “Constitution” of your codebase
- Separates investigation, planning, execution, review, and documentation into dedicated agents
- Keeps documentation in sync with real code changes

---

## Core Features

### 🤖 Multi-Agent System

- `finder` – Retrieval agent: finds relevant files, existing utils, and implicit rules.
- `ruler` – Standards agent: locates “Constitution” docs and external specs.
- `planner` – Strategy agent: analyzes complexity and writes `strategy-*.md`.
- `coder` – Execution agent: implements code strictly following Strategy and Constitution.
- `inspector` – Quality gate: audits code/doc for safety and standard compliance.
- `tracker` – Documentation agent: syncs `/llmdoc` with code reality.
- `mapper` – Map maker: builds and maintains the `/llmdoc` structure.

### 📝 Documentation-Driven Development

- `/initDoc` – Bootstraps a lean but complete `/llmdoc` system for the project.
- `/updateDoc` – Syncs documentation with recent code changes using git diffs and strategies.
- `/memo` – Appends “Lessons Learned” to `/llmdoc/reference/lessons-learned.md`.
- `doc-standard.example.md` – Example of the LLM-friendly documentation standard. Copy it to `llmdoc/guides/doc-standard.md` and customize.

### 🔧 Development Workflow

- `/what` – Strategic entrypoint. Analyzes your request, offers routes (fix / enhance / cleanup), then dispatches `/do`, `/mission`, or `/campaign`.
- `/do` – Direct action mode for small, explicit changes with automatic inspector + doc sync.
- `/mission` – Commander mode for complex features, refactors, or math-heavy tasks.
- `/campaign` – Swarm mode for batch tasks across multiple files or features.
- `/commit` – Smart commit gateway that enforces safety checks and Conventional Commit style.
- `/reviewPR` – Virtual Tech Lead review for GitHub PRs (via `gh pr` commands).
- `/audit` – System doctor that scans for performance issues, debug code, and architectural drift.

---

## Recommended Workflow

### 1. Initialize a New Project

```bash
# First-time setup: establish the /llmdoc documentation system
/initDoc
```

### 2. Daily Development Flow

```bash
# Get clear, doc-driven programming guidance
/what "I need to implement user authentication"

# For complex refactors or architecture changes
/mission "Refactor rendering pipeline for new design"

# For small, explicit edits
/do "Rename component LoginButton to SignInButton and update references"

# Generate a safe, conventional commit message
/commit
```

### 3. Documentation Maintenance

```bash
# Sync docs after code changes
/updateDoc

# Record lessons learned to avoid repeating mistakes
/memo "Avoid heavy synchronous work in React server components"
```

### 4. Code Quality Assurance

```bash
# Run a health check on a module
/audit "auth module"

# Review a Pull Request before merging
/reviewPR 123
```

---

<div align="center">

Made with ❤️ by **KhaosTian**

</div>

