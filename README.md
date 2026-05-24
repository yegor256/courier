# A Claude Code Plugin for Shipping Changes

[![License](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/yegor256/courier/blob/master/LICENSES/MIT.txt)

A small bundle of [Claude Code] skills that ship the work
  the user already has on disk — they do not author new
  changes; they record and forward what the user already
  produced.

The bundle ships these skills:

* [`commit-changes-to-git`](skills/commit-changes-to-git/SKILL.md)
  — inspect the working tree, stage only what the user
    named, compose one Conventional Commits message
    that names the change honestly, and stop without
    pushing.

* [`submit-a-pull-request`](skills/submit-a-pull-request/SKILL.md)
  — push the current branch to the remote, open a
    pull request with a short prose body that explains
    what changed and why, and ping the repository
    owner exactly once.

Suppose you work with [Claude Code].
You do not need to clone this repository — install the bundle as a
  plugin straight from GitHub.
Inside a Claude Code session, run:

```text
/plugin marketplace add yegor256/plugins
/plugin install courier@yegor256
```

The first command registers the [yegor256/plugins] marketplace,
  which lists every plugin maintained under the `yegor256` account;
  the second installs the `courier` plugin from it,
  which exposes the `commit-changes-to-git` and
  `submit-a-pull-request` skills to your sessions
  automatically.

To update later, run `/plugin marketplace update yegor256`;
  to remove, run `/plugin uninstall courier@yegor256`.

[yegor256/plugins]: https://github.com/yegor256/plugins
[Claude Code]: https://code.claude.com/docs/en/skills
