# How KOR Protocol Works

Three layers: **SDK → Backend → Blockchain**. The SDK talks to our backend, the backend signs transactions, your user's wallet submits them. Keeps blockchain complexity out of the way while preserving the security guarantees.

---

## Architecture

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
│  Validates, encodes,      │  │  MetaMask, Coinbase, whatever.   │
│  signs tx data            │  │  Signs + pays gas.               │
└───────────────────────────┘  └──────────────────────────────────┘
                    │                     │
                    └──────────┬──────────┘
                               ▼
┌─────────────────────────────────────────────────────────────────┐
│                      BASE NETWORK                               │
│                                                                 │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │
│  │ NFT Module  │  │  IP Module  │  │License Module│             │
│  └─────────────┘  └─────────────┘  └─────────────┘             │
│                                                                 │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │
│  │Royalty Module│ │ERC-6551     │  │  Dispute    │             │
│  └─────────────┘  │Registry     │  │  Module     │             │
│                   └─────────────┘  └─────────────┘             │
└─────────────────────────────────────────────────────────────────┘
```

---

## Transaction Flow

Every operation follows the same two-step pattern:

**Step 1: Get signature from backend**

Your app calls the SDK. SDK hits our backend. Backend validates your API key, encodes the transaction, signs it, sends back the signature + encoded data.

**Step 2: User wallet submits**

SDK takes that payload and routes it through the user's wallet. User sees the transaction, confirms, pays gas (fractions of a cent on Base).

Why this pattern? Users stay in control of their assets. They sign every transaction. But the protocol can still validate and authorize operations server-side.

```typescript
// Register an NFT as IP
const { request } = await kor.ip.registerIp({
  nftContract: "0x...",
  tokenId: "1",
  licensors: [{ licensorAddress: "0x...", licensorPercentage: 100 }]
});

// User signs and submits
const txHash = await walletClient.writeContract(request);
```

---

## Smart Contract Modules

Six modules, each handling a specific piece:

### NFT Module

Creates and manages collections.

| Function | What it does |
|----------|--------------|
| `createCollection` | Deploy a new ERC-721 collection |
| `createIpCollection` | Deploy a collection where mints auto-register as IP |
| `mint` | Mint to a collection |
| `mintFromIpCollection` | Mint + auto-register as IP Asset |

### IP Module

The core. Registers NFTs as IP and creates token-bound accounts.

| Function | What it does |
|----------|--------------|
| `registerIp` | Register any NFT as an IP Asset |
| `registerIpFromCollection` | Register with collection-level licensing |
| `registerDerivative` | Register work that derives from parent IP |
| `getIpAccount` | Get the ERC-6551 account address for an IP |

### License Module

Attaches terms to IP.

| Function | What it does |
|----------|--------------|
| `attachLicense` | Attach license terms to an IP Asset |
| `mintLicense` | Mint a license token for usage rights |
| `getLicenseTerms` | Query terms for an IP |

### Royalty Module

Handles splits and distributions.

| Function | What it does |
|----------|--------------|
| `setRoyaltySplit` | Define percentages for collaborators |
| `distributeRoyalties` | Trigger distribution |
| `claimRoyalties` | Claim what's owed |

### Dispute Module

For ownership disputes.

| Function | What it does |
|----------|--------------|
| `raiseDispute` | Initiate dispute |
| `resolveDispute` | Resolve with evidence |

### Asset Module

Off-chain metadata and storage.

| Function | What it does |
|----------|--------------|
| `uploadAsset` | Upload to decentralized storage |
| `getAssetMetadata` | Retrieve metadata |

---

## Token-Bound Accounts (ERC-6551)

This is the interesting part.

Every IP Asset registered on the protocol gets its own smart contract wallet. Not a wallet controlled by the creator. A wallet controlled by the IP itself.

```
┌─────────────────────────────────────────┐
│            NFT (IP Asset)               │
│         Contract: 0xABC...              │
│         Token ID: 42                    │
└─────────────────────────────────────────┘
                    │
                    │ ERC-6551 Registry creates
                    ▼
┌─────────────────────────────────────────┐
│      Token-Bound Account (TBA)          │
│         Address: 0xDEF...               │
│                                         │
│  → Receives royalty payments            │
│  → Holds licensing revenue              │
│  → Can own other assets                 │
│  → Controlled by NFT owner              │
└─────────────────────────────────────────┘
```

Why does this matter?

**IP can hold assets.** Revenue flows to the IP, not just the creator's wallet. Makes accounting cleaner when rights structures get complex.

**Programmable ownership.** The wallet executes transactions on behalf of the IP. Royalties split automatically. Licenses execute without manual intervention.

**Portable identity.** The IP has an onchain identity that persists across platforms. History, reputation, relationships travel with it.

When someone licenses your IP or a derivative generates revenue, payments go to the token-bound account. The NFT owner can withdraw whenever they want.

---

## Network Details

### Base Sepolia (Testnet)

| Contract | Address |
|----------|---------|
| NFT Module | `0x7797A484C7a9aAa238D40476A022E5C5e3e2e0e3` |
| IP Module | `0xd97fEB28aD630A3f8561a0decee0fed26842b718` |
| Backend API | `https://backend-production-a7215.up.railway.app/kor-sdk-api` |

Chain ID: `84532`

### Base Mainnet

Coming.

---

## What You Can Build

**Creator platforms** — register user content as IP, automate royalties on remixes

**Music distribution** — manage releases as IP Assets, split royalties between artists/producers/labels automatically

**AI training marketplaces** — license IP for model training with programmable usage rights

**Digital art galleries** — verify authenticity, track provenance through derivatives

**Brand partnership platforms** — match creators with brands, settle instantly on crypto rails

---

## Next

- [Developer Onboarding](./developer-onboarding.md) — set up your environment
- [SDK Reference](../Sdk-Reference/introduction.md) — full API docs
- [Key Business Flows](../Key-Flow/flow.md) — common patterns
