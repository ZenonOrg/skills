---
name: marketing-content-generation
description: Generate narrative-driven marketing content for Zenon Network using 7 verified angles, adapted for target audience segments and platform requirements.
---

# Marketing Content Generation

Generate content aligned with the current directive and intelligence data.

---

## Phase 1: Read Latest Intelligence

Get the most recent intelligence summary:

```bash
probe message list #marketing-intelligence --limit 3
```

**Extract:**
- Current trigger score and level (LOW/MEDIUM/HIGH/FLYWHEEL)
- Active narrative window (what crypto is talking about right now)
- Key on-chain events (new Pillars, burns, bridge activity)
- Competitor positioning (what others are saying)

**Also check directive:**

```bash
probe message directives --limit 1
```

Content must align with the organizational directive.

---

## Phase 2: Select Best Narrative Angle

Choose from the 7 verified angles based on current conditions:

| Angle | Best When |
|-------|-----------|
| 1 — Research Commons | Bitcoin narrative dominant, academic audience |
| 2 — Community Treasury | DAO/governance trending, decentralization discourse |
| 3 — Active Anon Development | New GitHub commits detected, dev activity narrative |
| 4 — Yield Ecosystem | DeFi yields compressing, passive income trending |
| 5 — Supernova Bitcoin+EVM | Bitcoin L2 narrative, EVM builder discourse |
| 6 — Multi-chain Expansion | Cross-chain narrative, new chain deployments |
| 7 — AI Agent Identity | AI agent narrative, autonomous systems trending |

**Selection rules:**
- FLYWHEEL mode (new commit detected) → always Angle 3
- Match angle to the dominant narrative window
- Rotate angles — don't repeat the same angle within 48 hours
- Check what performed best recently via Nexus task history

---

## Phase 3: Generate Content

Create content adapted for the target platform and audience:

**Content types by platform:**

| Platform | Format | Length | Tone |
|----------|--------|--------|------|
| X/Twitter | Thread (3-7 tweets) | 280 chars each | Sharp, urgent, data-driven |
| Reddit | Long-form post | 500-1500 words | Educational, technical, thorough |
| Medium | Article | 1000-2500 words | Research-grade, cited sources |
| Telegram | Message | 200-500 words | Community-focused, actionable |
| Stacker News | Post | 500-1000 words | Bitcoin-native, technical |

**Content rules (non-negotiable):**
- Every piece must include FOMO (if/when framing): "If [catalyst] happens while you're watching from the sidelines..."
- Tokenomics described as mechanics, not promises
- No price predictions or investment advice
- Cite verifiable GitHub commits with dates and links
- Dev activity: go-zenon May 15 2025, Syrius May 28 2025, zenonhub Oct 22 2025
- Disclose community-funded via Accelerator-Z
- Tell the investigation journey, never reveal who built it

**FOMO framing examples:**
- "If Dynamic Plasma ships while wZNN is under $5M market cap..."
- "When the next Pillar is created, 150,000+ QSR are burned permanently. At what price point does that become headline news?"
- "4,320 ZNN distributed every day. The question is whether you're earning them or watching others earn them."

---

## Phase 4: Quality Check

Before submitting, verify:

- [ ] Aligns with current Nexus directive
- [ ] Uses correct, verifiable facts only
- [ ] Includes FOMO framing (if/when)
- [ ] No price predictions or guaranteed returns
- [ ] No real names of pseudonymous community members
- [ ] Appropriate tone for target platform
- [ ] Includes call-to-action (research links, Uniswap, bridge)
- [ ] Does not reveal automation or system architecture

---

## Phase 5: Submit as Nexus Deliverable

If this content was generated for a specific Nexus task:

```bash
probe task update <task-id> --status "in-review" --comment "Content generated:
Angle: [ANGLE_NUMBER] - [ANGLE_NAME]
Platform: [TARGET_PLATFORM]
Type: [CONTENT_TYPE]
Trigger Score: [SCORE]
---
[CONTENT BODY]"
```

If this is a proactive content piece, propose it as an idea:

```bash
probe idea propose \
  --title "Content: [ANGLE] for [PLATFORM] — [HOOK]" \
  --description "## Alignment
[How this aligns with directive]

## Content
[Full content body]

## Target
Platform: [PLATFORM]
Audience: [SEGMENT]
Angle: [NUMBER] — [NAME]

## Expected Impact
[Why this content matters right now]" \
  --category "marketing"
```

---

## Summary

Every content generation cycle:
1. Read latest intelligence (trigger score, narrative window)
2. Select best narrative angle (match to conditions)
3. Generate platform-adapted content (with FOMO framing)
4. Quality check (facts, tone, compliance)
5. Submit to Nexus (task deliverable or idea proposal)
