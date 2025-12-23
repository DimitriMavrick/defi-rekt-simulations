# 🩸 DeFi Rekt Simulations

**Live Hardhat demos recreating $441M+ real DeFi exploits.** Run `npx hardhat test` → watch Yearn V1 die in 30 seconds.

[![Tests](https://github.com/DimitriMavrick/defi-rekt-simulations/actions/workflows/test.yml/badge.svg)](https://github.com/DimitriMavrick/defi-rekt-simulations/actions)

## Featured Exploits

| Attack | Loss | Status | Run |
|--------|------|--------|-----|
| [Yearn iearn TUSD V1](https://rekt.news/yearn-rekt4) | **$293k** | ✅ Live | `npx hardhat test` |
| [Aevo/Ribbon tx.origin](https://rekt.news/aevo-rekt) | **$2.7M** | 🛠 Coming | `git checkout aevo-proxy-admin` |
| [Balancer V2 rounding](https://rekt.news/balancer-rekt2) | **$128M** | 🛠 Coming | `git checkout balancer-rounding` |
| [Abracadabra Cauldron](https://rekt.news/abracadabra-rekt3) | **$1.8M** | 🛠 Coming | `git checkout abraca-cauldron` |

## 🚀 Quickstart (30 seconds)

git clone https://github.com/DimitriMavrick/defi-rekt-simulations
cd defi-rekt-simulations
npm install
npx hardhat test


**Watch Yearn V1 get rekt live:**
 NORMAL: Vault TUSD: 300000.0 | Share price: 1.0
💀 AFTER: Share price: 0.0 | Hacker yTUSD: 4.29e24 (∞!)
✅ $293k profit from $50 gas → VAULT DESTROYED


## Yearn iearn TUSD Exploit Breakdown

**The Bug** (iearn.finance V1 - deployed 2020):
TUSD vault + sUSD strategy mismatch
totalAsset() = TUSD.balance + strategy.balance() // WRONG asset!
sUSD dust transfer → ignored completely
Flashloan drain → TUSD dust (0.999) → integer truncation → sharePrice=0
mint(1 TUSD) → ∞ shares → dump Curve yPool → $293k


**Same bug hit $10M in 2023.** Immutable ≠ secure.


