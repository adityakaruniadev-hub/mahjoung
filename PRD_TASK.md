# PRD_TASK.md - Implementation Roadmap

## Status: ✅ PRD COMPLETE - Ready for Implementation

**Last Updated:** March 23, 2026  
**Project:** Mahjoung - Hong Kong Mahjong for Indonesia  
**Phase:** Phase 1 - Indonesia Launch (MVP)

---

## 📋 Decisions Summary (CONFIRMED)

| Decision | Choice | Rationale |
|----------|--------|-----------|
| **Variant** | Hong Kong Old Style | Simplest rules, 10-15 min games, underserved market |
| **Monetization** | Ads + Subscription (Rp 29,000/mo) | No gambling, local pricing, sustainable |
| **Audience** | Social players (all ages) | WhatsApp sharing, private tables, Indonesia → SEA → Global |
| **Platform** | Web-first PWA | No download, fast iteration, mobile-friendly |
| **Frontend** | React + TypeScript + Vite | Type safety, fast builds |
| **State** | Zustand | Lightweight, perfect for game state |
| **API/Data** | TanStack Query | Sync, caching |
| **Styling** | Tailwind CSS | Rapid UI dev |
| **Animations** | Framer Motion | Tile draw/discard effects |
| **Backend** | Go (Golang) | Performance, concurrency |
| **Database** | PostgreSQL + Redis | Persistence + cache/sessions |
| **Hosting** | Vercel/Netlify (FE), Singapore (BE) | <30ms latency to Jakarta |
| **AI** | Phase 2 | Not required for MVP |
| **Cosmetics** | Phase 3 | Needs designer, Gacha possible |

---

## 🎯 Phase 1 MVP Feature Checklist

### Sprint 1: Foundation (Weeks 1-2)

#### Frontend Setup
- [ ] Initialize Vite + React + TypeScript project
- [ ] Configure Tailwind CSS with custom theme
- [ ] Setup Zustand store structure
- [ ] Setup TanStack Query
- [ ] Configure ESLint + Prettier
- [ ] Setup folder structure (components, hooks, stores, types, utils)

#### Game Assets
- [ ] Design/buy tile assets (Dots, Bamboo, Characters, Winds, Dragons)
- [ ] Create tile component (rendering, selection states)
- [ ] Design table background
- [ ] Create player avatar placeholders

#### TypeScript Types
- [ ] Define `MahjongTile`, `TileSuit`, `Wind`, `Dragon` types
- [ ] Define `Player`, `Meld`, `GameState` interfaces
- [ ] Define `GameAction` union type
- [ ] Define WebSocket message types

#### UI Layout
- [ ] Lobby screen (create/join room)
- [ ] Game table layout (4 player positions)
- [ ] Tile hand component (concealed tiles)
- [ ] Discard pile component
- [ ] Game controls (draw, discard, claim buttons)
- [ ] Turn timer UI

### Sprint 2: Game Logic (Weeks 3-4)

#### HK Rules Engine
- [ ] Implement tile generation (136 tiles)
- [ ] Implement shuffle/deal logic
- [ ] Implement valid hand detection (4 melds + 1 pair)
- [ ] Implement winning condition validation
- [ ] Implement HK scoring (fan calculation)
  - [ ] Pong/Pong hand (3 fan)
  - [ ] All Terminals & Honors (3 fan)
  - [ ] Seven Pairs (4 fan)
  - [ ] Pure Straight (1 fan)
  - [ ] Common Hand (1 fan)
- [ ] Implement turn rotation
- [ ] Implement wall tracking

#### Player Actions
- [ ] Draw tile action
- [ ] Discard tile action
- [ ] Claim tile (Pon) action
- [ ] Claim tile (Chi) action
- [ ] Claim tile (Kong) action
- [ ] Declare win action
- [ ] Pass action

#### Game State Management
- [ ] Zustand store for local game state
- [ ] Action validation (is this move legal?)
- [ ] Game history tracking (for replay)
- [ ] Turn timer logic (20s default)

### Sprint 3: Multiplayer (Weeks 5-6)

#### Backend Setup (Go)
- [ ] Initialize Go project structure
- [ ] Setup WebSocket server (Gorilla or native)
- [ ] Setup PostgreSQL connection
- [ ] Setup Redis connection
- [ ] Deploy to Singapore region (AWS/GCP)

#### Room Management
- [ ] Create room endpoint (6-digit code generation)
- [ ] Join room endpoint
- [ ] Leave room endpoint
- [ ] Room state in Redis
- [ ] Room expiry (auto-close inactive rooms)

