# RStack Decisions

## Bootstrap Decisions

These decisions were made in the first fork pass.

## Kept

- top-level skill-per-directory structure
- markdown prompt files as the source of truth
- a small, high-signal core skill set

## Removed

- telemetry prompts
- analytics logging
- remote sync assumptions
- upgrade-check wrappers
- author and YC-specific branding in the shared runtime
- repo-vendored legacy source trees

## Changed

- shared generated preamble replaced with a small RStack runtime block
- `office-hours` closing section rewritten to remove YC application and promotional copy
- skill files now default to host-native fallback behavior when custom helpers are missing
- repo scope reduced to the lean supported set rather than every imported skill

## Lean Supported Set

These skills are the default public surface and the default `./setup` install set:

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

## Known Rough Edges

- several browser-oriented skills still assume a custom `browse` binary path
- some skills still refer to optional local state under `.rstack/`
- some shipped skills still reference companion workflows that are no longer in the lean set
- host-specific installation instructions have not been rewritten yet

## Intent

RStack should stay:

- anonymous
- markdown-first
- easy to copy between projects
- opinionated about quality, but not tied to one person, one company, or one telemetry pipeline
