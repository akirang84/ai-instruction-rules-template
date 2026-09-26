# Git flow: branch → PR → squash merge

Every change, big or small, follows this flow. Never commit directly to `main` or `staging`, never push to those branches, and never force-push.

## 1. Start a branch from `main`

Fetch and create a topic branch from the latest `origin/main`:

```bash
git fetch origin
git switch -c <type>/<topic> origin/main
```

Examples: `feat/account-search`, `fix/login-redirect`, `docs/git-flow`. Use `git switch -C <branch> origin/main` only when intentionally restarting work on a same-named branch after confirming the old branch is no longer needed.

## 2. Change, verify, commit

- Check `git status` and inspect the diff before committing.
- Run the relevant lint, typecheck, and tests; report any checks that could not run.
- Commit in small, coherent pieces. Commit message is title only, under about 50 characters:
  `<type>(<scope>): <short description>`
- Allowed types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`.
- Do not add a commit body, notes, trailers, `Co-Authored-By`, or session lines.

## 3. Push the topic branch

```bash
git push -u origin <branch>
```

Push only the topic branch. Never force-push.

## 4. Open a pull request

- PR title only, in Conventional Commits format; the title drives the version bump.
- Empty PR description: no summary, test plan, notes, or generated-by footer. Use `gh pr create --body ""`.
- PR into `main` is the production path (API on Railway, web on Vercel).
- PR into `staging` is the staging path (API on Render). Confirm the intended target with the user if it is not clear from the task.

## 5. Squash merge

Always squash merge with an empty commit body:

```bash
gh pr merge --squash --body ""
```

The remote branch is deleted automatically after merge. Drop the local copy after updating `main`:

```bash
git switch main
git pull
git branch -D <branch>
```

Only delete the local topic branch after verifying the PR is merged and the local work is no longer needed.

## 6. After merge

Never push more commits to a merged branch or reuse its PR. Follow-up work starts from the latest `main` and gets a new PR. A same-named topic branch is allowed when created from the latest `origin/main`.

## Safety and permissions

- Do not stage unrelated user changes. Inspect status and diff first; ask before including changes you did not make or do not understand.
- Do not merge a PR, delete a branch containing unmerged work, or alter shared history unless explicitly requested by the user. The standard flow describes the required process; user authorization is still needed for externally visible merge actions.
- If required branch protections, remote state, or CI checks prevent the flow, report the blocker; never bypass protections.
