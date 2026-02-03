# Module 1: Intro & Architecture (~20 min)

**Learning objectives:** By the end of this module, learners can explain what OpenClaw is, why it exists, and how the Gateway fits into the network.

---

## Key Concepts

1. **What OpenClaw is**
   - Messaging gateway: WhatsApp (Baileys), Telegram (grammY), Discord (channels.discord.js), iMessage (imsg CLI) → AI coding agent (Pi).
   - “Send a message, get an agent response — from your pocket.”
   - Self-hosted; you own the gateway and config.

2. **Gateway model**
   - Single long-running process that **owns** all channel connections and the WebSocket control plane.
   - One Gateway per host; it is the only process that opens the WhatsApp Web session.
   - Clients: macOS app, CLI, web Control UI, automations → connect over WS (default `ws://127.0.0.1:18789`).

3. **Network topology (from docs)**
   - Channels → Gateway → Pi (RPC) + tools.
   - Canvas host: HTTP on `canvasHost.port` (default 18793) for `/__openclaw__/canvas/`.
   - Nodes (iOS/Android/macOS) connect as WS clients with `role: node`.

4. **Why this matters**
   - Mobile-first agentic UX (chat from phone).
   - Tool execution on your machine (not just chat in a browser).
   - Multi-channel, multi-agent routing from one gateway.

---

## Lesson Plan

| Segment | Duration | Activity |
|---------|----------|----------|
| Hook | 2 min | “Why not just use Claude/ChatGPT?” — pocket access, tools on your machine, multi-agent. |
| What is OpenClaw | 5 min | Definition; bridge channels ↔ Pi; self-hosted. |
| Gateway architecture | 8 min | Single process, WS control plane, loopback-first; walk topology diagram from docs. |
| Invariants | 3 min | One Gateway per host; handshake mandatory; no event replay. |
| Wrap | 2 min | Preview Module 2: we’ll install and run it. |

---

## Doc References

- [OpenClaw (home)](https://docs.openclaw.ai)
- [Gateway Architecture](https://docs.openclaw.ai/concepts/architecture)
- [Network model](https://docs.openclaw.ai) (Quick start section)

---

## Checklist (Instructor)

- [ ] Show topology diagram from docs (channels → Gateway → Pi).
- [ ] Emphasize: config lives in `~/.openclaw/openclaw.json`; Gateway is the single source of truth.
- [ ] No hands-on yet; keep under 20 min so Module 2 can start terminal early.
