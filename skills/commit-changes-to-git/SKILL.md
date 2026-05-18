---
name: commit-changes-to-git
description: |
  Use this skill to commit changes that already sit in
  the working tree of the current Git repository, under
  the direct supervision of the user — inspect what is
  modified, stage only what the user named (or all
  modifications when the user said so), compose one
  Conventional Commits message that names the change
  honestly, and stop. One repository per run, one
  commit per run — then stop.
---

Operate on the Git repository in the current working
  directory; refuse to run when the directory is not a
  Git working tree or when no commits exist yet on the
  current branch and the user did not ask for an
  initial commit.

Trust the user — the changes in the working tree were
  made earlier on purpose and this skill only records
  them; do not edit source files, do not reformat code,
  do not run the linter, do not run the test suite, and
  do not start a build to "verify" the change before
  committing.

Run `git status` and `git diff` (and `git diff --staged`
  when something is already staged) before composing
  the message, so the subject and the body describe
  what is actually on disk and not what was discussed
  earlier in the conversation.

Show the user a one-line summary of the files about to
  be committed and the proposed commit subject before
  invoking `git commit`, so the user can redirect the
  scope or the wording with a single short reply.

Stage files explicitly with `git add <path>` for each
  path the user named, and never run `git add -A`,
  `git add .`, or `git commit -a` unless the user said
  in plain words to stage everything; those forms sweep
  in unrelated edits and leak secrets.

Refuse to stage files that look like secrets — `.env`,
  `*.pem`, `*.key`, `id_rsa`, `credentials.json`,
  `*.tfstate`, files inside `.ssh/`, or any file whose
  diff contains a high-entropy token — and warn the
  user instead of committing them silently.

Format the subject line as `<type>(<scope>): <description>`
  per the Conventional Commits 1.0.0 spec at
  https://www.conventionalcommits.org/en/v1.0.0/, where
  the scope in parentheses is optional and the
  colon-space separator is mandatory.

Pick the type from the standard set: `feat` for a new
  feature, `fix` for a bug fix, `docs`, `style`,
  `refactor`, `perf`, `test`, `build`, `ci`, `chore`,
  or `revert`; do not invent new types.

Prepend the related ticket number with a leading hash
  sign to the description (`fix(parser): #123 handle
  empty input`) whenever the user named an issue or a
  pull request in the conversation, so the subject
  links the change to its tracking ticket; omit the
  prefix when no ticket applies.

Append `!` after the type or scope (`feat!:` or
  `feat(api)!:`) and add a `BREAKING CHANGE:` footer
  when the commit introduces an incompatible change,
  so tooling can detect the break from the subject
  alone.

Write the description in the imperative mood,
  lowercase, with no trailing period, under 72
  characters (`fix(parser): handle empty input`, not
  `Fixed the parser.`).

Leave one blank line between the subject and the body,
  and another blank line between the body and any
  footer; the parser relies on these blank lines to
  split the message.

Keep the body to a few short sentences that explain
  the motivation and the visible effect, wrap lines at
  72 columns, and omit the body entirely when the
  subject already says everything — a one-line commit
  is a good commit.

Derive the message from the diff and from what the
  user said in the conversation, not from the branch
  name or from a guess about intent; when the diff and
  the conversation disagree, ask the user which one is
  right before committing.

Do not pad the message with restated diffs, file
  lists, or obvious summaries (`updated foo.js to add
  a function`); the diff already shows that — the
  message must add the reason.

Do not bundle unrelated changes into one commit; when
  the working tree mixes two unrelated edits, ask the
  user whether to split them into two commits or to
  stage only one of them now.

Add a `Closes #<number>` or `Fixes #<number>` footer
  only when the user named that exact issue and asked
  for the auto-close behaviour, and do not add a
  `Refs:` footer when the subject already carries the
  `#<number>` prefix because the reference is already
  visible.

Never add a `Co-authored-by:` trailer naming Claude,
  Claude Code, Anthropic, or any other coding agent;
  the commit is authored by the user running the agent
  and attribution to a tool is misleading.

Never add promotional trailers, signatures, emoji, or
  `Generated with ...` lines to the message; the
  commit log is a technical record, not a credit
  screen.

Never override the author or the committer on the
  command line with `--author`, `-c user.name=`,
  `-c user.email=`, `GIT_AUTHOR_NAME`, or
  `GIT_COMMITTER_EMAIL`; rely on the defaults
  configured in the repository or in the user's global
  Git config so the commit is attributed correctly.

Do not pass `--no-verify`, `--no-gpg-sign`, or any
  flag that bypasses hooks or signing unless the user
  has explicitly asked for it; a failing hook means
  the commit is not ready and the right move is to fix
  the underlying problem and stage the fix as part of
  this commit or as a follow-up.

Do not amend the previous commit, do not rebase, and
  do not force-push as part of this skill; when the
  previous commit was wrong, create a new commit on
  top and let the user decide whether to clean up the
  history.

Do not push the new commit to any remote; pushing is a
  separate, user-initiated step and the user may want
  to inspect, amend, or discard the commit before it
  leaves the machine.

Pass the message via a HEREDOC to `git commit -F -` or
  `git commit -m "$(cat <<'EOF' ... EOF)"` so blank
  lines, backticks, and quotes survive the shell
  intact.

After `git commit` succeeds, run `git log -1 --stat`
  and show the output to the user so the subject,
  body, footers, and file set are visible in one
  place; when anything looks wrong, propose a new
  commit on top rather than amending the one just
  created.

Stop after the single commit lands: do not open a
  pull request, do not push, do not start the next
  change — re-run this skill from the top when the
  user has more changes ready.
