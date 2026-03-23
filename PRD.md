# Product Requirements Document: Multiplayer Mahjong Website

**Version:** 1.0  
**Date:** March 23, 2026  
**Status:** ✅ **DECISIONS FINALIZED - Phase 1: Indonesia Launch**  
**Stakeholders:** Adit (Product Owner)

---

## 1. Executive Summary

### Project Overview
A web-based multiplayer Mahjong platform enabling real-time competitive and social gameplay between players worldwide. The platform prioritizes accessibility, social connection, and authentic gameplay experience.

### Key Decisions (CONFIRMED)
**✅ CRITICAL DECISIONS FINALIZED:**

| Question | Decision | Notes |
|----------|----------|-------|
| **Mahjong Variant** | **Hong Kong (HK) Old Style** | Most straightforward; other variants deferred indefinitely |
| **Monetization** | **Ads + Subscription** (remove ads) | Cosmetics Phase 3; Gacha mechanics possible Phase 3; **NO gambling** |
| **Primary Audience** | **Social players** (all ages) | Indonesia → SEA → Global rollout |
| **Geographic Focus** | **Phase 1: Indonesia** → Phase 2: SEA → Phase 3: Global | WhatsApp integration critical for IDN |
| **AI Opponents** | **Phase 2** | Not required for MVP |

### Proposed Scope (Confirmed)
- **Phase 1 (Indonesia Focus):** HK Mahjong only, real-time 4-player, web-only, Ads + Subscription monetization, WhatsApp sharing, IDN/EN localization
- **Phase 2:** SEA expansion, AI opponents for practice
- **Phase 3:** Global launch, cosmetics/Gacha, tournament system

---

## 2. Problem Statement & Market Opportunity

### Problem Statement

**For Social Players:**
Physical Mahjong requires gathering 4 people in person - increasingly difficult with dispersed families and busy schedules. Existing digital options either:
- Are single-player only (Microsoft Mahjong)
- Have poor UX/UI (generic apps)
- Are too competitive/intimidating for casual play (Mahjong Soul)
- Require VPN/language skills for Asian-market apps

**For Competitive Players:**
Western markets lack quality competitive Mahjong platforms with:
- Fair matchmaking
- Anti-cheat systems
- Ranking systems
- English language support

### Market Opportunity

**Market Size Data:**
| Metric | Value | Source/Confidence |
|--------|-------|-------------------|
| Global Mahjong Market | $2-3B annually | Industry estimates (includes physical, digital, gambling) |
| Digital Mahjong Revenue | $500M+ | App store data, platform reports |
| Mahjong Soul Revenue | ~$100M/year | Estimated from Sensor Tower data |
| Global Search Volume | 1M+ monthly "mahjong" searches | Google Trends |

**Addressable Market Segments:**
1. **Chinese Diaspora (Western countries):** 5M+ potential users, underserved by quality apps
2. **Anime/Manga fans (Global):** Growing interest in Riichi Mahjong, estimated 2M+ interested players
3. **Social card game players:** Bridge/Poker players looking for variety, 10M+ overlap
4. **Seniors seeking social connection:** Rapidly growing demographic, high engagement

### Competitive Analysis

| Competitor | Strengths | Weaknesses | Our Opportunity |
|------------|-----------|------------|-----------------|
| **Mahjong Soul** | Beautiful anime aesthetic, strong IP, global reach | Intimidating for beginners, no social features, competitive-only | Social/casual positioning |
| **World Mahjong Club** | Massive Chinese user base, WeChat integration | Chinese language only, poor Western UX | English-speaking Chinese diaspora |
| **Microsoft Mahjong** | Brand recognition, free | Single-player only, not authentic | Multiplayer focus |
| **Tabletop Sim** | Generic platform flexibility | Complex setup, no matchmaking | Integrated experience |

**Market Gap Identified:** English-language social Mahjong platform that balances authenticity with accessibility.

---

## 3. Target User Personas

### Primary Persona: "Social Connector - Sarah"
- **Demographics:** 52, retired accountant, lives in California
- **Goals:** Play Mahjong with her sister in New York and friends from her old Mahjong club
- **Pain Points:** 
  - Hard to coordinate 4 people for in-person games
  - Existing apps too complicated or competitive
  - Wants voice chat to socialize while playing
