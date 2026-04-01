---
name: add-new-install-target
description: Workflow command scaffold for add-new-install-target in everything-claude-code.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-new-install-target

Use this workflow when working on **add-new-install-target** in `everything-claude-code`.

## Goal

Adds support for a new install target (e.g., CodeBuddy, Gemini) to the system, including scripts, manifests, schemas, and tests.

## Common Files

- `manifests/install-modules.json`
- `schemas/ecc-install-config.schema.json`
- `schemas/install-modules.schema.json`
- `scripts/lib/install-manifests.js`
- `scripts/lib/install-targets/*.js`
- `tests/lib/install-targets.test.js`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create new install scripts (install.js, install.sh, uninstall.js, uninstall.sh) in a dedicated directory (e.g., .codebuddy/ or .gemini/).
- Add or update a README or documentation file for the new target.
- Update manifests/install-modules.json to register the new target.
- Update schemas/ecc-install-config.schema.json and schemas/install-modules.schema.json as needed.
- Update scripts/lib/install-manifests.js and scripts/lib/install-targets/<target>-project.js.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.