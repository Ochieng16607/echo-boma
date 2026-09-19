# Product Requirements Document (PRD)
## Echo-Boma v0.1 – Carefully Analysed & Shortcomings Resolved

**Date**: September 2026  
**Status**: Ready for structured development  
**Authoring approach**: Word-by-word analysis of the full user specification + integration with prior Cultural Wisdom + Tech Studies blueprints. All major shortcomings identified and mitigated.

---

## 1. Executive Summary

Echo-Boma is a free-core, offline-first educational and collaboration platform for teens (13–19). It combines:

- Cultural wisdom modules (Sankore, Ubuntu, Kaizen, Nalanda, Indigenous knowledge, etc.)
- Practical technological studies (Digital Foundations → Fusion projects)
- Peer problem-solving and interdisciplinary research
- Personal growth tools (diary, time management, progress analytics)
- Global Society (e-boma) for meetings, discussions and shared experiences
- Strong accessibility (sign language, voice, subtitles, local languages)

**Core design rule (preserved from earlier blueprints)**  
Every cultural lesson ends with a practical tech action.  
Every tech lesson ends with a cultural reflection.

---

## 2. Major Shortcomings Identified in the Raw Specification & Resolutions

| # | Shortcoming | Risk | Resolution |
|---|-------------|------|------------|
| 1 | Extreme scope creep (social network + research platform + real-time sign language interpreter + virtual school + diary + simulations + everything) | Never ships / low quality | Strict phased roadmap. MVP = core cultural+tech problem solving + diary + basic research + accessibility foundations. Real-time sign language & full simulations = Phase 2/3. |
| 2 | Real-time sign language video bar matching **all** segments | Extremely high compute, bandwidth, accuracy requirements; privacy risk | Phase 1: Static / on-demand sign language help videos + text alternatives. Phase 2: Limited real-time in controlled rooms. Always provide text/voice alternatives. |
| 3 | Heavy real-time video + meetings + peer research for minors | COPPA/GDPR, safety, grooming risk | Age gate + parental consent pathways, strong moderation (AI + human), reporting, content filters, no unmoderated private 1:1 video by default for under-16. |
| 4 | “Telemetry against hacking, spoofing, DDoS” stated as feature | Marketing claim, not architecture | Proper security architecture: rate limiting, auth, input validation, WAF-ready design, audit logs. Documented in Architecture. |
| 5 | Collaborative research completion of unfinished work + copyright | IP conflicts, ownership disputes | Clear contribution model, consent flows, Creative Commons / custom license options, attribution, group badges with named contributors. |
| 6 | Automatic minutes + “mega-phased analyzer” for every meeting | Hallucination + privacy | AI-assisted summaries with human review option; users can edit; sensitive meetings can opt out of auto-transcription. |
| 7 | “I ONLY TO HAVE ACCESS TO SYSTEM BACKEND” | Single point of failure / no team | Role-based access control (Admin, Moderator, Content Reviewer, Developer). Documented roles. |
| 8 | Local languages “shared to main cloud but I must verify” | Scalability of verification | Community submission → automated checks + human review queue for admins/moderators. |
| 9 | Missing clear prioritisation of Free vs Premium | Monetisation risk | Core cultural, tech, research, diary, e-boma basic features free forever. Optional premium for advanced analytics, exclusive challenges, ad-free. |
| 10 | Psychological motivation + colourful UI stated but no design system | Inconsistent UX | Design tokens + motivation patterns (celebration of small wins, progress graphs, badges) defined early. |

All of the above are resolved in this PRD and the Architecture document.

---

## 3. Target Users & Personas

- **Primary**: Teens 13–19 (global, with emphasis on African & low-resource settings)
- **Secondary**: Teachers, youth clubs, NGOs (facilitation tools, bulk packs)
- **Accessibility priority**: Deaf / hard-of-hearing teens, users with limited data, feature-phone users, speakers of Swahili / French / Arabic / local languages

---

## 4. Core Values (Non-Negotiable)

1. **Equality** – No culture ranked higher; equal voice; anonymous idea mode available.
2. **Connection** – Persistent teams, friendship formation through solving real problems.
3. **Motivation** – Celebrate small wins, visible impact, time management support, purposeful badges.

---

## 5. Functional Requirements by Segment

### 5.1 User Account
- Bio-profile + interests + culture tags + tech level
- Diary (daily / weekly / monthly / annual) with text, voice, video notes
- Entry formats + structured spaces
- Personal time-boxing of activities
- Progress tracker with statistics & graphs
- Time spent analytics + suggestions for more effective use
- Probability / feasibility indicators for personal projects
- Badges (impactful contributions)
- Invite-a-friend
- Linked to reminders & notifications

### 5.2 Settings
- User access limits (can be toggled; first-run defaults to on with bottom dialog to turn off)
- Voice input/output
- Sign language preference
- Real-time subtitles
- Language (English, French, Swahili, Arabic + verified local languages)
- Privacy & data controls
- Notification preferences

