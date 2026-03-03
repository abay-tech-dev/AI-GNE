# CLAUDE.md — AI-GNE Repository Guide

This file provides context and conventions for AI assistants (Claude Code and similar tools) working in this repository.

---

## Repository Overview

**Repository:** `abay-tech-dev/AI-GNE`
**Remote:** `http://local_proxy@127.0.0.1:24246/git/abay-tech-dev/AI-GNE`

> This repository is in its initial state. As source code is added, update this file to reflect the actual project structure, stack, and conventions.

---

## Git Workflow

### Branch Naming

- Feature branches: `feature/<short-description>`
- Bug fixes: `fix/<short-description>`
- Claude-generated branches: `claude/<task-slug>-<session-id>` (auto-assigned by Claude Code)

### Committing

Always sign commits (configured via `commit.gpgsign=true`). Commit messages should follow this format:

```
<type>: <short imperative summary>

<optional body explaining why, not what>
```

Types: `feat`, `fix`, `refactor`, `test`, `docs`, `chore`, `ci`

### Pushing

```bash
git push -u origin <branch-name>
```

Branch names must start with `claude/` for Claude Code sessions. Pushes to other branches require explicit user permission.

If a push fails due to a network error, retry up to 4 times with exponential backoff (2s, 4s, 8s, 16s).

### Pull Requests

Fetch specific branches rather than all refs:

```bash
git fetch origin <branch-name>
```

---

## Development Setup

> Fill in this section once the project stack is established.

### Prerequisites

- (List runtime versions, e.g. Python 3.11+, Node 20+)
- (List required CLI tools)

### Install Dependencies

```bash
# Example — replace with actual commands
pip install -r requirements.txt
# or
npm install
```

### Environment Variables

Copy `.env.example` to `.env` and fill in required values:

```bash
cp .env.example .env
```

---

## Project Structure

> Update this section as the codebase grows.

```
AI-GNE/
├── CLAUDE.md          # This file
├── README.md          # User-facing documentation
├── src/               # Main source code
├── tests/             # Test suite
└── docs/              # Additional documentation
```

---

## Running Tests

> Fill in once a test framework is configured.

```bash
# Example — replace with actual test commands
pytest
# or
npm test
```

All tests must pass before merging a PR. Do not bypass test failures — investigate and fix the root cause.

---

## Linting & Formatting

> Fill in once linting tools are configured.

```bash
# Example
ruff check .
ruff format .
# or
eslint . && prettier --check .
```

Run linters before committing. Do not use `--no-verify` to skip hooks.

---

## Key Conventions for AI Assistants

### Do

- Read files before modifying them
- Prefer editing existing files over creating new ones
- Keep changes minimal and focused on the task at hand
- Use dedicated tools (Read, Edit, Glob, Grep) instead of shell equivalents
- Mark todos complete immediately when done, one at a time
- Run tests after making code changes
- Confirm with the user before destructive or irreversible operations

### Do Not

- Push to branches other than the designated Claude branch without explicit permission
- Use `--no-verify`, `--force-push` to main/master, or `git reset --hard` without user approval
- Add features, refactor, or clean up code beyond what was explicitly requested
- Add comments, docstrings, or type annotations to code you didn't change
- Create helpers or abstractions for one-time use
- Design for hypothetical future requirements

### Security

- Never commit secrets, credentials, or `.env` files containing real values
- Validate input at system boundaries (user input, external APIs) — trust internal code
- Do not introduce SQL injection, XSS, command injection, or other OWASP Top 10 vulnerabilities

---

## Updating This File

Update `CLAUDE.md` whenever:
- The project stack or major dependencies change
- New tooling (linting, testing, CI/CD) is added
- Directory structure changes significantly
- New conventions are established by the team
