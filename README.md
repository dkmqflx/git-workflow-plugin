# git-workflow-plugin

[![Release](https://img.shields.io/badge/release-v0.2.0-blue)](https://github.com/dkmqflx/git-workflow-plugin/releases/tag/git-workflow--v0.2.0)

5 git workflow skills covering the full branch/worktree lifecycle: create a worktree or branch (from the current position or a named base branch), open a PR with an AI-drafted title/body, and clean up afterward. Base branch detection (`origin/HEAD`, falling back to `dev`/`main`/`master`) means these work regardless of what your repo calls its default branch.

## Supported Coding Agents

These skills can be installed via [`npx skills`](https://github.com/vercel-labs/skills) for any agent that supports the [Agent Skills specification](https://skills.sh), including Claude Code, Codex, Gemini CLI, Cursor, Windsurf, and more.

## Install

### Quick Install (any supported agent)

Using [`npx skills`](https://github.com/vercel-labs/skills):

```bash
# Current project
npx skills add dkmqflx/git-workflow-plugin --skill '*' --yes

# All projects (global)
npx skills add dkmqflx/git-workflow-plugin --skill '*' --yes --global
```

To target a specific agent:

```bash
npx skills add dkmqflx/git-workflow-plugin --agent codex --skill '*' --yes
npx skills add dkmqflx/git-workflow-plugin --agent gemini-cli --skill '*' --yes
```

### Claude Code Plugin

```
/plugin marketplace add dkmqflx/git-workflow-plugin
/plugin install git-workflow@git-workflow-plugin
```

Then run `/reload-plugins`. Skills are model-invoked automatically based on context (e.g. "start a new branch", "open a PR", "clean up this worktree") — you don't need to call them by name.

## Skills

| Skill | Description |
|-------|-------------|
| `worktree` | Create a new git worktree on a fresh branch before starting work |
| `start-branch` | Create a new branch — from current position by default, or from a named base branch (`dev`/`master`/`stage`/…) — and switch to it |
| `open-pr` | Push the current branch and open a pull request against the detected base branch, with an AI-drafted title/body confirmed by the user |
| `branch-done` | After opening a PR, delete the current feature branch and switch back to the detected base branch |
| `worktree-done` | Remove the current git worktree, switch the main checkout to the detected base branch, and delete the feature branch |

## Local development

```
claude --plugin-dir ./plugins/git-workflow
```

## License

MIT
