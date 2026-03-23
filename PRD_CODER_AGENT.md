# Coder Agent Analysis: Multiplayer Mahjong Website

## Status: ✅ DECISIONS FINALIZED

This document reflects confirmed decisions from Product Owner (Adit) as of March 23, 2026.

---

## Confirmed Technical Decisions

### 1. Mahjong Variant: Hong Kong Old Style ✅

**Decision:** Hong Kong Old Style ONLY for Phase 1. Other variants deferred indefinitely.

**Technical Implications:**
- ✅ Simplest rules, fastest implementation
- ✅ 10-15 min game duration (perfect for mobile/web)
- ✅ Scoring based on "fan" system (3 fan minimum to win)
- ✅ No riichi declarations, furiten, or complex Japanese rules

**Key Rules to Implement:**
- 136 tiles (no flowers/seasons for MVP)
- 3 fan minimum to declare win
- Standard patterns: Pong/Pong hand (3 fan), All Terminals & Honors (3 fan), Seven Pairs (4 fan), Pure Straight (1 fan), Common Hand (1 fan)

### 2. Platform: Web-First with PWA ✅

**Decision:** Web-only for Phase 1, PWA installable. Native apps deferred.

**Stack Confirmed:**
| Layer | Technology |
|-------|------------|
| Frontend | React + TypeScript |
| Build | Vite |
| State | Zustand |
| API/Data | TanStack Query (React Query) |
| Styling | Tailwind CSS |
| Animations | Framer Motion |
| Icons | Lucide React |
| Backend | Go (Golang) |
| DB | PostgreSQL + Redis |
| Hosting | Vercel/Netlify (FE), Singapore region (BE) |

### 3. Audience & Geography: Indonesia First ✅

**Decision:** Phase 1 = Indonesia only. Phase 2 = SEA. Phase 3 = Global.

**Technical Implications:**
- Backend hosted in Singapore (AWS/GCP `ap-southeast-1`)
- Target latency: <30ms Jakarta → Server
- Localization: Bahasa Indonesia + English
- WhatsApp sharing integration (critical for IDN market)
- Local payment methods: GoPay, OVO, Dana, LinkAja

### 4. Authentication: Google + Phone/WhatsApp OTP ✅

**Decision:** 
- Primary: Google Sign-In
- Alternative: Phone/WhatsApp OTP
- Guest play: 3 games before registration required

### 5. AI Opponents: Phase 2 ✅

**Decision:** NO AI for MVP. Focus on real multiplayer first.

### 6. Monetization: Ads + Subscription ✅

**Decision:** NO gambling. NO cosmetics for Phase 1.

| Tier | Features |
|------|----------|
| Free | Unlimited play, ads (banner + interstitial) |
| Premium | No ads, advanced stats, priority support |

**Pricing:** Rp 29,000/month (~$1.90) for Indonesia market

### 7. Scalability: 1,000 CCU target ✅

**Decision:** Initial target 1,000 concurrent users. Horizontal scaling later.

---

## MVP Feature Set (Phase 1)

### Core Gameplay
- [ ] HK Ruleset: 3 fan minimum, standard HK scoring
- [ ] 4-player tables: Real-time multiplayer via WebSocket
- [ ] Private rooms: 6-digit code generation
- [ ] Turn timer: 20s per turn (host configurable)
- [ ] Game state sync: Server-authoritative with client prediction

### Social Features
- [ ] WhatsApp sharing: One-tap invite links
- [ ] In-game emotes: 10+ preset reactions
- [ ] Global chat: Lobby chat with moderation
- [ ] Friend system: Add players, see online status

### Authentication
- [ ] Google Sign-In (primary)
- [ ] Phone/WhatsApp OTP (alternative)
- [ ] Guest play (3-game limit)

### Monetization
- [ ] Google AdMob/AdSense integration
- [ ] Subscription: Remove ads + basic stats
- [ ] Local payment: GoPay, OVO, Dana, LinkAja

