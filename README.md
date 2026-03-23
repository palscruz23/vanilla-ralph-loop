# Ralph Workflow

This repo uses two planning artifacts:

- `TASKS.md`: the human-readable project/task brief
- `prd.json`: the machine-readable task list consumed by `ralph_once.sh` and `ralph_loop.sh`

`prd.sample.json` in the repo is a starter example you can copy into `prd.json`.

## Generate `prd.json`

1. Start from the task brief in `TASKS.md`.
2. Use the local `prd` skill in [`skills/SKILL.md`](C:\Users\61422\Desktop\OMSCS\projects\ralph_vanilla\skills\SKILL.md).
3. Use that skill output to generate `prd.json` directly.
4. Keep one focused task per feature in `prd.json`.

Example with Codex:

```text
Read TASKS.md and use the local `prd` skill to generate `prd.json` directly.
Do not create a markdown PRD file.
Keep tasks small and ordered by priority.
Use `prd.sample.json` as the output shape.
```

If you are running Codex from this repo, a typical flow is:

```bash
codex
# then ask Codex:
# "Read TASKS.md and generate prd.json using the local prd skill and prd.sample.json as the schema."
```

Recommended JSON shape:

```json
{
  "project": "Focus Flow",
  "branchPrefix": "review/focus-flow",
  "description": "Simple web app for adding, completing, filtering, and deleting personal tasks.",
  "tasks": [
    {
      "id": "FE-001",
      "title": "Create web app structure",
      "description": "As a developer, I want a clean web app baseline so future features follow the same structure.",
      "acceptanceCriteria": [
        "Project contains folders for src, components, pages, styles, lib, and tests"
      ],
      "priority": 1,
      "implemented": false,
      "accepted": false,
      "notes": ""
    }
  ]
}
```

Rules:

- `branchPrefix` is used to create one branch per task.
- `priority` controls which task Ralph picks first.
- `implemented` is set by Ralph when a feature is done.
- `accepted` is reserved for human review.

## Use Ralph Once

`ralph once` runs a single implementation iteration for the highest-priority unfinished feature.

Linux/macOS or Git Bash:

```bash
cp prd.sample.json prd.json
bash ./ralph_once.sh
```

PowerShell:

```powershell
Copy-Item prd.sample.json prd.json
.\ralph_once.ps1
```

What it does:

- reads `prd.json`, `ralph.md`, and `progress.txt`
- creates or checks out the branch for the next feature
- asks Codex to implement exactly one feature
- updates `prd.json` and `progress.txt`
- pushes the branch and opens or reuses a PR

Prerequisites:

- `git`
- `node`
- `codex`
- `gh`
- Git remote `origin`
- Git Bash on Windows for the `.ps1` wrappers

## Use Ralph Loop

`ralph loop` repeats the one-feature workflow until all features are marked implemented or the loop hits its stop conditions.

Linux/macOS or Git Bash:

```bash
cp prd.sample.json prd.json
bash ./ralph_loop.sh
```

PowerShell:

```powershell
Copy-Item prd.sample.json prd.json
.\ralph_loop.ps1
```

Current loop limits from [`ralph_loop.sh`](C:\Users\61422\Desktop\OMSCS\projects\ralph_vanilla\ralph_loop.sh):

- maximum 20 iterations
- maximum 3 failed iterations before stopping

## Practical Flow

1. Write or update `TASKS.md`.
2. Use Codex with the local `prd` skill to generate `prd.json` using the sample format.
3. Run `ralph once` for a single feature, or `ralph loop` for repeated feature execution.
4. Review the PRs Ralph opens.
5. Mark features accepted during human review.
