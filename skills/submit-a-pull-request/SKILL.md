---
name: submit-a-pull-request
description: |
  Use this skill to submit the current local branch
  as a pull request to a GitHub repository.
---

Target the GitHub repository the user named, or `origin` otherwise.
Refuse on the default branch or with a dirty working tree.
Refuse when no commits sit ahead of the default branch.
Do not modify files, amend, rebase, squash, build, test, or lint.
Use the repository's actual default branch as the base.
Never hard-code `main`.
Confirm the branch is up to date with the remote default.
Refuse when an open pull request already targets the same branch.
Push the branch before opening the pull request.
Use an imperative-mood title, not `Fixes` or `Update`.
Derive title and body from the commits and the diff, not the branch name.
Write the body as a few short paragraphs.
Cover what changes, why, and any follow-up.
Quote a snippet of the most important change, no longer than ten lines.
Trust code to convey the change better than prose.
Write like a human.
Avoid AI cadence, boilerplate openings, and buzzword strings.
Never add `Generated with` footers or `Co-Authored-By` AI trailers.
Never add robot emoji.
Use a closing keyword only when the user or a commit already cites the issue.
The owner is the slug owner, or the top recent committer for an organization.
Stop and ask the user when the owner cannot be determined.
Post one follow-up comment `@`-mentioning the owner and offering to clarify.
Skip the comment when the owner is the authenticated account.
Keep the comment to one or two sentences.
Ping one account and never request a deadline.
Stop after the comment, or after the pull request when the comment was skipped.
