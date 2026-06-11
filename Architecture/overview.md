# Overview

KOR Protocol is an onchain clearinghouse for creative assets. The architecture is organized into three engines that coordinate across the lifecycle of a creative work.

***

## Three Engines

```
                ┌───────────────────────────────────┐
                │                                   │
                ▼                                   │
        VERIFY ───► ROUTE ───► SETTLE               │
    (what is real) (where it moves) (value clears)  │
                │                                   ▲
                │                                   │
                └───────── outcome data ────────────┘
                           reputation updates
```

**Verify** — establishes origin, ownership, and clearance state for a registered asset.

**Route** — moves a verified asset toward demand-side parties through specialized agents. _(In development)_

**Settle** — clears value across participants and writes commercial state back to the asset.

Each engine composes against external standards rather than reinventing infrastructure:

| Engine | Standards                                                                        |
| ------ | -------------------------------------------------------------------------------- |
| Verify | ERC-721 for asset registration, EAS-style attestation graph for commercial state |
| Route  | ERC-8004 for agent identity, A2A for messaging _(coming)_                        |
| Settle | ERC-6551 for token-bound accounts, stablecoin settlement in USDC                 |

***

## Module Organization

The protocol SDK exposes six modules, mapped to the engines:

### Verify Engine Modules

| Module           | Function                                                  |
| ---------------- | --------------------------------------------------------- |
| **NFT Module**   | Creates and manages ERC-721 collections                   |
| **IP Module**    | Registers NFTs as IP Assets, creates token-bound accounts |
| **Asset Module** | Off-chain metadata and decentralized storage              |

### Settle Engine Modules

| Module             | Function                            |
| ------------------ | ----------------------------------- |
| **License Module** | Attaches license terms to IP Assets |
| **Royalty Module** | Handles splits and distributions    |
| **Dispute Module** | Resolves ownership disputes         |

Four modules—IP, License, Royalty, and Dispute—are coordinated by the Orchestrator Architecture. This approach streamlines the system, reducing complexity and improving code organization.

***

## Component Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                        YOUR APPLICATION                         │
└─────────────────────────────────────────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────────┐
│                         KOR SDK                                 │
│            TypeScript. Handles API calls + tx submission.       │
└─────────────────────────────────────────────────────────────────┘
                               │
                    ┌──────────┴──────────┐
                    ▼                     ▼
┌───────────────────────────┐  ┌──────────────────────────────────┐
│      KOR BACKEND          │  │         USER WALLET              │
│  Validates, encodes,      │  │  MetaMask, Coinbase, etc.        │
│  signs tx data            │  │  Signs + pays gas.               │
└───────────────────────────┘  └──────────────────────────────────┘
                    │                     │
                    └──────────┬──────────┘
                               ▼
┌─────────────────────────────────────────────────────────────────┐
│                      BASE NETWORK                               │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                    VERIFY ENGINE                         │   │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐      │   │
│  │  │ NFT Module  │  │  IP Module  │  │Asset Module │      │   │
│  │  └─────────────┘  └─────────────┘  └─────────────┘      │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │              ROUTE ENGINE (In Development)               │   │
│  │         Agent Registry │ Match Engine │ Curation         │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                    SETTLE ENGINE                         │   │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐      │   │
│  │  │License Module│ │Royalty Module│ │Dispute Module│     │   │
│  │  └─────────────┘  └─────────────┘  └─────────────┘      │   │
│  └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                  TOKEN-BOUND ACCOUNTS                    │   │
│  │                     (ERC-6551 Registry)                  │   │
│  └─────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```

***

## Data Flow

### The Loop

![The Loop - KOR Protocol Flow](../.gitbook/assets/the-loop-diagram.jpg)

1. **Registration** — A creator registers an asset. Creates a canonical on-chain identifier, an attestation graph seeded with the initial ownership claim, and a clearance state derived from the graph.
2. **Routing** — Once an asset is registered and clear-to-move, Route agents ingest signal about the asset, query the attestation graph, and route toward partners. _(In development)_
3. **Settlement** — A closed match clears through the Settle layer. Splits are programmatic, denominated in stablecoin, executed atomically.
4. **Feedback** — Each settlement writes back to the protocol. The asset accumulates royalty history with timestamps and counterparties.

### Transaction Pattern

Every SDK operation follows the same two-step pattern:

**Step 1: Backend signature** Your app calls the SDK → SDK hits backend → Backend validates API key, encodes transaction, signs it → Returns signature + encoded data

**Step 2: User submission** SDK routes payload through user's wallet → User confirms → Transaction executes on Base

This pattern keeps users in control of their assets while allowing server-side validation.

***

## Core Primitives

### IP Assets

Each registered asset has:

* A canonical on-chain identifier (ERC-721 token)
* An off-chain content pointer (IPFS or Arweave hash)
* Signed metadata describing format, creation context, and AI-provenance status

The token is the index into protocol state. Commercial state lives in the attestation graph and is queried separately by downstream contracts.

### Token-Bound Accounts (ERC-6551)

Every IP Asset gets its own smart contract wallet controlled by the IP itself:

* Receives royalty payments
* Holds licensing revenue
* Can own other assets
* Controlled by NFT owner

### Attestation Graph

The attestation graph holds signed claims about an asset:

* Sample and derivative clearance claims
* Authorship and co-creation claims
* Commercial-state claims (licenses, deals, splits)

The graph is the data structure that the rest of the protocol queries when it needs to know anything about an asset.

### Clearance State

Clearance state is derived from the attestation graph. An asset is "clear-to-move" for a given action when the graph satisfies the required conditions. Different actions require different conditions.

***

## What's Coming

### Route Engine

Specialized agents with on-chain identity (ERC-8004):

* A\&R agents for talent discovery
* Sync-licensing agents for brand matching
* Partner-matching agents for distribution

### Agent Payments

x402 for HTTP-native stablecoin payments. Assets expose payment endpoints that agents can transact with directly.

### Cross-Chain Settlement

ERC-7683 intents for chain-abstracted value transfer.

***

## Next

* [NFT Module](module/nft-module.md)
* [IP Module](module/ip-module.md)
* [License Module](module/license-module.md)
* [Royalty Module](module/royalty-module.md)
