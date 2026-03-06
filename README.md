# 🧴 SkinIQ Market Pulse — OpenClaw Skill

> **An autonomous cosmeceutical market intelligence agent built with OpenClaw.**
> Runs on your machine 24/7, fetches live market signals from the web, and
> delivers structured intelligence reports to your phone via Telegram or WhatsApp.

---

## 📌 What This Is

SkinIQ Market Pulse is a custom **OpenClaw skill** — part of the SkinIQ portfolio project.

It demonstrates:
- **Agentic AI architecture** using OpenClaw as the autonomous agent backbone
- **Real-time web intelligence** gathering via OpenClaw's built-in web search tools
- **Structured prompt engineering** for consistent, business-grade report output
- **Scheduled automation** via OpenClaw's heartbeat + cron system
- **Domain expertise** in Bangladesh's cosmeceutical & FMCG market

Built as a practical demonstration of how AI automation can replace manual
competitor monitoring for a marketing or strategy team.

---

## 🎯 Use Case

A marketing or strategy professional at an FMCG/cosmeceutical company typically
spends 1–2 hours per week manually scanning news, competitor websites, and
industry reports. This skill automates that entirely — delivering a structured
intelligence brief every morning before work begins.

**Target sector:** Bangladesh cosmeceutical & skincare market
**Inspired by:** Bio-Xin Cosmeceuticals' operating environment

---

## 🏗️ Architecture

```
User / Cron Trigger
        │
        ▼
┌─────────────────────┐
│   OpenClaw Gateway  │  ← Runs locally (or on VPS), always on
│   (Node.js daemon)  │
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│  SkinIQ SKILL.md    │  ← Skill instructions loaded into agent context
│  (This repo)        │
└────────┬────────────┘
         │
    4 web searches
         │
         ▼
┌─────────────────────┐
│  Anthropic Claude   │  ← Synthesises signals → structured report
│  (via API)          │
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│  Telegram / WhatsApp│  ← Report delivered to your phone
└─────────────────────┘
```

---

## 📊 Sample Output

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━
🧴 SKINIQ MARKET PULSE
07 Mar 2026 | Daily Pulse
━━━━━━━━━━━━━━━━━━━━━━━━━━━

📊 MARKET SIGNALS (Top 3)
1. Niacinamide demand surge in BD market — Google Trends — 34% YoY search
   increase signals rising consumer awareness of brightening ingredients
2. Square Toiletries expanding skincare SKUs — Daily Star — Direct competitive
   pressure on mid-tier cosmeceutical positioning
3. New Bangladesh FDA import guidelines for cosmetics — BFDA circular —
   Compliance window opens opportunity for premium positioning

🔬 TREND WATCH
• Ingredient: Tranexamic Acid gaining traction as niacinamide alternative
• Behaviour: Gen Z BD consumers cross-referencing products on TikTok pre-purchase
• Regulatory: BFDA tightening labelling requirements Q2 2026

🏆 COMPETITOR RADAR
• Himalaya BD — Launched 3-SKU "Urban Defense" line — Targeting pollution-
  conscious urban segment, direct overlap with SPF/antioxidant category
• Garnier BD — 15% price drop on serum range — Defensive move vs local brands

💡 STRATEGIC INSIGHT
The convergence of rising ingredient literacy among Dhaka's urban consumers
and tightening BFDA labelling standards creates a window for brands that lead
with clinical transparency. Cosmeceutical positioning (science-backed claims +
dermatologist endorsement) is the highest-defensibility strategy in this
environment. First-mover advantage in compliant clinical marketing is significant.

📈 CONFIDENCE: High
Sources: [google.com/trends] [thedailystar.net] [bfda.gov.bd] [statista.com]
━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## ⚙️ Installation

### Prerequisites
- OpenClaw installed and configured (`npm install -g openclaw@latest`)
- Anthropic API key configured in OpenClaw
- At least one messaging channel connected (Telegram recommended)
- Node.js v22+

### Install the Skill

```bash
# Option 1: Clone directly into your OpenClaw skills folder
git clone https://github.com/yourusername/skiniq-market-pulse ~/.openclaw/skills/skiniq-market-pulse

# Option 2: Manual install
mkdir -p ~/.openclaw/skills/skiniq-market-pulse
cp SKILL.md ~/.openclaw/skills/skiniq-market-pulse/
```

### Verify Installation
```bash
openclaw skills list
# Should show: skiniq-market-pulse 🧴
```

### Run It
Message your OpenClaw agent (via Telegram/WhatsApp):
```
run market pulse
```

---

## ⏰ Set Up Daily Automated Reports

Add to your `~/.openclaw/workspace/HEARTBEAT.md`:
```markdown
- [ ] Daily SkinIQ Market Pulse: Run skiniq-market-pulse Daily Pulse
      every day at 08:00 local time. Deliver to Telegram.
```

OpenClaw's heartbeat system will trigger this automatically every morning.

---

## 🔒 Security Notes

- This skill only uses **read-only** web search tools — no write permissions
- No external API keys required beyond your existing Anthropic key
- Review the full `SKILL.md` before installing (best practice for any skill)
- Recommend running OpenClaw with tool allowlists configured

---

## 🗂️ Repository Structure

```
skiniq-market-pulse/
├── SKILL.md              # Main skill definition (OpenClaw reads this)
├── README.md             # This file
├── references/
│   └── bd-skincare-context.md   # Market context reference for the agent
└── examples/
    └── sample-report.md         # Example output for documentation
```

---

## 🚀 Part of the SkinIQ Portfolio

This skill is **Project Component 1** of the SkinIQ portfolio — a suite of
AI-powered tools demonstrating marketing analytics + AI automation capabilities
for the FMCG/cosmeceutical sector.

| Component | Description | Stack |
|-----------|-------------|-------|
| **Market Pulse** (this) | Autonomous intelligence gathering | OpenClaw + Claude API |
| **SkinIQ Dashboard** | Interactive market analytics | Python + Streamlit |
| **CampaignOS** | AI campaign planner | Claude API + Streamlit |
| **SalesPulse** | Sales performance analytics | Python + Plotly |

🔗 **Live Portfolio:** [your-github-pages-url]
📺 **Loom Walkthrough:** [your-loom-link]

---

## 👤 Author

**Osman Goni Akash**
Bachelor of Business Information Systems (Business Analytics)
Swinburne University of Technology, Melbourne, Australia

[LinkedIn](https://linkedin.com/in/yourprofile) · [Portfolio](https://yourusername.github.io)
