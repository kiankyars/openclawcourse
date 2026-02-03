# Security

- **Prompt injection:** Malicious users can craft messages that trick the agent into running unintended commands. Smaller models are more susceptible. Mitigate by enabling sandbox mode and restricting tool access for channels that accept messages from untrusted or unknown senders.

- **Sandbox:** Docker-based isolation runs tool execution in a container, protecting your host system. Set `sandbox.mode` to `non-main` (sandbox everyone except your main session) or `all` (sandbox everything). Use `sandbox.scope` to control container lifecycle (`session`, `agent`, or `shared`) and `workspaceAccess` to limit file access (`none`, `ro`, `rw`).

- **Tool policy:** Use `tools.deny` to block dangerous tools (like `exec`, `process`, `browser`) for agents handling untrusted input. Elevated mode bypasses the sandbox and runs on the host—never grant it to unknown senders.

- **Browser control:** The browser tool can navigate to any URL and interact with pages, making it high-risk for automation attacks. Restrict browser access by channel or sender allowlist. When possible, use the sandboxed browser to limit exposure.
