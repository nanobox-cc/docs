# Javascript docs

Any request to the Nanobox API can be crafted manually, but we provide a fetch
wrapper for Javascript which simplifies the setup.

### Setup Javascript Node

In your project, install the `nano-rpc-fetch` dependency from NPM:

    $ npm install nano-rpc-fetch

Then initialize the API by:

```javascript
// Load module
const nanobox = require('nano-rpc-fetch');

// Create API
const api = new nanobox.NodeRPCsApi(
    new nanobox.Configuration({
        basePath: 'https://api.nanobox.cc',
        username: 'API-USER',
        password: 'API-PASSWORD'
    })
);
```

## Authenticating with the API

