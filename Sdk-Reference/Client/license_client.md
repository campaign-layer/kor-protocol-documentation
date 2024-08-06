# License

## LicenseClient

The `LicenseClient` is used to register and manage licenses.

### Methods

- attachLicenseToCollection
- attachLicenseTermsToIp
- registerLicenseTerms
- mintLicenseToken

<head>
  <link rel="stylesheet" type="text/css" href="styles.css">
</head>


### attachLicenseToCollection

The `attachLicenseToCollection` function is used to associate a license with a specific collection of intellectual property (IP) assets.


<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>attachLicenseToCollection</code></td>
      <td><code>(request: attachLicenseToCollectionRequest) => Promise&lt; attachLicenseToCollectionResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.collectionIpId`: The collection Ip Id. 
    - `request.licenseTermId`: The identifier for the specific license term in the request.
    - `request.chainId`: The identifier for the blockchain network in the request.


- **Returns**:
    - `response.txhash` - The transaction hash.


### attachLicenseTermsToIp

The `attachLicenseTermsToIp` function is used to associate a license with a specific Ip asset.


<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>attachLicenseTermsToIp</code></td>
      <td><code>(request: attachLicenseTermsToIpRequest) => Promise&lt; attachLicenseTermsToIpResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.ipId`: The identifier for the Ip.
    - `request.licenseTermId`: The identifier for the license term.
    - `request.chainId`: The identifier for the blockchain network in the request.


- **Returns**:
    - `response.txhash` -  The transaction hash.



### registerLicenseTerms

The `registerLicenseTerms` function is used to register a new license terms.


<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>registerLicenseTerms</code></td>
      <td><code>(request: registerLicenseTermsRequest) => Promise&lt; registerLicenseTermsResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.licenseTerm`: The new license term.
    - `request.chainId`: The identifier for the blockchain network in the request.

- **Returns**:
    - `response.txhash` - The transaction hash.
    - `response.termId` - The term id for newly registed term 


### mintLicenseToken

The `mintLicenseToken` function is used to mint a license token that can be used for creating derivatives.

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>mintLicenseToken</code></td>
      <td><code>(request: mintLicenseTokenRequest) => Promise&lt; mintLicenseTokenResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.licenseId`: - The identifier for the specific license in the request.
    - `request.recipient`: - The recipient's information for the request.
    - `request.amount`: - The amount specified in the request.
    - `request.chainId`: The identifier for the blockchain network in the request.


- **Returns**:
    - `response.txhash` - The transaction hash.