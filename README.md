# RStack

RStack is a markdown-first skill pack built to stay lean, anonymous, telemetry-free, and easy to reuse across projects without generator or update machinery.

This repo keeps the specialist workflow and skill structure while stripping out productized repo machinery:

- No telemetry
- No analytics sync
- No YC or Garry Tan branding
- No generated-skill pipeline
- No install/update machinery in the repo itself

## What Is Here

Each skill lives in `skills/<name>/SKILL.md`. RStack only ships the lean supported surface.

The imported skills were sanitized for RStack:

- shared telemetry and upgrade wrappers removed
- common runtime replaced with a small RStack runtime block
- `office-hours` stripped of YC application and founder-marketing sections

## Install

### Fastest: install with `npx skills`

Once this repo is public on GitHub, people can install directly without cloning:

```bash
npx skills add ridhamdave/rstack --list
npx skills add ridhamdave/rstack --skill qa --agent codex
npx skills add ridhamdave/rstack --skill office-hours -g --agent claude-code
```

This repo now uses the standard `skills/` layout so `npx skills` and `skills.sh`
can discover it cleanly.

### Local install with `./setup`

Clone once, then run a repo-owned setup script that installs the skill collection
into your host's skill directory.

1. Clone the repo wherever you keep shared agent skills:

```bash
git clone https://github.com/ridhamdave/rstack.git ~/rstack
```

2. Run the installer:

```bash
cd ~/rstack
./setup
```

This installs the shipped lean skill set into detected host skill directories
and names them `rstack-<skill>` to avoid collisions.

RStack's setup does not build binaries, generate host-specific skill variants,
or maintain telemetry/config state. It only installs the skills.

Lean supported set:

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

Examples:

```bash
./setup --host codex
./setup --host claude
./setup --host all
./setup --host codex --no-prefix
```

Targets:

- Codex: `~/.codex/skills/`
- Claude: `~/.claude/skills/`

If you use `--no-prefix`, skills install as plain names like `qa` and `ship`.
Otherwise they install as `rstack-qa`, `rstack-ship`, and so on.

## Run

Invoke the workflow by skill name, then follow that skill's instructions.

Examples:

```text
/rstack-office-hours
/rstack-plan-eng-review
/rstack-qa
/rstack-ship
/rstack-design-review
```

If you installed with `--no-prefix`, use the plain names instead:

```text
/office-hours
/plan-eng-review
/qa
/ship
/design-review
```

If your host does not support slash commands directly, open the relevant file and
use it as the operating prompt:

```text
~/rstack/skills/office-hours/SKILL.md
~/rstack/skills/qa/SKILL.md
~/rstack/skills/design-review/SKILL.md
```

## Listing On skills.sh

There is no separate manual packaging step in this repo.

For `skills.sh`, the important parts are:

- the repo is public
- each skill has valid YAML frontmatter with `name` and `description`
- skills live in a standard discovery path, now `skills/`
- people install the repo through `npx skills add ...`

`skills.sh` says the leaderboard is powered by anonymous telemetry from the
`skills` CLI, so installs through `npx skills` are what help a public repo show
up and rank there.

## Current Shape

This is intentionally markdown-first. Some skills still mention helper commands
or browser flows that may depend on optional local tooling. For now, treat those
as playbooks:

- if the helper exists, use it
- if it does not, substitute the closest host-native tool
- if neither exists, trim the workflow to what the environment can actually do

## Repo Conventions

- skill source of truth lives in `skills/<name>/SKILL.md`
- local artifacts should go under `.rstack/`
- collaboration scratch files can go under `.context/`
- this repo is the fork source, not a generated output

## Skill Set

RStack ships an intentionally small default surface:

- product thinking: `office-hours`, `plan-ceo-review`, `plan-eng-review`
- design: `design-consultation`, `design-review`
- execution: `qa`, `ship`, `investigate`
- safety/helpers: `careful`, `freeze`, `guard`, `unfreeze`, `setup-deploy`

## Reference

RStack was informed by and takes inspiration from GStack by Garry Tan.
