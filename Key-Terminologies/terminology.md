# Key Terminologies

## Protocol Architecture

**Verify Engine**

The first of three protocol engines. Establishes origin, ownership, and clearance state for registered assets. Comprises the NFT Module, IP Module, and Asset Module.

**Route Engine**

The second protocol engine. Moves verified assets toward demand-side parties through specialized agents. Agents have on-chain identity, declared capabilities, and reputation scores. *(In development)*

**Settle Engine**

The third protocol engine. Clears value across participants when transactions close. Handles programmable splits, stablecoin settlement, and royalty distribution. Comprises the License Module, Royalty Module, and Dispute Module.

**Clearinghouse**

A system that coordinates verification, routing, and settlement for creative assets. KOR Protocol functions as an onchain clearinghouse.

---

## Core Primitives

**Attestation Graph**

The data structure that holds signed claims about a registered asset. The graph is queried by downstream contracts to determine clearance state. Contains sample clearance claims, authorship claims, AI provenance claims, and commercial-state claims.

**Clearance State**

A derived property of the attestation graph indicating whether an asset is clear to move for a given action. Different actions (transient license, sample license, full transfer) require different conditions to be satisfied.

**Clearing Function**

A protocol action that verifies, routes, or settles value. The three engines together implement the protocol's clearing functions.

**Commercial State**

The set of attestations describing licenses, deals, splits, and royalty obligations against an asset. Lives in the attestation graph, not on the token itself.

**Programmable Split**

A contract-encoded distribution of revenue across the parties to an asset. Declared at registration and updated by attestation as commercial relationships evolve.

**Royalty Memory**

The historical record of settlements against an asset. Every license, brand deal, sync, and micropayment is queryable with timestamps and counterparties.

---

## Standards

**ERC-721**

A widely recognized Ethereum token standard for creating non-fungible tokens (NFTs). Used by KOR for asset registration—each registered asset has a canonical on-chain identifier as an ERC-721 token.

**ERC-6551 (Token-Bound Accounts)**

A standard that allows NFTs to have associated accounts or wallets. Every IP Asset registered on KOR gets its own smart contract wallet that can hold assets, receive payments, and execute transactions.

**KOR ERC-6551**

A modified version of ERC-6551 that supports additional functionalities for the protocol, such as attaching licenses.

**ERC-8004**

A standard for AI agent identity, reputation, and validation. Defines three on-chain registries. KOR's Route Engine uses ERC-8004 for agent registration. *(Coming)*

**x402**

An open standard for HTTP-native stablecoin payments. Assets expose x402-compatible endpoints for transient licensing and usage payments. *(Coming)*

**ERC-7683**

A cross-chain intents standard for chain-abstracted settlement. Allows participants to sign intents that solver networks fulfill across multiple chains. *(Coming)*

**EAS (Ethereum Attestation Service)**

A style of attestation used for the protocol's claim graph. Attestations are signed claims backed by various trust mechanisms.

**C2PA**

A standard for AI provenance signatures. Where a creating model has signed output in C2PA-compatible format, the model's signature serves as the attestation.

---

## Assets and Identity

**IP Asset**

A registered creative work with a canonical on-chain identifier, off-chain content pointer, and signed metadata. The registration is the index into protocol state.

**IP Account**

A digital account associated with intellectual property, used to manage and track ownership and usage of IP assets. Created via ERC-6551 when an asset is registered.

**Collection IP Account**

A digital account associated with an intellectual property collection, used to mint new IPs with predefined licensing terms attached.

**Asset URI**

A Uniform Resource Identifier used to uniquely identify and access digital assets. Typically points to metadata or the digital file on IPFS or Arweave.

**KOR ID**

The identity layer of the protocol. Authenticates users via SIWE (Sign-In with Ethereum) and issues permanent identifiers. Also functions as an OAuth 2.0 / OpenID Connect provider. *(Coming)*

---

## Agents and Routing

**Route Agent**

A specialized agent registered with on-chain identity that moves assets toward demand-side parties. Types include A&R agents, sync-licensing agents, and partner-matching agents. *(Coming)*

**Agent Registry**

The on-chain registry where Route agents are registered with declared capability surfaces and bonded reputation scores. Built on ERC-8004. *(Coming)*

**Match Engine**

The system that produces ranked matches between registered assets and demand-side parties. Combines latent-space embeddings, learned ranking on historical outcomes, and reputation weighting. *(Coming)*

**Curation Rails**

A mechanism where humans and agents bond tokens behind explicit calls about talent, matches, or briefs. Successful calls earn from clearing fees. *(Coming)*

---

## Settlement

**Staked Attestation**

A claim against an asset's attestation graph backed by bonded tokens, subject to slashing if proven false.

**Stablecoin Settlement**

All protocol settlement is stablecoin-denominated, primarily in USDC. Provides practical rails for transactions that are too small, global, fast, or programmable for traditional banking.

**Mint Fees**

Charges associated with creating or issuing NFTs or other digital tokens on a blockchain. Covers transaction fees and network charges.

---

## Storage and Metadata

**IPFS (InterPlanetary File System)**

A decentralized file storage system using a peer-to-peer network. KOR uses IPFS for off-chain content pointers.

**Arweave**

A permanent decentralized storage network. Alternative to IPFS for off-chain content storage.

**Metadata**

Information that provides details about other data. For digital assets, includes title, author, date created, format, creation context, and AI-provenance status.

**ISCC (International Standard Content Code)**

A standard for uniquely identifying and managing digital content across different platforms and systems.

---

## Ecosystem

**KOR Protocol**

An onchain clearinghouse for creative assets. Coordinates three functions: verifying origin and ownership, routing to demand-side parties, and settling value across participants.

**Korus**

A music remixing and creation tool. Output flows into the Verify Engine through asset registration with authorship and AI-provenance attestations.

**VRSNS**

Viral video generation for creators. Short-form video output is registered into the protocol with provenance metadata.

**Pacer**

An AI operating system for music. The interface where artists interact with the protocol's routing and distribution capabilities.

**Streamline**

An AI operating system for creators. Extends the Pacer pattern across video, visual art, and multi-format workflows.

**Hubs**

Community engagement and monetization. Where partners, audiences, and creators connect. Settlement venue for subscriptions, fan tokens, and gated experiences.

---

## Disputes

**Arbitrator**

A neutral third party appointed to resolve disputes between parties. Used for high-value disputes that require human arbitration beyond bonded resolution.

**Dispute Resolution**

The process of resolving contested claims. The protocol uses bonded counter-claim mechanisms where parties stake tokens behind their positions.
