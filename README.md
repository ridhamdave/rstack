# RStack

Inspired by and forked from GStack by Garry Tan, RStack keeps the specialist markdown workflow but makes it leaner, anonymous, telemetry-free, and easier to reuse across projects without generator or update machinery.

This repo keeps the specialist workflows and skill structure, but strips out the parts that made `gstack` feel productized around one author or one org:

- No telemetry
- No analytics sync
- No YC or Garry Tan branding
- No generated-skill pipeline
- No install/update machinery in the repo itself

## What Is Here

Each skill lives in `skills/<name>/SKILL.md`. The repo still contains the full imported catalog, but RStack now treats a smaller set as the default supported surface.

The copied skills were sanitized from the local `gstack` source:

- shared telemetry and upgrade wrappers removed
- common runtime replaced with a small RStack runtime block
- `open-gstack-browser` renamed to `open-browser`
- `office-hours` stripped of YC application and founder-marketing sections

## Install

### Fastest: install with `npx skills`

Once this repo is public on GitHub, people can install directly without cloning:

```bash
npx skills add ridhamdave/rstack --list
npx skills add ridhamdave/rstack --skill review --agent codex
npx skills add ridhamdave/rstack --skill office-hours -g --agent claude-code
```

Install all skills:

```bash
npx skills add ridhamdave/rstack --skill '*' --agent codex
```

This repo now uses the standard `skills/` layout so `npx skills` and `skills.sh`
can discover it cleanly.

### Local install with `./setup`

This is the path closest to how `gstack` handled installation: clone once, then
run a repo-owned setup script that installs the skill collection into your host's
skill directory.

1. Clone the repo wherever you keep shared agent skills:

```bash
git clone https://github.com/ridhamdave/rstack.git ~/rstack
```

2. Run the installer:

```bash
cd ~/rstack
./setup
```

By default this installs the lean supported set into detected host skill
directories and names them `rstack-<skill>` to avoid collisions.

Unlike `gstack`, RStack's setup does not build binaries, generate host-specific
skill variants, or maintain telemetry/config state. It only installs the skills.

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
./setup --all-skills
./setup --host codex --no-prefix
```

Targets:

- Codex: `~/.codex/skills/`
- Claude: `~/.claude/skills/`

If you use `--no-prefix`, skills install as plain names like `qa` and `ship`.
Otherwise they install as `rstack-qa`, `rstack-ship`, and so on.

Use `--all-skills` only if you want the full imported catalog, including sidecar
or legacy workflows that are not part of the lean default surface.

## Run

Invoke the workflow by skill name, then follow that skill's instructions.

Examples:

```text
/rstack-office-hours
/rstack-plan-eng-review
/rstack-review
/rstack-qa
/rstack-ship
```

If you installed with `--no-prefix`, use the plain names instead:

```text
/office-hours
/plan-eng-review
/review
/qa
/ship
```

If your host does not support slash commands directly, open the relevant file and
use it as the operating prompt:

```text
~/rstack/skills/office-hours/SKILL.md
~/rstack/skills/review/SKILL.md
~/rstack/skills/qa/SKILL.md
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

This is intentionally markdown-first. Some skills still mention helper commands or browser flows that originally depended on custom `gstack` binaries. For now, treat those as playbooks:

- if the helper exists, use it
- if it does not, substitute the closest host-native tool
- if neither exists, trim the workflow to what the environment can actually do

## Repo Conventions

- skill source of truth lives in `skills/<name>/SKILL.md`
- local artifacts should go under `.rstack/`
- collaboration scratch files can go under `.context/`
- this repo is the fork source, not a generated output

## Lean Default

RStack keeps the full imported skill catalog in-repo for reference, but the
default install surface is intentionally smaller:

- product thinking: `office-hours`, `plan-ceo-review`, `plan-eng-review`
- design: `design-consultation`, `design-review`
- execution: `qa`, `ship`, `investigate`
- safety/helpers: `careful`, `freeze`, `guard`, `unfreeze`, `setup-deploy`

Everything else is currently extra inventory, not part of the default public surface.
