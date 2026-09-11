
---
name: linear-cli
description: Use the locally installed `linear` CLI for all Linear operations, including working with issues, comments, statuses, parent issues, projects, and related resources. Always use this CLI rather than calling the Linear API directly.
---

# Linear

For all Linear operations:

- Always use the locally installed `linear` CLI.
- Never call the Linear API directly.
- Use `linear --help` and subcommand `--help` as the authoritative documentation for available operations and arguments.
- Before invoking `linear`, if its API key is not already available, run:
  `. "$HOME/Documents/skills/linear/linear.env"`
- Never print, inspect, log, or otherwise expose the Linear API key.

## Comment Rules

- Keep comments explanatory and concise.
- When linking files, follow the rules in `$HOME/Documents/skills/linking.md`.

## Reporting Rules

When starting work on an issue:

- Move the issue to `In Progress`.
- Ensure every ancestor issue is also `In Progress`.
- Add a comment describing the agreed scope, goals, and relevant implementation decisions.

While working:

- Add comments when useful to record important implementation decisions, blockers, limitations, or significant changes in direction.
- Also add comments whenever explicitly requested.

When work is complete:

- Move the issue to `Ready for Review`.
- Add a comment describing:
  - what was implemented;
  - important implementation decisions;
  - known blockers;
  - known limitations;
  - anything the reviewer should pay particular attention to.

Every issue state change must have an explanatory comment associated with it.

Do not automatically move parent issues to `Ready for Review` solely because a child issue is ready for review unless the parent's own work is complete.