- **Behaviors:** 
  - Plays 2-3 times per week
  - Prefers private tables with friends
  - Low tolerance for complex tutorials
  - Uses Facebook, FaceTime
- **Acquisition Channel:** Word of mouth, Facebook ads
- **Monetization:** Willing to pay for cosmetic table themes, not competitive about rankings

### Secondary Persona: "Competitive Player - Alex"
- **Demographics:** 28, software engineer, lives in London
- **Goals:** Learn Riichi Mahjong seriously, compete in tournaments, improve rank
- **Pain Points:
  - Can't find local players at his skill level
  - Mahjong Soul feels pay-to-win with gacha characters
  - Wants detailed statistics and hand analysis
- **Behaviors:** 
  - Plays daily, 1-2 hours
  - Studies strategy, watches Mahjong streams
  - Uses Discord, Reddit
  - Cares about ELO/rankings
- **Acquisition Channel:** Reddit r/Mahjong, YouTube, Discord
- **Monetization:** Willing to pay for premium analysis features, cosmetics that show status

### Tertiary Persona: "Curious Learner - Jordan"
- **Demographics:** 24, graduate student, anime fan
- **Goals:** Learn Mahjong because it looks interesting in anime/manga
- **Pain Points:** 
  - Rules seem overwhelming
  - Afraid of looking stupid in live games
  - Needs guided learning
- **Behaviors:** 
  - Plays sporadically
  - Needs extensive tutorials
  - Likely to churn if not supported
- **Acquisition Channel:** YouTube tutorials, app store search
- **Monetization:** Low, high churn risk unless properly onboarded

---

## 4. Core Features & Functionality

### MVP Features (Phase 1)

| Feature | Description | Acceptance Criteria | Priority |
|---------|-------------|---------------------|----------|
| **User Authentication** | Email/password, Google OAuth | Can register, login, logout, reset password | P0 |
| **Guest Play** | Limited play without registration | Can play 3 games before requiring registration | P1 |
| **Real-time Game** | 4-player synchronous game | <100ms latency, handles disconnections | P0 |
| **Matchmaking** | Find random opponents | Queue time <60s, skill-based matching | P0 |
| **Private Tables** | Create games with friends | Invite via link/code, password protected | P0 |
| **Game Rules Engine** | Validates legal moves | 100% rule compliance, no exploits | P0 |
| **Score Display** | Shows current scores, game history | Real-time updates, game log export | P0 |
| **Basic Chat** | Text chat in game | Messages synced with game state | P1 |
| **Tutorial** | Interactive rules learning | New users complete before first game | P1 |

### Phase 2 Features

| Feature | Description | Acceptance Criteria | Priority |
|---------|-------------|---------------------|----------|
| **Ranking System** | ELO-based skill rating | Fair rating changes, visible rank | P1 |
| **AI Practice** | Play against computer | 3 difficulty levels, rule-compliant AI | P2 |
| **Hand Replay** | Review past games | Step through decisions, share links | P2 |
| **Cosmetics Shop** | Avatar, tiles, tables | Purchase with credits, preview before buy | P1 |
| **Daily Rewards** | Login incentives | Progressive rewards, streak bonus | P2 |
| **Mobile PWA** | Installable web app | Offline support, push notifications | P2 |

### Phase 3 Features

| Feature | Description | Acceptance Criteria | Priority |
|---------|-------------|---------------------|----------|
| **Tournaments** | Bracket competitions | Registration, bracket management, prizes | P3 |
| **Spectator Mode** | Watch live games | Real-time viewing, chat with other viewers | P3 |
| **Clubs/Communities** | Player organizations | Create/join clubs, club leaderboards | P3 |
| **Voice Chat** | In-game voice | Push-to-talk, mute controls | P3 |
| **Multi-Variant** | Support multiple rule sets | HK, Riichi, etc. as separate modes | P3 |
| **Native Apps** | iOS/Android apps | Feature parity with web, app store presence | P3 |

---

## 5. Technical Architecture (CONFIRMED)

### Tech Stack (Final Decision)

