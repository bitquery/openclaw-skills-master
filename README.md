# OpenClaw Skills

This repository contains OpenClaw agent skills that you can install from [ClawHub](https://clawhub.ai/) (the public skill registry for OpenClaw).

## Skills in this repo

ClawHub listings:

| `clawhub install` | ClawHub listing | Description |
|-------------------|-----------------|-------------|
| **bitcoin-price-feed** | [bitquery-crypto-price-stream](https://clawhub.ai/divyn/bitquery-crypto-price-stream) | Real-time streaming Bitcoin price feed over WebSocket: OHLC ticks, volume, and derived metrics (moving averages, % change) from the Bitquery API. |
| **crypto-chart-usd** | [crypto-chart-usd](https://clawhub.ai/divyn/crypto-chart-usd) | Real-time streaming multi-token crypto chart feed with 1-second OHLC ticks and USD pricing: OHLC, volume (Base/Quote/USD), and moving averages from the Bitquery Trading.Tokens API. |
| **pumpfun-usd-price-stream** | [pumpfun-usd-price-stream](https://clawhub.ai/divyn/pumpfun-usd-price-stream) | Real-time streaming PumpFun token feed on Solana with live USD pricing: OHLC, volume, moving averages, and tick-to-tick % change from the Bitquery API. |
| **polymarket-real-time-trades** | [polymarket-real-time-trades](https://clawhub.ai/divyn/polymarket-real-time-trades) | Real-time streaming Polymarket prediction trades on Polygon (matic): outcome trades, buyer/seller, collateral in USD, market question, outcome labels, and transaction details from the Bitquery API. |
| **stablecoin-payments** | [solana-stablecoin-payments-tracking](https://clawhub.ai/divyn/solana-stablecoin-payments-tracking) | Real-time streaming Solana SPL USDC and USDT transfers over WebSocket (mint filter; excludes program methods containing "swap"), with amounts, USD values, sender/receiver, block time/slot, transaction signature/fees, and program method from Bitquery. |

### Source directories (this repo)

| `clawhub install` | ClawHub listing | Folder |
|-------------------|-----------------|--------|
| `bitcoin-price-feed` | [bitquery-crypto-price-stream](https://clawhub.ai/divyn/bitquery-crypto-price-stream) | [`bitquery-bitcoin-price-skill/`](bitquery-bitcoin-price-skill/) · [`SKILL.md`](bitquery-bitcoin-price-skill/SKILL.md) |
| `crypto-chart-usd` | [crypto-chart-usd](https://clawhub.ai/divyn/crypto-chart-usd) | [`crypto-chart-usd-skill/`](crypto-chart-usd-skill/) · [`SKILL.md`](crypto-chart-usd-skill/SKILL.md) |
| `pumpfun-usd-price-stream` | [pumpfun-usd-price-stream](https://clawhub.ai/divyn/pumpfun-usd-price-stream) | [`pumpfun-skill/`](pumpfun-skill/) · [`SKILL.md`](pumpfun-skill/SKILL.md) |
| `polymarket-real-time-trades` | [polymarket-real-time-trades](https://clawhub.ai/divyn/polymarket-real-time-trades) | [`polymarket-skill/`](polymarket-skill/) · [`SKILL.md`](polymarket-skill/SKILL.md) |
| `stablecoin-payments` | [solana-stablecoin-payments-tracking](https://clawhub.ai/divyn/solana-stablecoin-payments-tracking) | [`stablecoin-payments-skill/`](stablecoin-payments-skill/) · [`SKILL.md`](stablecoin-payments-skill/SKILL.md) |

---

## Prerequisites

- **OpenClaw** (ClawHub CLI is included with OpenClaw), or install the ClawHub CLI alone
- **Node.js** 18.0 or higher (for ClawHub CLI)
- **Git** (for ClawHub authentication when publishing)
- **Python 3** and **pip** (required to run the streaming scripts used by these skills)

---

## Install the ClawHub CLI

If you don’t have OpenClaw yet, install OpenClaw (which includes ClawHub):

```bash
# macOS / Linux
curl -sSL https://openclaw.ai/install | bash

# Verify
openclaw --version
clawhub --version
```

Or install only the ClawHub CLI:

```bash
npm i -g clawhub
# or
pnpm add -g clawhub
```

---

## Install skills from ClawHub

### 1. (Optional) Log in to ClawHub

Login is optional for installing public skills but needed for publishing and some features:

```bash
clawhub login
clawhub whoami
```

### 2. Search for these skills (optional)

```bash
clawhub search "bitcoin price feed"
clawhub search "crypto chart"
clawhub search "pumpfun price"
clawhub search "polymarket"
clawhub search "stablecoin solana"
```

### 3. Install the skills

Install one or more skills by name (slug):

```bash
# Bitcoin price feed — real-time streaming BTC OHLC/volume from Bitquery
clawhub install bitcoin-price-feed

# PumpFun token feed — real-time streaming PumpFun tokens on Solana (USD) from Bitquery
clawhub install pumpfun-usd-price-stream

# Polymarket prediction trades — real-time streaming on Polygon (matic) from Bitquery
clawhub install polymarket-real-time-trades

# Crypto chart USD — real-time 1-second multi-token OHLC/volume/USD from Bitquery
clawhub install crypto-chart-usd

# Stablecoin payments — real-time Solana USDC/USDT transfers from Bitquery
clawhub install stablecoin-payments

# Install multiple at once
clawhub install bitcoin-price-feed crypto-chart-usd pumpfun-usd-price-stream polymarket-real-time-trades stablecoin-payments
```

### 4. Install a specific version (optional)

```bash
clawhub install bitcoin-price-feed@1.0.0
clawhub install pumpfun-usd-price-stream --version 1.0.0
clawhub install polymarket-real-time-trades@1.0.0
clawhub install crypto-chart-usd@1.0.0
clawhub install stablecoin-payments@1.0.0
```

### 5. Verify installation

```bash
clawhub list
```

By default, skills are installed into `./skills` (or your OpenClaw workspace). Start a new OpenClaw session so it picks up the new skills.

---

## After installing: runtime setup

These skills use the **Bitquery WebSocket API** and need:

1. **`BITQUERY_API_KEY`**  
   Set your [Bitquery](https://bitquery.io/) API token:

   ```bash
   export BITQUERY_API_KEY="your_bitquery_api_key"
   ```
---

## Update and manage skills

```bash
# List installed skills
clawhub list

# Update all installed skills
clawhub update --all

# Update one skill
clawhub update bitcoin-price-feed
clawhub update pumpfun-usd-price-stream
clawhub update polymarket-real-time-trades
clawhub update crypto-chart-usd
clawhub update stablecoin-payments

# Overwrite local changes when updating
clawhub update bitcoin-price-feed --force
```

---

## Quick reference

| Action | Command |
|--------|--------|
| Search | `clawhub search "query"` |
| Install | `clawhub install bitcoin-price-feed` |
| Install multiple | `clawhub install bitcoin-price-feed crypto-chart-usd pumpfun-usd-price-stream polymarket-real-time-trades stablecoin-payments` |
| List installed | `clawhub list` |
| Update all | `clawhub update --all` |
| Skill info | `clawhub info bitcoin-price-feed` |

---

## Links

- **ClawHub**: [clawhub.ai](https://clawhub.ai/)
- **OpenClaw**: [openclaw.ai](https://openclaw.ai/)
- **ClawHub docs**: [docs.openclaw.ai/tools/clawhub](https://docs.openclaw.ai/tools/clawhub)
