# courier

[![License](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/yegor256/courier/blob/master/LICENSES/MIT.txt)

A single Claude Code skill that submits the commits on
  the current local branch as a new GitHub pull
  request — it does not author new commits; it ships
  the work that the user already has on the branch.

The bundle ships exactly one skill:

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
  which exposes the `submit-a-pull-request` skill to your sessions
  automatically.

To update later, run `/plugin marketplace update yegor256`;
  to remove, run `/plugin uninstall courier@yegor256`.

[yegor256/plugins]: https://github.com/yegor256/plugins

[Claude Code]: https://code.claude.com/docs/en/skills