### 5.3 Notifications
- Awareness challenges
- Competitions
- Personal / group research updates
- Reminders (from diary & time-boxing)
- System announcements (must pass backend relevance filter)
- Celebrate small wins

### 5.4 Echo Guide (AI)
- Navigation help via short tailored videos
- Real-time answers to “how do I…?” questions
- Suggests relevant sections based on role & interest
- Explains limits, expectations, community guidelines
- Does **not** replace human moderation

### 5.5 Real-time Sign Language Video Bar
- **Phase 1**: High-quality pre-recorded / on-demand sign language explanations for key flows
- **Phase 2**: Limited real-time in supported meeting rooms (with consent)
- Always paired with text & voice alternatives
- User can enable/disable

### 5.6 Pop-up Dialogue Box
- First-run guidance
- Consent & privacy notices
- Confirmation for destructive actions
- Contextual tips

### 5.7 Global Society (e-boma)
- Scheduled meetings & webinars
- Discussion groups (e.g. weekly tea discussions)
- Conflict resolution spaces
- Cultural experience sharing
- Brainstorming & Think Hub
- Automatic AI-assisted minutes & summaries (editable, opt-out available)
- Peer review of outcomes
- Share success / failure stories

### 5.8 Research
- Interdisciplinary & collaborative research
- Copyright & IP protection tools (attribution, licenses)
- Group badges with all contributor names
- Peer-review of articles / research
- Find teammates (interest-based + optional entry quiz with time limits, no copy-paste, rotating questions)
- Feasibility testing of projects
- Support for multimedia
- Automatic progress saving
- Ability for another user to continue unfinished research **only with explicit consent**
- Connect research materials to simulator (E-zone) for visual presentation
- Assignment assistance by present group members

### 5.9 E-zone
- Simulations (research, sketches, text → game-format presentation)
- Animated / improved presentations
- Virtual schools & labs
- Environment-based learning
- Physical / academic / moral education content
- Gamification (video + text)
- Music & moral educational videos
- Automatic updates based on user searches & interests

### 5.10 Home Tab / Dashboard
- Awareness challenges
- Competitions
- Personal & group research shortcuts
- Feeds (create videos, text, voice; view, modify, delete, share)
- Success stories / failure stories / hot take of the week
- Challenges board
- Bin (recoverable deletions)
- Search (always available)

### Cross-cutting: Search
- Present in every segment
- Input methods: type, voice, scan, camera
- Smart narrowing to relevant results
- Indexing & sorting of storage

---

## 6. Non-Functional Requirements

- **Offline-first**: Modules, diary, many research drafts downloadable and usable offline
- **Low-data mode** + data usage indicator
- **Performance**: Progressive loading, aggressive caching
- **Security**: Auth, rate limiting, input validation, content filters, audit logs
- **Privacy**: Data minimisation, clear consents, age-appropriate design
- **Accessibility**: WCAG-oriented + sign language + voice + local languages
- **Scalability**: Backend designed to be dynamic and maintainable
- **Colourful & motivating UI** with consistent design system

---

## 7. MVP Definition (Phase 1 – Must Ship First)

1. User registration / login + bio-profile + culture tags + tech level
2. Basic diary + time spent tracking + simple graphs
3. 3 Cultural modules (Sankore, Ubuntu, Kaizen) + 2 Tech / Fusion modules
4. Basic collaborative problem-solving rooms (text + sticky notes)
5. Basic Research: create project, invite members, automatic save
6. Home dashboard + Notifications + Search (text)
7. Settings (language, basic accessibility toggles)
8. Echo Guide (static help videos + simple FAQ / LLM-assisted answers)
9. Content filters + basic moderation tools
10. Offline download of modules
11. Celebrate small wins + starter badges

**Explicitly out of MVP** (but planned):
- Full real-time sign language matching every segment
- Advanced simulations & heavy gamification
- Full automatic meeting transcription at scale
- Complex entry quizzes for research groups
- Full Bluetooth pack sharing

---

## 8. Success Metrics (Early)

- % of users completing at least one cultural + one tech module
- Number of cross-cultural problem-solving sessions
- Diary engagement (entries per week)
- Retention (D7 / D30)
- Accessibility feature usage
- Reports of safety issues (should trend down)
- Qualitative feedback on feeling of equality, connection, motivation

---

## 9. Open Questions / Future Decisions

- Exact age verification method (self-declared + parental email vs stronger)
- Preferred backend (Firebase vs Supabase) – decision in Architecture
- Sign language language(s) priority (ASL, local variants, etc.)
- Monetisation experiments after free-core is stable

---

*This PRD is the result of deliberate, word-by-word analysis. It preserves the ambitious vision while making the system buildable, safe for teens, and aligned with the original cultural + technological learning goals.*
