# Morning Brief — Claude Code Context

This file gives any Claude instance full context to generate, push, and email the daily morning brief without needing the original conversation history.

---

## What This Project Is

A daily HTML intelligence briefing for **Marcio Herlein**, SAP Enterprise Risk Manager based in Buenos Aires. Covers markets, geopolitics, portfolio analysis, regulatory deadlines, and SAP intelligence. Published to GitHub at `github.com/marcioherlein/morning` and emailed to `marciofabrizio@gmail.com` (personal) and `marcio.herlein@sap.com` (SAP).

**Delivery:** 7:00 AM ART and 5:00 PM ART, weekdays.

---

## Portfolio

| Cluster | ~Weight | Key Tickers |
|---------|---------|-------------|
| 🇺🇸 US Equities | 30% | SPY, QQQ, DIA, NVDA, ARKK, TSLA |
| 🇧🇷 Brazil | 25% | NU, PBR, VALE, STNE, PAGS, BBD |
| 🇦🇷 Argentina | 20% | PAMP, TGSU2, EDN, METR, CEPU, VIST, YPFD, GGAL, BMA |
| 🏦 Fixed income | 12% | S16M6 Letes, FCI COCOSPPA, GD38, AL30, AO27 |
| 🌏 Asia | 8% | TSM, BABA, JD |
| 🛢️ Energy | 5% | VIST, PBR, LAR |

**Zero gold/commodity hedge — always flag this gap.**

**Key FX levels:** USD MEP/CCL brecha, USD/BRL R$5.10 (bull) / R$5.30 (stress), peso mayorista vs BCRA band ceiling ARS ~1,634.

---

## Markets to Cover

- **US:** S&P 500, Nasdaq, Dow, VIX, 10Y yield
- **Commodities:** Brent, WTI, Gold (flag zero exposure)
- **Argentina:** Merval, country risk (EMBI), USD MEP/CCL/blue, BCRA reserves
- **Brazil:** Ibovespa, USD/BRL, Selic (14.75%)

---

## Active Geopolitical Context (as of March 25, 2026)

### Iran War — War Day 26
- Feb 28: Operation Epic Fury launched. Khamenei killed. Hormuz effectively closed.
- Oil went from $60 → $119 peak → now ~$97 on ceasefire signals.
- Mar 23: Trump 5-day pause. "Very good and productive" talks announced. Oil −11%.
- Mar 25: US 15-point plan sent via Pakistan (nuclear dismantlement + proxy cessation + Hormuz). Vance + Rubio personally involved. Iran military mocks plan; FM silent.
- **5-day window expires ~March 28. Mediators: Oman, Pakistan, Turkey, Egypt.**
- Iran told UN "non-hostile vessels" may transit Hormuz with coordination — first crack.
- War still active: Israeli strikes continuing. Saudi intercepting Iranian drones.

**Portfolio impact:** VIST/YPFD/PBR = war winners (trim into ceasefire). SPY/QQQ recovering. Argentina country risk: 602 peak → 555 now, target sub-500.

### US Macro
- Fed holds 3.50–3.75%. Zero 2026 cuts projected by many FOMC members.
- Macquarie: next move is a HIKE (H1 2027).
- PPI Feb +0.7% (double consensus). 10% global tariff + 35–50% China threat.

### Argentina
- Merval ATH: 3,296,502 (Jan 28). Currently ~16% below.
- BCRA: 50+ consecutive buying sessions, $3.3B+ YTD, reserves ~$46B.
- Country risk: 602 peak → 555. Sub-500 = sovereign market re-access.
- Milei 10-reform agenda. AO27 licitación targeting $2B.
- Ecogás replaced Telecom Argentina in S&P Merval (March 23).

### Brazil
- Selic cut to 14.75% (March 18). First cut since May 2024.
- Ibovespa recovering. IPCA hot. BRL watch R$5.10–5.30.

---

## Active Regulatory Deadlines

| Framework | Deadline | Status |
|-----------|----------|--------|
| **EU AI Act HRAI** | Aug 2, 2026 | 🚨 PAST safe window. Expedited (3-month) process must start THIS WEEK. Joule HR/Finance = Annex III. €35M or 7% turnover. |
| **NIS2 Germany BSI** | ~Apr 2026 | 🚨 FINAL WINDOW (~1 week). €10M or 2% turnover. Management personally liable. |
| **DORA** | Live Jan 2026 | SAP as CTPP. Q1 audits. |
| **CRA** | CABs Jun 11 | SBOMs required. Reporting Sep 11. |

---

## SAP Intelligence Topics

Always include 4–5 of these, with red/amber/green priority signals:

1. **CCB pipeline** — Q4 2025 missed (16% vs 26%). Q1 late April = key test.
2. **EU AI Act / Joule** — 130 days, execution crisis.
3. **Gulf energy pipeline** — war froze deals; ceasefire = massive thaw.
4. **BofA $308 target** (+60% upside). SAP −29% past year. AI disruption "overstated."
5. **NVDA $1T backlog** (GTC 2026) — confirms AI buildout through 2027 → Joule pipeline.
6. **LATAM revenue** — BRL +3% Feb, Argentine energy capex expansion.
7. **SAP as CTPP under DORA** — Q1 audits intensifying.
8. **Macquarie hike call** — CFOs face higher financing costs, scrutinize SAP cloud deals.

---

## Design System

Header gradient changes with market regime:
- `#065f46 → #1e1b4b` = green (ceasefire/bullish)
- `#1e1b4b → #7f1d1d` = dark red (war/risk-off)
- `#1c3a5e → #1e1b4b` = navy (neutral/talks)

Always use the latest brief (`briefs/2026-03-25.html`) as the design template.

**Sections:** Header → Overview Alerts → Action Items (5) → Geopolitics (4–5) → Portfolio (factors + scenarios + recommendations) → Markets grid → Regulation → SAP Intelligence → Week Ahead → Footer.

---

## GitHub Workflow

```bash
DATE=$(date +%Y-%m-%d)
# 1. Save brief to briefs/$DATE.html
# 2. cp briefs/$DATE.html index.html
# 3. Update archive.html (add entry at top)
# 4. git add . && git commit -m "Brief $DATE · [headline]" && git push
```

Repo: `https://github.com/marcioherlein/morning`

---

## Email Delivery

```
Tool: gmail_create_draft
To: marciofabrizio@gmail.com
Content-Type: text/html
Subject: ☀️ Morning Brief · DD Mon YYYY · [headline]
```

---

## One-Shot Prompt for Claude Code

```
Read CONTEXT.md. Search for today's market data, Iran war update, Argentina, 
and Brazil. Generate a morning brief HTML matching the design in 
briefs/2026-03-25.html. Save to briefs/YYYY-MM-DD.html, update index.html 
and archive.html, git commit and push, then create a Gmail draft to 
marciofabrizio@gmail.com.
```
