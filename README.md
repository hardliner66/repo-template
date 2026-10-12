# Repository Template

A starting point for new repositories. Copy the files and adapt the project
documentation, agent guidance, and configuration to the project you are
creating.

## Getting started

1. Copy this template into your new repository.
2. Review `AGENTS.md` and `CLAUDE.md`. In this template, `CLAUDE.md` is a
   symlink to `AGENTS.md`, so both tools share the same guidance. Keep the
   symlink unless the project needs distinct tool-specific instructions; if
   so, replace it with a separate file and document the difference.
3. Replace applicable placeholders with verified project information. Remove
   placeholders that do not apply; ask the user about missing details rather
   than guessing. If the user is unavailable, leave those placeholders clearly
   marked.
4. Review the other included configuration files and keep only what applies
   to your project.
5. Ask before replacing this README with project-specific setup, usage, and
   development instructions.

## Instructions for agents

When setting up this template for a project, ask the user whether they want
you to replace this README with information about their project. Do not replace
its contents with project-specific documentation until the user agrees.

## Template contents

- `AGENTS.md` contains a starting point for project-specific agent guidance.
- `CHANGELOG.md` is a place to record notable project changes.
- `CLAUDE.md` links to `AGENTS.md` so Claude-compatible tools use the same
  agent guidance.
