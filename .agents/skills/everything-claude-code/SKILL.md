```markdown
# everything-claude-code Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill documents the core development patterns, coding conventions, and agentic workflows used in the `everything-claude-code` (ECC) repository. The project is written in JavaScript (no framework detected) and implements modular, agent-driven automation and installable skills. This guide covers how to contribute new skills, commands, install targets, agent definitions, and more, following the repository's conventions and workflows.

## Coding Conventions

ECC follows consistent JavaScript coding and repository organization conventions:

### File Naming

- Use **camelCase** for JavaScript files and modules.
  - Example: `myModule.js`, `installTarget.js`

### Import Style

- Use **relative imports** for internal modules.
  ```js
  // Good
  const utils = require('./utils');
  import { doThing } from '../lib/doThing.js';
  ```

### Export Style

- Both **CommonJS** and **ES module** exports are used, depending on context.
  ```js
  // CommonJS
  module.exports = function doSomething() { ... };

  // ES Module
  export function doSomethingElse() { ... }
  ```

### Commit Messages

- Prefix with `fix:`, `feat:`, `docs:`, or `chore:`
- Keep messages concise (average ~56 characters)
  ```
  feat: add support for new install target
  fix: resolve agent prompt parsing bug
  ```

## Workflows

### Add or Update a Skill

**Trigger:** When introducing or updating a skill for agentic workflows  
**Command:** `/add-skill`

1. Create or update a `SKILL.md` file under `skills/{skill-name}/` or `.agents/skills/{skill-name}/`.
2. Optionally update `AGENTS.md`, `README.md`, and localized docs (e.g., `README.zh-CN.md`).
3. Update `manifests/install-modules.json` and/or `install-components.json` if the skill is installable.
4. Optionally add or update related agent markdown files.
5. Optionally update tests or scripts if the skill introduces new hooks or behaviors.

**Example:**
```shell
mkdir -p skills/myNewSkill
touch skills/myNewSkill/SKILL.md
# Edit SKILL.md with documentation
```

---

### Add or Update a Command Workflow

**Trigger:** When adding or updating a repeatable workflow command  
**Command:** `/add-command`

1. Create or update a markdown file in `commands/` (e.g., `prp-*.md`, `gan-*.md`, `santa-loop.md`).
2. Document workflow phases, usage, and outputs in the file.
3. Optionally update related skills or agent definitions.
4. Optionally add shell scripts or orchestrators if automation is needed.
5. Optionally update `AGENTS.md` or `README.md` to reference the new command.

**Example:**
```shell
touch commands/prp-myworkflow.md
# Document the workflow steps in markdown
```

---

### Add or Update an Install Target

**Trigger:** When supporting a new IDE/platform or updating install logic  
**Command:** `/add-install-target`

1. Add or update install scripts (`install.sh`, `install.js`, `uninstall.sh`, `uninstall.js`) in a new or existing directory (e.g., `.codebuddy/`).
2. Update `manifests/install-modules.json` and `schemas/ecc-install-config.schema.json`.
3. Update `scripts/lib/install-manifests.js` and `scripts/lib/install-targets/{target}.js`.
4. Add or update tests for install targets.
5. Optionally update `README.md` or `AGENTS.md`.

**Example:**
```shell
mkdir -p .codebuddy
touch .codebuddy/install.sh
# Implement install logic
```

---

### Update Hooks and Hook Tests

**Trigger:** When refactoring, fixing, or extending system hooks  
**Command:** `/update-hook`

1. Edit `hooks/hooks.json` to change configuration or add/remove hooks.
2. Edit or add `scripts/hooks/*.js` to implement hook logic.
3. Edit or add `tests/hooks/*.test.js` to cover new or changed behaviors.
4. Optionally update related scripts or documentation.

**Example:**
```json
// hooks/hooks.json
{
  "pre-commit": ["format", "typecheck"]
}
```

---

### Dependency Bump via Dependabot

**Trigger:** When updating dependencies for security or features  
**Command:** `/bump-dependency`

1. Update dependency version in `package.json`, `yarn.lock`, or workflow YAML files.
2. Commit with a standardized message (often by dependabot).
3. Optionally update related documentation or changelogs.

**Example:**
```json
// package.json
"dependencies": {
  "some-lib": "^2.0.0"
}
```

---

### Add or Update Agent Definition

**Trigger:** When adding or modifying agent definitions/prompts  
**Command:** `/add-agent`

1. Add or update agent markdown files (`agents/*.md`).
2. Add or update prompt files (`.opencode/prompts/agents/*.txt`).
3. Update `.opencode/opencode.json` to register new agents.
4. Update `AGENTS.md` to document new agents.
5. Optionally update related skills or orchestrators.

**Example:**
```shell
touch agents/myAgent.md
touch .opencode/prompts/agents/myAgent.txt
```

## Testing Patterns

- Test files follow the pattern `*.test.js`.
- Testing framework is **unknown** (not detected), but test files are placed alongside code or in `tests/` directories.
- Example test file:
  ```js
  // tests/hooks/formatHook.test.js
  const formatHook = require('../../scripts/hooks/formatHook');
  test('should format code correctly', () => {
    // test implementation
  });
  ```

## Commands

| Command            | Purpose                                                        |
|--------------------|----------------------------------------------------------------|
| /add-skill         | Add or update a skill and its documentation                    |
| /add-command       | Add or update a workflow command                               |
| /add-install-target| Add or update an install target (IDE/platform/environment)     |
| /update-hook       | Refactor, fix, or extend system hooks and their tests          |
| /bump-dependency   | Update dependency versions in package or workflow files         |
| /add-agent         | Add or update agent definitions and prompts                    |
```
