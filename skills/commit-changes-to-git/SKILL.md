---
name: commit-changes-to-git
description: |
  Use this skill to commit changes
  in the working tree of the current Git repository.
---

Operate on the Git repository in the current working directory.
Do not edit files, reformat, lint, test, or build before committing.
Stage only the paths the user named, or everything when the user said so.
Refuse to stage secrets and warn the user instead.
Refuse to bundle unrelated changes into one commit.
Confirm the file list and the subject with the user before committing.
Respect the Conventional Commits 1.0.0 standard.
Prepend the ticket number to the description with a `#`.
Do this when the user named an issue.
Derive the message from the diff and the conversation.
Never use the branch name as the source.
Never add `Co-authored-by:` trailers, promotional lines, signatures, or emoji.
Never override the author or the committer identity.
Do not bypass hooks or signing unless the user asked for it.
Do not amend, rebase, force-push, or push to any remote.
Stop after the single commit lands.
