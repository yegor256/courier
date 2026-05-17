---
name: submit-a-pull-request
description: |
  Use this skill to submit the commits sitting on the
  current local branch as a single new pull request
  against a specific GitHub repository — push the
  branch, open the PR with a clear title and a short
  body that explains what changed and why, and post
  one follow-up comment pinging the repository owner.
  One branch per run, one pull request per run, one
  ping per run — then stop.
---

Operate on the GitHub repository named in the user's
  prompt as the target, or on the `origin` remote of
  the current working directory when the user names no
  explicit target; refuse to run when neither is
  available.

Refuse to run when the current branch is the
  repository's default branch (`main` or `master`) or
  when it has no commits ahead of the default branch —
  this skill submits work that already exists, and
  never invents commits.

Refuse to run when the working tree has uncommitted
  changes — staged, unstaged, or untracked — because a
  pull request must reflect a clean, committed state
  and not a half-finished edit on disk.

Do not modify a single source file, do not amend
  existing commits, do not rebase, and do not squash
  the branch; the only writes this skill performs are
  the `git push`, the new pull request, and its
  follow-up comment on GitHub.

Do not run the build, do not execute the test suite,
  do not start any linter, and do not invoke any
  static analysis tool — this skill ships the branch
  as it stands and trusts the author to have verified
  it.

Identify the default branch with
  `gh repo view <owner>/<repo> --json defaultBranchRef --jq .defaultBranchRef.name`
  and use that name as the base of the pull request,
  not a hard-coded `main` or `master`.

Confirm the current branch is up to date with the
  remote default branch (for example with
  `git fetch origin && git log --oneline origin/<default>..HEAD`)
  so the diff in the pull request reflects the
  author's intended change and not an accidental
  merge backlog.

List every open pull request in the repository (for
  example with
  `gh pr list --repo <owner>/<repo> --state open --limit 200 --json number,title,headRefName,author`)
  and discard the run when one already targets the
  same head branch — a second pull request from the
  same branch is a duplicate.

Push the current branch to `origin` with
  `git push -u origin <branch>` before opening the
  pull request, because `gh pr create` refuses to
  open a pull request from a branch the remote does
  not yet know about.

Open the pull request with
  `gh pr create --repo <owner>/<repo> --base <default> --head <branch> --title ... --body ...`
  using a short, declarative title that names the
  change in the imperative mood — for example
  `Drop trailing newline guard in parser` — and not
  a vague phrase like `Fixes` or `Update`.

Derive the title and the body from the commit
  messages on the branch (for example via
  `git log --reverse --pretty=format:%s%n%n%b origin/<default>..HEAD`)
  and from the diff itself, not from the branch name
  alone, because the branch name rarely tells the
  reviewer what the change does.

Write the body as a few short paragraphs of plain
  prose: one paragraph naming what the change does,
  one paragraph explaining why it is needed, and one
  paragraph naming any follow-up the reviewer should
  know about.

Keep the body compact — a handful of sentences, not
  a wall of text — because maintainers read short
  pull requests and skim long ones.

Talk like a human in the pull request body and the
  follow-up comment: use your own words, write in
  plain conversational phrasing, and drop the stock
  AI cadence, boilerplate openings, and buzzword
  strings.

Do not add AI markers to the pull request or the
  comment: no mention of Claude, ChatGPT, an LLM, or
  any model name; no `Generated with ...` footer, no
  `Co-Authored-By` AI trailer, no robot emoji, no
  disclosure that the text was written by an
  assistant.

Reference the related issue in the body with a
  closing keyword (for example `Closes #123`) only
  when the user named that issue explicitly or when
  a commit message on the branch already names it —
  never invent an issue number to look thorough.

Do not request reviewers, do not assign the pull
  request to anyone, do not attach labels, and do not
  set a milestone; leave those triage decisions to
  the maintainer.

Do not mark the pull request as a draft unless the
  user asked for a draft, because a ready pull
  request signals the work is up for review and a
  draft signals it is not.

Identify the repository owner as the `owner` of the
  slug when it is a user account, or as the most
  active recent committer to the default branch when
  the owner is an organization (for example via
  `gh api repos/<owner>/<repo>/contributors` combined
  with `gh api repos/<owner>/<repo>/commits?since=...`).

After the pull request is created, capture the new
  pull request number from the `gh pr create` output
  and use it for the follow-up comment in the next
  step.

Post one follow-up comment on the new pull request
  (for example with
  `gh pr comment <number> --repo <owner>/<repo> --body ...`)
  that `@`-mentions the owner, asks them to take a
  look when they have a moment, and offers to
  clarify if anything in the change is unclear.

Keep the follow-up comment to one or two sentences
  of plain prose — no headings, no bullet lists, no
  emojis, no AI-disclosure boilerplate — because a
  ping is a ping, not a second description.

Do not ping more than one account in the follow-up
  comment, do not @-mention the whole organization,
  and do not request a deadline or a priority label.

Stop after the follow-up comment is posted: do not
  open a second pull request, do not push another
  branch, and do not start a follow-up change —
  re-run this skill from the top for the next
  branch.
