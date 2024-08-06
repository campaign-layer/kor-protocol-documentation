# Royalty

## RoyaltyClient

The `RoyaltyClient` is used to distribute and manage royalty payouts.

### Methods

- mintRoyaltyToken
- claimRoyalty
- payRoyalty
- payLicenseRoyaltyFee

<head>
  <link rel="stylesheet" type="text/css" href="styles.css">
</head>


### mintRoyaltyToken

Mint royalty token to recipient address.

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>mintRoyaltyToken</code></td>
      <td><code>(request: mintRoyaltyTokenRequest) => Promise&lt;mintRoyaltyTokenResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `response.recipient` - The recipient address.
    - `response.amount` - Amount of token to mint.
    - `request.chainId`: The identifier for the blockchain network in the request.

- **Returns**:
    - `response.txHash` - The transaction hash.


### claimRoyalty

Royalty token holders can claim their royalties proportionate to their share of tokens held.

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>claimRoyalty</code></td>
      <td><code>(request: claimRoyaltyRequest) => Promise&lt;claimRoyaltyResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `response.recipient` - The recipient address.
    - `request.chainId`: The identifier for the blockchain network in the request.

- **Returns**:
    - `response.txHash` - The transaction hash.


### payRoyalty

The payRoyalty function disburses royalties to token holders based on their ownership share. 

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>payRoyalty</code></td>
      <td><code>(request: payRoyaltyRequest) => Promise&lt;payRoyaltyResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `response.ipId` - The Ip asset Id for which royalties are to be paid.
    - `request.chainId`: The identifier for the blockchain network in the request.

- **Returns**:
    - `response.txHash` - The transaction hash.




### payLicenseRoyaltyFee

The payLicenseRoyaltyFee function is designed to mint a license token by paying the necessary license fee.

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>payLicenseRoyaltyFee</code></td>
      <td><code>(request: payLicenseRoyaltyFeeRequest) => Promise&lt;payLicenseRoyaltyFeeResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `response.ipId` - The Ip asset Id for which license fee to be paid.
    - `response.licenseId` - License Id.
    - `response.amount` - Amount to be paid.
    - `request.chainId`: The identifier for the blockchain network in the request.

- **Returns**:
    - `response.txHash` - The transaction hash.


