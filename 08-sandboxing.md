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
