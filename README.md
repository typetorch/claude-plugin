# TypeTorch Claude Code plugins

A [Claude Code](https://claude.com/claude-code) plugin marketplace for [TypeTorch](https://github.com/typetorch):
hot-swap deploys for roblox-ts Roblox games.

## Install

In Claude Code:

```text
/plugin marketplace add typetorch/claude-plugin
/plugin install typetorch@typetorch
```

From a shell instead:

```sh
claude plugin marketplace add typetorch/claude-plugin
claude plugin install typetorch@typetorch
```

From a local checkout: `claude plugin marketplace add ./claude-plugin`.

`typetorch init` (the CLI's guided setup) adds this marketplace by itself when it offers to start Claude Code at the
end.

## Plugins

| Plugin | Contents |
|---|---|
| `typetorch` | the **typetorch-migrate** skill: migrates a roblox-ts game to TypeTorch, or sets up a new one from the template |

Use it by asking "migrate this project to typetorch" (or "set up typetorch"), or run `/typetorch:typetorch-migrate`.
The skill does every local step (detect, plan, migrate, build, check the payload) and never touches API keys, signing
keys, Roblox or deploys. It ends with a numbered "What you need to do" list.

The skill is a copy of `agents/skills/typetorch-migrate/SKILL.md` in [typetorch/docs](https://github.com/typetorch/docs);
the full playbook is [agents/AGENTS.md](https://github.com/typetorch/docs/blob/main/agents/AGENTS.md) there. Keep both
copies in sync.

## Layout

```text
.claude-plugin/marketplace.json                     the marketplace (name: typetorch)
plugins/typetorch/.claude-plugin/plugin.json        the plugin manifest
plugins/typetorch/skills/typetorch-migrate/SKILL.md the skill
```

Check changes with `claude plugin validate .` and `claude plugin validate ./plugins/typetorch`.

## The TypeTorch MCP server

Not part of this plugin: the TypeTorch CLI is an MCP server itself (`typetorch mcp`, CLI 0.11+). It lets an agent run
the Studio loop (`typetorch serve`) and drive the attached Studio. Add it from the game repo:

```sh
claude mcp add typetorch -- bunx typetorch mcp
```

Tools: `serve_status`, `serve_start`, `serve_stop`, `serve_logs`, `studio_logs`, `studio_reconnect`, `studio_play`,
`studio_stop`.

**Planned:** more skills (framework, deploy, assets, the UI kit) and a Claude Code mod (deploy pane, status line,
`/tt` commands, toasts).

## License

MIT
