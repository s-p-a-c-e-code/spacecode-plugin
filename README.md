# SpaceCode Plugin for Claude Code

Run tasks, code reviews, and CI in ephemeral cloud sandboxes — directly from Claude Code.

## Install

```
/plugin install github:s-p-a-c-e-code/spacecode-plugin
```

On first use, you'll be prompted to sign in with GitHub via OAuth. No API keys needed.

## What You Get

### MCP Tools (8 tools, auto-connected)

| Tool | Description |
|------|-------------|
| `remote_exec` | Run a task in an ephemeral cloud sandbox |
| `remote_exec_batch` | Run tasks across multiple repos in parallel |
| `remote_tasks` | List active/recent tasks |
| `remote_task_status` | Get task details |
| `remote_cancel` | Cancel a running task |
| `remote_wait_all` | Wait for tasks to complete |
| `agent_create` | Create a service account |
| `agent_list` | List agent accounts |

### Skills (4 slash commands)

| Command | Description |
|---------|-------------|
| `/cloud-exec` | Guided cloud task execution |
| `/cloud-review` | Remote code review |
| `/cloud-batch` | Parallel multi-repo tasks |
| `/cloud-status` | Task dashboard |

### Agents (4 autonomous agents)

| Agent | Triggers |
|-------|----------|
| `cloud-reviewer` | "review my code", "code review", pre-PR |
| `cloud-ci` | "run tests", "lint", "type-check" remotely |
| `multi-repo-runner` | "across repos", batch operations |
| `cloud-explorer` | "explore repo", "how does X work" for external repos |

### Hooks (4 safety/convenience hooks)

- **Destructive command guard** — blocks `rm -rf /`, `git push --force`, etc.
- **Auto-status** — reminds to check results after cloud task completion
- **Sandbox cleanup** — prompts to cancel orphaned tasks on session end
- **Repo detection** — auto-injects current repo context on each prompt

## How It Works

This plugin connects to the [SpaceCode](https://spacecode.app) MCP server at `mcp.spacecode.app`. Each task runs in an ephemeral Cloudflare container with:

- Git, GitHub CLI, Claude Code pre-installed
- Full repo clone with branch checkout
- Automatic cleanup on completion

Code changes are returned as git diffs but never auto-pushed.

## Auth

Authentication uses OAuth 2.1 with PKCE via GitHub. Claude Code handles the flow automatically — just sign in with GitHub when prompted.

## License

MIT
