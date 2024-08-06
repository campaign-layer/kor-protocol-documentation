# Dispute

## DisputeClient

The `DisputesClient` can be used to raise, cancel, and resolve disputes.

### Methods

- raiseDispute
- cancelDispute
- resolveDispute
- checkDispute

<head>
  <link rel="stylesheet" type="text/css" href="styles.css">
</head>


### raiseDispute

Raises a dispute on a given IpId

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>raiseDispute</code></td>
      <td><code>(request: raiseDisputeRequest) => Promise&lt;raiseDisputeResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.ipId`: Ip Id for the disputed asset.
    - `request.evidenceLink`: External evidence link.
    - `request.tag`: Dispute type tag.
    - `request.tier`: Tier type of dispute.
    - `request.amount`: Amount required to pay for raising the dispute.
    - `request.chainId`: The identifier for the blockchain network in the request.

- **Returns**:
    - `response.txhash` -  The transaction hash.
    - `response.disputeID` - Dispute Id.


### cancelDispute

Cancel a dispute on a given Ip Id.

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>cancelDispute</code></td>
      <td><code>(request: cancelDisputeRequest) => Promise&lt;cancelDisputeResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.disputeId`: Dispute Id.
    - `request.chainId`: The identifier for the blockchain network in the request.

- **Returns**:
    - `response.txhash` -  The transaction hash.


### resolveDispute

Resolve a dispute on a given Ip Id

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>resolveDispute</code></td>
      <td><code>(request: resolveDisputeRequest) => Promise&lt;resolveDisputeResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.disputeId`: Dispute Id.
    - `request.chainId`: The identifier for the blockchain network in the request.


- **Returns**:
    - `response.txhash` -  The transaction hash.


### checkDispute

Check dispute status on a given Ip Id

<table>
  <thead>
    <tr>
      <th style="text-align: center;">Method</th>
      <th style="text-align: center;">Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>checkDispute</code></td>
      <td><code>(request: checkDisputeRequest) => Promise&lt;checkDisputeResponse&gt;</code></td>
    </tr>
  </tbody>
</table>

- **Parameters**:
    - `request.disputeId`: Dispute Id.
    - `request.chainId`: The identifier for the blockchain network in the request.

- **Returns**:
    - `response.status` -  Status of dispute on a given Ip Id.




