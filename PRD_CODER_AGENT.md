# Coder Agent Analysis: Multiplayer Mahjong Website

## Introduction
I'm the Coder Agent focused on technical feasibility, architecture decisions, and implementation constraints.

## Critical Clarifying Questions

### 1. Mahjong Variant Selection
**Question:** Which Mahjong variant should we prioritize?

**Technical Implications:**
- **Hong Kong Old Style:** Simplest rules, fastest games (~10-15 min), easiest to implement
- **Japanese Riichi:** Most complex (riichi declarations, furiten rules, dora indicators), requires sophisticated validation
- **Chinese Classical:** Traditional rules, longer games, more scoring complexity
- **American Mahjong:** Uses Jokers, Charleston phase, very different tile set

**My Recommendation:** Start with Hong Kong Old Style - it has the simplest rule set while still being authentic, making MVP delivery faster and debugging easier.

### 2. Real-Time vs Async Architecture
**Question:** Real-time synchronous play only, or async option?

**Technical Implications:**
- **Synchronous:** Requires WebSocket infrastructure, presence management, reconnection handling
- **Async:** Can use polling/HTTP, simpler state machine, longer game sessions (hours/days)
- **Hybrid:** Most complex but flexible

**Concerns:**
- Async Mahjong loses the "social" aspect that makes the game engaging
- Real-time requires handling network latency, disconnections, rejoining mid-game
- Turn timer handling (what happens when a player AFKs?)

### 3. Platform Strategy
**Question:** Web-only or mobile app required?

**Technical Implications:**
- **Web-only:** Faster MVP, single codebase, instant deployment, but limited offline support
- **PWA:** Good middle ground, offline support, push notifications
- **Native apps:** Best UX, app store distribution, but 3x development cost

**My Recommendation:** Start web-only with PWA features for mobile-like experience.

### 4. Authentication Strategy
**Question:** Guest play vs registered users only?

**Technical Implications:**
- Guest play reduces friction but creates challenges:
  - ELO/ranking systems need persistent identity
  - Report/ban systems need identity
  - Progression systems don't work
- Registered-only ensures accountability but increases drop-off

**My Recommendation:** Guest play allowed but with heavy limitations (no ranked, limited tables), must convert to register for full features.

### 5. AI Opponents
**Question:** Include AI for practice/single-player?

**Technical Implications:**
- Mahjong AI is computationally expensive (hidden information, probabilistic decisions)
- Simple rule-based AI is doable but won't be challenging
- Strong AI requires ML/neural networks (Mahjong Soul uses deep learning)
- Resource requirements for AI inference

**Concerns:**
- Do we have ML expertise?
- What's the compute budget?
- Is single-player mode a priority or nice-to-have?

### 6. Ranking & Competitive Systems
**Question:** Ranking/ELO system? Tournaments?

**Technical Implications:**
- **ELO:** Requires matchmaking algorithms, rating calculations, decay systems
- **Tournaments:** Complex bracket management, registration systems, prize distribution
- **Leaderboards:** Database query optimization for real-time updates

**Open Questions:**
- Is this competitive or social-focused?
- How serious is the ranking system?
- What about smurf detection and boosting prevention?

### 7. Gambling & Legal Considerations
**Question:** In-game currency? Real money gambling?

**CRITICAL LEGAL CONCERNS:**
- **Real money gambling:** Requires gambling licenses ( varies by jurisdiction)
- **Social casino model:** Common in Asia, legal gray area in many Western markets
- **Free-to-play with cosmetics:** Safest legally, but lower monetization

**My Strong Recommendation:** Avoid real money gambling entirely. Use cosmetic monetization only. Gambling compliance is extremely complex.

### 8. Scalability Requirements
**Question:** Expected concurrent user load?

**Technical Implications:**
- 100 CCU vs 10,000 CCU vs 100,000 CCU = completely different architectures
- Table state needs to be synchronized across servers
- WebSocket connection pooling and load balancing
- Database write patterns (game logs, player stats)

### 9. Regional Considerations
**Question:** Target regions/markets?

**Technical Implications:**
- Latency requirements (Asia vs Western players on same server?)
- Localization (Chinese text, RTL considerations)
- Data residency laws (GDPR, etc.)
- CDN strategy

### 10. Existing Technical Constraints
**Question:** Any existing team preferences or constraints?

- Preferred tech stack?
- Existing infrastructure?
- Budget constraints for hosting?
- DevOps maturity?

## Technical Architecture Concerns

### Game State Management
- Must be server-authoritative (prevent cheating)
- Game state serialization for crash recovery
- Replay system for dispute resolution
- Handling disconnections gracefully

### Real-Time Communication
- WebSocket vs WebRTC vs SSE?
- Message ordering guarantees
- Handling network partitions
- Reconnection storm protection

### Database Design
- Player profiles and stats
- Game history and replay data
- Leaderboards (materialized views?)
- Real-time vs batch analytics

### Security Concerns
- Bot detection
- Collusion detection (players communicating outside game)
- Rate limiting on table creation
- Input validation for all game actions

## Initial Architecture Recommendation (Subject to Clarification)

**Stack:**
- Backend: Node.js with TypeScript + Socket.io (WebSocket abstraction)
- Frontend: React with TypeScript
- Database: PostgreSQL (game state), Redis (session/cache/leaderboards)
- Hosting: Vercel/Netlify (frontend), Railway/Render (backend) for MVP

**Why:**
- Fastest time to market
- Good ecosystem for real-time games
- Scales reasonably well to moderate loads
- TypeScript reduces bugs in game logic

## Open Technical Questions
1. What's the budget for infrastructure?
2. What's the timeline for MVP?
3. Do we need replay functionality?
4. How do we handle table chat?
5. What about spectator mode?
6. Anti-cheat requirements?
