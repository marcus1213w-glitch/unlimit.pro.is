# Unlimit.pro — UI Prototypes (Low Fidelity)

A workspace of click-through, low-fidelity UI prototypes. All screens are
intentionally black & white wireframes — with a few special-case colors for
status (green / amber / red) — so flows can be reviewed without visual-design bias.

> **Latest Release**: v2.1.0 (April 28, 2026) — Copy Trading feature, improved stats labeling, wallet connection gating

## Quick FAQ (v2.1.0 Updates)

### 1. How is versioning tracked? Where's the history?

All version history is documented in:
- **HTML Comments**: `intelligent-system/index.html` lines 1–40 contain a detailed changelog with dates, features, and breaking changes
- **CHANGELOG.md**: Full formatted changelog with sections for v2.1.0 (April 28), v2.0.0 (April 15), design principles, and roadmap
- **Version Badge**: Latest release version shown at top of this README

To view diff details, compare the HTML comments section or reference CHANGELOG.md for detailed feature changes.

### 2. Why does Copy Trading require both Pro subscription AND wallet connection?

**Strategic Reasoning:**
- **Pro subscription**: Copy trading is a premium feature with real-money implications; restricts access to paying customers
- **Wallet connection**: Trades execute directly to user's wallet; requires active custody control and security ownership
  - Protects both user (no custody required) and platform (accountability)
  - Prevents accidental trading without active wallet setup
  - Aligns with blockchain security best practices (user = wallet owner)

**UX Implementation:**
1. **Free tier users** → Upgrade modal (Pro plan, 14-day trial CTA)
2. **Pro tier, no wallet** → Connect wallet modal (security assurance: "Your private keys stay secure")
3. **Pro + wallet connected** → Full feature access

Wallet drawer shows context-aware CTA at every step, ensuring users always see the immediate next action.

### 3. What exactly is "Market Momentum" (formerly "Top 100 Gainers")?

**Definition:**
A market sentiment metric showing what percentage of the top 100 Solana tokens by market cap had positive 24h price change.

**In the Overview widget:**
- **Stat Value**: "61 / 100" (61 assets positive out of top 100)
- **Metric**: Average change across those 61 → "+3.2%"
- **Label**: "Market Momentum · 24h" (scoped to last 24 hours)

**Why renamed?**
- "Top 100 Gainers" implied a leaderboard of best performers
- "Market Momentum" better describes the metric: **market's directional strength** (bullish = many assets up, bearish = many down)
- Clarity: Ambiguous old name didn't signal the denominator (61 out of 100)

**Interpretation Guide:**
- **80%+ positive** → Strong bullish momentum (whales buying, retail following)
- **50–79%** → Mixed sentiment (sector rotation, selective buying)
- **<50%** → Bearish pressure (market-wide selling, flight to stablecoins)

**Uses:**
- Analysts cross-reference with "Active Alerts" to gauge news impact
- Traders check momentum before opening positions (high momentum = tailwind)
- Risk managers monitor for sudden reversals (80% to <50% = warning sign)

## Open the prototypes

Open `index.html` in any browser to use the launcher, or open a prototype directly.

**📋 See [CHANGELOG.md](CHANGELOG.md) for detailed version history and feature roadmap.**

| Project              | Path                                       | Status |
| -------------------- | ------------------------------------------ | ------ |
| Launcher (home)      | `index.html`                               | Live   |
| Wallet — picker      | `wallet/index.html`                        | Live   |
| Wallet · Web App     | `wallet/webapp/index.html`                 | Live   |
| Wallet · Extension   | `wallet/extension/index.html`              | Live   |
| Wallet · Mobile      | `wallet/mobile/index.html`                 | Live   |
| Intelligent System   | `intelligent-system/index.html`            | Live   |

## Unlimit.pro Wallet prototype

A self-custody crypto wallet wireframe across three surfaces, branded as **Unlimit.pro Wallet**. Inspired by
MetaMask, Phantom, Rabby, Trust Wallet, Rainbow, Coinbase Wallet, Zerion,
Argent and Ledger Live. Every screen and control is clickable.

### Shared features (all platforms)

- **Key management** — recovery phrase (BIP-39 12/24), private key, JSON keystore,
  hardware wallet (Ledger / Trezor / Keystone / GridPlus), watch-only addresses,
  Shamir backup, encrypted cloud backup (iCloud / Drive)
- **Multi-chain** — Ethereum, Polygon, Arbitrum, Optimism, Base, BNB, Solana,
  Bitcoin, plus custom RPC
- **Send / Receive / Swap / Bridge / Buy** — with QR, contacts, gas editor,
  slippage, MEV protection, route comparison, fiat on/off-ramp providers
