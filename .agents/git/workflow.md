## Git Workflow

The repository follows a strict **feature-branch + Pull Request** workflow.
Agent will NEVER update this rule, must follow.

### 1. Protected `main`

* `main` is the only integration branch.
* NEVER commit directly to `main`.
* NEVER push directly to `main`.
* NEVER merge directly into `main`.
* NEVER use another branch as an integration target unless explicitly instructed.
* All changes MUST enter `main` through a Pull Request.

The required flow is:

`main <- Pull Request <- task branch`

Never use:

`main <- direct commit`

`main <- direct push`

`feature-a <- feature-b <- main`

### 2. One Task = One New Branch

Every feature, bug fix, refactor, improvement, or code modification MUST be performed on a new branch.

Before modifying code:

1. Check the current branch.
2. Check the working tree.
3. Preserve and understand any pre-existing changes.
4. Create a new branch from the latest appropriate `main`.

Branch naming:

* `feature/<description>` — new functionality
* `fix/<description>` — bug fix
* `refactor/<description>` — refactoring
* `chore/<description>` — maintenance
* `docs/<description>` — documentation

Use short, descriptive, kebab-case names.

### 3. Never Work Directly on `main`

If the agent starts on `main`:

* Do NOT modify files first.
* Create the task branch before making any code changes.

If the agent starts on another branch:

* Determine whether that branch belongs to the current task.
* Do not reuse an unrelated branch.
* Create a new task branch when necessary.

### 4. Protect Existing User Changes

The working tree may contain changes that were made before the current task.

The agent MUST:

* Preserve all pre-existing changes.
* Never overwrite, discard, reset, or revert them.
* Never include unrelated changes in the current task's commit.
* Never assume uncommitted changes belong to the current task.

NEVER run destructive commands such as:

* `git reset --hard`
* `git clean -fd`
* `git restore <file>`
* `git checkout -- <file>`
* `git rebase`
* `git push --force`

unless explicitly instructed by the user.

If the existing Git state makes the requested workflow unsafe or ambiguous, stop and ask for clarification.

### 5. Branch Isolation

Each task branch should contain only changes required for that task.

Do NOT:

* Mix unrelated features or fixes.
* Perform opportunistic refactoring.
* Rename unrelated files or symbols.
* Reformat unrelated code.
* Modify unrelated configuration.
* Commit pre-existing user changes.

If unrelated changes are already present, leave them untouched.

### 6. Commit Rules

Create exactly one commit per task, containing only changes belonging to that task.

Before committing:

1. Run `git status`.
2. Review the diff.
3. Verify that only intended files are changed.
4. Stage only the required files.
5. Verify the staged diff.
6. Create a clear commit message.

Do NOT blindly use:

`git add .`

or:

`git add -A`

when unrelated changes may exist.

Never commit:

* Secrets
* API keys
* Credentials
* Private keys
* `.env` files containing secrets
* Other sensitive information

Do not amend existing commits unless explicitly instructed.

### 7. Keep Branches Based on `main`

Task branches should be created from `main`.

Do not create a task branch from another task branch.

Do not merge one task branch into another.

Do not create long-lived integration branches.

If the task requires changes from another unfinished branch, stop and ask for explicit instructions rather than creating an implicit branch dependency.

### 8. Validation Before PR

Before creating a Pull Request:

* Run the relevant tests.
* Run linting and formatting checks when applicable.
* Run build/type-check validation when applicable.
* Review the final Git diff.
* Verify that no unrelated files or changes are included.
* Verify the branch contains only the intended task changes.

If validation fails, do not hide or ignore the failure. Report it clearly.

### 9. Pull Request Is Mandatory

Every task intended to be integrated into the repository MUST be submitted through a Pull Request.

The agent should:

1. Commit the completed task.
2. Push the task branch to the remote.
3. Create a Pull Request targeting `main`.
4. Provide a concise PR title.
5. Provide a useful PR description containing:

   * What changed
   * Why it changed
   * Important implementation details
   * Tests and validation performed
   * Known limitations or remaining issues

The PR target MUST be:

`main`

Do not create PRs targeting another task branch or integration branch unless explicitly instructed.

### 10. Never Auto-Merge

Creating a Pull Request does NOT authorize merging it.

The agent MUST NOT:

* Merge its own PR.
* Approve its own PR.
* Bypass required reviews.
* Bypass branch protection.
* Force-push to bypass review or CI.
* Automatically merge after creating the PR.

The PR must remain pending for the normal review/merge process unless the user explicitly instructs the agent to perform a permitted merge.

### 11. Git History

Protect repository history.

Do not:

* Rewrite shared branch history.
* Rebase shared branches.
* Force-push.
* Amend commits that may already have been pushed.
* Delete or rewrite commits belonging to other work.

Any history-rewriting operation requires explicit user instruction.

### 12. Standard Agent Workflow

For every code task, follow this sequence:

1. `git status`
2. `git branch --show-current`
3. Inspect and preserve existing changes.
4. Update local `main` when appropriate.
5. Create a new task branch from `main`.
6. Implement the task.
7. Run relevant validation.
8. Review `git diff`.
9. Stage only task-related changes.
10. Commit.
11. Push the task branch.
12. Create a PR targeting `main`.
13. Report the PR and validation results.
14. Stop and wait for manual review/merge process.
15. After PR is merged, delete the task branch locally and remotely (if applicable).

### 13. Final Rule

When in doubt, prefer **preserving existing work and stopping for clarification** over performing a potentially destructive Git operation.

The repository's integration model is:

`main`
`  ↑`
`Pull Request`
`  ↑`
`feature/* | fix/* | refactor/* | chore/* | docs/*`

`main` is the single integration point.
All task work happens on isolated branches.
All integration happens through Pull Requests.
Never bypass this workflow unless explicitly instructed.
