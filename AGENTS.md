# Project notes for agents

<!--
Copy this file to AGENTS.md in a new repository, then replace the placeholders
and remove guidance that does not apply to that project's languages, tools, or
workflow.

If you're an agent, ask the user if you should fill in the missing pieces.
Do not guess at missing project details. If the user does not provide them,
leave the placeholders clearly marked.

When setting up this template, ask the user whether they want this README
replaced with project-specific information. Do not replace it without their
approval.

When adapting this template, you may update its agent instruction files for
the new project. In other contexts, do not modify agent instruction files
unless explicitly asked.
-->

## Project overview

<!-- Describe the product, primary languages/frameworks, users, and docs URL. -->

`<PROJECT_NAME>` is `<SHORT_DESCRIPTION>`. It is built with
`<LANGUAGES_AND_FRAMEWORKS>`. Project documentation: `<DOCUMENTATION_URL>`.

## Agent rules

- `CLAUDE.md` is a symlink to `AGENTS.md`, so both tools share the same
  guidance. Keep the symlink while the guidance is shared. If the project
  needs different tool-specific guidance, replace the symlink with a separate
  file and document the distinction.
- Remove placeholders that do not apply. For project details you cannot
  determine reliably, ask the user rather than guessing; if they are
  unavailable, leave the placeholders clearly marked.
- Never push changes unless explicitly told to.
- Do not commit to `main`. If the current branch is `main`, ask the user before
  changing files whether to create a branch or make the changes without
  committing.
- After changing files, run the project's formatter using its configured
  settings. Do not override project formatting configuration or invoke a
  formatter directly on individual files unless project guidance says to.
- Use conventional commits with the types used by this project. Use `!` and a
  `BREAKING CHANGE:` footer for breaking API or behavior changes.
- End commit messages with a co-author trailer appropriate to the agent and
  product. For example:
  `Co-Authored-By: <AGENT_NAME> <AGENT_EMAIL>`.
- Inform the user about commits and other Git changes, including commit
  messages.
- Commit changes after each step unless the user says not to or a project
  no-commit marker such as `.NOCOMMIT` exists in the repository root.
  - Changes affecting compilation or tests may only be committed after the
    relevant build, lint, and test checks pass.
  - Documentation, CI, editor, and deployment configuration changes may not
    require code checks; follow the project's validation requirements.
  - Check the current branch before every commit.
- Commit formatting-only changes separately when formatting reformats code
  unrelated to the functional changes.
- Add user-visible changes to the project's `Unreleased` changelog section
  using its established format, creating that section if needed.

## Repository structure

<!-- Record key source, tests, configuration, docs, and generated-code paths. -->

- `<SOURCE_DIRECTORY>/`: application and library source.
- `<TEST_DIRECTORY>/`: active tests; note any test directories not run by the
  normal project commands.
- `<CONFIG_DIRECTORY>/`: default configuration.
- `<DOCUMENTATION_DIRECTORY>/`: user and developer documentation.

Keep directly related documentation in sync with API, configuration, and
behavior changes.

## Architecture and constraints

<!-- Summarize important design facts and invariants that prevent regressions. -->

- `<IMPORTANT_SUBSYSTEMS_AND_ENTRY_POINTS>`
- `<PLATFORM_OR_FEATURE_CONSTRAINTS>`
- `<SECURITY_OR_CONCURRENCY_INVARIANTS>`
- `<KNOWN_LIMITATIONS_AND_UNSUPPORTED_BEHAVIOR>`

Avoid bypassing established abstractions or weakening these invariants without
explicitly discussing the consequences.

## Commands

<!-- Replace these placeholders with the smallest useful project commands. -->

```sh
<FORMAT_COMMAND>
<BUILD_COMMAND>
<LINT_COMMAND>
<TEST_COMMAND>
```

Document feature-specific, platform-specific, and integration checks as
needed. State any required working directory, environment variables, services,
or generated prerequisites.

## Conventions

- Write comments for *why*, not *what*: invariants, non-obvious constraints, workarounds (with the reason or a link),
  and units/timebases where the type doesn't say. Never restate what the code does.
- Before committing, review every comment in your diff (`git diff`): delete those that restate the code or describe
  the change itself (e.g. "now uses X instead of Y"; that belongs in the commit message), and shorten the rest to one line where possible.
- Comment only code that needs clarification; keep comments short.
- Follow the repository's formatting, lint, error-handling, logging, and
  dependency-management conventions.
- Prefer existing helpers and patterns; keep changes focused and surface
  failures explicitly.
- Preserve existing line endings when editing files that use non-default line
  endings.
- Do not add tests in locations the project's normal test commands do not
  discover.

## Code reviews

For reviews of commits, branches, diffs, or specific files, report every
finding as an entry in a list with this shape:

- **Location:** `file:line` (use a range such as `file:120-146` when the
  finding spans several lines)
- **Category:** one of `Blocking`, `FYI`, or `Nit` (use another category, such
  as `Question`, only when none of those fit)
- **Comment:** the concrete issue or risk and, when claiming a defect, its
  failure scenario rather than only an abstract concern

Order findings by severity, with `Blocking` first. Use `Blocking` for defects,
unbounded resource use, or policy violations that must change before merge;
use `FYI` for design consequences and risks worth a conscious decision; use
`Nit` for style and cleanliness. Verify findings against the code and run the
relevant lint and test commands before reporting them. Say when a finding is a
possibility rather than a confirmed defect.
