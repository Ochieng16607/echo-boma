# Echo-Boma

**Cultural Learning • Peer Problem-Solving • Research • Virtual School • Tech Studies**

> Equality • Connection • Motivation  
> Offline-first • Accessible (Sign Language, Local Languages, Voice) • Free-core

**Repository**: https://github.com/Ochieng16607/echo-boma  
**Target users**: Teens (13–19) worldwide, with special focus on African and low-resource communities.

---

## Vision

Echo-Boma is an interactive platform where teens from every culture collaborate to solve real problems using **global cultural wisdom** (Sankore University legacy, Ubuntu, Kaizen, Nalanda, Indigenous knowledge systems, and more) **together with practical technological skills**.

The system combines:

- Cultural problem-solving rooms
- Interdisciplinary research collaboration
- Virtual School (Culture Lab + Tech Lab + Fusion Lab)
- Personal growth diary with time management & progress analytics
- Global Society (e-boma) for meetings, discussions, and shared experiences
- Strong accessibility (real-time sign language video bar, subtitles, local languages, voice)
- Psychological safety, celebration of small wins, and motivation systems

**Core principle**: Every cultural lesson ends with a practical tech action. Every tech lesson ends with a cultural reflection.

---

## Main Navigation (10 Core Segments)

| # | Segment | Purpose |
|---|---------|--------|
| 1 | **User Account** | Bio-profile, interests, diary, progress tracker (graphs + statistics), time management, badges, invitations |
| 2 | **Settings** | Access limits, voice, sign language, subtitles, language, privacy, notifications preferences |
| 3 | **Notifications** | Awareness challenges, competitions, research updates, reminders, system announcements |
| 4 | **Echo Guide** | AI navigation assistant – tailored videos, real-time Q&A, role/interest-based suggestions, help & limits |
| 5 | **Real-time Sign Language Video Bar** | Accessibility layer that can overlay / match ongoing activities across segments |
| 6 | **Pop-up Dialogue Box** | Contextual help, consent, first-run guidance, confirmations |
| 7 | **Global Society (e-boma)** | Meetings, conflict resolution, webinars, discussion groups, cultural experiences, brainstorming hub |
| 8 | **Research** | Interdisciplinary & collaborative research, peer-review, teammate finding, feasibility testing, IP protection |
| 9 | **E-zone** | Simulations, gamified presentations, virtual schools/labs, environment-based learning, music & moral content |
| 10 | **Home Tab** | Dashboard – awareness challenges, competitions, personal/group research, feeds, search |

**Search Tab** is present in all segments (text, voice, scan, camera).

---

## Key System Capabilities (Backend & Cross-Cutting)

- Cloud saving + local caching of real-time progress
- Verification, validation & content filters (inappropriate content, spam)
- Telemetry, rate limiting, anti-spoofing, DDoS protection foundations
- Automatic save & update of every segment
- Indexing, sorting, interest-based grouping
- Smart search that narrows to relevant results
- Celebrate all small wins
- Bluetooth / local Wi-Fi sharing for offline packs
- Dynamic backend for maintenance and modification
- Strong data security & privacy by design

---

## Interdisciplinary Learning Fields

- Science & Technology
- Life Sciences
- Culture & Traditions (especially as they impact life sciences)
- History (learning from societal pasts)
- Medical Research
- Liberal Arts

Focus: Better existing policies and personal practices starting at the individual level.

---

## Accessibility & Inclusion (Non-Negotiable)

- Real-time sign language video bar
- Real-time subtitles
- Voice input/output
- Local languages (Swahili, English, French + community-submitted languages after verification)
- Offline-first modules and packs
- Low-data mode
- Feature-phone / SMS-USSD fallback paths where feasible
- Colourful, psychologically motivating UI

---

## Development Status

This repository starts with a carefully analysed Product Requirements Document, Architecture, and Feature Map that resolve the major shortcomings of the initial feature dump (scope, safety for minors, technical feasibility of real-time sign language, privacy, IP, moderation).

**Recommended stack** (from prior blueprints + feasibility analysis):

- Frontend: Flutter (Android-first, iOS, Web/PWA) + offline (Hive/SQLite)
- Backend: Firebase or Supabase
- Real-time: Firebase Realtime / WebRTC / Agora (adaptive bitrate)
- AI assistance: Echo Guide (LLM + retrieval), later specialised models for sign language
- Content packs: Downloadable offline modules

---

## Getting Started (for developers)

1. Read `docs/PRODUCT_REQUIREMENTS.md` (prioritised, shortcomings resolved)
2. Read `docs/ARCHITECTURE.md`
3. Read `docs/FEATURE_MAP.md`
4. Follow `.cursor/rules` for consistent AI-assisted coding (Cursor / Copilot style)
5. Start with MVP milestones listed in the PRD

---

## Values

**Equality** – Every culture and every teen has equal voice.  
**Connection** – Real cross-cultural friendships through solving problems together.  
**Motivation** – Purposeful gamification, visible impact, celebration of small wins, time management support.

---

*Built with careful word-by-word analysis of the full specification. All major shortcomings have been identified and resolved in the documentation before coding begins.*