| Layer | Technology | Rationale |
|-------|------------|-----------|
| **Frontend** | React + TypeScript | Type safety, component reusability |
| **Build Tool** | Vite | Faster dev/build vs CRA |
| **State Management** | Zustand | Lightweight, perfect for game state |
| **API/Data** | TanStack Query (React Query) | Sync with backend, caching |
| **Styling** | Tailwind CSS | Rapid UI dev, social menus |
| **Animations** | Framer Motion | Tile draw/discard/Pong/Chi effects |
| **Icons** | Lucide React | Clean, lightweight |
| **Backend** | Go (Golang) | Performance, concurrency |
| **Database** | PostgreSQL + Redis | Persistence + session/cache |
| **Hosting** | Vercel/Netlify (FE), Singapore region (BE) | Low latency for IDN users |

### TypeScript Game State Interface

```typescript
// Core tile definition for HK Mahjong
type TileSuit = 'Dots' | 'Bamboo' | 'Characters' | 'Winds' | 'Dragons';
type Wind = 'East' | 'South' | 'West' | 'North';
type Dragon = 'Red' | 'Green' | 'White';

interface MahjongTile {
  id: string;           // Unique instance ID
  suit: TileSuit;
  value: number;        // 1-9 for suits, 1-4 for winds
  name: string;         // Display name
}

interface Player {
  id: string;
  username: string;
  hand: MahjongTile[];      // Concealed tiles (13-14)
  exposed: Meld[];          // Called melds (Pon/Chi/Kong)
  windSeat: Wind;           // Current seat wind
  score: number;
  isReady: boolean;
  isDisconnected: boolean;
}

interface Meld {
  type: 'Pon' | 'Chi' | 'Kong' | 'ConcealedKong';
  tiles: MahjongTile[];
  claimedFrom?: string;     // Player ID if claimed discard
}

interface GameState {
  gameId: string;
  status: 'waiting' | 'playing' | 'paused' | 'finished';
  currentRound: number;     // 1-4 (East 1-4, South 1-4, etc.)
  prevailingWind: Wind;
  currentTurn: string;      // Player ID
  wall: MahjongTile[];      // Undrawn tiles
  deadWall: MahjongTile[];  // Reserved tiles (if needed for HK)
  discardPile: { tile: MahjongTile; playerId: string }[];
  players: Player[];
  lastAction?: GameAction;
  timerSeconds: number;     // Turn timer
}

type GameAction =
  | { type: 'DRAW'; playerId: string; tile: MahjongTile }
  | { type: 'DISCARD'; playerId: string; tile: MahjongTile }
  | { type: 'PON'; playerId: string; tiles: MahjongTile[]; fromPlayerId: string }
  | { type: 'CHI'; playerId: string; tiles: MahjongTile[]; fromPlayerId: string }
  | { type: 'KONG'; playerId: string; tiles: MahjongTile[] }
  | { type: 'WIN'; playerId: string; hand: MahjongTile[]; winningTile: MahjongTile; points: number };
```

### Scoring (HK Old Style)
- **Minimum:** 3 fan to win (or 1 fan depending on house rules)
- **Common Patterns:**
  - **Pong/Pong Hand:** All triplets (3 fan)
  - **All Terminals & Honors:** Only 1/9 suits + winds/dragons (3 fan)
  - **All Honors:** Only winds + dragons (huge fan)
  - **All Terminals:** Only 1/9 tiles (huge fan)
  - **Seven Pairs:** 7 pairs instead of 4 melds + pair (4 fan)
  - **Pure Straight:** 1-9 of same suit (1 fan)
  - **Mixed Straight:** 1-9 across suits (1 fan)
  - **Common Hand:** 4 chows + pair, no honors (1 fan)

### Infrastructure (Indonesia-Optimized)

| Component | Provider | Region | Notes |
|-----------|----------|--------|-------|
| Frontend | Vercel/Netlify | Global CDN | Edge caching |
| Backend API | AWS/GCP | Singapore (ap-southeast-1) | <30ms to Jakarta |
| WebSocket | Same as API | Singapore | Game state sync |
| Database | AWS RDS/GCP Cloud SQL | Singapore | Primary |
| Cache | Redis (ElastiCache/Memorystore) | Singapore | Sessions, game state |
| Media | Cloudflare R2/S3 | Global | Avatars, assets |

