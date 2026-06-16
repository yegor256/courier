---
name: commit-changes-to-git
description: |
  Use this skill when the user wants to commit changes
  in the working tree of the current Git repository.
---

## Scope

Operate on Git repository in current working directory.
Refuse to bundle unrelated changes into one commit.

## Boundaries

Do not edit files, reformat, lint, test, or build before committing.
Do not bypass hooks or signing unless user asked for it.
Do not amend, rebase, force-push, or push to any remote.

## Staging

Stage only paths user named, or everything when user said so.
Refuse to stage secrets.
Warn user about skipped secrets instead.

## Message

Respect Conventional Commits 1.0.0 standard.
Prepend ticket number to description with `#` when user named issue.
Derive message from diff and conversation.
Never use branch name as source.

## Review

List staged files for user before committing.
Show commit subject to user before committing.

## Authorship

Never add `Co-authored-by:` trailers, promotional lines, signatures, or emoji.
Never override author or committer identity.

## Stop

Stop after single commit lands.
