# Unlimit.pro — UI Prototypes (Low Fidelity)

A workspace of click-through, low-fidelity UI prototypes. All screens are
intentionally black & white wireframes — with a few special-case colors for
status (green / amber / red) — so flows can be reviewed without visual-design bias.

## Open the prototypes

Open `index.html` in any browser to use the launcher, or open a prototype directly.

| Project              | Path                                       | Status |
| -------------------- | ------------------------------------------ | ------ |
| Launcher (home)      | `index.html`                               | Live   |
| Wallet — picker      | `wallet/index.html`                        | Live   |
| Wallet · Web App     | `wallet/webapp/index.html`                 | Live   |
| Wallet · Extension   | `wallet/extension/index.html`              | Live   |
| Wallet · Mobile      | `wallet/mobile/index.html`                 | Live   |
| Intelligent System   | `intelligent-system/index.html`            | WIP    |

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
