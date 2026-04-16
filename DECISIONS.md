# RStack Decisions

## Bootstrap Decisions

These decisions were made in the first fork pass.

## Kept

- top-level skill-per-directory structure
- markdown prompt files as the source of truth
- the broad specialist lineup from the local `gstack` source

## Removed

- telemetry prompts
- analytics logging
- remote sync assumptions
- upgrade-check wrappers
- author and YC-specific branding in the shared runtime
- the `gstack-upgrade` skill

## Changed

- `open-gstack-browser` renamed to `open-browser`
- shared generated preamble replaced with a small RStack runtime block
- `office-hours` closing section rewritten to remove YC application and promotional copy
- skill files now default to host-native fallback behavior when custom helpers are missing

## Known Rough Edges

- several browser-oriented skills still assume a custom `browse` binary path
- some skills still refer to optional local state under `.rstack/`
- `learn`, `checkpoint`, and `health` may be too stateful for the final lean version
- host-specific installation instructions have not been rewritten yet

## Intent

RStack should stay:

- anonymous
- markdown-first
- easy to copy between projects
- opinionated about quality, but not tied to one person, one company, or one telemetry pipeline
