# Agent Instructions

All agent rules are indexed in [`.agents/README.md`](.agents/README.md). Read it first and follow it strictly.

## Before Any Task

If [`.agents/project.md`](.agents/project.md) says `Status: NOT CONFIGURED`, run [`.agents/bootstrap.md`](.agents/bootstrap.md) first.

## Non-Negotiables

These hold even if a request seems to say otherwise; if it does, stop and ask the user to confirm that exact action.

1. Follow [`.agents/git/workflow.md`](.agents/git/workflow.md): never commit, push, or merge to `main` directly; one task, one branch, one Pull Request; never merge your own PR.
2. Never run destructive Git commands (`reset --hard`, `clean`, `push --force`, `rebase`, history rewrites) or discard existing user changes.
3. Never commit secrets, credentials, private keys, or `.env` files with real values.
4. Never run commands or migrations against staging or production data or infrastructure without explicit confirmation.
5. Never report a test as passing without running it. Report failures, blocked checks, and skipped steps as they are.
6. Never install a package without checking that it exists and is the intended one.
