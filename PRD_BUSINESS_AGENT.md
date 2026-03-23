# Business Analytics Agent Analysis: Multiplayer Mahjong Website

## Status: ✅ STRATEGY FINALIZED

This document reflects confirmed business decisions from Product Owner (Adit) as of March 23, 2026.

---

## Executive Summary

**Product:** Hong Kong Mahjong - Web-based multiplayer platform  
**Primary Market:** Indonesia (Phase 1) → SEA (Phase 2) → Global (Phase 3)  
**Target Audience:** Social players of all ages  
**Monetization:** Ads + Subscription (remove ads)  
**Timeline:** Quality-focused, no immediate pressure  

---

## Confirmed Strategic Decisions

### 1. Mahjong Variant: Hong Kong Old Style ✅

**Decision:** HK Old Style ONLY. Other variants deferred indefinitely.

**Rationale:**
- Simplest rules = fastest to implement
- 10-15 min games (perfect for mobile/web)
- Broader appeal than Riichi (less intimidating)
- Underserved market (Mahjong Soul dominates Riichi)

**Market Positioning:**
- Position as "accessible authentic Mahjong"
- Contrast with Mahjong Soul's competitive/anime focus
- Target: Social players, families, casual groups

### 2. Geographic Rollout: Indonesia First ✅

**Phase Plan:**
| Phase | Region | Focus | Timeline |
|-------|--------|-------|----------|
| 1 | Indonesia | Primary launch market | TBD |
| 2 | Southeast Asia | Thailand, Philippines, Malaysia, Singapore | After IDN validation |
| 3 | Global | Western markets, Chinese diaspora | Long-term |

**Why Indonesia First?**
- Large population (270M+)
- Growing digital economy
- Strong social gaming culture
- WhatsApp is ubiquitous (critical for viral sharing)
- Less saturated than Western markets
- Competitive but not dominated by Mahjong Soul

**Go-to-Market (Indonesia):**
- WhatsApp sharing integration (primary viral channel)
- Local payment: GoPay, OVO, Dana, LinkAja
- Bahasa Indonesia localization
- Influencer partnerships (local gaming YouTubers)
- Facebook/Instagram ads (cheaper CAC than West)

### 3. Target Audience: Social Players ✅

**Primary Persona: "The Social Connector"
- Age: 25-65 (broad)
- Goal: Play with friends/family remotely
- Behaviors:
  - Prefers private tables
  - Shares via WhatsApp
  - Casual, low competitive drive
  - Values emotes/chat
- Acquisition: Word of mouth, WhatsApp shares, Facebook
- Retention: HIGH (playing with friends)

**Secondary Persona: "The Casual Player"
- Age: 35-55
- Goal: Pass time, socialize
- Behaviors:
  - Short sessions
  - Drops in/out
  - Minimal learning curve tolerance
- Acquisition: App store, ads
- Retention: MEDIUM

**Not Targeting (for Phase 1):**
- ❌ Hardcore competitive players (let Mahjong Soul have them)
- ❌ Learners needing extensive tutorials
- ❌ Single-player preference

### 4. Monetization: Ads + Subscription ✅

**Model:** Freemium with ad removal subscription

| Tier | Price (IDN) | Features |
|------|-------------|----------|
| Free | Free | Unlimited play, ads (banner + interstitial) |
| Premium | Rp 29,000/mo (~$1.90) | No ads, advanced stats, priority support |

**Ad Strategy:**
- Placement: Post-match interstitial (every 3 games), banner in menus
- Frequency cap: Max 1 interstitial per 5 minutes
- Networks: Google AdMob (primary), local networks
- Rules: No ads during active gameplay

**Phase 3 Expansion:**
- Cosmetics shop (requires designer)
- Gacha mechanics (if legally viable)
- Battle Pass (seasonal)

**⚠️ STRICTLY AVOID:**
- ❌ Gambling mechanics
- ❌ Real money wagering
- ❌ Pay-to-win advantages

**Revenue Projections (Indonesia Market):**
- CAC target: <$0.50 (Facebook/WhatsApp organic boost)
- Conversion to Premium: 2-5%
- ARPU (blended): $3-8/year
- Target: 10,000 DAP Month 12, 50,000 DAP Month 24

### 5. Competitive Differentiation ✅

**vs. Mahjong Soul:**

