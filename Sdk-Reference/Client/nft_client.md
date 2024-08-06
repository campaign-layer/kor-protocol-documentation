# NFT 

## NFTClient

The `NFTClient` allows you to perform various operations related to NFTs.

### Methods

- createCollection
- mintFromCollection
- mintIpFromArtistCollection
- mintFromKorProtocol
- updateMetadata 


### createCollection

The `createCollection` function is used to create a standard collection or an Artist collection.

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>createCollection</code></td>
      <td><code>(request: createCollectionRequest) => Promise&lt; createCollectionResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.name`: The name associated with the collection.
    - `request.symbol`: The symbol representing the collection.
    - `request.bannerImage`: The banner image for collection.
    - `request.type`: Collection type (Artist || Standard).
    - `request.mintingFee`: The fee associated while minting NFT.
    - `request.chainId`: The identifier for the blockchain network in the request.

- **Returns**:
    - `response.txhash` - The transaction hash.
    - `response.contractAddress` - The collection contract address.


### mintFromCollection

The `mintFromCollection` function is used to mint an NFT from standard collection.

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>mintFromCollection</code></td>
      <td><code>(request: mintFromCollectionRequest) => Promise&lt; mintFromCollectionResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.contractAddress`: The address of the collection contract.
    - `request.uri`: The URI associated with the NFT.
    - `request.chainId`: The identifier for the blockchain network in the request.

- **Returns**:
    - `response.txhash` - The transaction hash.
    - `response.tokenId` - The token id of an NFT.



### mintIpFromArtistCollection

The `mintIpFromArtistCollection` function is used to mint an NFT from artist collection.

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>mintIpFromArtistCollection</code></td>
      <td><code>(request: mintIpFromArtistCollectionRequest) => Promise&lt; mintIpFromArtistCollectionResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.contractAddress`: The address of the collection contract.
    - `request.mintingFee`: The amount to be paid for minting fee.
    - `request.chainId`: The identifier for the blockchain network in the request.

- **Returns**:
    - `response.txhash` - The transaction hash.
    - `response.tokenId` - The token id of an NFT.
    - `response.ipId` - The Ip Id of an asset.


### mintFromKorProtocol

The `mintFromKorProtocol` function is used to mint an NFT from Kor protocol collection.

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>mintFromKorProtocol</code></td>
      <td><code>(request: mintFromKorProtocolRequest) => Promise&lt; mintFromKorProtocolResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.uri`: The URI associated with the NFT.

- **Returns**:
    - `response.txhash` - The transaction hash.
    - `response.tokenId` - The token id of an NFT.
    - `request.chainId`: The identifier for the blockchain network in the request.

### updateMetadata

The `updateMetadata` function is used to update metadata of already minted NFT.

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>updateMetadata</code></td>
      <td><code>(request: updateMetadataRequest) => Promise&lt; updateMetadataResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.uri`: The new URI associated with the NFT.
    - `request.chainId`: The identifier for the blockchain network in the request.

- **Returns**:
    - `response.txhash` - The transaction hash.


