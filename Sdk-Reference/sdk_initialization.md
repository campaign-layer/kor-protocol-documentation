# SDK Initialization

To initialize the SDK, you need to provide your API key and the RPC URL of the blockchain network.

```markdown
import { Kor } from '@kor-protocol/core-sdk';

const apiKey = 'your-api-key';
const rpcUrl = 'https://your-rpc-url';
const backendUrl = 'https://kor-backend-url';

const sdk = new Kor(rpcUrl, apiKey, backendUrl);
```

1. **API Key**: This is your unique key to authenticate your requests to the Kor Protocol backend.

2. **RPC URL**: This is the URL of the blockchain network you are connecting to. It could be the URL of a public or private Ethereum node.

3. **Backend URL**: This is the URL of the Kor Protocol backend services.

By using the Kor class from the `@kor-protocol/core-sdk package`, you can create an instance of the SDK by providing these parameters. This instance will allow you to interact with the Kor Protocol APIs and perform various blockchain operations.

