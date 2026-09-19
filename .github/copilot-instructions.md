# GitHub Copilot Instructions for Echo-Boma

You are assisting with the development of **Echo-Boma**, a free-core, offline-first platform for teens (13–19).

## Product Vision (never lose this)

Echo-Boma helps teens from every culture solve real problems together using:
- Global cultural wisdom (Sankore University legacy, Ubuntu, Kaizen, Nalanda, Indigenous knowledge systems, etc.)
- Practical technological skills

**Core design rule**:
- Every cultural lesson ends with a practical tech action.
- Every tech lesson ends with a cultural reflection.

**Core values** (non-negotiable):
- **Equality** – Every culture and every teen has equal voice. No hierarchy of cultures.
- **Connection** – Real cross-cultural friendships formed through collaborative problem-solving.
- **Motivation** – Celebrate small wins, show progress clearly, support good time management.

Target users: Teens 13–19 worldwide, with special focus on African and low-resource communities. Strong accessibility (sign language path, voice, subtitles, local languages) is required.

## Main App Structure (10 segments)

1. User Account (bio, interests, diary, progress graphs, time management, badges, invite)
2. Settings (access limits, voice, sign language, subtitles, language, privacy)
3. Notifications
4. Echo Guide (AI navigation assistant – help videos + real-time Q&A)
5. Real-time Sign Language Video Bar (Phase 1 = on-demand videos + text alternatives)
6. Pop-up Dialogue Box (contextual help & consent)
7. Global Society / e-boma (meetings, discussions, cultural experiences, brainstorming)
8. Research (collaborative, peer-review, teammate finding, feasibility, IP protection)
9. E-zone (simulations, virtual school/labs, gamification, moral content)
10. Home Tab (dashboard, feeds, challenges, search)

Search is available in every segment (text, voice, scan, camera).

## Technical Preferences

- **Frontend**: Flutter (Android-first, then iOS & PWA)
- **Backend**: Prefer Supabase or Firebase
- **Offline**: Hive / Isar + background sync. Core flows must work offline.
- **Realtime**: Adaptive bitrate (Agora / Daily / WebRTC)
- Strong typing, clear separation of concerns, feature flags
- Content (modules, help videos) comes from versioned packs – never hard-code large content
- Soft deletes + recoverable bin for user content
- Automatic save of progress wherever the user creates content

## Critical Rules for Generated Code

1. Always consider offline / low-connectivity cases.
2. Never introduce unmoderated private 1:1 video for younger users by default.
3. Respect the phased roadmap:
   - **MVP (Phase 1)**: User account + diary + cultural modules (Sankore, Ubuntu, Kaizen) + tech/fusion modules + basic collaborative rooms + basic research + search + notifications + settings + basic Echo Guide + content filters + offline packs + celebrate small wins.
   - Real-time sign language matching everything, advanced simulations, complex entry quizzes = later phases.
4. Safety & privacy for minors are mandatory (moderation hooks, consent flows, age-appropriate design).
5. Keep Equality, Connection, and Motivation visible in UX (progress graphs, badges that reward contribution & connection, micro-celebrations of small wins).
6. Prefer readable, well-named code. Comments only when intent is non-obvious.
7. When adding features, keep the 10-segment structure consistent with `docs/FEATURE_MAP.md`.

## Key Documents to Respect

- `docs/PRODUCT_REQUIREMENTS.md` – prioritised requirements and resolved shortcomings
- `docs/ARCHITECTURE.md` – security, data models, offline strategy, accessibility
- `docs/FEATURE_MAP.md` – exact mapping of all requested features
- `.cursor/rules` – additional consistent rules

## UI & Copy Tone

- Encouraging, respectful, celebrates small wins
- Clear about limits and community guidelines
- Never condescending
- Colourful and psychologically motivating, while maintaining good contrast and accessibility

## When in doubt

- Prioritise teen safety, offline capability, and the culture + tech integration rule.
- Prefer simple, shippable MVP solutions over complex complete implementations of later-phase features.
- Ask for clarification only if a request clearly contradicts the core values or the phased roadmap.

This file is the primary custom instruction source for GitHub Copilot on this repository.
