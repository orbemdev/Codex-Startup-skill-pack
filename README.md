# Codex Startup Skill Pack

A skills-only Codex plugin that bundles a practical development workflow in one installable package.

## Included skills

- `using-superpowers`
- `brainstorming`
- `writing-plans`
- `executing-plans`
- `dispatching-parallel-agents`
- `subagent-driven-development`
- `test-driven-development`
- `systematic-debugging`
- `verification-before-completion`
- `requesting-code-review`
- `receiving-code-review`
- `using-git-worktrees`
- `finishing-a-development-branch`
- `writing-skills`
- `frontend-design`
- `grill-me`

## Install

Register the GitHub repository as a Codex marketplace, then install the plugin:

```bash
codex plugin marketplace add orbemdev/Codex-Startup-skill-pack --ref main
codex plugin add codex-startup-skill-pack@codex-startup-skill-pack
```

Or clone the repository and register the local checkout:

```bash
git clone https://github.com/orbemdev/Codex-Startup-skill-pack.git
codex plugin marketplace add ./Codex-Startup-skill-pack
codex plugin add codex-startup-skill-pack@codex-startup-skill-pack
```

Restart Codex after installation so the skill catalog reloads. If the repository is private, the recipient must have GitHub access and authenticate Git before installing it.

The multi-agent workflow skills require this setting in `~/.codex/config.toml`:

```toml
[features]
multi_agent = true
```

Do not remove existing configuration when adding it.

## Sources and licenses

The Superpowers skills are redistributed from [obra/superpowers](https://github.com/obra/superpowers) under the MIT License. `frontend-design` is redistributed from [anthropics/skills](https://github.com/anthropics/skills) under the Apache License 2.0. See [`THIRD_PARTY_NOTICES.md`](THIRD_PARTY_NOTICES.md) and the bundled license files.

`grill-me` and this plugin's packaging are original to this repository.
