# Ky Gray

### Solutions Engineer · Security Technology · AI-Enabled Solutions

I’m a Solutions Engineer with 20+ years across IT and security technology. I build working software around problems I’ve seen in the field — from solutions-engineering workflows and physical-security design to field capture, contractor operations, AI voice agents, and an AI companion for everyday users.

My approach: **understand the real workflow → map the problem → build the solution → ship it → improve it through use.**

[![Portfolio](https://img.shields.io/badge/Digital_Portfolio-Visit-0f766e?style=for-the-badge)](https://ky-gray-portfolio.vercel.app/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Ky_Gray-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/kygray/)

> **Ask Ky:** My digital portfolio includes an AI assistant that answers questions about my actual experience, projects, and skills using project documentation as its source material.

---

## Featured Projects

### 🧭 SE Command Center
**Solutions Engineering opportunity workspace**

Keeps technical opportunities, dependencies, RFP/InfoSec work, deadlines, demos, validation, and next actions visible from discovery through handoff. An Impact view connects logged SE hours to the pipeline they support, and **Suggest next step** has Claude draft an opportunity's next action for the SE to review and approve.

**[▶ Launch the interactive demo](https://se-command-center-opal.vercel.app/demo)** (no sign-in, guided tour, fictional data) · [Read the case study](https://ky-gray-portfolio.vercel.app/#se-command-center)

`Solutions Engineering` `Workflow` `Opportunity Management` `Technical Discovery`

### 🛡️ SightFlow
**Physical-security field survey and system-design workspace**

Carries security projects from field survey through equipment planning, controller and device mapping, cable requirements, BOM creation, licensing, and installer handoff documentation.

[Read the case study](https://ky-gray-portfolio.vercel.app/#sightflow) · [Open the app](https://sightflow-suite.vercel.app/) (sign-in required)

`Physical Security` `Access Control` `CCTV` `Intrusion` `BOM` `Field Engineering`

### ⚡ PowerQuote Lite
**Lead-to-quote workflow for small service contractors**

Built around missed-call intake, lead management, customer conversations, quotes, invoices, reviews, support requests, and business coaching for small contractor operations.

[Try the interactive demo](https://powerquote-lite.vercel.app/demo)

`SaaS` `Multi-tenant` `Contractor Operations` `CRM` `Supabase`

### 📸 PicTalk
**Offline-first photo + voice field capture, with Engineering Mode and an Evaluation Lab**

A field tech starts a job, photographs each stop, and talks. PicTalk keeps the photo, recording, and transcript together. Install it on your phone's home screen (Chrome, Firefox, or DuckDuckGo) and it opens and works with no signal: start and end jobs, take photos, record voice notes, and save stops. Everything waits on the phone, and when signal returns PicTalk uploads it and transcribes the voice notes automatically, with nothing to tap. Deepgram transcribes the voice notes using a security-trade vocabulary. Wrap-up notes show words live while the tech talks, through a short-lived token, so the API key never reaches the phone. A finished job becomes a reviewable AI summary drafted by Claude, with every action item tied to the stop it came from, and a PDF report.

**Engineering Mode** is off by default, so field techs never see it. It makes the offline-first pipeline visible:
- what's waiting on the phone, upload retries and errors, and the next automatic sync;
- real timings for each stop: upload per file, then transcription split into audio download and Deepgram time;
- live-words connection speed;
- each AI summary's time, attempts, and tokens.

The **Evaluation Lab** proves the offline claims instead of asserting them. A simulator drives the real app in a phone-sized browser and cuts the signal at the worst moments: mid-recording, mid-upload, mid-sentence of live words, app closed while offline. It then checks that every recording still reaches the cloud whole and gets written down. Its first run caught three problems, two of which could reach real users (live words dropping mid-sentence could lose words, and the PDF tools weren't saved for offline use). All three are fixed, and all 21 runs now pass (October 2026).

This project demonstrates the full loop: **field capture → offline sync → speech-to-text → AI summary → a measurable, tested pipeline.**

[Try the live app](https://pictalk-6cbff.web.app) · [Evaluation Lab](https://pictalk-6cbff.web.app/lab) · [View the code](https://github.com/mrkygray-art/pictalk)

`React` `Firebase` `Offline-first (IndexedDB)` `Installable PWA` `Cloud Functions` `Deepgram` `Live Streaming` `Claude API` `Observability` `Evaluation Lab`

### 🌙 NightAgent
**AI voice service orchestration + agent evaluation**

NightAgent goes beyond a voice-agent demo. It handles after-hours service intake, triage, ticket creation, simulated dispatch and repair, customer follow-up, and service-to-sales handoff — then exposes the engineering behind the agents through **Simple Mode / Engineering Mode** and an **Evaluation Lab**. It can be added to a phone's home screen from Chrome, Firefox, or DuckDuckGo and opens like an app.

Engineering Mode makes the voice workflow inspectable: where the call is right now, each tool call timed, and ElevenLabs' own turn-by-turn timings after the call. The caller's words are never shown.

The **Evaluation Lab** measures how well the agents do, from what really happened:
- a **scorecard** that keeps tests and real calls apart: emergencies escalated, priority vs. the rules, tool calls and handoffs that worked, calls completed, AI-judged checks, response time, and ElevenLabs' price per call, each number shown with the sample it's based on;
- **21 regression tests** across three agents, run against the live ElevenLabs agents three times each, including **five where a caller tries to trick the agent** (fake "system notices", "ignore your instructions", pressure to escalate, asking for alarm codes or another customer's details);
- **voice tests with real audio**: a scripted caller streams recorded speech to the live agent in noise and over a simulated phone line, measuring phone numbers and names heard exactly, talking over the agent, going quiet, and how long the caller waits;
- a **fixes log** of 14 real problems: why each happened, what changed, and whether the fix still holds in the latest runs;
- **failure injection** that replays known failures through the real server code in a sandbox;
- **[Jargon Bench](https://github.com/mrkygray-art/nightagent/tree/main/bench)**, a speech-to-text benchmark on security trade terms: with keyterm boosting, jargon heard correctly on recorded speech rose from 62.1% to 89.7% (Deepgram) and from 79.3% to 95.4% (ElevenLabs), in runs on October 4, 2026.

New tests keep catching real problems. A caller who wouldn't give a name was refused help (0 of 3 runs passed), and a burning smell from the alarm panel didn't always get "call 911" (2 of 3). In the trick tests, the agent once announced a ticket without creating it; fixing that and re-running every test caught a second problem, a fake "system notice" that got the agent to page the technician, which a new guardrail closed. On real audio, every phone number came through exactly, and in a loud café one caller's name was misheard.

This project demonstrates the full loop: **voice interaction → operational workflow → measurement → failure → fix → retest.**

[Try the live demo](https://nightshift-dispatch.vercel.app/demo) · [See the Evaluation Lab](https://nightshift-dispatch.vercel.app/lab) · [View the code](https://github.com/mrkygray-art/nightagent)

`AI Voice` `ElevenLabs` `Agent Evaluation` `Regression Testing` `Voice Testing` `Prompt-Injection Testing` `Failure Injection` `Tool Calling` `FastAPI` `Supabase` `Observability`

### 🔵 Bluey
**An AI companion that helps everyday people get better results from AI, without learning prompt engineering**

Bluey is a friendly blue orb for people who don't think of themselves as AI users. You type or talk in plain language. Before every reply, a structured "brain" step decides how to act: **DO** (the request is clear, so just do it), **DISCOVER** (one missing detail truly blocks a useful answer, so ask one plain question), or **GROW** (help now, then mention a better way of working). It also tracks the current goal so an old topic doesn't take over a new one, and picks an initiative level from "just answer" to "propose an improvement", which has to be earned with real evidence. Users can add up to five photos, hear replies spoken aloud, and have Bluey create PDF, Word, or Excel files. The OpenAI key stays in Vercel serverless functions, and every reply comes back as strict JSON.

The **Brain Lab** tests the brain like a product: 15 regression conversations run through the real chat endpoint, including topic changes, a "continue" turn, a recurring weekly task, and ordinary tasks that must not turn into business ideas. Each reply is checked for the mode, the initiative taken, and the number of questions asked, and generic help-desk phrasing and repeated answers are flagged. Built with ChatGPT. An alpha in active testing.

[Talk to Bluey](https://bluey-ai-friend.vercel.app/) · [Read the case study](https://ky-gray-portfolio.vercel.app/#bluey) · [View the code](https://github.com/mrkygray-art/bluey-ai-friend)

`OpenAI API` `Structured Output` `Conversational UX` `Speech-to-Text` `Text-to-Speech` `LLM Evaluation` `Regression Testing` `Vercel`

### 🔥 WeldMate
**Welding learning and field companion**

Brings welding calculators, reference material, and practice into one mobile-first tool: heat-input, fillet, V-groove/filler, carbon-equivalent, and conversion calculators, plus an eight-section learning path, knowledge checks, weld-symbol and position practice, visual-inspection training, WPS practice cards, and instructor/practice check-offs. Built with AI-assisted development using Google Gemini.

[Open WeldMate](https://ky-gray-portfolio.vercel.app/weldmate)

`Learning Tools` `Field Reference` `Mobile-first` `JavaScript` `Local Storage` `AI-assisted Development`

### 🎮 Last Light Outpost
**Browser-based zombie base-defense game**

A browser game with progressive waves, base building, upgrades, multiple maps, commanders, missions, leaderboards, cloud saves, and adaptive AI difficulty.

[Play Last Light Outpost](https://last-outpost-standing.vercel.app/)

`Game Systems` `AI-assisted Development` `State Management` `Progressive Gameplay`

---

## How I Build

**01 — Start with a real problem**  
I look for workflows that break down in the field: scattered survey notes, missed leads, hidden deadlines, difficult handoffs, or repetitive service processes.

**02 — Map the workflow**  
I define the users, steps, decisions, data, integrations, and handoffs before shaping the interface.

**03 — Build with AI**  
I use AI as part of the engineering workflow — not just as a chatbot. Claude, ChatGPT, Gemini, Claude Code, APIs, speech-to-text, voice agents, agent testing, and evaluation workflows help me design, build, test, and refine applications.

**04 — Ship and improve**  
I deploy working applications, test real workflows, identify friction, convert failures into repeatable tests, and iterate.

---

## Technology

**AI & Voice**  
`Claude` `ChatGPT` `Gemini` `Claude Code` `Claude API` `OpenAI API` `ElevenLabs` `Deepgram` `Agent Testing` `LLM Evaluation`

**Application Development**  
`Next.js` `React` `JavaScript` `TypeScript` `Python` `FastAPI` `SQL`

**Cloud & Platform**  
`Supabase` `Firebase` `GitHub` `Vercel` `Twilio`

**Security & Solutions Engineering**  
`Access Control` `CCTV / VMS` `Intrusion` `Intercom` `Mercury` `Cloud Security Platforms` `Identity / SSO` `REST APIs` `Technical Discovery` `Demos` `RFP / InfoSec` `System Design` `BOM` `Technical Validation`

---

## From field problems to working software

These aren't tutorial projects built around arbitrary feature lists. They come from workflows I understand through years of IT, physical security, sales engineering, field engineering, and customer-facing technical work.

I’m particularly interested in work where **Solutions Engineering, AI, SaaS, workflow automation, voice AI, agent evaluation, and security technology** overlap.

### Explore the interactive portfolio

See the applications, project case studies, resume, and **Ask Ky** AI assistant:

### ➡️ [ky-gray-portfolio.vercel.app](https://ky-gray-portfolio.vercel.app/)
