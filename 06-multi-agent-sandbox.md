# Multi-Agent Routing

## Key Concepts

### Why multi-agent

- Isolation: different personas, permissions, workspaces (e.g. family vs work).
- Per-agent: workspace, sessions, auth profiles, sandbox, tool policy.

See: [Multi-Agent Routing](https://docs.openclaw.ai/concepts/multi-agent)

### agents.list + bindings

- **agents.list[]:** id, default, name, workspace, agentDir, model, identity, groupChat, sandbox, tools, etc.
- **bindings[]:** route inbound messages to agentId by `match.channel`, `match.accountId`, `match.peer`, `match.guildId`/`match.teamId`. Deterministic match order in docs.

See: [Multi-agent routing (config)](https://docs.openclaw.ai/gateway/configuration#multi-agent-routing-agents-list--bindings)

### Per-agent access profiles

- Full access (sandbox off), read-only tools + workspace, or messaging-only (no filesystem). Examples in config docs.

See: [Per-agent access profiles](https://docs.openclaw.ai/gateway/configuration#per-agent-access-profiles-multi-agent)

### Sandboxing

- Optional Docker-based isolation for tool execution; Gateway stays on host.
- **Modes:** `off` | `non-main` | `all`.
- **Scope:** `session` | `agent` | `shared` (containers).
- **workspaceAccess:** `none` | `ro` | `rw` (sandbox workspace vs agent workspace).
- Default image: `openclaw-sandbox:bookworm-slim`; build with `scripts/sandbox-setup.sh`.

See: [Sandboxing](https://docs.openclaw.ai/gateway/sandboxing)

### Tool policy

- `tools.allow` / `tools.deny`; per-agent `agents.list[].tools`; sandbox tool policy (`tools.sandbox.tools`). Deny wins.
- Elevated exec runs on host and bypasses sandbox.

See: [Sandbox vs Tool Policy vs Elevated](https://docs.openclaw.ai/gateway/sandbox-vs-tool-policy-vs-elevated)

### Docker hardening

- Network isolation (default none); resource limits; optional custom image / setupCommand.

See: [Sandboxing](https://docs.openclaw.ai/gateway/sandboxing) (images + setup)

## Doc References

- [Multi-Agent Routing](https://docs.openclaw.ai/concepts/multi-agent)
- [Configuration: multi-agent](https://docs.openclaw.ai/gateway/configuration#multi-agent-routing-agents-list--bindings)
- [Sandboxing](https://docs.openclaw.ai/gateway/sandboxing)
- [Sandbox vs Tool Policy vs Elevated](https://docs.openclaw.ai/gateway/sandbox-vs-tool-policy-vs-elevated)
- [Multi-Agent Sandbox & Tools](https://docs.openclaw.ai/multi-agent-sandbox-tools)