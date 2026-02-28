# ⬡ 2048 TOKEN — Play & Earn on Bitcoin

> A fully on-chain Bitcoin gaming experience built on **OP_NET**. Play 2048, earn **2048 TOKEN**, and compete on the global leaderboard — all powered by an AI Agent via MCP.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Token Economics](#token-economics)
- [Supported Wallets](#supported-wallets)
- [AI Agent](#ai-agent)
- [Swap (Coming Soon)](#swap-coming-soon)
- [Leaderboard](#leaderboard)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Tech Stack](#tech-stack)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

**2048 TOKEN** is a browser-based Play-to-Earn game that fuses the classic 2048 puzzle with Bitcoin's OP_NET smart contract layer. Every move you make can earn you **2048 TOKEN** — a BRC-20-compatible token with a fixed supply of **10,000,000,000 (10 Billion)**.

The game features a built-in **AI Agent** powered by [Claude](https://www.anthropic.com) via the [OPNet MCP server](https://ai.opnet.org/mcp) that can analyze the board and suggest — or even auto-play — the optimal move in real time.

```
Play → Score Points → Earn 2048 TOKEN → Climb Leaderboard
```

---

## Features

### 🎮 Game
- Classic 4×4 2048 board with smooth tile animations
- Full keyboard support (Arrow Keys)
- Touch/swipe support for mobile
- On-screen arrow button controls
- Score tracking with personal best
- Move counter per session
- Tile milestone detection (128 → 2048)

### 🪙 Play-to-Earn
- Earn **2048 TOKEN** automatically as you score
- Milestone bonus rewards for reaching tile thresholds
- Session earnings tracked separately from total balance
- Real-time USD value estimate based on token price
- Floating earn effects for visual feedback

### 👛 Bitcoin Wallet Integration
- Auto-detect installed wallets
- Connect via **OP_WALLET** (primary / recommended)
- Support for UniSat, Xverse, OKX Wallet, and Leather
- BTC-native only — no EVM wallets
- Wallet address displayed in topbar after connecting

### 🤖 AI Agent (MCP-Powered)
- Real-time board analysis via Claude Sonnet
- Connects to `ai.opnet.org` MCP server
- Single move recommendation with reasoning (Bahasa Indonesia)
- Auto-play mode: AI moves automatically every ~2.4 seconds
- Offline heuristic fallback if MCP is unreachable

### 🏆 Leaderboard
- Global leaderboard with live player data
- Sort by: Best Score, Total Tokens, Weekly
- Your row auto-highlighted when wallet is connected
- Personal stats panel (Rank, Best Score, Total Tokens)

### ⇄ Swap *(Coming Soon)*
- **2048 TOKEN → PILL**
- **2048 TOKEN → MOTO**
- AMM liquidity pools
- Slippage control
- Cross-chain bridge
- LP token rewards
- Governance voting
- Join waitlist for early access

---

## Token Economics

| Property | Value |
|---|---|
| Token Name | 2048 TOKEN |
| Symbol | 2048 |
| Total Supply | 10,000,000,000 (10B) |
| Distribution Method | Play-to-Earn |
| Network | Bitcoin via OP_NET |
| Token Price (launch) | $0.0000024 |

### Earn Rate

| Action | Tokens Earned |
|---|---|
| Per 100 score points | +1 TOKEN |
| Reach Tile 128 | +50 BONUS |
| Reach Tile 256 | +150 BONUS |
| Reach Tile 512 | +400 BONUS |
| Reach Tile 1,024 | +1,000 BONUS |
| Reach Tile 2,048 🏆 | +5,000 BONUS |

> Milestone bonuses are awarded **once per game session** per tile threshold.

---

## Supported Wallets

All wallets are **Bitcoin-native**. No EVM/Ethereum wallets are supported.

| Wallet | Status | Detection |
|---|---|---|
| ⬡ **OP_WALLET** | ⭐ Recommended | `window.opnet` |
| 🟠 UniSat | Supported | `window.unisat` |
| ✦ Xverse | Supported | `window.btc_providers` |
| ⬤ OKX Wallet | Supported | `window.okxwallet.bitcoin` |
| 🟤 Leather | Supported | `window.LeatherProvider` |

### Installing OP_WALLET (Recommended)

OP_WALLET is the **official wallet for OP_NET** and gives you the best experience with 2048 TOKEN.

1. Install from [Chrome Web Store](https://chromewebstore.google.com/detail/opwallet/pmbjpcmaaladnfpacpmhmnfmpklgbdjb)
2. Create or import your Bitcoin wallet
3. Return to the game and click **Connect Wallet**
4. OP_WALLET will appear at the top as the recommended option

> The wallet modal auto-detects which wallets are installed and shows a **DETECTED** badge. Uninstalled wallets show a direct install link.

---

## AI Agent

The AI Agent is powered by **Claude Sonnet** (Anthropic) connected to the OP_NET MCP server at `https://ai.opnet.org/mcp`.

### How it works

1. When you press **⚡ AI Move**, the current board state and score are serialized
2. The state is sent to the Claude API with the OPNet MCP server attached
3. Claude analyzes the board and returns the optimal direction + reasoning in Bahasa Indonesia
4. The move is automatically executed after a short delay

### Auto Mode

Toggle **AUTO** to let the AI play continuously. The AI evaluates and moves every ~2.4 seconds. Great for farming tokens while AFK.

### Offline Fallback

If the MCP server is unreachable, the game falls back to a local heuristic:
- Evaluates all 4 directions
- Picks the move that maximizes empty cells × 20 + score gain
- Displays `[Offline]` in the AI panel

---

## Leaderboard

The leaderboard tracks all connected wallet players globally.

**Tabs:**
- **By Score** — ranked by highest single-game score
- **By Token** — ranked by total 2048 TOKEN accumulated
- **Weekly** — this week's top performers

Your row is highlighted in green and tagged with `[YOU]` when your wallet is connected and you have a score on the board.

> Leaderboard data auto-refreshes every 60 seconds. You must have a connected wallet to appear.

---

## Getting Started

### Prerequisites

- A modern browser (Chrome recommended)
- [OP_WALLET](https://chromewebstore.google.com/detail/opwallet/pmbjpcmaaladnfpacpmhmnfmpklgbdjb) or any supported BTC wallet extension

### Run Locally

```bash
# Clone the repository
git clone https://github.com/your-username/2048-token.git
cd 2048-token

# No build step required — it's a single HTML file
open 2048-web3.html
```

Or simply serve it with any static file server:

```bash
npx serve .
# then open http://localhost:3000/2048-web3.html
```

### Deploy

Since this is a single self-contained HTML file, you can deploy it anywhere:

```bash
# Netlify (drag & drop the HTML file at netlify.com/drop)

# GitHub Pages
cp 2048-web3.html index.html
git add index.html && git commit -m "deploy" && git push

# Vercel
vercel --prod
```

---

## Project Structure

```
2048-token/
├── 2048-web3.html      # Main application (single-file, self-contained)
└── README.md           # This file
```

The entire project is a single HTML file with embedded CSS and JavaScript — no dependencies, no build pipeline, no node_modules.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML, CSS, JavaScript |
| Fonts | Orbitron, DM Mono (Google Fonts) |
| Blockchain | Bitcoin via OP_NET |
| AI Agent | Claude Sonnet (Anthropic) |
| MCP Server | `https://ai.opnet.org/mcp` |
| Wallet APIs | OP_WALLET, UniSat, Xverse, OKX, Leather |
| Hosting | Any static file host |

---

## Roadmap

- [x] Core 2048 game engine
- [x] Play-to-Earn token mechanic
- [x] AI Agent with MCP integration
- [x] Bitcoin wallet connection (OP_WALLET, UniSat, Xverse, OKX, Leather)
- [x] Global leaderboard
- [ ] On-chain token minting via OP_NET smart contract
- [ ] Token swap: 2048 → PILL
- [ ] Token swap: 2048 → MOTO
- [ ] AMM liquidity pools
- [ ] Cross-chain bridge
- [ ] LP staking rewards
- [ ] Governance voting with 2048 TOKEN
- [ ] Mobile app (PWA)
- [ ] Multiplayer / battle mode
- [ ] Tournament system with prize pools

---

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

```bash
# Fork the repo and create your branch
git checkout -b feature/your-feature-name

# Make your changes to 2048-web3.html
# Test locally by opening in browser

# Commit and push
git commit -m "feat: your feature description"
git push origin feature/your-feature-name

# Open a Pull Request on GitHub
```

---

## License

MIT License — see [LICENSE](LICENSE) for details.

---

<div align="center">

Built on **Bitcoin** · Powered by **OP_NET** · AI by **Claude**

[Play Now](https://your-deploy-url.com) · [OP_WALLET](https://chromewebstore.google.com/detail/opwallet/pmbjpcmaaladnfpacpmhmnfmpklgbdjb) · [OPNet Docs](https://docs.opnet.org)

</div>