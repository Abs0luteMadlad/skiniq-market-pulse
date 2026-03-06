---
name: skiniq-market-pulse
description: >
  Use this skill when the user asks to: "run market pulse", "skincare report",
  "cosmeceutical news", "what's trending in beauty", "Bangladesh skincare market",
  "competitor analysis", "beauty market brief", or any request for skincare/cosmeceutical
  industry intelligence. Fetches live market signals, competitor activity, and
  trend data from the web, then produces a structured intelligence report.
version: 1.0.0
metadata:
  openclaw:
    emoji: "🧴"
    requires:
      env:
        - ANTHROPIC_API_KEY
      bins:
        - curl
    primaryEnv: ANTHROPIC_API_KEY
    alwaysOn: false
---

# SkinIQ Market Pulse 🧴

**Purpose:** Autonomous cosmeceutical market intelligence agent. Runs on demand
or on a cron schedule. Fetches real signals from the web, synthesises them into
a structured brief, and delivers it via the configured channel (Telegram/WhatsApp).

Built by Osman Goni Akash as part of the SkinIQ portfolio project.
Target domain: Bangladesh cosmeceutical & skincare market.

---

## Workflow

### Step 1 — Define the scope
Determine which of the following report types is being requested:
- **Daily Pulse** — quick 5-point brief of today's top signals
- **Weekly Deep Dive** — full competitor + trend analysis
- **Product Launch Radar** — new product launches in BD skincare market
- **Competitor Snapshot** — focused analysis on a named brand

If no type specified, default to **Daily Pulse**.

### Step 2 — Fetch live market signals
Use the web search tool to gather fresh data across these 4 signal categories.
Run all 4 searches. Do not skip any.

**Signal 1 — Bangladesh skincare market news (last 7 days)**
Search query: `Bangladesh skincare cosmeceutical market 2026`
Extract: brand launches, pricing moves, distribution news, regulatory updates.

**Signal 2 — Global cosmeceutical trend signals**
Search query: `cosmeceutical skincare trends 2026 Asia`
Extract: ingredient trends, technology innovations, consumer behaviour shifts.

**Signal 3 — Competitor activity (Bio-Xin + local peers)**
Search query: `Bio-Xin cosmeceuticals Bangladesh OR "skincare Bangladesh" new product launch`
Extract: new SKUs, campaigns, pricing, channel expansions.

**Signal 4 — Social/consumer sentiment**
Search query: `Bangladesh skincare beauty consumer demand 2026`
Extract: trending ingredients, price sensitivity signals, channel preferences.

### Step 3 — Structure the report
Produce the report in this exact format. Do not deviate from it.

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━
🧴 SKINIQ MARKET PULSE
[DATE] | [REPORT TYPE]
━━━━━━━━━━━━━━━━━━━━━━━━━━━

📊 MARKET SIGNALS (Top 3)
1. [Signal — Source — Why it matters]
2. [Signal — Source — Why it matters]
3. [Signal — Source — Why it matters]

🔬 TREND WATCH
• [1 emerging ingredient or technology trend]
• [1 consumer behaviour shift]
• [1 regulatory or compliance note if relevant]

🏆 COMPETITOR RADAR
• [Brand] — [Activity observed] — [Strategic implication]
• [Brand] — [Activity observed] — [Strategic implication]

💡 STRATEGIC INSIGHT
[2-3 sentences. What does this mean for a cosmeceutical brand
operating in the Bangladesh market right now? Be specific,
not generic. Frame as an actionable opportunity.]

📈 CONFIDENCE: [High / Medium / Low]
Sources: [list URLs used, max 4]
━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Step 4 — Deliver
Send the completed report through the active channel.
If running on heartbeat/cron, append:
`⏰ Scheduled pulse — next run: [next scheduled time]`

---

## Cron / Heartbeat Configuration

To run this skill automatically every morning at 8 AM, add to your
`HEARTBEAT.md` in the OpenClaw workspace:

```
- [ ] Daily SkinIQ Market Pulse: Run skiniq-market-pulse Daily Pulse
      every day at 08:00 local time. Deliver to Telegram.
```

---

## Error Handling

- If web search returns no results for a query: note "No fresh signals found"
  for that category and continue with the remaining categories.
- If fewer than 2 signal categories return results: flag as LOW CONFIDENCE
  and recommend the user re-run later.
- Never fabricate signals. If data is stale or unavailable, say so explicitly.

---

## Examples

**User says:** "run market pulse"
→ Execute Daily Pulse. All 4 searches. Full report. Deliver to channel.

**User says:** "give me a Bio-Xin competitor snapshot"
→ Execute Competitor Snapshot. Focus Signal 3 on Bio-Xin specifically.
  Expand competitor radar section to 5 entries.

**User says:** "what's trending in Dhaka skincare?"
→ Execute Daily Pulse with emphasis on Signal 4 (consumer sentiment).
  Lead the report with Trend Watch section instead of Market Signals.
