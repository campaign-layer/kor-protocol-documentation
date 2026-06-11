# Introducing KOR Protocol

## What is KOR Protocol?

KOR Protocol is an onchain clearinghouse for creative assets. The protocol coordinates three functions across the lifecycle of a creative work: **verifying** origin and ownership, **routing** the work to demand-side parties, and **settling** value across the participants.

Built on Base. Stablecoin-native. Designed for a world where AI agents need to license content at machine speed.

***

## Why This Exists

AI collapsed the cost of production to near zero.

A 19-year-old in Bandung produces a track that out-mixes a major-label release. A solo creator in Lagos ships a series that out-performs a Netflix original. A bedroom DJ in Berlin builds a sound that rivals Tale of Us. A digital painter in Seoul moves more prints in a month than a Chelsea gallery moves in a year.

The tools caught up. The infrastructure didn't.

There's no trusted record of origin. Ownership lives in PDFs and email threads. Payments take 30-90 days and eat 5-10% in fees. And autonomous systems that want to license a sound for 0.3 seconds of a generated video? They can't even participate.

The creative economy runs on rails built for a different era. KOR Protocol is the upgrade.

***

## Three Engines

The protocol is organized into three engines:

```
                ┌───────────────────────────────────┐
                │                                   │
                ▼                                   │
                |   VERIFY ───► ROUTE ───► SETTLE   │
           (what is real) (where it moves) (value clears)  
                │                                   ▲
                │                                   │
                └───────── outcome data ────────────┘
                           reputation updates
```

### Verify

_What is real, who owns it, and is it clear to move?_

The Verify Engine establishes origin, ownership, and clearance state for registered assets. Before anything can be distributed, licensed, remixed, or monetized, someone needs to know where it came from.

Each asset gets a canonical on-chain identifier, an attestation graph for commercial state, and clearance derived from that graph. The token gives the asset a stable identity. The graph carries the data that changes over time—licenses, derivatives, commercial relationships.

This is the clearing function that makes assets legible enough to route downstream.

### Route

_Where does it move?_

The Route Engine moves verified assets toward demand-side parties through specialized agents. Agents have on-chain identity, declared capabilities, and reputation scores. Routing produces actions: pitches, workflows, deal-flow handoffs.

Route is in development. The current release focuses on Verify and Settle.

### Settle

_Clear value back to source._

The Settle Engine clears value across participants when transactions close. Splits are programmatic, denominated in stablecoin, executed atomically.

Each settlement writes back to the protocol. The asset accumulates a royalty history—every license, brand deal, sync, and micropayment queryable with timestamps and counterparties.

Crypto rails aren't ideological here. They're practical. The AI era creates transactions that are too small, too global, too fast, and too programmable for SWIFT wires and 60-day net invoices. Stablecoins fix that.

***

## Why Base?

Base is Coinbase's L2. We picked it for straightforward reasons:

* **Fast**: sub-second finality
* **Cheap**: fractions of a cent per transaction
* **Secure**: inherits Ethereum's security
* **Connected**: 100M+ Coinbase users, native USDC
* **Standards**: x402, ERC-8004, and account abstraction have their deepest deployments here

When an AI agent needs to pay a creator in Jakarta and another in LA, they settle on the same rail. No FX. No correspondent banks. No waiting.

KOR is not a chain. The protocol does not run a sequencer or validator infrastructure. We pick the chain that already has the users, the liquidity, and the standards.

***

## Core Primitives

Four building blocks power the Verify and Settle engines today:

**IP Assets** Register any creative work onchain. Music, video, images, code. Origin and ownership become verifiable. Each registration creates an on-chain identifier and seeds an attestation graph with the initial ownership claim.

**Token-Bound Accounts** Every IP Asset gets its own wallet (ERC-6551). The IP itself can hold assets, receive payments, execute transactions. Not the creator's wallet—the IP's wallet. This matters for programmable royalties and autonomous licensing.

**Licensing** Attach terms directly to IP. Who can use it, under what conditions, at what price. Enforced by code, not lawyers chasing invoices.

**Royalty Distribution** When IP generates money, it splits automatically. No invoices. No net-60. The rules are set upfront and the contracts execute them. Splits are declared at registration and updated by attestation as commercial relationships evolve.

***

## Who Uses This

**Creators** who want provable authenticity, discoverability through intelligent routing, and instant payment when their work gets used.

**Labels and publishers** managing catalogs with complex rights structures who are tired of quarterly reconciliation nightmares.

**Agencies and MCNs** settling brand deals across 40 markets without the banking friction.

**Platforms** that need verified IP and native licensing.

**AI agents** that need to transact at machine speed without asking permission.

***

## Ecosystem

KOR Protocol is the infrastructure layer: registry, attestation graph, settlement contracts, licensing. The protocol is permissionless—anyone can build against it.

The following surfaces operate on the protocol today, built and operated by the KOR team:

**Korus** — Music remixing and creation. Output registers into the protocol with authorship and provenance attached at creation.

**VRSNS** — Video generation for creators. Assets register with provenance metadata and become licensable immediately.

**Pacer** — AI operating system for music. The interface where artists interact with the protocol's routing and distribution capabilities.

**Streamline** — AI operating system for creators more broadly. Extends the Pacer pattern across video, visual art, and multi-format workflows.

**Hubs** — Community engagement and monetization. Where partners, audiences, and creators connect. Settlement for subscriptions, fan tokens, and gated experiences runs through the protocol.

The protocol layer is open. You can register assets, integrate licensing, and settle through the same contracts these surfaces use.

***

## What's Next

The current release focuses on the Verify and Settle engines. The Route Engine—with specialized agents, match engine, and curation rails—is in active development.

Standards we're building toward:

| Standard | Function                        | Status |
| -------- | ------------------------------- | ------ |
| ERC-721  | Asset identifier                | Live   |
| ERC-6551 | Token-bound accounts            | Live   |
| ERC-8004 | Agent identity, reputation      | Coming |
| x402     | HTTP-native stablecoin payments | Coming |
| ERC-7683 | Cross-chain intents             | Coming |

***

## Next

* [How KOR Protocol Works](Introduction/how-kor-protocol-works.md) — the technical architecture
* [Developer Onboarding](Introduction/developer-onboarding.md) — get running in 5 minutes
* [SDK Reference](Sdk-Reference/introduction.md) — full API docs
