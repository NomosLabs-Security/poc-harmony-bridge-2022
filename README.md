# Harmony Horizon Bridge Exploit PoC — Multi-Sig Key Compromise

## Overview
- **Date:** 2022-06-24
- **Loss:** ~$100M
- **Chain:** Harmony / Ethereum
- **Category:** Access Control Failures
- **Block:** 15012646

## Vulnerability
Harmony's Horizon Bridge used a 2-of-5 multi-sig for cross-chain validations. The attacker compromised 2 validator private keys and used them to authorize 11 fraudulent withdrawal transactions, draining ETH, USDC, USDT, WBTC, and other tokens. Attributed to Lazarus Group.

## Reproduction
```bash
git clone https://github.com/NomosLabs-Security/poc-harmony-bridge-2022
cd poc-harmony-bridge-2022
forge install foundry-rs/forge-std --no-git
forge test -vvvv
```

## Key Contracts
- `Horizon Bridge`: Contract holding locked tokens on Ethereum
- `Multi-Sig Validator`: 2-of-5 threshold for confirming withdrawals
- `No timelock`: Immediate execution upon reaching threshold

## References
- [Harmony Post-Mortem](https://medium.com/harmony-one/harmonys-horizon-bridge-hack-1e8d283b6d66)
- [Elliptic Lazarus Attribution](https://www.elliptic.co/blog/the-100-million-horizon-hack-following-the-trail-through-tornado-cash-to-north-korea)