### Latency Targets (Indonesia)

| Metric | Target | Max |
|--------|--------|-----|
| Jakarta → Server | <30ms | 50ms |
| State broadcast | <100ms | 200ms |
| Reconnection | <2s | 5s |
| Matchmaking (IDN) | <15s | 30s |

### Game State Management

**Server-Authoritative Design:**
- All game logic runs on server
- Clients send "intent" ("I want to discard this tile")
- Server validates, updates state, broadcasts to all clients
- Prevents cheating, ensures consistency

**State Synchronization:**
- WebSocket for real-time updates
- Message ordering with sequence numbers
- Client-side prediction + server reconciliation for responsive feel
- Full state sync on reconnection

**Disconnection Handling:**
- 30-second grace period for reconnect
- AI takes over temporarily (optional)
- Game continues with 3 players if player doesn't return
- Forfeit after timeout

### Database Schema (High-Level)

```
users
├── id, email, username, created_at, last_login
├── stats: games_played, wins, losses, elo_rating
└── preferences: theme, avatar, notifications

games
├── id, status, variant, created_at, started_at, ended_at
├── players: [user_ids], scores
├── current_state: JSON (full game state)
└── history: [actions] (for replay)

tables
├── id, type (casual/ranked/private), status
├── host_user_id, max_players
└── settings: time_limit, ruleset_variant

matches
├── id, game_id, user_ids, status
├── started_at, ended_at
└── result: {winner_id, scores, game_log}
```

### Scalability Considerations

**Current Architecture Handles:**
- 1,000 concurrent games (~4,000 CCU)
- Single server + database
- Vertical scaling

**Scale Triggers for Architecture Change:**
- >5,000 CCU: Add game server sharding
- >50,000 CCU: Separate game servers from API, regional deployment
- >100,000 CCU: Custom game server (Go/C++), database partitioning

---

## 6. Game Mechanics & Rules

### ⚠️ VARIANT DECISION REQUIRED

**Option A: Japanese Riichi Mahjong**
- **Complexity:** HIGH
- **Game Duration:** 15-25 minutes
- **Target Market:** Competitive players, anime fans
- **Key Rules:** Riichi declaration, furiten, dora indicators, yaku scoring
- **Pros:** Popular globally, deep strategy, existing player education
- **Cons:** Steep learning curve, complex implementation

**Option B: Hong Kong Old Style**
- **Complexity:** MEDIUM
- **Game Duration:** 10-15 minutes
- **Target Market:** Chinese diaspora, casual players
- **Key Rules:** Faan scoring, simpler patterns, no riichi
- **Pros:** Faster games, easier to learn, less crowded market
- **Cons:** Smaller global audience

**Option C: Chinese Classical**
- **Complexity:** VERY HIGH
- **Game Duration:** 30-60 minutes
- **Target Market:** Traditional players
- **Key Rules:** Complex scoring, flower/season tiles, exhaustive draw
- **Pros:** Authentic traditional experience
- **Cons:** Very long games, complex implementation, limited appeal

**Recommendation (Pending User Input):**
- **For Social/Casual Focus:** Hong Kong Old Style
- **For Competitive Focus:** Japanese Riichi

### Core Game Loop (Generic)

```
1. TABLE CREATED
   └─ Host sets parameters (variant, time limit, public/private)

2. PLAYERS JOIN (1-4)
   └─ Wait for 4 players or AI fill

3. GAME START
   └─ Tiles shuffled and dealt
   └─ Each player gets 13 tiles

4. TURN LOOP
   ├─ Current player draws tile (14th)
   ├─ Check for win (Tsumo - self-draw)
   ├─ Player discards 1 tile
   ├─ Check for win (Ron - claim discard)
   ├─ Other players can claim discard (Pon, Chi, Kan)
   └─ Next player's turn

5. GAME END CONDITIONS
   ├─ Player wins (reaches winning hand)
   ├─ Exhaustive draw (no winner, wall empty)
   └─ Abortive draw (rare conditions)

6. SCORING
   └─ Calculate points based on hand value
   └─ Update player totals
   └─ Option to play another round
```

### Technical Validation Requirements

