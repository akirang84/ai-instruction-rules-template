# New Project Bootstrap

Run this when `project.md` says `Status: NOT CONFIGURED`. The goal is a filled `project.md`, confirmed by the user, before any code is written.

## Rules

- Follow `git/workflow.md`: do the bootstrap on a `chore/configure-agent-rules` branch and submit it as a Pull Request.
- Edit only `project.md` (and delete unused files in `stacks/` if the user agrees). Never edit core rule files or stack files to fit the project; record deviations in `project.md` section 8.
- Inspect the repository first (README, package files, lockfiles, CI, Docker, existing code) and pre-fill what can be detected. Ask only what cannot be detected, and show detected values for confirmation.
- Ask in small batches (3–6 questions), grouped by topic, in the user's language. Offer a recommended default for each question; the user may accept defaults in bulk.
- Do not invent answers. Unknown values stay `TBD`.

## Question Batches

1. **Product**: purpose, MVP scope, actors and roles, domain (to choose domain expert perspectives), glossary terms.
2. **Platforms and stacks**: backend (default Node.js + TypeScript + NestJS), database (default PostgreSQL + version) and data-access tool (Prisma / TypeORM / other), web frontend (Angular / React Native Web / none), mobile (React Native + Expo / none), repository layout.
3. **Technical decisions**: Node LTS version, package manager, test runners, E2E tools, authentication approach, ID type, UI library, state approach, i18n library and locales, browser and device matrix.
4. **Environments**: hosting per environment, region and data residency, secret store, monitoring tools.
5. **Commands**: install, run, lint, type check, test, E2E, build, migrate, seed. For a new repository, propose them from the chosen stack.
6. **Non-functional and process**: load and growth, SLO, RPO/RTO, compliance, sensitive data, budget, ticket prefix, docs locations, reviewers.

## Blocking vs. Deferrable

- Must be answered before scaffolding or writing code: batch 2, Node version and package manager, authentication approach, and anything about personal or regulated data.
- May stay `TBD` and be asked when first needed: everything else. When a later task depends on a `TBD`, ask then and update `project.md` in that task's PR.

## Finish

1. Summarize the final configuration and the remaining `TBD` items, and get the user's confirmation.
2. Set `Status: CONFIGURED`.
3. Commit, push, and open the PR as `git/workflow.md` requires.

## Updating Later

When a decision changes, update `project.md` in the same PR as the change that depends on it. Changes to core or stack rules go to the template repository, not to the project copy.
