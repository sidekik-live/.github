# Sidekik

**An AI apprentice that learns how your experts work, then coaches the next hire.**

When an experienced employee leaves, their judgment leaves with them: nobody wrote down *why* they do things the way they do. Sidekik sits next to the expert while they work, asks "why?" at the right moments, and turns what it learns into a playbook that coaches new hires on their own screen, catching mistakes before they're saved.

Built for the Hack-Nation 7th Global AI Hackathon, Challenge 01 (ElevenLabs). Live at [sidekik.live](https://www.sidekik.live).

## How it works

| | What happens |
|---|---|
| **1. Capture** | The expert shares their screen and works as usual. Sidekik watches and stays silent. At a natural pause after a judgment call, its voice agent asks one short question, such as *"Why did you change the cost center from 4711 to 0400?"* |
| **2. Work Map** | When the task is done, Sidekik drafts a **Work Map**: every step, the decision made, the expert's reason in their own words, and the rules they follow. A short spoken debrief fills the gaps, then Sidekik reads the process back until the expert confirms it. Every step links to the screen moment and the quote it came from. |
| **3. Coach** | A new hire does the same work on their own screen. Sidekik asks them to predict decisions, and when they're about to break a rule, it **blocks the save**, explains it in the expert's words, and replays the expert's screen moment. A mastery report shows what to practise next. |

**Example:** Sabine codes a €6,350 CNC fixture to capex and explains why. Weeks later, Lena picks the opex cost center for a €7,200 spindle motor and presses Save. Sidekik stops her: *"Hold on before you save. Sabine said: anything over five thousand net for equipment is a fixed asset, so 0400."*

## What makes it different

- **Knows when to stay quiet.** A pause detector in plain code plus fast typed decisions decide when a question won't interrupt. The voice agent says nothing while the expert narrates or types.
- **Evidence for everything.** Every rule in a Work Map cites the expert's exact words and a screen moment; code checks that each quote really appears in the transcript.
- **Deterministic safety checks.** The check before save is plain rule evaluation (JSON-Logic), with no model call, so it's fast and predictable.
- **Private by design.** Raw screen frames are never stored, personal data is redacted before anything is saved, and saying "off the record" stops capture immediately.
- **Works where people work.** In the browser, or as a bot that joins Google Meet, Zoom or Teams.

## Built with

- **[ElevenLabs Agents](https://elevenlabs.io):** the voice interviewer, debrief and tutor agents (Scribe speech recognition, Eleven v3 voices, turn-taking, client and webhook tools), defined as code
- **[Claude](https://www.anthropic.com/claude):** screen understanding (Haiku 4.5 vision), question drafting, and Work Map building (Sonnet)
- **TypeSafe Jev:** fast, low-cost typed decisions, such as "is this a natural pause?" or "did the expert confirm?"
- **[Recall.ai](https://recall.ai):** the meeting bot for Google Meet, Zoom and Teams
- **Supabase** (Postgres, Auth, Realtime, Storage), **Redis Streams**, **Presidio** for PII redaction, **TypeScript**, Fastify, React and TanStack Start, deployed on Railway and Cloudflare

## Repositories

| Repo | What it does |
|---|---|
| [sidekik-web](https://github.com/sidekik-live/sidekik-web) | The web app: dashboard, Capture and Tutor rooms, Work Map viewer, MiniERP sandbox, replay mode, meeting tile |
| [sidekik-voice](https://github.com/sidekik-live/sidekik-voice) | ElevenLabs agents as code, conversation tokens, transcripts, Work Map sync to the tutor agent |
| [sidekik-perception](https://github.com/sidekik-live/sidekik-perception) | Turns screen frames into events, redacted keyframes and clips |
| [sidekik-brain](https://github.com/sidekik-live/sidekik-brain) | Decides when and what to ask: pause detection, Jev decisions, question planning |
| [sidekik-gateway](https://github.com/sidekik-live/sidekik-gateway) | Public API: sessions, consent, off the record, redaction, real-time commands, costs, replay |
| [sidekik-mapper](https://github.com/sidekik-live/sidekik-mapper) | Builds the Work Map, runs the debrief, compiles and exports the rules |
| [sidekik-tutor](https://github.com/sidekik-live/sidekik-tutor) | Coaching: step tracking, the check before save, predictions, mastery reports |
| [sidekik-meetbot](https://github.com/sidekik-live/sidekik-meetbot) | Recall.ai connector for Google Meet, Zoom and Teams |
| [sidekik-platform](https://github.com/sidekik-live/sidekik-platform) | Shared contracts, event bus, database migrations, dev tools |
| [sidekik-docs](https://github.com/sidekik-live/sidekik-docs) | Architecture, schema and design docs |

## Team

- **Sahil Mohanty** ([@heisenberg1804](https://github.com/heisenberg1804)): screen understanding, decisions, shared platform
- **Aadil Abdul Karim** ([@aadilxx1](https://github.com/aadilxx1)): web app and voice experience
- **Mayukh Sinha** ([@neu-msinha](https://github.com/neu-msinha)): sessions, Work Maps, tutor, meeting bot
