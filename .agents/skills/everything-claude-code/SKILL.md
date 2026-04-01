```markdown
# everything-claude-code Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches the core development patterns, coding conventions, and collaborative workflows used in the `everything-claude-code` repository. The codebase is written in JavaScript (no framework detected) and is organized for modularity, clarity, and extensibility. It emphasizes clear commit messages, structured documentation, and repeatable workflows for adding new skills, commands, integrations, and conventions.

## Coding Conventions

- **File Naming:**  
  Use `camelCase` for JavaScript files and directories.  
  _Example:_  
  ```
  scripts/lib/installTargets.js
  tests/hooks/formatCheck.test.js
  ```

- **Import Style:**  
  Use **relative imports** for modules within the codebase.  
  _Example:_  
  ```js
  const installTarget = require('../../lib/installTargets');
  ```

- **Export Style:**  
  Both CommonJS (`module.exports`) and ES module (`export`) styles are present.  
  _Example (CommonJS):_  
  ```js
  module.exports = function runHook() { ... };
  ```
  _Example (ES Module):_  
  ```js
  export function addSkill() { ... }
  ```

- **Commit Messages:**  
  Follow the **Conventional Commits** standard.  
  - Prefixes: `fix`, `feat`, `docs`, `chore`
  - _Example:_  
    ```
    feat: add install target for VSCode integration
    fix: correct agent configuration parsing bug
    ```

- **Documentation:**  
  Markdown files are used extensively for documenting skills, commands, agents, and conventions.

## Workflows

### Add New Skill or Agent
**Trigger:** When introducing a new skill or agent  
**Command:** `/add-skill`

1. Create a new `SKILL.md` file under `skills/<skill-name>/` or `.agents/skills/<agent-name>/`.
2. Optionally, add supporting agent definition files (e.g., `agents/<agent-name>.md` or `.codex/agents/<agent-name>.toml`).
3. Update or create related documentation/configuration files (e.g., `AGENTS.md`, `.opencode/opencode.json`).

_Example:_
```
skills/myNewSkill/SKILL.md
.agents/skills/myAgent/SKILL.md
agents/myAgent.md
.codex/agents/myAgent.toml
```

---

### Add or Update Command
**Trigger:** When introducing a new CLI command or workflow  
**Command:** `/add-command`

1. Create or update a markdown file in `commands/` (e.g., `commands/myCommand.md`).
2. Document usage, purpose, and output in YAML frontmatter and markdown sections.
3. Optionally update related documentation or test files.

_Example:_
```
commands/reviewFlow.md
```

---

### Add or Update Install Target
**Trigger:** When supporting a new IDE, platform, or agent integration  
**Command:** `/add-install-target`

1. Add new install scripts and documentation under a tool-specific directory (e.g., `.codebuddy/`, `.gemini/`).
2. Update `manifests/install-modules.json` and related schema files.
3. Update or add scripts in `scripts/lib/install-targets/<target>.js`.
4. Update or add tests for install targets.

_Example:_
```
.codebuddy/install.sh
manifests/install-modules.json
scripts/lib/install-targets/codebuddy.js
tests/lib/install-targets.test.js
```

---

### Dependency Bump for GitHub Actions
**Trigger:** When a new version of a GitHub Actions dependency is released  
**Command:** `/bump-action`

1. Update version numbers in `.github/workflows/*.yml` for specific actions.
2. Commit with a standardized message indicating the dependency and new version.

_Example:_
```
.github/workflows/ci.yml
# Update:
- uses: actions/checkout@v4
```

---

### Fix or Update Hook Scripts
**Trigger:** When improving or repairing CLI/editor hooks  
**Command:** `/fix-hook`

1. Modify `hooks/hooks.json` to adjust hook configuration or add/remove hooks.
2. Update or add scripts in `scripts/hooks/*.js` or `scripts/hooks/*.sh` for hook logic.
3. Update or add tests in `tests/hooks/*.test.js`.

_Example:_
```
hooks/hooks.json
scripts/hooks/formatCheck.js
tests/hooks/formatCheck.test.js
```

---

### Add or Update ECC Conventions Bundle
**Trigger:** When formalizing or updating project conventions and team/process documentation  
**Command:** `/add-convention`

1. Add or update markdown or JSON files under `.claude/commands/`, `.claude/rules/`, `.claude/team/`, `.claude/research/`, or `.claude/skills/`.
2. Document new or updated conventions, rules, or playbooks.

_Example:_
```
.claude/commands/codeReview.md
.claude/rules/commitMessage.md
.claude/team/members.json
.claude/skills/automation/SKILL.md
```

## Testing Patterns

- **Test Files:**  
  Test files follow the pattern `*.test.js` and are colocated with the code they test or in dedicated `tests/` directories.

- **Framework:**  
  No specific testing framework detected; use standard Node.js assertions or your preferred test runner.

_Example:_
```
tests/lib/install-targets.test.js
tests/hooks/formatCheck.test.js
```

## Commands

| Command           | Purpose                                                        |
|-------------------|----------------------------------------------------------------|
| /add-skill        | Add a new skill or agent, including documentation and config   |
| /add-command      | Add or update a CLI command or workflow                       |
| /add-install-target | Add or update an install target for integrations            |
| /bump-action      | Bump GitHub Actions workflow dependencies                     |
| /fix-hook         | Fix, refactor, or enhance hook scripts and configuration      |
| /add-convention   | Add or update ECC conventions, rules, or team configs         |
```
