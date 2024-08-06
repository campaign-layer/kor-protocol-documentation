## Event Listener Service

The Event Listener Service is a crucial component of our architecture, designed to monitor and handle events emitted by the Kor protocol smart contracts. This service is responsible for ensuring that all relevant blockchain events are captured, processed, and stored efficiently for further analysis and use.

### High-Level Architecture

1. **Connection to RPC Providers**:
    - The Event Listener Service is connected to both Ankr and Alchemy RPC providers. These providers offer robust and reliable access to the Ethereum network, allowing our service to monitor the Kor protocol smart contracts for any events.
2. **Event Detection**:
    - When an event is emitted by a Kor protocol smart contract, the Event Listener Service detects this event in real-time. This ensures that no significant blockchain activity goes unnoticed.
3. **Message Queue Integration**:
    - Upon detecting an event, the Event Listener Service sends the event data to AWS SQS (Simple Queue Service). This decouples the event detection from the processing, allowing for more scalable and fault-tolerant operations.
4. **Consumer Service**:
    - The Consumer Service picks up the events from the AWS SQS queue. It decodes the event data and processes it to extract relevant information.
5. **Data Storage**:
    - The processed event data is then transmitted to a database where it is stored in an indexed form. This allows for efficient querying and retrieval of event data for various applications.


![](../../image/kor-Event-Listener.drawio%20(1).png)


### Workflow

1. **Listening for Events**:
    - The Event Listener Service continuously listens to the Kor protocol smart contracts through the connected RPC providers (Ankr and Alchemy).
2. **Event Emission**:
    - When an event is emitted, it is immediately detected by the Event Listener Service.
3. **Queuing the Event**:
    - The event data is packaged and sent to AWS SQS, ensuring it is queued for further processing.
4. **Consuming the Event**:
    - The Consumer Service retrieves the event from the AWS SQS queue, decodes it, and processes the data.
5. **Storing the Event**:
    - The processed data is stored in a database with appropriate indexing, facilitating efficient data management and retrieval.