| Dimension | Mahjong Soul | Our Product |
|-----------|--------------|-------------|
| **Variant** | Japanese Riichi | Hong Kong Old Style |
| **Focus** | Competitive, anime | Social, accessible |
| **Audience** | Hardcore, young | Casual, all ages |
| **Aesthetic** | Anime characters | Clean, simple, friendly |
| **Monetization** | Cosmetics gacha | Ads + sub (no gambling) |
| **Platform** | Mobile-first | Web-first (PWA) |
| **Geography** | Global | Indonesia → SEA → Global |

**Key Differentiators:**
1. **HK Rules** (not Riichi) - simpler, faster, less intimidating
2. **Social-first** - WhatsApp sharing, private rooms, emotes
3. **Web accessibility** - no download required
4. **Local focus** - Indonesian payments, language, culture
5. **Non-predatory monetization** - no gacha for Phase 1

### 6. Market Opportunity (Indonesia)

**Market Size:**
- Population: 270M+
- Internet users: 200M+
- Mobile-first gaming culture
- WhatsApp: 90%+ penetration
- Digital payments: Rapidly growing

**Competitive Landscape (IDN):**
- Mahjong Soul: Present but less dominant than in JP/CN
- Local competitors: Limited quality options
- Opportunity: First-mover advantage for HK variant

**Acquisition Strategy:**

| Channel | Approach | Budget Priority |
|---------|----------|---------------|
| WhatsApp Sharing | Viral invites (core feature) | $0 (organic) |
| Facebook/Instagram | Targeted ads, 35-65 demo | High |
| Influencers | Local gaming YouTubers | Medium |
| App Store | ASO for "mahjong", "remi" | Low (web-first) |
| Community | Facebook Groups, Discord | Low |

**Target CAC (Indonesia):** $0.30-0.50

### 7. Success Metrics (KPIs)

**North Star Metric:**
- Daily Active Players in Games (DAP)
- Target M6: 5,000 | M12: 10,000 | M24: 50,000

**Acquisition:**
| Metric | Target |
|--------|--------|
| Signup conversion (visitor → user) | >15% |
| WhatsApp share rate | >20% of private rooms |
| CAC | <$0.50 |

**Engagement:**
| Metric | Target |
|--------|--------|
| Games per DAU | >3 |
| Session length | >12 min |
| DAU/MAU ratio | >25% |
| Private table creation | >40% of games |

**Retention:**
| Metric | Target |
|--------|--------|
| D1 retention | >45% |
| D7 retention | >25% |
| D30 retention | >15% |

**Monetization:**
| Metric | Target |
|--------|--------|
| Premium conversion | >3% |
| ARPDAU | >$0.02 |
| Ad eCPM (IDN) | $1-3 |

### 8. Risk Analysis

**High Risk:**
| Risk | Likelihood | Mitigation |
|------|------------|------------|
| Mahjong Soul enters HK market | Medium | Build social moat first, local lock-in |
| Low WhatsApp virality | Medium | Fallback to other social channels |
| Ad rates collapse | Low | Subscription provides baseline |

**Medium Risk:**
| Risk | Likelihood | Mitigation |
|------|------------|------------|
| Indonesia regulations | Low | No gambling features, legal review |
| Localization gaps | Medium | Native speaker review, beta testing |
| Payment integration issues | Medium | Use established providers (Xendit, Midtrans) |

**Low Risk:**
- Technical failure (proven stack)
- Team execution (no timeline pressure)
- Market doesn't exist (Mahjong = universal in Asia)

---

## Open Business Questions

1. **Launch Timing:** Any seasonal considerations for Indonesia? (Ramadan, holidays?)
2. **Partnerships:** Any existing relationships with Indonesian influencers or gaming communities?
3. **Budget:** What's the total budget for Phase 1 (dev + marketing)?
4. **Legal:** Do we need local entity in Indonesia for payments?
5. **Support:** Customer support language (IDN/EN)?

---

## Summary: The Pitch

**"Hong Kong Mahjong for Indonesian Friends"**

A web-based multiplayer Mahjong platform focused on the Hong Kong variant - simpler and faster than Japanese Riichi. Built for social players who want to play with friends and family, not compete in tournaments.

**Why it wins:**
- WhatsApp-native sharing (viral growth)
- No download required (web-first)
- Local payments + language
- Accessible rules (HK vs intimidating Riichi)
- Fair monetization (no gambling, no predatory gacha)

**Next:** Build MVP → Beta test in Indonesia → Iterate → Scale to SEA

---

*Last updated: March 23, 2026 by Business Analytics Agent*
