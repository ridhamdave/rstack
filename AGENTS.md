# RStack

RStack is a markdown-first skill pack. Each skill lives in `skills/<name>/SKILL.md`.

## How To Use This Repo

- When a request clearly matches a skill, open that skill's `SKILL.md` and follow it directly.
- Treat the skill file as executable workflow guidance, not as background reading.
- Prefer repo-local context first: files, git history, tests, docs, and running code.
- If a skill references helper tooling that does not exist in the current environment, use the closest host-native alternative and continue.
- Do not add telemetry, analytics, remote sync, or hidden auto-update behavior.
- Keep outputs concrete: name files, commands, risks, and next actions.

## Local State

- Use `.rstack/` for local artifacts that should persist across sessions.
- Use `.context/` for scratch notes shared across agents in this workspace.
- Do not write hidden data outside those locations unless the user explicitly asks.

## Supported Skills

These are the lean default skills RStack should prefer and install by default:

- `office-hours`
- `plan-ceo-review`
- `plan-eng-review`
- `design-consultation`
- `design-review`
- `ship`
- `qa`
- `investigate`
- `careful`
- `freeze`
- `guard`
- `unfreeze`
- `setup-deploy`

Other directories under `skills/` are extra workflows kept in-repo for reference,
but they are not the default public surface.