- **Tokens & NFTs** — import, hide spam, multi-chain detection, NFT gallery,
  send / list / hide
- **DeFi & Earn** — Lido / Marinade staking, Aave / Compound lending,
  Uniswap LP, claim rewards
- **Approvals manager** — list active allowances with risk badges, revoke
  individually or in bulk
- **Security center** — health check, tx simulation (Blockaid-style),
  phishing & address-poisoning warnings, auto-lock, biometrics, privacy mode,
  Tor / private RPC, Smart Account (EIP-7702), gasless tx, Snaps
- **dApp connect** — featured list, WalletConnect (URI / QR), connected sites
  manager, signature requests, contract interaction with risk callouts
- **Activity** — all / pending / completed / failed, speed-up & cancel,
  CSV export, search
- **Onboarding** — welcome, terms, create password (biometric), seed reveal,
  seed confirm, success; plus full **Import** flow with private key, JSON,
  HW pairing & cloud restore
- **Lock / Unlock** — password + biometrics, forgot-password reset

### Per-platform highlights

**Web App** (`wallet/webapp/index.html`)
- Sidebar navigation, full-width portfolio dashboard
- Performance chart with timeframes, top assets table, position table
- WalletConnect QR pairing, large activity table with filters & export
- Approvals manager and security center as first-class pages

**Browser Extension** (`wallet/extension/index.html`)
- Mock Chrome window with tabs and URL bar; popup anchored to the toolbar icon
- Page buttons trigger dApp prompts into the popup:
  Connect Wallet · Sign Message · Confirm Transaction · Risky Approval
- Tx-confirm screen with simulation, risk callout (green / amber / red), and
  a dedicated risky-approval flow with destructive confirmation
- Expand-to-tab affordance, lock, full settings inside the popup

**Mobile** (`wallet/mobile/index.html`)
- Phone frame with notch, bottom nav (Home · Browser · Earn · Activity · Settings)
- Bottom-sheet pickers for networks / accounts / tokens / gas / sign / confirm
- In-app dApp browser with verified-site indicator
- QR scanner mock, push notifications center, Face ID unlock
- Biometric & cloud-encrypted backup, Shamir split option

### Color usage (special cases only)

- **Green** — confirmed / safe / OK
- **Amber** — pending / warning / non-default network (e.g. BSC)
- **Red**   — failed / destructive (Reset, Revoke, Risky tx)

Everything else is black, white and grayscale.

## Project structure

```
prototype/
├── index.html                       # Low-fi launcher
├── README.md                        # This file
├── intelligent-system/
│   └── index.html
└── wallet/
    ├── index.html                   # Platform picker (Web / Extension / Mobile)
    ├── lowfi.css                    # Shared low-fi component styles
    ├── webapp/index.html
    ├── extension/index.html
    └── mobile/index.html
```

## Tech notes

- No build step, no dependencies — just open the HTML files.
- Pure HTML + CSS + a small amount of inline JS for screen routing,
  modals / sheets / drawers.
- Each platform file is self-contained and only depends on `wallet/lowfi.css`
  for shared component styles.
- Designed for desktop and mobile widths (responsive).

## Unlimit.pro Intelligent System prototype

A Nansen/Dune/Glassnode-inspired analytics suite at `intelligent-system/index.html`.
Low-fidelity wireframe (white background, black/grey UI, emerald for positive PnL only).
Every control is clickable. **Solana-only chain.**

### Architecture — page-per-feature with shared drawers

```
Unauthenticated
  └─ Content: Welcome page (sign-in / create account CTAs only)
  └─ Sidebar: hidden

Authenticated
  └─ Sidebar: Overview · Top 100 Assets · Smart Money · Intelligence Feed · Settings
  └─ Content: routed by sidebar nav item
```

### Pages

| Sidebar item | Page | Description |
|---|---|---|
| 📊 Overview | `overview` | Condensed dashboard: stats bar + 4 mini-widgets |
| 💎 Top 100 Assets | `top100` | Sortable Solana token table (Rank/Price/24hChange/MCap) |
| ⚡ Smart Money | `smartMoney` | Full leaderboard + live signals panel |
| 📰 Intelligence Feed | `feed` | AI-enriched news grid (sort by impact or time) |
| 🔔 Signals | `signals` | All elite signals feed (filter BUY/SELL) |
| ⚙️ Settings | `settings` | Account · Billing · API Keys |

### Overview dashboard layout (Nansen-style widgets)

