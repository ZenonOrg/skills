---
name: marketing-intelligence
description: Collect real-time market data, monitor competitors, track narrative cycles, detect on-chain scarcity events for Zenon Network.
---

# Marketing Intelligence Collection

Execute this skill every heartbeat cycle to maintain fresh intelligence data.

---

## Phase 1: Check Nexus Inbox for Directives

Read any directives that should adjust intelligence collection priorities:

```bash
probe message directives --limit 3
```

**Parse carefully:**
- Has the organizational focus changed?
- Are there specific intelligence requests from ZOE?
- Should any monitoring targets be added or removed?

All collection must align with the current directive.

---

## Phase 2: Collect Market Data

Gather core price and volume data for wZNN across all chains:

**Primary sources:**
- DexScreener API: wZNN/ETH price, 24h volume, liquidity depth, price change (1h, 6h, 24h)
- CoinGecko API: BTC price, ETH price, total crypto market cap for context
- Etherscan API: wZNN holder count, new holders in 24h, large transfers

**Contract addresses:**
- Ethereum: `0xb2e96a63479c2edd2fd62b382c89d5ca79f572d3`
- Also check BNB Chain and Optimism deployments

**What to flag:**
- Volume spike > 2x 7-day average
- New holder count acceleration
- Large bridge inflows (> 100 ZNN in 24h)
- Whale wallet movements

---

## Phase 3: Monitor X for Zenon Mentions and Narrative Trends

Search for Zenon-related activity and dominant crypto narratives:

**Zenon-specific queries:**
- "Zenon ZNN wZNN" mentions in last 24 hours
- "@Zenon_Network" engagement metrics
- "Network of Momentum" discussions

**Narrative trend queries:**
- "Bitcoin SPV research crypto" — aligns with Angle 1
- "low-cap gems under $10M" — identifies potential audience
- "dominant crypto narrative right now" — timing intelligence
- "AI agents crypto" — aligns with Angle 7

**What to flag:**
- Any organic Zenon mention by accounts with > 5K followers
- Narrative windows opening (e.g., Bitcoin narrative surging = deploy Angle 1)
- Competitor momentum shifts

---

## Phase 4: Track Competitor Activity

Monitor comparable projects for positioning intelligence:

**Competitors:**
- Kaspa (KAS) — similar DAG architecture, similar market cap range
- Stacks (STX) — Bitcoin L2 positioning overlap
- RGB — Bitcoin smart contracts positioning overlap
- Ergo (ERG) — fair launch, research-heavy positioning overlap

**What to track:**
- New partnership announcements
- Exchange listings
- Developer activity spikes
- Content strategy shifts

---

## Phase 5: Detect On-Chain Scarcity Events

Monitor NoM chain for supply contraction signals:

**Via zenonhub.io API or RPC:**
- New Pillar created = 150,000+ QSR burned permanently
- New Sentinel deployed = 5,000 ZNN + 50,000 QSR locked
- Orbital LP deposits = ZNN/QSR locked 1-12 months
- Staking increases = ZNN locked in 30-day cycles
- Delegation changes = participation shifts

**Via GitHub API:**
- New commits on zenon-network/go-zenon or zenon-network/syrius
- New AZ proposals on forum.zenon.org
- Any commit = FLYWHEEL trigger (highest priority)

---

## Phase 6: Calculate Trigger Score and Report

Compute an aggregate trigger score (0-100):

| Signal | Points |
|--------|--------|
| Galaxy score > 70 | +30 |
| Volume rate of change > 50% | +25 |
| Bridge inflows > 100 ZNN/24h | +20 |
| New delegators > 3/24h | +15 |
| New Pillar created | +25 |
| BTC up > 5% in 24h | +15 |
| New GitHub commit detected | +50 (override) |
| New AZ proposal detected | +20 |

**Post intelligence summary to Nexus:**

```bash
probe message send #marketing-intelligence "Intelligence Summary [DATE]:
- wZNN: $[PRICE] ([CHANGE]% 24h) | Vol: $[VOL] | Holders: [COUNT]
- Trigger Score: [SCORE]/100 ([LEVEL])
- Narrative Window: [ACTIVE_NARRATIVE]
- On-Chain: [KEY_EVENTS]
- Competitors: [NOTABLE_MOVES]
- Recommendation: [ACTION_LEVEL]"
```

**If trigger score > 60:** Flag as HIGH priority in the message.
**If new GitHub commit:** Flag as FLYWHEEL — all channels should activate.

---

## Summary

Every intelligence cycle:
1. Check directives (align collection)
2. Collect market data (price, volume, holders)
3. Monitor X (mentions, narratives)
4. Track competitors (positioning shifts)
5. Detect on-chain events (scarcity signals)
6. Report summary to Nexus with trigger score
