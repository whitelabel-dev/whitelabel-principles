# Doctrine — Proactive AI, not Reactive AI

**Claimed 2026-06-26.** This is a positioning thesis, not a feature.

## The framing

> Most people will use AI reactively — they ask, it responds. We're building AI that's *proactive* — it sees, it notices, it acts (or escalates) before the human asks.

Reactive AI = waits for a prompt. *"How do I fix this?"* *"Schedule a meeting."* *"Summarize this doc."* Useful but limited — the human is always the loop initiator.

Proactive AI = the loop initiator. *Watches state, detects change, dispatches action or surfaces decision.* The human is in the loop, but not the trigger.

## Why this is a positioning moat, not just a feature

Every cloud LLM (ChatGPT, Claude, Gemini) is structurally reactive. Their business model is "you send a prompt, we charge per token." They optimize for one-shot quality, not standing-watch continuity.

A proactive AI ecosystem looks fundamentally different:
- **It runs 24/7**, not just when you open a tab.
- **It owns its own infrastructure** (the fleet, the memory store, the world model, the dispatch surfaces) — because proactive requires persistence + state that cloud chat can't economically maintain.
- **It produces outputs** the user didn't explicitly ask for: alerts, tickets, recommendations, scheduled meetings, drafted emails, dispatched vendors.
- **It has the moral weight of getting it right** because acting without being asked is harder than answering when asked.

This is unfortunately also why most companies *won't* build it — too operationally heavy, too much liability, too much infrastructure. That's the moat.

## What proactive AI needs to work

Five substrates, all of which whitelabel.dev is building:

| Substrate | Role | Repo |
|---|---|---|
| **Eyes (world model)** | Can't react to what you can't see | [whitelabel-3d](https://github.com/whitelabel-dev/whitelabel-3d) |
| **Persistent memory** | State + history that survives a chat closing | [whitelabel-memory](https://github.com/whitelabel-dev/whitelabel-memory) |
| **Compute that's always on** | Where the watching happens | [whitelabel-agents](https://github.com/whitelabel-dev/whitelabel-agents) (Mac mini fleet) |
| **Dispatch surfaces** | What the AI uses to act | [whitelabel-orchestrator](https://github.com/whitelabel-dev/whitelabel-orchestrator) · [whitelabel-channels](https://github.com/whitelabel-dev/whitelabel-channels) · [whitelabel-flow](https://github.com/whitelabel-dev/whitelabel-flow) |
| **An overseer** | Independent layer that watches the watchers | [whitelabel-terminal](https://github.com/whitelabel-dev/whitelabel-terminal) |

## What proactive AI looks like in the ecosystem

| Reactive (most companies) | Proactive (us) |
|---|---|
| "What's the status of my Notion mirror?" → AI checks + reports | AI watches the mirror nightly; alerts only when something drifted, with the fix already proposed |
| "Schedule my meeting with X" | Calendar AI sees X in your inbox + your calendar; pre-blocks slots + drafts the invite, waits for your nod |
| "Find me a plumber" | [whitelabel-house-manager](https://github.com/whitelabel-dev/whitelabel-house-manager) detects the water-flow anomaly + dispatches a plumber + texts you what happened |
| "Did anything change in my contracts?" | [whitelabel-office-manager](https://github.com/whitelabel-dev/whitelabel-office-manager) calendar-watches every renewal; T-30/T-14/T-7 reminders + auto-drafts the review email |
| "Walk to the kitchen and grab water" | Voice → [whitelabel-flow](https://github.com/whitelabel-dev/whitelabel-flow) → [whitelabel-robotics](https://github.com/whitelabel-dev/whitelabel-robotics) → the humanoid finds the kitchen in [whitelabel-3d](https://github.com/whitelabel-dev/whitelabel-3d) + executes |
| "Help me cancel SaaS we don't use" | [whitelabel-office-manager](https://github.com/whitelabel-dev/whitelabel-office-manager) detects "nobody has logged in for 60 days" → surfaces the cancellation candidate with savings math attached |

## Non-negotiables when designing AI features

1. **Default to proactive.** If a feature can plausibly run on a schedule / on state change / on a sensor reading, design it that way first. Reactive is a fallback, not the starting point.

2. **Always-on means always-explained.** If the AI acts without being asked, it must say *why*. A ticket opened automatically needs a "this happened because X" line. A dispatched vendor needs a "I called them because Y."

3. **Escalation, not autonomy.** Proactive AI surfaces decisions to humans — it doesn't make irreversible ones alone. The default action is *notify the human with a recommendation*; the high-trust default is *act and notify* for clearly safe actions (e.g., scheduling a vendor visit). Never *act silently.*

4. **State persistence is foundational.** Proactive requires memory that outlives any single chat. Use [whitelabel-memory](https://github.com/whitelabel-dev/whitelabel-memory). Don't build features that assume the AI's "memory" is the current chat context.

5. **The fleet runs the watch.** Proactive work happens on the Mac mini fleet ([[project_agent_fleet]]), not in user-initiated browser sessions. If a feature needs continuous monitoring, it needs a fleet home.

6. **World model is the substrate where applicable.** Spatial / physical work (house, office, robot, voice navigation) resolves against [whitelabel-3d](https://github.com/whitelabel-dev/whitelabel-3d). You can't be proactive about a physical space you can't see.

## What this rules in / out

**Rules in:**
- Auto-dispatch loops (house-manager + office-manager)
- Anomaly detection on data + sensors + telemetry
- Calendar-driven workflows (renewals, recurring service, compliance)
- Drift / regression detection (whitelabel-terminal overseer pattern)
- Always-on assistants (Flow listening for voice triggers)
- Humanoid embodiment (the robot watches the world + acts)
- Proactive sales motion (CRM detects buying signals + drafts outreach)

**Rules out:**
- Chat-only assistants with no state
- Features that require the user to remember to open them
- "AI" as a button you click for a one-shot response
- Surveillance dashboards that watch the user (vs. watch the world FOR the user)

## Related doctrines + repos

- [[disability-employment]] — Track 2 (the assistive layer) is inherently proactive: the AI sees what the worker needs before they ask
- [whitelabel-3d](https://github.com/whitelabel-dev/whitelabel-3d) — the eyes
- [whitelabel-memory](https://github.com/whitelabel-dev/whitelabel-memory) — the state
- [whitelabel-agents](https://github.com/whitelabel-dev/whitelabel-agents) — the always-on compute
- [whitelabel-terminal](https://github.com/whitelabel-dev/whitelabel-terminal) — the overseer
- [whitelabel-orchestrator](https://github.com/whitelabel-dev/whitelabel-orchestrator) — the dispatcher
- [whitelabel-flow](https://github.com/whitelabel-dev/whitelabel-flow) — the voice surface
- [whitelabel-house-manager](https://github.com/whitelabel-dev/whitelabel-house-manager) + [whitelabel-office-manager](https://github.com/whitelabel-dev/whitelabel-office-manager) — proactive ops in action
- [whitelabel-robotics](https://github.com/whitelabel-dev/whitelabel-robotics) — proactive embodiment

## The doctrine sentence

> Most people will use AI reactively. We build AI that's proactive — it sees, it notices, it acts, it escalates. The world model gives it eyes; memory gives it continuity; the fleet gives it always-on compute; the overseer keeps it honest.

That's the entire positioning.
