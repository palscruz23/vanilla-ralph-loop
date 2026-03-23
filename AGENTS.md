# AGENTS.md

This document defines the rules, architecture guidance, and workflow for AI agents working in this repository template.

Agents must keep changes inside this repository only.

---

# 1. Project Overview

This repository is a template repo for iterative product work driven by:

- a human-readable task brief in `TASKS.md`
- a machine-readable `prd.json`
- repeatable execution through `ralph once` and `ralph loop`

The goal is to keep the codebase easy to understand, easy to extend, and safe for repeated automated iterations.

Agents must prioritize readability, correctness, maintainability, and incremental delivery.

---

# 2. Technology Stack

Use the technology stack already present in the project.

Rules:
- prefer existing frameworks and libraries
- do not introduce new major dependencies unless necessary
- keep tooling choices consistent with the current repo

If a new dependency is required:
- explain why it is needed
- prefer widely used and actively maintained options
- keep the addition small and justified

---

# 3. Architecture Rules

Follow the architecture already established in the repo.

General rules:
- keep UI concerns in UI-focused modules
- keep business logic out of presentation components
- keep persistence and integration logic behind clear abstractions
- avoid coupling unrelated layers directly

Preferred flow:

UI -> state/controller layer -> domain/business logic -> data/integration layer

If the repository does not yet have a clear structure, create one that is simple, conventional, and easy to extend.

---

# 4. Folder Structure

Follow the existing structure when adding files.

If no clear structure exists, prefer grouping by responsibility, for example:

```text
src/
  components/
  pages/
  features/
  lib/
  styles/
  tests/
```

Rules:
- UI logic stays near UI modules
- business logic stays in feature or domain modules
- persistence/integration logic stays in data-oriented modules
- tests should live in the project's existing test locations

---

# 5. UI Development Guidelines

When modifying UI:

- keep components focused and composable
- prefer stateless components when practical
- pass state and handlers explicitly
- support loading, empty, error, and content states where relevant
- reuse existing design patterns before inventing new ones

If the project includes previews, examples, demos, or playground pages, add or update them when helpful.

---

# 6. State Management

Preferred pattern:

UI -> state/controller layer -> business logic -> data layer

Rules:
- avoid scattering state across unrelated components
- keep derived state predictable and easy to trace
- centralize side effects and data writes in the appropriate layer

---

# 7. Persistence and Integrations

Rules:
- isolate persistence and external service access behind clear interfaces or modules
- do not let UI components talk directly to storage or remote services unless the repo already uses that pattern intentionally
- keep data models explicit and easy to understand

If you add a new integration:
- document the contract
- keep secrets out of source control
- use environment-based configuration where applicable

---

# 8. Code Quality Rules

Agents must:

- prefer simple implementations
- avoid unnecessary abstraction
- keep functions and modules reasonably small
- use meaningful names
- avoid duplicate logic
- preserve or improve readability

Make focused changes. Do not rewrite large sections of the codebase without a clear reason.

---

# 9. Testing Requirements

Business logic should be testable.

Agents should add or update tests for:

- business logic
- data-layer behavior
- utility functions
- integration points when practical

Pure presentational code does not always require tests unless behavior is non-trivial.

---

# 10. Build Rules

Before finishing a task, agents must ensure:

- the relevant build command succeeds when feasible
- the relevant test command succeeds when feasible
- no known compile or type errors were introduced

Agents must not change core toolchain or platform versions unless required and explained.

---

# 11. Ralph Workflow Rules

This repo is designed for iterative execution.

Agents should understand:

- `TASKS.md` is the human-readable plan
- `prd.json` is the machine-readable feature list
- `ralph_once.sh` executes one feature
- `ralph_loop.sh` executes multiple features until completion or stop conditions

When creating or updating `prd.json`:

- each task should represent one focused feature
- tasks should be small enough for one iteration when practical
- `priority` determines execution order
- `implemented` is for agent-completed work
- `accepted` is reserved for human review

---

# 12. Security Rules

Never hardcode:

- API keys
- secrets
- tokens
- credentials

Sensitive data must come from:

- environment variables
- secure local configuration
- secret managers, if the project already uses them

---

# 13. Allowed Tasks

Agents may:

- implement features
- refactor code
- add tests
- improve architecture
- fix bugs
- improve docs and workflow files

Agents must NOT:

- rewrite large sections without reason
- delete functionality without confirmation
- introduce breaking architecture changes without explanation
- modify files outside this repository

---

# 14. Output Format

When completing work, agents should include:

1. Files changed
2. Summary of changes
3. Reasoning
4. Possible improvements

Example:

Files Changed
- src/components/TaskList.tsx
- src/lib/storage.ts

Summary
Added local task persistence and task list rendering.

Follow-up
Add edit-task support and better filter persistence.

---

# 15. General Philosophy

Prefer:

- clarity over cleverness
- maintainability over speed
- small incremental changes
- readable code
- explicit assumptions

The codebase should remain easy for humans and future agents to understand.