**Rules Engine Must Handle:**
- ✅ Tile distribution (136 tiles for standard)
- ✅ Valid hand detection (4 melds + 1 pair)
- ✅ Winning condition validation
- ✅ Scoring calculation (variant-specific)
- ✅ Illegal move prevention
- ✅ Turn timer enforcement
- ✅ Disconnection mid-hand

**Testing Requirements:**
- Unit tests for all rule combinations
- Edge case coverage (furiten, multiple winners, etc.)
- Performance: validate 1,000 hands/second minimum

---

## 7. Multiplayer & Real-Time Systems

### Communication Protocol

**WebSocket Architecture**
```
Client ↔ WebSocket Server ↔ Game Room Manager ↔ Game Logic Server
```

**Message Types:**
```typescript
// Client → Server
interface ClientMessage {
  type: 'DRAW' | 'DISCARD' | 'CLAIM' | 'PASS' | 'DECLARE_WIN' | 'CHAT';
  tableId: string;
  data: any;
  timestamp: number;
}

// Server → Client
interface ServerMessage {
  type: 'STATE_UPDATE' | 'ACTION_CONFIRMED' | 'ACTION_REJECTED' | 'PLAYER_JOINED' | 'PLAYER_LEFT' | 'GAME_ENDED' | 'CHAT';
  tableId: string;
  data: any;
  sequenceNumber: number;
}
```

### Latency Requirements

| Metric | Target | Maximum |
|--------|--------|---------|
| Input latency | <50ms | 100ms |
| State broadcast | <100ms | 200ms |
| Reconnection | <2s | 5s |
| Matchmaking | <30s | 60s |

**Mitigation Strategies:**
- Client-side prediction for immediate feedback
- Server reconciliation for authoritative truth
- Regional server deployment for Asia/Western players

### Disconnection Handling

**Scenario: Player disconnects mid-game**
1. Server detects WebSocket disconnect
2. 30-second grace period initiated
3. Other players notified: "Player disconnected - waiting to reconnect"
4. If reconnects: Resume from saved state
5. If timeout: AI takes over OR player auto-forfeits (configurable)

**State Persistence:**
- Game state saved to Redis every action
- Can restore from any point
- Prevents rage-quit exploits

### Anti-Cheat Measures

**Server-Authoritative:** All validation on server (prevents client hacks)

**Rate Limiting:**
- Max 10 actions/minute per player
- Exponential backoff on rejected actions

**Collusion Detection:**
- Track IP addresses of frequent playing partners
- Flag accounts with abnormal win rates together
- Manual review for suspected "soft play"

**Bot Detection:**
- CAPTCHA on suspicious patterns
- Behavior analysis (inhuman reaction times)
- Report system for players

---

## 8. User Flows & UX Considerations

### Primary User Flow: New Player Onboarding

```
Landing Page
    ↓
Sign Up (or Guest Play)
    ↓
Tutorial (Interactive)
    ├─ What is Mahjong?
    ├─ Tile types explanation
    ├─ Basic hand structure
    ├─ Turn flow demonstration
    └─ Practice hand vs AI
    ↓
First Real Game (Bot-assisted)
    ├─ Matched with other new players
    ├─ Hints available
    └─ No time pressure
    ↓
Post-Game
    ├─ "What could you have done better?"
    ├─ Option to add opponents as friends
    └─ Rate experience
```

**Success Metrics:**
- Tutorial completion rate: Target >70%
- First game completion: Target >80%
- D1 retention: Target >40%

### Primary User Flow: Social Player (Private Table)

```
Dashboard
    ↓
"Create Private Table"
    ├─ Select variant
    ├─ Set time limits
    └─ Generate invite code/link
    ↓
Share link (Copy/SMS/WhatsApp/Facebook)
    ↓
Friends join via link
    ↓
Game starts automatically when 4 ready
    ↓
Play with integrated chat
    ↓
Post-game lobby ("Play again?")
```

### Primary User Flow: Competitive Player (Ranked)

```
Dashboard
    ↓
"Ranked Match"
    ├─ Skill assessment (if first time)
    └─ Queue for opponent matching
    ↓
Match found → Accept/Decline
    ↓
Play game with timer
    ↓
ELO updates automatically
    ↓
View stats and progress
    ↓
Leaderboard check
```

