# SatoshiSafe: Bitcoin-Native DeFi Lending Protocol

[![Stacks Layer](https://img.shields.io/badge/Built%20on-Stacks%20L2-5546ff.svg)](https://www.stacks.co)

A decentralized lending protocol enabling Bitcoin holders to access USD liquidity while maintaining self-custody of BTC collateral. Built on Stacks L2 with Bitcoin settlement finality.

## Table of Contents

- [SatoshiSafe: Bitcoin-Native DeFi Lending Protocol](#satoshisafe-bitcoin-native-defi-lending-protocol)
	- [Table of Contents](#table-of-contents)
	- [Protocol Overview](#protocol-overview)
	- [Key Features](#key-features)
		- [Core Protocol Mechanics](#core-protocol-mechanics)
		- [Technical Innovations](#technical-innovations)
	- [Technical Specifications](#technical-specifications)
		- [Protocol Parameters](#protocol-parameters)
	- [Smart Contract Functions](#smart-contract-functions)
		- [User Operations](#user-operations)
		- [Vault Management](#vault-management)
		- [Risk Operations](#risk-operations)
		- [Administrative Functions](#administrative-functions)
	- [Risk Management](#risk-management)
		- [Collateral Safety](#collateral-safety)
		- [Liquidation Protections](#liquidation-protections)
	- [Governance](#governance)
		- [Parameter Controls](#parameter-controls)
		- [Upgrade Process](#upgrade-process)
	- [Oracles \& Price Feeds](#oracles--price-feeds)
		- [Hybrid Oracle System](#hybrid-oracle-system)
		- [Price Validation](#price-validation)
		- [Requirements](#requirements)
		- [External Resources](#external-resources)

## Protocol Overview

SatoshiSafe enables:

- 🛡️ 1:1 BTC collateralization via cryptographic proofs
- 💵 USD-pegged stablecoin borrowing
- ⚡️ Sub-second transactions via Stacks L2
- 🔒 Non-custodial asset management
- 📈 Institutional-grade risk parameters

```text
User Flow:
1. Deposit BTC → Generate cryptographic proof
2. Lock collateral on Stacks L2
3. Borrow against collateral value
4. Manage position via transparent dashboard
5. Repay loan to reclaim full collateral
```

## Key Features

### Core Protocol Mechanics

- **Collateral Management**

  - Minimum Collateral Ratio: 150% (adjustable)
  - Liquidation Threshold: 125% with 10% penalty
  - BTC Price Feed: TWAP with 1hr validity

- **Debt Management**

  - Base Interest Rate: 5% APY
  - Protocol Fee: 1% of interest
  - Compound Interest: Per-block accrual

- **Liquidation Engine**
  - Partial liquidation system
  - Liquidator incentives
  - Anti-sniping protections

### Technical Innovations

- Hybrid Oracle System

  - Decentralized price feeds
  - Institutional data sources
  - Price sanity checks

- Regulatory Compliance
  - Non-custodial design
  - AML-compliant hooks
  - Transparent audit trails

## Technical Specifications

### Protocol Parameters

| Parameter                      | Value | Description                      |
| ------------------------------ | ----- | -------------------------------- |
| `minimum-collateral-ratio`     | 150%  | Minimum collateralization ratio  |
| `liquidation-threshold`        | 125%  | Liquidation trigger level        |
| `liquidation-penalty`          | 10%   | Penalty on liquidated collateral |
| `borrow-interest-rate`         | 5%    | Annual borrowing rate            |
| `protocol-fee-rate`            | 1%    | Protocol revenue share           |
| `oracle-price-validity-period` | 3600s | Price feed expiration            |

## Smart Contract Functions

### User Operations

| Function              | Parameters   | Description                     |
| --------------------- | ------------ | ------------------------------- |
| `deposit-collateral`  | `btc-amount` | Add BTC to collateral vault     |
| `withdraw-collateral` | `amount`     | Remove BTC from vault (if safe) |
| `borrow`              | `usd-amount` | Draw debt against collateral    |
| `repay`               | `usd-amount` | Reduce outstanding debt         |

### Vault Management

| Function           | Description                 | Error Codes           |
| ------------------ | --------------------------- | --------------------- |
| `get-vault-info`   | Returns vault statistics    | `ERR_VAULT_NOT_FOUND` |
| `get-vault-health` | Calculates collateral ratio | `ERR_ORACLE_ERROR`    |

### Risk Operations

| Function    | Description                                    | Triggers               |
| ----------- | ---------------------------------------------- | ---------------------- |
| `liquidate` | Initiate undercollateralized vault liquidation | Collateral ratio <125% |

### Administrative Functions

| Function                       | Permission | Description                   |
| ------------------------------ | ---------- | ----------------------------- |
| `update-btc-price`             | Oracle     | Update BTC/USD price feed     |
| `set-minimum-collateral-ratio` | Owner      | Adjust collateral requirement |
| `toggle-protocol-pause`        | Owner      | Emergency shutdown            |

## Risk Management

### Collateral Safety

- Price feed validity checks
- Maximum 50% parameter change limits
- Basel III-inspired capital requirements

### Liquidation Protections

- Partial liquidation system
- 10% minimum collateral buffer
- Anti-frontrunning mechanisms

## Governance

### Parameter Controls

- Contract owner can adjust:
  - Collateral ratios
  - Fee structures
  - Protocol pause state

### Upgrade Process

1. Two-step ownership transfer
2. Time-locked parameter changes
3. Governance token integration (future)

## Oracles & Price Feeds

### Hybrid Oracle System

1. Primary: Decentralized TWAP
2. Secondary: Institutional data streams
3. Fallback: Manual override (owner)

### Price Validation

- Maximum $100,000/BTC ceiling
- 10% maximum hourly deviation
- 1-hour price expiration

### Requirements

- Stacks CLI v3.0+
- Bitcoin testnet node
- Clarinet SDK

### External Resources

- [Stacks Documentation](https://docs.stacks.co)