### Localization
- [ ] Bahasa Indonesia (full UI)
- [ ] English (fallback)
- [ ] Cultural emotes/chat phrases

### Technical Infrastructure
- [ ] PWA: Installable, offline detection
- [ ] Singapore backend: <30ms latency
- [ ] Reconnection: Resume dropped games
- [ ] Graceful degradation: Handle poor connections

### Out of Scope (Phase 2+)
- ❌ AI opponents
- ❌ Ranked/ELO system
- ❌ Cosmetics shop
- ❌ Tournament system
- ❌ Voice chat
- ❌ Multiple variants
- ❌ Native mobile apps

---

## Open Technical Questions for Implementation

### Game State Management
1. How granular should the game state be stored in Redis? (Every action vs periodic snapshots)
2. Replay system: JSON format for game logs? Storage cost estimate?

### Real-Time Communication
1. WebSocket library: Gorilla vs native Go websockets?
2. Message protocol: JSON vs binary (protobuf) for efficiency?
3. How to handle WebSocket reconnection with missed events?

### Database Design
1. Player stats: Aggregate in real-time or batch job?
2. Game history retention: 30 days? 90 days? Forever?
3. Leaderboards: Redis Sorted Sets vs PostgreSQL materialized views?

### Security & Anti-Cheat
1. Rate limiting: Actions per minute per player?
2. Collusion detection: IP tracking sufficient or need behavior analysis?
3. Input validation: How strict on client payloads?

### WhatsApp Integration
1. WhatsApp Business API or click-to-chat deep links?
2. Invite link format: 6-digit codes vs UUIDs?

### Ads
1. Frequency caps: Max 1 interstitial per 5 minutes?
2. Preroll ads or only post-game?

---

## Initial Architecture (Draft)

```
┌─────────────────────────────────────────────────────────────┐
│                        CLIENT                               │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │   React TS   │  │   Zustand    │  │ Framer Motion│      │
│  │   (Vite)     │──│  (Game State)│──│ (Animations) │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
│         │                                                   │
│    WebSocket / HTTP                                         │
└─────────┼───────────────────────────────────────────────────┘
          │
┌─────────┼───────────────────────────────────────────────────┐
│         ▼                                                   │
│  ┌────────────────────────────────────────────────────┐    │
│  │              LOAD BALANCER (AWS ALB)                │    │
│  └────────────────────┬───────────────────────────────┘    │
│                       │                                      │
│         ┌─────────────┼─────────────┐                       │
│         ▼             ▼             ▼                       │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐                │
│  │ Go API   │  │ Go API   │  │ Go API   │                │
│  │ Server 1 │  │ Server 2 │  │ Server N │                │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘                │
│       └─────────────┼─────────────┘                       │
│                     │                                      │
│  ┌──────────────────┼──────────────────┐                 │
│  │                  ▼                   │                 │
│  │  ┌──────────┐  ┌──────────┐  ┌───────┴──┐             │
│  │  │PostgreSQL│  │  Redis   │  │  Redis   │             │
│  │  │(Game DB) │  │(Session) │  │(Cache/WS)│             │
│  │  └──────────┘  └──────────┘  └──────────┘             │
│  │                                                       │
│  │           SINGAPORE REGION (ap-southeast-1)             │
│  └────────────────────────────────────────────────────────┘
```

---

## Implementation Priority

### Sprint 1: Foundation
- Project setup (Vite + React + TS)
- Basic UI layout (lobby, game table)
- Tile rendering system
- WebSocket connection

### Sprint 2: Game Logic
- HK rules engine
- Game state management
- Player actions (draw, discard, claim)
- Turn timer

### Sprint 3: Multiplayer
- Room creation/joining
- WhatsApp sharing
- Real-time sync
- Reconnection handling

### Sprint 4: Polish & Monetization
- Animations (Framer Motion)
- Ad integration
- Subscription flow
- Indonesian localization

---

*Last updated: March 23, 2026 by Coder Agent*
