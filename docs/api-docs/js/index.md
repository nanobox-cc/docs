# Introduction

Any request to the Nanobox API can be crafted manually. However, we provide a simple [nano client](https://github.com/nanobox-cc/nano-client) to help with the setup.
Using this is fully optional and requests to Nanobox can be crafted by hand as well.

# Setup

## Dependencies

In your Javascript project, install the [nanobox nano client](https://github.com/nanobox-cc/nano-client) dependency. With yarn:
    
    $ yarn add @nanobox/nano-client

Or with NPM

    $ npm install @nanobox/nano-client

## Initialize client

```javascript
import { NanoClient } from "@nanobox/nano-client";

const client = new NanoClient({
    url: "https://api.nanobox.cc",
    // Supply your credentials from Nanobox
    // credentials: { username: 'username', password: 'password' }
})
```

## List transactions

We're going to list the last transactions for a given account:

```javascript
// The account address we want to fetch
const account = 'nano_1x7biz69cem95oo7gxkrw6kzhfywq4x5dupw4z1bdzkb74dk9kpxwzjbdhhs'

// Construct promise based request
client.getTransactions(account)
    .then(transactions => {
        console.log(transactions)
    })
```

## Success!

Given that you successfully authenticated, the last transactions for this account should now have been listed.
You can continue to the [the next step](/api-docs/js/transaction) where we craft our first transaction.
