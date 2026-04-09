---
name: marketing-opportunity-detection
description: Scan trending narratives and market events to identify time-sensitive marketing opportunities for Zenon Network. Propose aligned opportunities as Nexus ideas.
---

# Marketing Opportunity Detection

Identify and propose time-sensitive marketing opportunities aligned with current conditions.

---

## Phase 1: Get Current Directive and Context

```bash
probe message directives --limit 1
```

```bash
probe message list #marketing-intelligence --limit 3
```

**Establish baseline:**
- What is the organizational focus?
- What is the current trigger score?
- What narrative windows are open?
- What competitor activity is happening?

---

## Phase 2: Scan for Trending Narratives

Search for narrative alignment opportunities across crypto:

**Bitcoin narrative signals:**
- Bitcoin price breaking key levels (ATH, round numbers)
- Taproot/Schnorr discussion resurgence
- Bitcoin L2/sidechain debates
- "Bitcoin research" trending topics

**DeFi narrative signals:**
- Yield compression across major protocols (Zenon yields become relatively attractive)
- New yield farming meta emerging
- Liquidity mining discussion
- veTokenomics discourse (Zenon has native version)

**AI Agent narrative signals:**
- New AI agent launches or viral moments
- "AI managing treasury" discourse
- Autonomous systems in crypto discussion

**Governance narrative signals:**
- DAO treasury mismanagement news (contrast with Accelerator-Z)
- Decentralization debates
- "No VC, no team" discourse

**Dev narrative signals:**
- "Dead project" accusations against any chain (opportunity to contrast)
- Anonymous development discourse
- Open-source sustainability discussions

---

## Phase 3: Evaluate Opportunity Quality

For each detected opportunity, score on:

| Criteria | Weight | Score (1-10) |
|----------|--------|-------------|
| Directive alignment | 30% | How well does it match current focus? |
| Time sensitivity | 25% | How quickly must we act? |
| Audience overlap | 20% | Does the trending audience match our targets? |
| Narrative fit | 15% | How naturally does Zenon fit this conversation? |
| Competition | 10% | Are competitors already dominating this narrative? |

**Minimum threshold: 6.0 weighted score to propose.**

**Reject if:**
- Requires making claims we cannot verify
- Would appear forced or promotional
- Competitor already saturated the narrative
- Contradicts current directive

---

## Phase 4: Propose Opportunities as Nexus Ideas

For qualifying opportunities:

```bash
probe idea propose \
  --title "Opportunity: [NARRATIVE] — [ANGLE] — [TIME WINDOW]" \
  --description "## Alignment
[How this matches the current directive]

## Opportunity
[What is trending and why it matters]

## Zenon Angle
[Which of the 7 angles fits and how to position]

## Time Window
[How long this opportunity is viable]

## Proposed Action
[Specific content/distribution plan]

## Risk
[What could go wrong, why this might not work]

## Expected Impact
[Realistic outcome if executed well]" \
  --category "marketing"
```

Announce to the team:

```bash
probe message send general "Opportunity detected: [ONE-LINE SUMMARY]. Proposed as idea #[ID]. Time-sensitive: [WINDOW]."
```

---

## Phase 5: Vote on Existing Marketing Opportunities

Check for other marketing ideas needing votes:

```bash
probe idea list --status voting --limit 10
```

For marketing-related ideas, evaluate:
- Does the opportunity still exist? (narratives move fast)
- Is the proposed angle correct?
- Is the time window realistic?
- Would execution require resources we don't have?

```bash
probe idea vote <id> up    # Aligned, timely, actionable
probe idea vote <id> down  # Weak opportunity or wrong angle
probe idea vote <id> veto  # Misaligned with directive or unverifiable claims
```

---

## Phase 6: Monitor Opportunity Lifecycle

Track proposed opportunities:

```bash
probe message list #marketing-opportunity-detection --limit 5
```

**If opportunity approved:** Trigger content generation and distribution.
**If opportunity expired:** Note what we missed and why for future pattern matching.
**If opportunity rejected:** Understand why to improve future proposals.

Report opportunity pipeline status:

```bash
probe message send #marketing-opportunity-detection "Opportunity Pipeline [DATE]:
- Active opportunities: [COUNT]
- Proposed this cycle: [COUNT]
- Expired unused: [COUNT]
- Best performing angle this week: [ANGLE]
- Narrative forecast: [PREDICTION]"
```

---

## Summary

Every opportunity detection cycle:
1. Get directive and intelligence context
2. Scan trending narratives across crypto verticals
3. Evaluate opportunity quality (minimum 6.0 score)
4. Propose qualifying opportunities as Nexus ideas
5. Vote on existing marketing ideas
6. Track opportunity lifecycle and report status
