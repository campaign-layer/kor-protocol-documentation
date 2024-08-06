# Asset 

## AssetClient

The `AssetClient` allows you to perform various operations related to asset metadata.

Using the `AssetClient` simplifies the process of managing and storing asset metadata for your projects.

### Methods

- uploadAsset
- uploadAssetFolder
- uploadMetadata
- uploadMetadataFolder
- generateISCC
- checkISCCSimilarity  

<head>
  <link rel="stylesheet" type="text/css" href="styles.css">
</head>

### uploadAsset

Upload an asset to IPFS and return the CID.
<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>uploadAsset</code></td>
      <td><code>(request: UploadAssetRequest) => Promise&lt;UploadAssetResponse&gt;</code></td>
    </tr>
  </tbody>
</table>


**Parameters**

- `request.data`: The data to be uploaded to IPFS.

**Returns**

- `response.uri`: The URI of the uploaded data.



### uploadAssetFolder

Upload an asset folder to IPFS and return the base CID.
<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>uploadAssetFolder</code></td>
      <td><code>(request: UploadAssetFolderRequest) => Promise&lt;UploadAssetFolderResponse&gt;</code></td>
    </tr>
  </tbody>
</table>


**Parameters**

- `request.data`: The data to be uploaded to IPFS.

**Returns**

- `response.baseUri`: The Base URI of the uploaded data.


### uploadMetadata

Upload metadata to IPFS and return the CID.
<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>uploadMetadata</code></td>
      <td><code>(request: UploadMetadataRequest) => Promise&lt;UploadMetadataResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.data` - The actual metadata content.
    - `request.name` - The name of the metadata.    
    - `request.symbol` - The symbol of the metadata.
    - `request.description` - The description of the metadata.
    - `request.attributes` - An array of attributes, where each attribute is an object with `trait_type` and `value` properties.

- **Returns**:
    - `response.metadataURI` - The URI (e.g., IPFS URI) where the metadata is stored.


### uploadMetadataFolder

Upload an metadata folder to IPFS and return the base CID.
<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>uploadMetadataFolder</code></td>
      <td><code>(request: uploadMetadataFolderRequest) => Promise&lt;uploadMetadataFolderResponse&gt;</code></td>
    </tr>
  </tbody>
</table>


**Parameters**

- `request.data`: The data to be uploaded to IPFS.

**Returns**

- `response.baseUri`: The Base URI of the uploaded data.


### generateISCC

Generate the ISCC of the content.

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>generateISCC</code></td>
      <td><code>(request: generateISCCRequest) => Promise&lt;generateISCCResponse&gt;</code></td>
    </tr>
  </tbody>
</table>


- **Parameters**:
    - `request.data` - The actual content.
- **Returns**:
    - `response.code` - The ISCC code of content.  

### checkISCCSimilarity

Check Similarity between two ISCC Code

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>checkISCCSimilarity</code></td>
      <td><code>(request: checkISCCSimilarityRequest) => Promise&lt;checkISCCSimilarityResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.ISCC1` - First ISCC Code.
    - `request.ISCC2` - Second ISCC Code
- **Returns**:
    - `response.percentage` - Similarity percentage of two ISCC code.  
