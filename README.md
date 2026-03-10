# OpenClaw Skills

This repository contains OpenClaw agent skills that you can install from [ClawHub](https://clawhub.ai/) (the public skill registry for OpenClaw).

## Skills in this repo

| Skill | Description |
|-------|-------------|
| **bitcoin-price-feed** | Real-time streaming Bitcoin price feed over WebSocket: OHLC ticks, volume, and derived metrics (moving averages, % change) from the Bitquery API. |
| **pumpfun-usd-price-stream** | Real-time streaming PumpFun token feed on Solana with live USD pricing: OHLC, volume, moving averages, and tick-to-tick % change from the Bitquery API. |

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
clawhub search "pumpfun price"
```

### 3. Install the skills

Install one or both skills by name (slug):

```bash
# Bitcoin price feed — real-time streaming BTC OHLC/volume from Bitquery
clawhub install bitcoin-price-feed

# PumpFun token feed — real-time streaming PumpFun tokens on Solana (USD) from Bitquery
clawhub install pumpfun-usd-price-stream

# Install both at once
clawhub install bitcoin-price-feed pumpfun-usd-price-stream
```

### 4. Install a specific version (optional)

```bash
clawhub install bitcoin-price-feed@1.0.0
clawhub install pumpfun-usd-price-stream --version 1.0.0
```

### 5. Verify installation

```bash
clawhub list
```

By default, skills are installed into `./skills` (or your OpenClaw workspace). Start a new OpenClaw session so it picks up the new skills.

---

## After installing: runtime setup

Both skills use the **Bitquery WebSocket API** and need:

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

# Overwrite local changes when updating
clawhub update bitcoin-price-feed --force
```

---

## Quick reference

| Action | Command |
|--------|--------|
| Search | `clawhub search "query"` |
| Install | `clawhub install bitcoin-price-feed` |
| Install both | `clawhub install bitcoin-price-feed pumpfun-usd-price-stream` |
| List installed | `clawhub list` |
| Update all | `clawhub update --all` |
| Skill info | `clawhub info bitcoin-price-feed` |

---

## Links

- **ClawHub**: [clawhub.ai](https://clawhub.ai/)
- **OpenClaw**: [openclaw.ai](https://openclaw.ai/)
- **ClawHub docs**: [docs.openclaw.ai/tools/clawhub](https://docs.openclaw.ai/tools/clawhub)
