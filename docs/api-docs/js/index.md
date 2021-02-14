# Introduction

Any request to the Nanobox API can be crafted manually, but we provide a fetch
wrapper for Javascript which simplifies the setup. This is a Typescript wrapper, meaning that you'd get types for the
requests and responses if you're working with a [Typescript application](https://www.typescriptlang.org/). However, the library will work just as well in a vanilla
Javascript project.

## Setup

### Dependencies
In your node.js project, install the [nano-rpc-fetch](https://www.npmjs.com/package/nano-rpc-fetch) dependency from NPM.
We also need [node-fetch](https://www.npmjs.com/package/node-fetch) to support the Javascript Fetch API. 

    $ npm install nano-rpc-fetch node-fetch

### Initialize client
```javascript
// Load modules
const nanobox = require('nano-rpc-fetch');
const fetch = require('node-fetch');

// Create API
const api = new nanobox.NodeRPCsApi(
    new nanobox.Configuration({
        basePath: 'https://api.nanobox.cc',
        fetchApi: fetch,
        headers: {
            Authorization: 'AUTH HEADER' // Auth header provided by Nanobox
        },
    })
);
```

### Retrieving info from the Nano network

We're gonna issue an [account_info](/api-docs/nano-api/#operations-Nanobox_API-account_info) request to get some basic information for an account:

```javascript
// The account address we want to fetch
const account = 'nano_1x7biz69cem95oo7gxkrw6kzhfywq4x5dupw4z1bdzkb74dk9kpxwzjbdhhs'

// Construct promise based request
api.accountInfo({
    accountInfoRequest: {
        // The action we're issuing
        action: nanobox.AccountInfoRequestActionEnum.AccountInfo,
        // The account we want to fetch
        account: account,
        // Whether to include the representative in the response
        representative: nanobox.ModelBoolean.True,
    },
}).then(accountInfo => {
    // Log out response
    console.log(`Account balance in RAW: ${accountInfo.balance}`);
})
```

### Success!

Given that you successfully authenticated, the account balance should now have been printed. 
