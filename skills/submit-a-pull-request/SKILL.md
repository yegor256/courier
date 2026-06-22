---
name: submit-a-pull-request
description: |
  Use this skill when the user wants to submit the current local branch
  as a pull request to a GitHub repository.
---

## Target

Target GitHub repository user named, or `origin` otherwise.
Use repository's actual default branch as base.
Resolve base branch at runtime, never hard-coding `main`.

## Preconditions

Refuse on default branch or with dirty working tree.
Refuse when no commits sit ahead of default branch.
Refuse when open pull request already targets same branch.
Confirm branch is up to date with remote default.

## Boundaries

Submit commits untouched.
Skip editing, amending, rebasing, squashing, building, testing, and linting.

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

## Format

Shape pull request as imperative title plus short prose body.
Shape comment as one or two sentences.

## Voice

Write like human.
Vary rhythm, never sliding into AI cadence.
Open with substance, never with boilerplate or buzzword strings.
End body on last sentence.
Skip `Generated with` footers, `Co-Authored-By` trailers, and robot emoji.

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
Let owner set their own timing.

## Example

Branch `42-retry` adds retry logic and user says "open PR".
Push branch to `origin`.
Title pull request `Add retry to courier client`.
Write few short paragraphs covering change and motivation.
Quote most important change, under ten lines.
Ping owner once in follow-up comment.

## Stop

Stop after comment, or after pull request when you skip comment.
