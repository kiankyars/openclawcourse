# Pedagogy & Instructor Notes

Guidance for teaching the 3-hour OpenClaw course: pacing, pitfalls, and how to keep it rigorous and planned.

---

## Design Principles

1. **Start with the “why”.** Most learners won’t see why they’d want this over using Claude/ChatGPT in the browser. Lead with: pocket access via WhatsApp/Telegram, tool execution on their machine, multi-agent orchestration. Use [Showcase](https://docs.openclaw.ai/start/showcase) for concrete examples (14+ agents, Roborock, Home Assistant).

2. **Hands-on from early.** Don’t do 20 minutes of slides before touching the terminal. Get `openclaw onboard` running in Module 2 quickly; explain concepts while the wizard runs.

3. **Config > code.** OpenClaw is config-heavy. Spend real time on JSON structure; use [Configuration Examples](https://docs.openclaw.ai/gateway/configuration-examples) and minimal config. Don’t rush through `openclaw.json`.

4. **Don’t skip sandboxing.** It’s the differentiator from “just run Claude Code.” Learners must understand mode (off / non-main / all), scope (session / agent / shared), and workspaceAccess. Security model (sandbox + tool policy + prompt injection by model tier) is non-trivial.

5. **Concrete > abstract.** Prefer live config edits and one working skill over long theory. Steal from Showcase for demos.

---

## Pacing

- **Modules 1–2:** Set the mental model and get one channel working. If pairing fails, have a backup (e.g. WebChat or a pre-paired demo).
- **Modules 3–4:** Deepen config and workspace; this is where learners often get lost. Walk one full `openclaw.json` and one workspace folder.
- **Modules 5–6:** Skills and multi-agent/sandbox are the “power user” blocks. One minimal skill + one second agent with binding is enough.
- **Modules 7–8:** Automation and security can be mostly explain + link; capstone is “build the thing” with doctor/status at the end.

---

## Common Pitfalls

- **Wrong CLI name:** It’s `openclaw` (one word). The wizard is `openclaw onboard` (not “onboard” only). Dashboard is port **18789** (not 18793; 18793 is canvas host).
- **Config validation:** Unknown keys or invalid values → Gateway won’t start. Always run `openclaw doctor` after editing config; point learners to [Strict config validation](https://docs.openclaw.ai/gateway/configuration#strict-config-validation).
- **Workspace vs state:** Workspace = agent context and files. Config and sessions live under `~/.openclaw/` and must not be committed to the workspace repo.
- **Skill eligibility:** Skills are filtered at load time (bins, env, config). If a skill doesn’t appear, check metadata.openclaw.requires and sandbox (binaries must exist in container if sandboxed).
- **Sandbox without Docker:** If Docker isn’t available, teach the config and concepts; skip live sandbox run. Mention `scripts/sandbox-setup.sh` for later.

---

## Checklist Before Class

- [ ] Node ≥22 and OpenClaw installed; wizard already run so demo is stable.
- [ ] At least one channel paired (WhatsApp or Telegram) and one successful message → reply.
- [ ] Backup copy of `openclaw.json` for safe edits.
- [ ] Optional: default sandbox image built (`scripts/sandbox-setup.sh`) if you’ll demo sandbox.

---

## After the Course

- Point to [Help](https://docs.openclaw.ai/help), [Troubleshooting](https://docs.openclaw.ai/help/troubleshooting), [FAQ](https://docs.openclaw.ai/help/faq).
- Suggest: Tailscale for remote access, Nix/Docker for deploy, [Formal Verification (Security Models)](https://docs.openclaw.ai/security/formal-verification) for deeper security.
- Invite learners to share projects in [#showcase on Discord](https://discord.gg/clawd) or [@openclaw on X](https://x.com/openclaw).
