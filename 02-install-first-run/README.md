# Module 2: Installation & First Run (~25 min)

**Learning objectives:** Learners install OpenClaw, run the onboarding wizard, pair at least one channel, open the Control UI, and send a message that receives an agent response.

---

## Prerequisites (Verify Before Class)

- Node ≥22 (`node -v`)
- Docker installed if you will demo sandboxing later
- Phone/account ready for WhatsApp or Telegram pairing

---

## Key Steps (Aligned to Docs)

1. **Install**
   - `npm install -g openclaw@latest` (or `pnpm add -g openclaw@latest`).
   - [Install](https://docs.openclaw.ai/install)

2. **Onboard + daemon**
   - `openclaw onboard --install-daemon`
   - Wizard: config path, workspace, service (launchd/systemd).
   - [Onboarding Wizard](https://docs.openclaw.ai/start/wizard)

3. **Pair a channel**
   - WhatsApp: `openclaw channels login` → QR in terminal; scan with phone.
   - Telegram: add `channels.telegram` with bot token; [Telegram](https://docs.openclaw.ai/channels/telegram).
   - [Pairing](https://docs.openclaw.ai/start/pairing)

4. **Control UI**
   - Local: http://127.0.0.1:18789/ (or http://localhost:18789/).
   - If it fails, start Gateway: `openclaw gateway`.
   - [Control UI](https://docs.openclaw.ai/web/control-ui)

5. **First message → agent reply**
   - Send a message from the paired channel (or WebChat); confirm agent responds.
   - Optional: `openclaw message send --target <peer> --message "Hello from OpenClaw"` (requires running Gateway).

---

## Lesson Plan

| Segment | Duration | Activity |
|---------|----------|----------|
| Install | 5 min | `npm install -g openclaw@latest`; verify `openclaw --version`. |
| Onboard | 8 min | `openclaw onboard --install-daemon`; walk wizard choices (config, workspace, daemon). |
| Pair channel | 7 min | WhatsApp QR or Telegram bot; ensure one channel works. |
| Control UI + first message | 5 min | Open dashboard; send message; see reply. |

---

## Doc References

- [Getting Started](https://docs.openclaw.ai/start/getting-started)
- [Onboarding Wizard](https://docs.openclaw.ai/start/wizard)
- [Pairing](https://docs.openclaw.ai/start/pairing)
- [Control UI](https://docs.openclaw.ai/web/control-ui)
- [Quick start](https://docs.openclaw.ai) (code blocks)

---

## Checklist (Instructor)

- [ ] Run install and onboard **before** class so you can focus on wizard explanation.
- [ ] If QR fails, mention channel troubleshooting: [Channel Troubleshooting](https://docs.openclaw.ai/channels/troubleshooting).
- [ ] After first reply, briefly point to “where that came from”: Gateway → Pi → tools (tease Module 3).