### UX Principles

**Accessibility:**
- Color-blind friendly tile designs
- High contrast mode
- Adjustable font sizes
- Keyboard shortcuts for power users

**Mobile-First Design:**
- Touch-friendly tile selection
- Swipe gestures for common actions
- Responsive layout (works on phone/tablet/desktop)

**Performance:**
- First contentful paint <1.5s
- Time to interactive <3s
- 60fps animations during tile movements

**Localization:**
- i18n framework from day one
- Primary: English
- Phase 2: Simplified Chinese, Traditional Chinese, Japanese

---

## 9. Monetization Strategy (CONFIRMED)

### Revenue Model: Ads + Subscription

| Feature | Free Tier | Premium (Subscription) |
|---------|-----------|------------------------|
| **Play games** | Unlimited | Unlimited |
| **Private tables** | ✅ | ✅ |
| **Matchmaking** | ✅ | ✅ |
| **Ads** | Banner + Interstitial | **No ads** |
| **Cosmetics** | Basic only | Full access (Phase 3) |
| **Advanced stats** | Basic | Detailed analytics |
| **Priority support** | - | ✅ |

### Pricing (Indonesia-Adjusted)

| Market | Monthly | Annual (Discount) |
|--------|---------|-------------------|
| Indonesia | Rp 29,000 (~$1.90) | Rp 249,000 (~$16) |
| SEA/Global | $2.99 | $24.99 |

### Ad Strategy

| Placement | Frequency | Type |
|-----------|-----------|------|
| Post-match | Every 3 games | Interstitial (5s skip) |
| Menu screens | Always | Banner (bottom) |
| Waiting lobby | During queue | Native/native video |

**Rules:**
- ✅ Non-intrusive, skippable ads
- ✅ No ads during active gameplay
- ✅ Frequency capped (max 1 interstitial per 5 min)

### Phase 3 Expansion (Future)

| Feature | Description | Model |
|---------|-------------|-------|
| **Cosmetics** | Tile themes, table backgrounds, avatars, effects | Direct purchase |
| **Gacha** | Cosmetic loot boxes (if legal/regional) | Random draw |
| **Battle Pass** | Seasonal progression with rewards | One-time purchase |

**⚠️ STRICTLY PROHIBITED:**
- ❌ Real money wagering
- ❌ Gambling mechanics in core gameplay
- ❌ Pay-to-win advantages

---

## 10. Phase 1 MVP Features (Indonesia Launch)

### Core Gameplay
- [ ] **HK Ruleset:** 3 fan minimum, standard HK scoring
- [ ] **4-player tables:** Real-time multiplayer
- [ ] **Private rooms:** 6-digit code, password optional
- [ ] **Turn timer:** 20s per turn (configurable by host)

### Social Features
- [ ] **WhatsApp sharing:** One-tap invite to rooms
- [ ] **In-game emotes:** 10+ preset reactions (😂 🤔 🔥 etc.)
- [ ] **Global chat:** Lobby chat with moderation
- [ ] **Friend system:** Add players, see online status

### Authentication
- [ ] **Google Sign-In:** Primary method
- [ ] **Phone/WhatsApp OTP:** Alternative (if API available)
- [ ] **Guest play:** 3 games before registration required

### Monetization
- [ ] **Ad integration:** Banner + interstitial (Google AdMob/AdSense)
- [ ] **Subscription:** Remove ads + basic stats
- [ ] **Payment:** Local methods (GoPay, OVO, Dana, LinkAja)

### Localization
- [ ] **Bahasa Indonesia:** Full UI translation
- [ ] **English:** Fallback/default
- [ ] **Cultural:** Localized emotes, chat phrases

### Technical
- [ ] **Web-first:** PWA installable
- [ ] **Singapore backend:** <30ms latency to Jakarta
- [ ] **Offline detection:** Graceful handling
- [ ] **Reconnection:** Resume dropped games

### Out of Scope (Phase 2+)
- ❌ AI opponents
- ❌ Ranked/ELO system
- ❌ Cosmetics shop
- ❌ Tournament system
- ❌ Voice chat
- ❌ Multiple variants

---
- More complex pricing communication

**Estimated ARPU:** $10-25/year blended