```
┌─ Stats bar ──────────────────────────────────────────────────────┐
│ Sentiment · Active Alerts · Elite Wallets · Verified Assets       │
└──────────────────────────────────────────────────────────────────┘
┌─ Top 100 widget ─────────┐  ┌─ Smart Money widget ──────────────┐
│ Top 5 tokens mini-table   │  │ Top 4 wallets mini-table           │
│ "View All Top 100 →"      │  │ "View Full Leaderboard →"          │
└───────────────────────────┘  └───────────────────────────────────┘
┌─ Intelligence Feed widget ┐  ┌─ Live Signals widget ─────────────┐
│ Top 3 high-impact cards   │  │ Latest 4 signals                   │
│ "View All News →"         │  │ "View All Signals →"               │
└───────────────────────────┘  └───────────────────────────────────┘
```

### Drawers (right slide-over, `Esc` or ✕ to close)

**Wallet Detail drawer** — opens from leaderboard row or wallet link in signals:
- Full Solana address (monospace) + 📋 Copy icon (read-only, no edit)
- Total Net Worth, Realized PnL, Unrealized PnL (split boxes)
- Top 3 Profitable Positions chips with emerald profit figures
- Transactions table with All / Inflow / Outflow tabs and hover-copy on every address
- Portfolio sidebar (token, price, 24h change, amount, USD value)

**News Detail drawer** — opens from any news card:
- Full headline, time, Rank badge, Impact score, Token chip
- Full article body (expanded from truncated preview)
- LLM Intelligence block with italicised `market_prediction`
- Sentiment, Emotion, "View Original Source ↗" button

### Flow map

```
Welcome (unauth)  ──Sign In──►  Overview
                                  ├─► Top 100 Assets (sortable: rank/price/change)
                                  ├─► Smart Money Leaderboard
                                  │     ├─ click row / signal wallet ──► Wallet Detail Drawer
                                  │     └─ "View All Signals →"        ──► Signals Page
                                  ├─► Intelligence Feed
                                  │     └─ click card                  ──► News Detail Drawer
                                  └─► Settings
```

### Design decisions vs previous version

| Item | Previous | Now |
|---|---|---|
| Unauthenticated home | Showed dashboard | Welcome page only |
| Navigation | Single "Dashboard" item | 4 dedicated nav items |
| Smart Money external links | Solscan / Birdeye / Helius badges | Removed (Solana-only badge shown instead) |
| Wallet txn detail | Had ✏️ Edit Label button | Read-only (button removed) |
| View All Signals | Toast notification | Full dedicated Signals page |
| News click | Toast notification | Right slide-over News Detail drawer |
| News feed ordering | Insertion order | Sorted by Impact score desc by default |
| Top 100 Assets | Not present | Full sortable table with real-time badge |



### Unified Command Center dashboard

All three features live on one page so analysts never lose context:

```
┌──────────────────────────────────────────────────────────────┐
│  Hero · Title  ·  [Overview | Smart Money | Intelligence Feed] │
├──────────────────────────────────────────────────────────────┤
│  Stats Bar  · Sentiment · Active Alerts · Elite Wallets · Verified Assets │
├──────────────────────────────────────────────────────────────┤
│  ⚡ SMART MONEY LEADERBOARD                       [search]      │
│  ┌──────────────────────────┐  ┌────────────────────────────┐  │
│  │ Sortable PnL/Win-Rate    │  │ ● Live Elite Signals (WS)  │  │
│  │ Click row → drawer →→→→ │  │ BUY/SELL stream            │  │
│  └──────────────────────────┘  └────────────────────────────┘  │
├──────────────────────────────────────────────────────────────┤
│  📰 INTELLIGENCE FEED                              [search]    │
│  Filters: All · Bullish · Bearish · High Impact                │
│  3-col grid of AI-enriched news cards                          │
└──────────────────────────────────────────────────────────────┘
                                                  ┌──────────┐
                            slide-over drawer →→  │ Wallet   │
                                                  │ Detail   │
                                                  └──────────┘
```

The top-right segmented control (`Overview / Smart Money / Intelligence Feed`)
either shows everything (Overview) or focuses on a single section while
smooth-scrolling it into view — a Dune-style dashboard pattern.

### Features

- **Top stats bar** — Market Sentiment (Fear & Greed Index), Active Alerts
  (high-impact stories with score > 7), Elite Wallets, Verified Assets
  (CoinGecko-validated tokens).
- **⚡ Smart Money Leaderboard**
  - Sortable table (toggle asc/desc on PnL or Win-Rate columns)
  - Wallet search filter (truncated or full address)
  - Win-rate bar visualization
  - External-link icon per row → Solscan/Birdeye toast
  - **Click any row** → opens the **Wallet Detail drawer** (slide-over panel)
