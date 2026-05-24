---
name: submit-a-pull-request
description: |
  Use this skill to submit the current local branch
  as a pull request to a GitHub repository.
---

Target the GitHub repository the user named, or `origin` otherwise.
Refuse on the default branch, with no commits ahead of it, or with a dirty working tree.
Do not modify files, amend, rebase, squash, build, test, or lint.
Use the repository's actual default branch as the base, not a hard-coded `main`.
Confirm the branch is up to date with the remote default.
Refuse when an open pull request already targets the same branch.
Push the branch before opening the pull request.
Title in the imperative mood — not `Fixes` or `Update`.
Derive title and body from the commits and the diff, not the branch name.
Body: a few short paragraphs — what changes, why, and any follow-up.
Write like a human — no AI cadence, boilerplate openings, or buzzword strings.
Never add AI markers: no `Generated with` footer, no `Co-Authored-By` AI trailer, no robot emoji.
Use a closing keyword only when the user or a commit already cites the issue.
Owner: the slug owner, or the top recent committer for an organization.
Post one follow-up comment `@`-mentioning the owner and offering to clarify.
Skip the comment when the owner is the authenticated account.
Keep the comment to one or two sentences, ping one account, and never request a deadline.
Stop after the comment, or after the pull request when the comment was skipped.
