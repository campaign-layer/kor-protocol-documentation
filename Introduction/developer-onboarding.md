# Developer Onboarding

Get running in 5 minutes.

---

## Checklist

- [ ] [Get your API key](#1-get-your-api-key)
- [ ] [Install the SDK](#2-install-the-sdk)
- [ ] [Connect to Base Sepolia](#3-connect-to-base-sepolia)
- [ ] [Register your first IP Asset](#4-register-your-first-ip-asset)

---

## 1. Get Your API Key

The SDK authenticates through API keys scoped to specific domains.

{% hint style="info" %}
**Testnet access:** Contact the KOR team for a Base Sepolia API key.
{% endhint %}

Your key looks like:
```
kor_sk_test_a1b2c3d4e5f6...
```

Don't commit it to version control.

---

## 2. Install the SDK

{% tabs %}
{% tab title="npm" %}
```bash
npm install @kor-protocol/sdk ethers
```
{% endtab %}

{% tab title="yarn" %}
```bash
yarn add @kor-protocol/sdk ethers
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm add @kor-protocol/sdk ethers
```
{% endtab %}
{% endtabs %}

---

## 3. Connect to Base Sepolia

```typescript
import { KorClient } from '@kor-protocol/sdk';
import { createWalletClient, http } from 'viem';
import { baseSepolia } from 'viem/chains';
import { privateKeyToAccount } from 'viem/accounts';

const kor = new KorClient({
  apiKey: process.env.KOR_API_KEY,
  network: 'base-sepolia'
});

const account = privateKeyToAccount(process.env.PRIVATE_KEY);
const walletClient = createWalletClient({
  account,
  chain: baseSepolia,
  transport: http()
});
```

### Add Base Sepolia to your wallet

| Field | Value |
|-------|-------|
| Network Name | Base Sepolia |
| RPC URL | `https://sepolia.base.org` |
| Chain ID | `84532` |
| Currency | ETH |
| Explorer | `https://sepolia.basescan.org` |

### Get testnet ETH

1. Grab Sepolia ETH from [sepoliafaucet.com](https://sepoliafaucet.com)
2. Bridge to Base Sepolia at [bridge.base.org](https://bridge.base.org)

---

## 4. Register Your First IP Asset

Take an NFT you own and register it as an IP Asset.

```typescript
async function registerMyIP() {
  const kor = new KorClient({
    apiKey: process.env.KOR_API_KEY,
    network: 'base-sepolia'
  });

  // Get signed tx from backend
  const { request } = await kor.ip.registerIp({
    nftContract: '0xYourNftContract...',
    tokenId: '1',
    licensors: [
      {
        licensorAddress: '0xYourWallet...',
        licensorPercentage: 100
      }
    ]
  });

  // Submit through wallet
  const txHash = await walletClient.writeContract(request);
  console.log('Submitted:', txHash);

  // Wait for confirmation
  const receipt = await publicClient.waitForTransactionReceipt({ hash: txHash });
  console.log('Registered at block:', receipt.blockNumber);
}
```

What happened:
1. Backend validated your API key and signed the transaction
2. Your wallet signed and submitted (gas cost: ~$0.001 on Base)
3. NFT is now a registered IP Asset
4. ERC-6551 token-bound account deployed for that IP

---

## 5. Verify It Worked

```typescript
const ipAccount = await kor.ip.getIpAccount({
  nftContract: '0xYourNftContract...',
  tokenId: '1'
});

console.log('IP Account:', ipAccount);
// 0x... (your IP's smart contract wallet)
```

Check it on [Base Sepolia Explorer](https://sepolia.basescan.org).

---

## Common Operations

### Create an IP Collection

Collections where every mint auto-registers as IP:

```typescript
const { request } = await kor.nft.createIpCollection({
  name: 'My Catalog',
  symbol: 'CAT',
  maxSupply: 10000,
  mintPrice: '0',
  licensors: [
    { licensorAddress: '0x...', licensorPercentage: 100 }
  ]
});
```

### Mint from IP Collection

```typescript
const { request } = await kor.nft.mintFromIpCollection({
  collectionAddress: '0xYourCollection...',
  recipient: '0xRecipient...',
  tokenUri: 'ipfs://...'
});
```

### Register a Derivative

Link derivative work to parent IP:

```typescript
const { request } = await kor.ip.registerDerivative({
  nftContract: '0xDerivativeNft...',
  tokenId: '1',
  parentIpIds: ['0xParentIpAccount...'],
  licensors: [
    { licensorAddress: '0x...', licensorPercentage: 80 },
    { licensorAddress: '0x...', licensorPercentage: 20 }
  ]
});
```

---

## Next

| What you want | Where to go |
|---------------|-------------|
| Understand the architecture | [How KOR Protocol Works](./how-kor-protocol-works.md) |
| Full API reference | [SDK Reference](../Sdk-Reference/introduction.md) |
| Integration patterns | [Key Business Flows](../Key-Flow/flow.md) |
| Contract addresses | [Smart Contract Reference](../Smart-Contract-Reference/SC.md) |

---

## Help

- **Discord:** [Join](#)
- **GitHub:** [github.com/kor-protocol](https://github.com/kor-protocol)
- **Email:** developers@kor.xyz
