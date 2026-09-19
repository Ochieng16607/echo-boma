# Architecture Document
## Echo-Boma

**Goal**: Secure, offline-capable, accessible, maintainable system that can grow from MVP to full vision without rewriting the core.

---

## 1. High-Level Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        Clients                               │
│  Flutter App (Android-first)  │  PWA / Web  │  Future iOS   │
│  + Hive / SQLite offline cache + background sync            │
└─────────────────────┬───────────────────────────────────────┘
                      │ HTTPS / WebSocket (adaptive)
┌─────────────────────▼───────────────────────────────────────┐
│                     API Gateway / BFF                        │
│  Auth • Rate limiting • Input validation • Content filters  │
└─────────────────────┬───────────────────────────────────────┘
                      │
        ┌─────────────┼─────────────┐
        ▼             ▼             ▼
┌──────────────┐ ┌──────────┐ ┌─────────────────┐
│  Auth & User │ │ Content  │ │ Collaboration   │
│  Service     │ │ & Modules│ │ (Rooms, Research│
│              │ │ Service  │ │  Meetings)      │
└──────────────┘ └──────────┘ └─────────────────┘
        │             │             │
        └─────────────┼─────────────┘
                      ▼
┌─────────────────────────────────────────────────────────────┐
│  Data Layer                                                  │
│  PostgreSQL / Firestore  +  Object Storage (media packs)     │
│  Search Index (Algolia / Meilisearch / Typesense or native)  │
│  Cache (Redis)                                               │
└─────────────────────────────────────────────────────────────┘
```

**Recommended starting stack** (balances speed, offline, cost, teen-scale):

- **Frontend**: Flutter 3.x
- **Backend**: Supabase (Postgres + Auth + Realtime + Storage + Edge Functions)  
  *or* Firebase (Auth + Firestore + Cloud Functions + Storage) – decision at sprint 0
- **Offline**: Hive (or Isar) + connectivity-aware sync
- **Realtime meetings**: Agora or Daily.co (adaptive bitrate) or WebRTC via Supabase Realtime
- **AI (Echo Guide)**: LLM API + retrieval over app documentation & cultural modules
- **Search**: Typesense or Meilisearch (self-hostable) or Algolia
- **Media**: Aggressive compression + progressive delivery
- **Sign language (Phase 2)**: Separate specialised service; never block core flows

---

## 2. Core Data Models (Simplified)

```text
User
  id, email/phone, displayName, bio, cultureTags[], languages[],
  techLevel, interests[], deviceType, offlinePreference,
  privacySettings, parentalConsentStatus, createdAt, lastActive

Module (Culture | Tech | Fusion)
  id, type, title, description, contentPackUrl, durationMin,
  reflectionPrompts[], offlineSizeKb, languages[], version

DiaryEntry
  id, userId, period (daily|weekly|monthly|annual),
  content (text/voice/video refs), timeBoxedActivities[],
  mood/ reflection, createdAt

Challenge / Problem
  id, title, description, suggestedCultures[], suggestedTechTools[],
  creatorId, status, tags[]

ResearchProject
  id, title, description, members[] (with roles & contribution %),
  status, license, feasibilityScore, files[], peerReviews[],
  canBeContinuedByOthers (bool + consent log)

Room / Session
  id, type (problem|meeting|discussion), members[],
  challengeId or researchId, messages[], whiteboardState,
  aiSummary (editable), recordingConsent

Progress / Badge
  userId, completedModules[], badges[], portfolioItems[],
  timeSpentStats, impactMetrics

ContentPack
  version, modules[], offlineManifest, checksum

ModerationFlag / Report
  id, targetType, targetId, reporterId, reason, status, reviewedBy
```

All sensitive fields encrypted at rest where required. Soft deletes + recoverable bin for user content.

---

## 3. Security & Safety Architecture

- **Authentication**: Secure auth (email/phone + optional social). Age declaration + parental consent flow for under-16/18 as required by jurisdiction.
- **Authorisation**: Role-based (User, Moderator, ContentReviewer, Admin, Developer). Principle of least privilege.
- **Input validation & sanitisation** on every write path.
- **Content filters**: Automated (keyword + ML classifier) + human review queue for research, feeds, meetings.
- **Rate limiting & abuse prevention**: Per-user, per-IP, progressive delays. Foundation for DDoS resistance.
- **Audit logs**: Critical actions (moderation, research ownership transfer, admin changes).
- **Privacy**: Data minimisation, purpose limitation, easy export/delete. Clear privacy policy in-app.
- **Meetings**: Default to group rooms with moderation tools. 1:1 video restricted or heavily logged for younger users.
- **Telemetry**: Performance + security events only; no selling of personal data. Transparent to users.

---

## 4. Offline & Low-Data Strategy

- Content packs (modules, key help videos) downloadable on Wi-Fi.
- Diary and research drafts fully usable offline; sync when online.
- Progressive Web App option for lightweight access.
- Low-data mode: text-first, compressed images, optional media.
- Bluetooth / local Wi-Fi sharing of packs for school / rural groups (Phase 1.5).
- Data usage indicator visible to user.

---

## 5. Accessibility Architecture

- Sign language: Phase 1 = curated video library + text alternatives. Phase 2 = limited real-time in supported contexts.
- Real-time subtitles (speech-to-text) where video/audio is used.
- Voice input/output throughout.
- Screen-reader friendly Flutter widgets + semantic labels.
- High-contrast & colourful themes (user selectable).
- Language packs: English, French, Swahili, Arabic first; community languages via moderated submission.

---

## 6. Echo Guide (AI Navigation)

- Retrieval-augmented generation over:
  - App documentation
  - Cultural & tech module summaries
  - Community guidelines
- Short video library for common tasks.
- Never makes irreversible decisions; always suggests and explains.
- Logging of interactions for improvement (opt-in / anonymised).

---

## 7. Backend Dynamism & Maintainability

- Feature flags for gradual rollout.
- Content (modules, challenges, help videos) stored as versioned packs, not hard-coded.
- Admin / moderator dashboards for review queues, announcements, language verification.
- Clear separation of concerns so new segments can be added without breaking existing ones.

---

## 8. Psychological Motivation & UI

- Design system with vibrant but calm colour palette (accessible contrast).
- Micro-celebrations for small wins (module completed, first research contribution, streak).
- Progress graphs and “time well spent” insights in the diary.
- Badges that emphasise contribution and connection, not just competition.
- Hot-take / success / failure story formats that normalise learning from mistakes.

---

## 9. Phased Delivery Alignment

**Phase 1 (MVP)** – Core loop working offline + online, safe for teens, cultural + tech integrated.  
**Phase 2** – Richer e-boma meetings, improved research tools, limited real-time accessibility features.  
**Phase 3** – Advanced simulations (E-zone), deeper AI assistance, broader language & sign-language support.

---

*This architecture deliberately resolves the technical and safety shortcomings of the original feature list while remaining faithful to the ambitious vision.*
