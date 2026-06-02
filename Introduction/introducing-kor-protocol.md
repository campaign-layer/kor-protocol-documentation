# Introducing KOR Protocol

## What is KOR Protocol?

KOR Protocol is the onchain infrastructure for the creative asset clearinghouse. It handles two things: **verification** (proving what's real and who owns it) and **settlement** (moving money at the speed the market actually needs).

Built on Base. Stablecoin-native. Designed for a world where AI agents need to license content and can't exactly open a Chase account.

---

## Why This Exists

AI collapsed the cost of production to near zero.

A 19-year-old in Bandung produces a track that out-mixes a major-label release. A solo creator in Lagos ships a series that out-performs a Netflix original. A bedroom DJ in Berlin builds a sound that rivals Tale of Us. A digital painter in Seoul moves more prints in a month than a Chelsea gallery moves in a year.

The tools caught up. The infrastructure didn't.

There's no trusted record of origin. Ownership lives in PDFs and email threads. Payments take 30-90 days and eat 5-10% in fees. And autonomous systems that want to license a sound for 0.3 seconds of a generated video? They can't even participate.

The creative economy runs on rails built for a different era. KOR Protocol is the upgrade.

---

## Two Engines

The broader KOR system has three engines. The protocol powers two of them:

### Verification

*What is real, who owns it, and is it clear to move?*

Before anything can be distributed, licensed, remixed, or monetized, someone needs to know where it came from. The protocol creates that record at the point of origin. Register a track, a video, a piece of art. It goes onchain with provenance attached. No one has to think about blockchain to use it, but the record is there when it matters.

This is the first clearing function: making assets legible enough to route downstream.

### Monetization

*Clear value back to source.*

Once something is registered and routed, the protocol handles the money. Payouts. Splits. Commissions. Licensing flows. Transactions that AI agents initiate without a human in the loop.

Crypto rails aren't ideological here. They're practical. The AI era creates transactions that are too small, too global, too fast, and too programmable for SWIFT wires and 60-day net invoices. Stablecoins fix that.

---

## Why Base?

Base is Coinbase's L2. We picked it for straightforward reasons:

- **Fast**: sub-second finality
- **Cheap**: fractions of a cent per transaction
- **Secure**: inherits Ethereum's security
- **Connected**: 100M+ Coinbase users, native USDC
- **Familiar**: standard EVM tooling

When an AI agent needs to pay a creator in Jakarta and another in LA, they settle on the same rail. No FX. No correspondent banks. No waiting.

---

## Core Primitives

Four building blocks:

**IP Assets**
Register any creative work onchain. Music, video, images, code. Origin and ownership become verifiable.

**Token-Bound Accounts**
Every IP Asset gets its own wallet (ERC-6551). The IP itself can hold assets, receive payments, execute transactions. Not the creator's wallet. The IP's wallet. This matters for programmable royalties and autonomous licensing.

**Licensing**
Attach terms directly to IP. Who can use it, under what conditions, at what price. Enforced by code, not lawyers chasing invoices.

**Royalty Distribution**
When IP generates money, it splits automatically. No invoices. No net-60. The rules are set upfront and the contracts execute them.

---

## Who Uses This

**Creators** who want provable authenticity and instant payment when their work gets used.

**Labels and publishers** managing catalogs with complex rights structures who are tired of quarterly reconciliation nightmares.

**Agencies and MCNs** settling brand deals across 40 markets without the banking friction.

**Platforms** that need verified IP and native licensing.

**AI agents** that need to transact at machine speed without asking permission.

---

## Ecosystem

KOR Protocol is the contract layer: registry, settlement, licensing. It's open, and third-party applications can build against it.

The following surfaces run on the protocol today:

**Korus** — Music remixing and creation. Output registers into the protocol with authorship and provenance attached at creation.

**VRSNS** — Video generation for creators. Assets register with provenance metadata and become licensable immediately.

**Pacer** — AI operating system for music. The interface where artists interact with the protocol's routing and distribution capabilities.

**Streamline** — AI operating system for creators more broadly. Extends Pacer's pattern across video, visual art, and multi-format workflows.

**Hubs** — Community engagement and monetization. The venue where partners, audiences, and creators connect. Settlement for subscriptions, fan tokens, and gated experiences runs through the protocol.

The protocol layer is open. You can register assets, integrate licensing, and settle through the same contracts these surfaces use.

---

## Next

- [How KOR Protocol Works](./how-kor-protocol-works.md) — the technical architecture
- [Developer Onboarding](./developer-onboarding.md) — get running in 5 minutes
- [SDK Reference](../Sdk-Reference/introduction.md) — full API docs