---

**Option D: Tournament Fees (HIGH LEGAL RISK)**

- Entry fee: $1-5 per tournament
- Winner takes percentage of pot
- Platform takes 10-15% fee

**Pros:**
- High engagement
- Competitive appeal
- High ARPU per engaged user

**Cons:** 
- **GAMBLING REGULATIONS APPLY**
- Requires gambling licenses in most jurisdictions
- Age verification requirements
- Restricted advertising
- Apple/Google app store restrictions

**⚠️ LEGAL WARNING:** This model classifies as gambling in most jurisdictions and requires:
- Gambling licenses (cost: $100K-$1M+ per jurisdiction)
- Age verification systems
- Responsible gambling features
- Significant legal compliance costs

**Recommendation:** Do NOT pursue this model without legal counsel and significant budget.

---

### Final Recommendation

**Phase 1:** Option A (Cosmetics only)
**Phase 2:** Add Option B (Optional subscription for power users)
**Phase 3:** Evaluate tournament fees ONLY if legal framework allows

### Pricing Strategy

**Cosmetic Pricing:**
- Individual items: $0.99 - $4.99
- Bundles: $4.99 - $19.99
- Battle Pass/Season: $9.99 quarterly

**Value Proposition:**
- "Support the game, express yourself"
- No gameplay advantages
- Limited-time exclusives create urgency

---

## 10. Success Metrics (KPIs)

### North Star Metric
**Daily Active Players (DAP) in Active Games**
- Definition: Unique users who complete at least one game per day
- Target (Month 12): 10,000 DAP
- Target (Month 24): 50,000 DAP

### Input Metrics (Acquisition)

| Metric | Target M6 | Target M12 | Measurement |
|--------|-----------|------------|-------------|
| New signups/month | 5,000 | 15,000 | Registration events |
| Visitor-to-signup rate | >15% | >20% | Funnel analysis |
| CAC | <$2 | <$1.50 | Ad spend / new users |
| Organic traffic % | >30% | >50% | UTM attribution |

### Engagement Metrics

| Metric | Target | Industry Benchmark |
|--------|--------|-------------------|
| Games per DAU | >3 | 2-4 |
| Session length | >15 min | 10-20 min |
| DAU/MAU ratio | >25% | 15-25% |
| Tutorial completion | >70% | 50-60% |
| Table chat usage | >40% | N/A |

### Retention Metrics (Cohort Analysis)

| Retention | Target D7 | Target D30 |
|-----------|-----------|------------|
| Day 1 | >50% | - |
| Day 7 | >25% | >35% |
| Day 30 | >15% | >20% |

### Monetization Metrics

| Metric | Target | Notes |
|--------|--------|-------|
| Conversion rate | >3% | Free → Paid |
| ARPDAU | >$0.03 | Industry: $0.02-0.05 |
| LTV | >$15 | Must exceed CAC |
| Payback period | <6 months | LTV/CAC ratio |

### Quality Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| Crash rate | <0.1% | Error tracking |
| Bug reports/game | <0.01 | Support tickets |
| CSAT score | >4.0/5 | In-app survey |
| NPS | >40 | Quarterly survey |

---

## 11. Risk Analysis & Mitigation

### Technical Risks

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| **Real-time sync issues** | High | High | Extensive testing, fallback mechanisms, beta testing |
| **Scaling bottlenecks** | Medium | High | Load testing early, sharding strategy, caching layers |
| **Security vulnerabilities** | Medium | Critical | Security audit, bug bounty program, encryption |
| **Game logic bugs** | Medium | High | Comprehensive test suite, replay system for debugging |

### Business Risks

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| **Mahjong Soul dominance** | High | High | Clear differentiation, social focus, underserved niches |
| **Low user acquisition** | Medium | Critical | Content marketing, community building, low CAC channels |
| **Regulatory issues** | Medium | Critical | Avoid gambling features, legal review, age verification |
| **High churn** | Medium | High | Strong onboarding, social features, retention mechanics |
| **Monetization failure** | Medium | High | Diverse revenue streams, generous free tier |

