# IP

## IPClient

The `IPClient` provides functionality for managing intellectual property (IP) assets.
The `IPClient` simplifies the management of IP assets, making it easier to create, retrieve, and list them as needed.

### Methods

- registerIp
- registerDerivative
- mintAndRegisterIp
- registerIpAndAttachLicense
- getIpAsset

<head>
  <link rel="stylesheet" type="text/css" href="styles.css">
</head>


### registerIp

Register an NFT as an Intellectual Property Asset


<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>registerIp</code></td>
      <td><code>(request: registerIpRequest) => Promise&lt;registerIpResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.nftContractAddress`: The address of the NFT Contract address.
    - `request.tokenId`: The token id of the NFT.
    - `request.signature`: Data signature.
    - `request.deadline`: The deadline for the signature in milliseconds.
    - `request.licenseeRoles[]`: An address array specifying the roles assigned to licensees
    - `request.copyrightRoles[]`: An address array detailing the roles related to copyrights.
    - `request.chainId`: The identifier for the blockchain network in the request.




- **Returns**:
    - `response.txhash` -  The transaction hash.
    - `response.ipId` - The ipId of the newly registered Ip Asset.


### registerDerivative

Register an derivative of an Ip Asset


<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>registerDerivative</code></td>
      <td><code>(request: registerDerivativeRequest) => Promise&lt;registerDerivativeResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.parentIpId`: The identifier for the parent intellectual property (IP) in the request
    - `request.signature`: Data signature.
    - `request.deadline`: The deadline for the signature in milliseconds.
    - `request.chainId`: The identifier for the blockchain network in the request.


- **Returns**:
    - `response.txhash` -  The transaction hash.
    - `response.ipId` - The Ip Id of the newly registered Ip Asset.


### mintAndRegisterIp

Mint an NFT and regsiter it as an Intellectual Property Asset

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>mintAndRegisterIp</code></td>
      <td><code>(request: mintAndRegisterIpRequest) => Promise&lt;mintAndRegisterIpResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.nftContractAddress`: The address of the NFT Contract address.
    - `request.signature`: Data signature.
    - `request.deadline`: The deadline for the signature in milliseconds.
    - `request.licenseeRoles[]`: An address array specifying the roles assigned to licensees
    - `request.copyrightRoles[]`: An address array detailing the roles related to copyrights.
    - `request.chainId`: The identifier for the blockchain network in the request.


- **Returns**:
    - `response.txhash` -  The transaction hash.
    - `response.ipId` - The Ip Id of the newly registered Ip Asset.
    - `response.tokenId` - The tokenId of the issued NFT.



### registerIpAndAttachLicense

Register an Ip and attach a license to it.

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>registerIpAndAttachLicense</code></td>
      <td><code>(request: registerIpAndAttachLicenseRequest) => Promise&lt;registerIpAndAttachLicenseResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.nftContractAddress`: The address of the NFT Contract address.
    - `request.tokenId`: The token id of the NFT.
    - `request.licenseTermId`: The term id of the license.
    - `request.signature`: Data signature.
    - `request.deadline`: The deadline for the signature in milliseconds.
    - `request.licenseeRoles[]`: An address array specifying the roles assigned to licensees
    - `request.copyrightRoles[]`: An address array detailing the roles related to copyrights.
    - `request.chainId`: The identifier for the blockchain network in the request.


- **Returns**:
    - `response.txhash` -  The transaction hash.
    - `response.ipId` - The Ip Id of the newly registered Ip Asset.


### getIpAsset

Get details of a registered Ip.

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>getIpAsset</code></td>
      <td><code>(request: getIpAssetRequest) => Promise&lt;getIpAssetResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `response.ipId` - The Ip Id of the registered Ip Asset.
    - `request.chainId`: The identifier for the blockchain network in the request.

- **Returns**:
    - `response.license` - The license details.
        - `response.license.id` - The license Id.
        - `response.license.termId` - The identifier for the license term.
        - `response.license.templateAddress` - The address of the license template.
        - `response.license.ipfsUri` - The IPFS URI for the license document.
    - `response.royalty` - The royalty information. 
        - `response.royalty.vaultAddress` - The address of the royalty vault.
        - `response.royalty.royaltyTokenAddress` - The address of the royalty token.
    - `response.dispute` - The dispute details.
        - `response.dispute.disputed`- Indicates if there is a dispute.
        - `response.dispute.tag` - The tag associated with the dispute.
        - `response.dispute.disputeCount` - The number of disputes.
        - `response.dispute.locked` - Indicates if the dispute is locked.