#### WebSocket Protocol
- [ ] Define message schemas (JSON)
- [ ] Client → Server: DRAW, DISCARD, CLAIM, PASS, DECLARE_WIN, CHAT
- [ ] Server → Client: STATE_UPDATE, ACTION_CONFIRMED, ACTION_REJECTED, PLAYER_JOINED, PLAYER_LEFT, GAME_ENDED
- [ ] Message ordering with sequence numbers

#### Real-Time Sync
- [ ] Server-authoritative game state
- [ ] State broadcast to all players
- [ ] Client-side prediction for responsiveness
- [ ] Server reconciliation for authoritative truth

#### Reconnection Handling
- [ ] Detect WebSocket disconnect
- [ ] 30-second grace period
- [ ] Rejoin game with full state sync
- [ ] Handle mid-game reconnections

### Sprint 4: Polish & Monetization (Weeks 7-8)

#### Animations
- [ ] Tile draw animation (Framer Motion)
- [ ] Tile discard animation
- [ ] Pon/Chi/Kong claim animations
- [ ] Winning hand celebration
- [ ] Turn indicator animation

#### Social Features
- [ ] WhatsApp share integration (deep links)
- [ ] 6-digit room code sharing
- [ ] In-game emotes (10+ preset reactions)
- [ ] Lobby chat (WebSocket)
- [ ] Friend system (add/remove, online status)

#### Authentication
- [ ] Google Sign-In (Firebase Auth or custom)
- [ ] Guest play (3-game limit)
- [ ] Phone/WhatsApp OTP (Phase 1.5 if API available)
- [ ] JWT token management

#### Monetization
- [ ] Google AdMob integration (banner)
- [ ] Google AdMob integration (interstitial)
- [ ] Subscription checkout (Xendit/Midtrans for IDN payments)
- [ ] Premium feature gates (no ads, advanced stats)
- [ ] Revenue tracking

#### Localization
- [ ] i18n framework setup
- [ ] Bahasa Indonesia translations
- [ ] English translations
- [ ] RTL considerations (if needed)

### Sprint 5: Testing & Launch Prep (Weeks 9-10)

#### Testing
- [ ] Unit tests for rules engine
- [ ] Integration tests for WebSocket
- [ ] End-to-end tests for user flows
- [ ] Load testing (1,000 CCU target)
- [ ] Device testing (mobile browsers)

#### DevOps
- [ ] CI/CD pipeline (GitHub Actions)
- [ ] Monitoring (error tracking)
- [ ] Analytics (Amplitude/Mixpanel)
- [ ] Crash reporting (Sentry)

#### Beta Launch
- [ ] Internal testing (friends & family)
- [ ] Soft launch (Indonesia, small cohort)
- [ ] Feedback collection
- [ ] Bug fixes

#### Marketing Prep
- [ ] Landing page
- [ ] WhatsApp viral mechanics
- [ ] Influencer outreach list
- [ ] Facebook ad creatives

---

## ❌ Out of Scope (Phase 2+)

| Feature | Phase | Notes |
|---------|-------|-------|
| AI opponents | Phase 2 | Practice mode vs bots |
| Ranked/ELO system | Phase 2 | Competitive matchmaking |
| Cosmetics shop | Phase 3 | Requires designer |
| Gacha mechanics | Phase 3 | Legal review required |
| Tournament system | Phase 3 | Bracket management |
| Voice chat | Phase 3 | Infrastructure heavy |
| Multiple variants | Phase 3 | Riichi, American, etc. |
| Native mobile apps | Phase 3 | iOS/Android native |
| Spectator mode | Phase 3 | Watch live games |
| Hand replay/analysis | Phase 2 | Educational feature |
| Clubs/Communities | Phase 3 | Social groups |

---

## 🚀 Next Actions

1. **Review this roadmap** - Confirm sprint breakdown
2. **Setup repositories** - Frontend (React), Backend (Go)
3. **Create GitHub issues** - From sprint checklists above
4. **Assign team** - Who's building what?
5. **Set Sprint 1 start date** - When do we begin?

---

## 📚 Reference Documents

| Document | Description |
|----------|-------------|
| `PRD.md` | Full product requirements |
| `PRD_CODER_AGENT.md` | Technical specifications |
| `PRD_BUSINESS_AGENT.md` | Market strategy & KPIs |

---

*Last updated: March 23, 2026*
