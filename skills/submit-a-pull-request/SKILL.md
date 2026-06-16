---
name: submit-a-pull-request
description: |
  Use this skill when the user wants to submit the current local branch
  as a pull request to a GitHub repository.
---

## Target

Target GitHub repository user named, or `origin` otherwise.
Use repository's actual default branch as base.
Never hard-code `main`.

## Preconditions

Refuse on default branch or with dirty working tree.
Refuse when no commits sit ahead of default branch.
Refuse when open pull request already targets same branch.
Confirm branch is up to date with remote default.

## Boundaries

Do not modify files, amend, rebase, squash, build, test, or lint.

## Branch

Push branch before opening pull request.

## Title

Use imperative-mood title, not `Fixes` or `Update`.
Derive title and body, never from branch name.

## Body

Write body as few short paragraphs.
Cover what changes, why, and any follow-up.
Quote snippet of most important change, no longer than ten lines.
Trust code to convey change better than prose.

## Voice

Write like human.
Avoid AI cadence, boilerplate openings, and buzzword strings.
Never add `Generated with` footers or `Co-Authored-By` AI trailers.
Never add robot emoji.

## Closing

Use closing keyword only when user or commit already cites issue.

## Owner

Read owner from repository slug.
For organization, use top recent committer as owner.
Stop when owner stays unknown.
Ask user to resolve it.

## Comment

Skip comment when owner is authenticated account.
Post one follow-up comment to owner otherwise.
Mention owner in that comment.
Offer to clarify in that comment.
Keep comment to one or two sentences.
Ping one account.
Never request deadline.

## Stop

Stop after comment, or after pull request when you skip comment.
