# Selected case studies

[Русская версия](./CASE_STUDIES_RU.md) · [Back to profile](./README.md)

These notes separate implemented functionality from roadmap items. Private commercial source code can be discussed in an architecture walkthrough or demonstrated without exposing client credentials.

## QuickPult

**Role:** solo founder, product owner and developer  
**Type:** multi-channel business-process SaaS  
**Status:** controlled pilot; private repository

### Problem

Small businesses receive customer requests through disconnected messengers and manually move information between chats, calendars and spreadsheets. A useful automation must complete an operation — book, sell, collect payment evidence or escalate — instead of only producing plausible text.

### What I built

- A shared runtime for Telegram, VK and a web widget.
- A production workflow from customer request through project configuration, test, approval, connection and handoff.
- Bookings with schedules, specialists, duration-aware slot reservation, cancellation and reminders.
- Payment-evidence review with reversible revenue accounting.
- Human takeover and safe return to automation with retained context.
- Conversation control, operational monitoring, reporting and versioned workflow configuration.
- A custom scenario engine with validated transitions and deterministic business actions.
- Authentication, subscription gates, audit events, media handling and channel security checks.
- Docker/deployment configuration, database migrations, backup/restore scripts and customer/admin documentation.

### Engineering decisions

Prices, availability, bookings, payment state and sales totals are deterministic. AI is used where probabilistic behavior is useful — understanding free text and natural response generation — without allowing a model to invent business facts.

### Proof and boundaries

- 201 automated tests cover critical logic.
- Telegram, VK and the web widget have working end-to-end flows.
- The WhatsApp Cloud API layer is implemented; final production E2E verification remains.
- Cross-channel identity and full multi-agent department orchestration remain roadmap items.

**Demo:** [quickbizauto.com](https://quickbizauto.com)

## AI Telegram Assistant

**Role:** developer  
**Type:** multimodal assistant prototype  
**Repository:** [leksmustang/Ai_tg_bot](https://github.com/leksmustang/Ai_tg_bot)

The bot combines an OpenAI-compatible LLM endpoint with vision, voice transcription and task-specific tools:

- conversation history and selectable system behavior;
- image analysis through alternative vision models;
- local Russian speech transcription with Faster-Whisper;
- PDF, DOCX and TXT extraction followed by question answering or summarization;
- FLUX image generation through Replicate;
- deterministic math through SymPy before LLM formatting;
- URL extraction, weather lookup, usage limits, subscription states and scheduled reminders.

The project demonstrates routing a user request to the right tool instead of sending every task directly to one language model. It is a portfolio prototype, not presented as a production SaaS.

## Coordinate Meter

**Role:** product owner and developer  
**Type:** Windows/Electron OCR utility  
**Status:** packaged Windows 1.5.11 build; private repository

### Problem

Field photos from different camera applications contain coordinates in inconsistent overlays. Incorrect OCR can silently produce wrong measurements, so a useful tool needs uncertainty handling and manual control.

### What I built

- image-local coordinate recognition across mixed photo formats;
- application-specific cropping and recognition variants;
- selected-area OCR retry with review and explicit application;
- validation that avoids reconstructing uncertain points from neighboring coordinates;
- all-pairs distance calculation, filtering and pagination;
- map opening and a packaged Windows workflow.

### Verification

Stabilization datasets passed 20/20 and 15/15; core and OCR integration tests passed 24/24. Android work was intentionally deferred while the Windows workflow was completed.

## Business automation bots

**Role:** developer and process designer  
**Repository:** [leksmustang/dance-psy_bot](https://github.com/leksmustang/dance-psy_bot)

Earlier domain projects for a dance studio, a psychologist and automotive detailing include:

- Telegram flows built with aiogram and python-telegram-bot;
- booking states and persistence;
- Google Calendar availability and event creation;
- payment and rescheduling state;
- anti-flood middleware and domain-specific questionnaires.

These projects exposed the cost of maintaining separate bots and directly informed the shared runtime and configuration model later built in QuickPult.

## Pora: Dom

**Role:** solo product developer  
**Type:** Android household-maintenance application  
**Status:** signed artifacts prepared; store release process in progress; private repository

The product explores recurring household tasks and reminders. I handled product framing, application packaging, signed APK/AAB artifacts, store listing materials, privacy publication and release workflow. I deliberately distinguish a signed build, an uploaded draft, moderation and an actually published release.

## How I work

1. Translate the business outcome into observable acceptance criteria.
2. Separate deterministic operations from AI-assisted interpretation.
3. Build the smallest complete user flow.
4. Test the real flow, including integrations and failure states.
5. Package deployment, documentation and operational recovery.
6. Report what is working, what is partial and what is still roadmap.
