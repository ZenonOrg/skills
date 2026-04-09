---
name: marketing-distribution
description: Deploy approved marketing content across X, Reddit, Medium, Telegram, and other channels. Track engagement metrics and report performance back to Nexus.
---

# Marketing Distribution

Deploy approved content and track its performance.

---

## Phase 1: Get Approved Content from Nexus

Check for tasks with approved content ready for distribution:

```bash
probe task ready --limit 5
```

Filter for tasks tagged with `marketing`, `content`, or `distribution`.

Also check for direct distribution requests:

```bash
probe message list #marketing-distribution --limit 5
```

**Only distribute content that has been approved** through the Nexus idea/task pipeline. Never distribute draft content.

---

## Phase 2: Deploy to Target Platforms

Deploy content to the appropriate channels based on the content type and angle:

### X/Twitter
- Post thread via Buffer API (scheduled with timing jitter)
- Add timing jitter: +/- 30% of scheduled time to avoid automation fingerprinting
- Vary writing style slightly from other platforms
- Include relevant hashtags: #ZNN #Zenon #DeFi #Bitcoin (max 3)
- Tag @Zenon_Network only when directly relevant
- Rate limit: maximum 5 posts per day

### Reddit
- Post to relevant subreddits: r/CryptoTechnology, r/defi, r/altcoin, r/CryptoMoonShots
- Match subreddit rules exactly (many ban promotional content)
- Use educational framing — never promotional
- Engage with comments for 24 hours post-deployment
- Rate limit: maximum 2 posts per day per subreddit

### Medium
- Publish via zenonaliencommons or dedicated publication
- SEO-optimize title and first paragraph
- Include canonical links to zenon.network, zenon.org
- Cross-post to Mirror.xyz for on-chain permanence

### Telegram
- Post to community channels
- Use concise formatting with key data points
- Include direct links (bridge, Uniswap, Syrius download)

### Stacker News / HackerNews / BitcoinTalk
- Adapt Bitcoin-adjacent content (Angle 1, 5)
- Technical depth required — no fluff
- Engage with discussion threads

### Conversation Insertion
- Find existing discussions matching our narrative angles
- Reply with genuine value — not promotional spam
- Link to research/data when adding to discussion

---

## Phase 3: Track Engagement

After deployment, monitor performance metrics:

**Per-platform metrics:**
- X: impressions, likes, retweets, replies, link clicks
- Reddit: upvotes, comments, save rate
- Medium: views, reads, read ratio, claps
- Telegram: views, forwards, reactions

**Cross-platform metrics:**
- Total reach (sum of impressions)
- Engagement rate (interactions / impressions)
- Click-through rate (link clicks / impressions)
- Volume correlation (did wZNN volume change after content?)

---

## Phase 4: Report Performance to Nexus

Post distribution results:

```bash
probe message send #marketing-distribution "Distribution Report [DATE]:
- Platform: [PLATFORM]
- Content: [ANGLE] — [TITLE/HOOK]
- Reach: [IMPRESSIONS]
- Engagement: [RATE]%
- Link Clicks: [COUNT]
- Volume Correlation: [CORRELATION]
- Status: [PERFORMING/UNDERPERFORMING/VIRAL]"
```

If content is performing well (engagement > 2x baseline):

```bash
probe message send #marketing-intelligence "SIGNAL: Content performing well on [PLATFORM]. Angle [N] resonating. Consider doubling down."
```

Update the task status:

```bash
probe task update <task-id> --status "completed" --comment "Distributed to [PLATFORMS]. Engagement: [SUMMARY]"
```

---

## Phase 5: Learn and Adapt

Track which angles and platforms perform best:

**Weekly analysis:**
- Which angle generated most engagement?
- Which platform drove most link clicks?
- What time of day performed best?
- Did any content correlate with volume increases?

Feed learnings back to content generation via Nexus messaging:

```bash
probe message send #marketing-content-generation "Performance insight: Angle [N] on [PLATFORM] outperformed by [X]%. Recommend increasing [ANGLE] frequency."
```

---

## Summary

Every distribution cycle:
1. Get approved content from Nexus tasks
2. Deploy to target platforms (with timing jitter)
3. Track engagement metrics per platform
4. Report performance to Nexus
5. Feed learnings back to content generation
