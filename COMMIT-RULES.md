# Commit Rules

Read this before starting any task that includes staging or committing. The commit rules in `AGENTS.md` also apply.

## Format and scope

- Follow, in order: an explicitly requested format, documented repository rules within their scope, then the repository's recent commit-message style if it is clear and consistent. If none applies, use Conventional Commits.
- Split unrelated changes into independently revertible commits.

## Before editing and staging

- Inspect the initial status and relevant diffs before editing.
- Before staging or committing, recheck the branch, HEAD state, staged content, conflicts, and ongoing Git operations.
- Do not continue, abort, skip, or commit an ongoing Git operation, resolve existing conflicts, or commit on a detached HEAD unless the task explicitly covers that exact state.
- Stage only explicit, validated paths or known hunks that belong to the commit.
- If the requested changes cannot be safely separated from user changes, stop and report instead of altering or including them.
- Immediately before each commit, review the complete staged diff and file list for unintended changes and apparent secrets. Commit only that reviewed content.

## Commit message

Keep messages concise. Explain why the change exists, not only what the diff contains. Name symbols, interfaces, invariants, limits, or hardware constraints that help future debugging, preferring concrete names searchable in Git history.

For a non-trivial change, one whose purpose, failure mechanism, trade-off, or verification is not clear from the subject and diff alone, record the applicable context in the repository's message format. Labels are optional.

- **Problem:** observable failure, limitation, or requirement
- **Cause:** verified technical cause or failure mechanism
- **Decision:** chosen solution and important trade-off, when relevant
- **Verification:** checks actually performed and their outcomes; relevant checks not run and why; environment limitations that affect confidence

Do not invent causes, alternatives, or verification results. Do not claim tests passed unless they ran and passed. Leave out implementation diaries and private reasoning. If verification ran in a dirty working tree, do not imply it validated only the committed diff.

## After committing

- If a hook fails or changes files, the index, or the message, re-inspect status and diffs. Do not retry blindly.
- After each commit, verify its identifier, message, and diff, then re-inspect the index and working tree.
- Report unexpected differences without pushing or rewriting. Preserve and report any unrelated changes.
