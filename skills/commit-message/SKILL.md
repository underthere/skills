---
name: commit-message
description: Draft a commit message from the staged diff, matching the repo's existing style. Use when the user asks for a commit message, or asks to commit staged work.
---

Draft a commit message for the currently staged changes. Draft only: show the message to the user, and don't run `git commit` unless they asked you to commit.

## Steps

1. Run `git diff --cached --stat` and `git diff --cached` to see what is staged. If nothing is staged, say so and stop; don't stage files yourself.
2. Run `git log --oneline -15` to learn this repo's message style (language, tense, prefix conventions). The repo's own history wins over any generic convention.
3. If the history shows no clear convention, fall back to Conventional Commits — see [CONVENTIONS.md](CONVENTIONS.md).
4. Draft the message:
   - Subject line: what the change does and why it matters, ≤ 72 chars.
   - Body (only when the diff needs explaining): the why, not a restatement of the diff.
   - One logical change per commit. If the staged diff mixes unrelated changes, say so and suggest a split instead of papering over it with "misc changes".
5. Show the draft. If the user asked to commit, commit with it.

## What makes a bad message

- Subject describes the files touched, not the behavior changed ("update utils.ts").
- Body narrates the diff line by line.
- Vague verbs: "fix stuff", "improve", "clean up" with no object.
