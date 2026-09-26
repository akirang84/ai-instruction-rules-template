# Claude Code project instruction template

Copy `CLAUDE.md` and the `.claude/` directory to the root of a new project. Claude Code uses the root instruction file as the entry point; it links to focused instruction files by topic.

## Contents

- `CLAUDE.md`: onboarding behavior, defaults, safeguards, and instruction map.
- `.claude/*.instruction.md`: scoped rules for architecture, backend, frontend, database, security, testing, deployment, and Git flow.

## First project setup

At the first session, inspect the existing repository or interview the user for material unknowns. Confirm the ORM, database, state management choices, deployment targets, and product-specific architecture before substantial scaffolding. Once agreed, write the decisions and actual project commands into the README or existing project documentation.

Adapt the template to the actual app. Remove rules for unused components and add the project’s real package scripts, directory layout, API conventions, CI commands, environment names, and release process. Keep the root `CLAUDE.md` short and put details in the linked files.

## Reference inspiration

The structure follows the progressive-disclosure pattern recommended by Claude Code’s documentation (short root instructions linking to focused project context), with examples and ideas reviewed from public Claude Code/NestJS template repositories:

- [Claude Code documentation: CLAUDE.md](https://docs.anthropic.com/en/docs/claude-code/memory)
- [NestJS boilerplate architecture example](https://github.com/oNo500/nestjs-boilerplate/blob/master/docs/architecture.md)
- [Claude Code project template](https://github.com/tomcwxyz/claude-code-template)