### Market Risks

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| **Cultural barrier** | Medium | Medium | Education content, AI assistance, beginner-friendly design |
| **Platform policy changes** | Low | High | Web-first strategy, multiple distribution channels |
| **Economic downturn** | Medium | Medium | Conservative burn rate, focus on organic growth |

### Mitigation Strategies

**Technical:**
- MVP launch to limited beta (500 users) before scaling
- Automated testing for game logic
- Real-time monitoring and alerting
- Regular penetration testing

**Business:**
- Focus on underserved niches (social play, specific variants)
- Build community before product launch
- Diversify acquisition channels
- Maintain 12+ months runway

**Legal:**
- Legal review of all monetization features
- Clear terms of service
- Robust age verification if needed
- Geographic restrictions where required

---

## 12. Open Questions

### Critical Decisions (User Input Required)

1. **Mahjong Variant Selection**
   - Which variant should we prioritize?
   - Can we support multiple variants later?
   - Timeline constraints?

2. **Monetization Approach**
   - What's risk tolerance for gambling-adjacent features?
   - What's budget for legal compliance if needed?
   - Revenue targets and timeline?

3. **Primary Target Audience**
   - Social players, competitive, or learners?
   - Geographic focus?
   - Age demographic priority?

4. **Technical Constraints**
   - Preferred tech stack?
   - Team size and expertise?
   - Hosting budget?
   - Timeline pressure?

5. **Scope Decisions**
   - Is AI practice mode required for MVP?
   - Mobile app requirement or web-only for Phase 1?
   - Guest play required?

### Research Gaps

1. **Market Data:**
   - Exact market size for social Mahjong (vs competitive)
   - Willingness to pay for cosmetics in this demographic
   - Regional preferences (survey needed?)

2. **Competitive Intelligence:**
   - Detailed Mahjong Soul feature analysis
   - User sentiment analysis (Reddit, reviews)
   - Pricing sensitivity research

3. **Technical Validation:**
   - Performance benchmarks for chosen stack
   - WebSocket scalability testing
   - AI complexity assessment

### Assumptions to Validate

1. There is sufficient demand for social (vs competitive) Mahjong
2. Users will pay for cosmetics without gameplay advantages
3. Web-based platform can achieve mobile-app-like engagement
4. Hong Kong or Riichi variant has broad enough appeal
5. Discord/Reddit communities can drive organic growth

---

## 13. Appendix

### A. Legal Considerations

**Gambling Laws by Jurisdiction:**
- **United States:** Skill games generally legal, but varies by state. Social casino OK.
- **European Union:** Generally more permissive for skill games. GDPR compliance required.
- **China:** Strict gambling laws. ICP license required for hosting. Great Firewall considerations.
- **Japan:** Strict gambling laws. Social casino legal but regulated.
- **Singapore:** Gambling regulations strict. Social games generally OK.

**Recommendation:** Position as "skill game" not gambling. No real money wagering. Cosmetics only.

### B. Technical Glossary

- **CCU:** Concurrent users
- **ELO:** Rating system for player skill
- **Furiten:** Japanese Mahjong rule (can't win on discard if previously discarded winning tile)
- **Pon:** Claiming a discard to make triplet
- **Chi:** Claiming a discard to make sequence
- **Kan:** Four identical tiles
- **Tsumo:** Winning by self-draw
- **Ron:** Winning by claiming discard
- **Yaku:** Scoring elements in Japanese Mahjong
- **Faan:** Scoring unit in Hong Kong Mahjong

### C. Reference Resources

**Mahjong Rules:**
- World Mahjong Organization (Chinese)
- European Mahjong Association (Riichi)

**Technical:**
- Socket.io documentation
- WebSocket best practices
- Game server architecture patterns

**Competitive Analysis:**
- Mahjong Soul (yostar.com)
- Mahjong Time (mahjongtime.com)
- Tenhou (tenhou.net)

---

## Document Sign-off

**Prepared by:** Coder Agent & Business Analytics Agent  
**Date:** March 23, 2026  
**Status:** Awaiting user input on critical decisions  

**Next Steps:**
1. User review of critical decisions (Section 1)
2. Clarification questions answered
3. PRD finalized with confirmed decisions
4. Technical specification document created
5. UI/UX wireframes initiated

---

*This PRD is a living document. Decisions documented here should be revisited as new information becomes available.*