- **🐋 Copy Trading (Pro + Wallet Connected)**
  - NEW in v2.1.0: Mirror trades from elite wallets in real time
  - Requires both Pro subscription AND connected Solana wallet
  - Per-wallet configuration: allocation per trade ($50–$1K or % of portfolio),
    daily budget cap, slippage tolerance (0.5%–5%), execution mode (Auto / Confirm)
  - Follow button on wallet drawer or Copy Trading page
  - Copy trade history with PnL tracking (BUY/SELL, amount, USD value, outcome)
  - Summary stats: Following count, Total Copied Trades, Copy PnL with win rate, Total Volume
  - Risk disclaimer at bottom
- **Live Elite Signals panel** — pulsing real-time indicator, BUY/SELL tags,
  wallet address (clickable → opens drawer for that wallet), token chip
  (clickable → toast for Birdeye), "Just now" timestamps. Note about
  "WebSocket push within 5s of block finalization" is shown inline.
- **🪟 Wallet Detail drawer** (right slide-over, `Esc` to close)
  - Full wallet address as primary monospace title
  - **Copy Address** (📋) and **Copy Trading CTA** (New v2.1.0)
    - Follow & Copy button if Pro + Wallet connected
    - Upgrade button if Free tier
    - Connect Wallet button if unconnected
  - Full-length address shown verbatim below for transparency
  - **External link badges**: Solscan · Birdeye · Helius
  - **Top 3 Profitable Positions** as token chips with profit highlighted
    in emerald (e.g., `SOL $12.4M`)
  - **Total Net Worth** displayed prominently
  - **PnL split**: clearly distinguishes **Realized** vs **Unrealized** PnL
  - **Transactions** with sub-tabs (All · Inflow · Outflow); hover-revealed
    clipboard icons on every from/to address; muted style for system
    destinations like `Stake Account`
  - **Portfolio** sidebar listing each token with price, 24h change,
    holdings amount and USD value
  - **Close** ✕ button in the top-right corner (also Esc)
- **📰 Intelligence Feed**
  - Responsive grid (1 / 2 / 3 columns)
  - Each card: CoinGecko **Rank badge**, time, **Impact score** badge with
    ⚡ Zap for high impact, line-clamped title & description
  - **LLM Intelligence** insight block with italicized `market_prediction`
  - **Sentiment** (Bullish / Bearish / Neutral) and **Emotion** labels with
    appropriate emphasis, plus a token chip for the related asset
  - **Search** by title or token symbol; filter pills
    **All · Bullish · Bearish · High Impact**
  - Hover state on cards and source link

### Updated v2.1.0 Flows

```
Sidebar: Dashboard (Overview)
   ├─ Stats Bar
   │   ├─ Market Sentiment (24h Fear & Greed Index + delta)
   │   ├─ Active Alerts (high-impact stories in 24h)
   │   ├─ Active Elite Wallets (traded in 24h vs total)
   │   └─ Market Momentum (% of top 100 positive in 24h)
   │
   ├─ Smart Money Table  ──────── click row ──────┐
   ├─ Live Signals       ──────── click wallet ──┤────► Wallet Detail Drawer
   │                                               │      (Esc / ✕ closes)
   │                                               │      ├─ Copy Trading CTA
   │                                               │      ├─ Portfolio
   │                                               │      └─ Txn History
   └─ Intelligence Feed  ───────► click card ──────┘──► News Detail Drawer

Sidebar: Copy Trading (Pro + Wallet Connected)
   ├─ Summary Stats (Following, Copied Trades, Copy PnL, Volume)
   ├─ Elite Wallets List
   │   ├─ Follow & Copy button (enabled)
   │   └─ Configuration (allocation, daily cap, slippage, mode)
   ├─ Copy Trade History (BUY/SELL, wallet, token, PnL, time)
   └─ Risk Disclaimer

Sidebar: Copy Trading (Free tier OR unconnected)
   └─ Gate page with upgrade/connect CTA

Sidebar: Settings  ──►  Billing · API Keys · Profile · Notifications
   ├─ Billing
   │   ├─ Plan management
   │   ├─ Subscription plans table
   │   └─ Billing history
   ├─ API Keys
   │   ├─ Create / revoke keys
   │   └─ Security: CORS & IP whitelist
   ├─ Profile
   │   ├─ Account info (username, email, avatar)
   │   ├─ Linked wallet (connect / disconnect)
   │   ├─ Current plan (upgrade / downgrade)
   │   └─ Account Actions (sign out)
   └─ Notifications
       ├─ 3 alert types (togglable)
       └─ 2 delivery channels (browser push, email digest)
```

### Flow

```
Sidebar: Dashboard (default)
   │
   ├─ Smart Money table  ─ click row ────────┐
   ├─ Live Signals       ─ click wallet ────┤────► Wallet Detail Drawer
   │                                         │      (Esc / ✕ closes)
   └─ Intelligence Feed  ─ search / filter / open card → toast (source)

Sidebar: Settings  ─►  Account · Billing · API Keys (existing)
```
