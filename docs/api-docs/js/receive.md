# Pocket a transaction

This section assumes you've completed [the previous step](/api-docs/js/). We will build on that code example. Next up we're
gonna do something more advanced:

1. Derive a new [Nano Seed] and an account for that seed
2. Send some funds to the new account
3. Get the new balance of the new account

## Create or import an account to use

The client provides a utility function to generate a Wallet and deriving keys locally:

```javascript
const wallet = client.generateWallet()
const account = wallet.accounts[0]
```
`generateWallet` also accepts a seed so that you can re-create the wallet and account deterministically as displayed below:

```javascript
const recreatedWallet = client.generateWallet('2EBB12AB10EFD2E540428004B5F5166CE52FEA7F44B4C656BD7CF61E1187B846')
```

## Send funds to the new account

Now you have to send funds to this new account. To get the address of this account:

```javascript
console.log(account.address) 
```

## Update account

After you know the transaction has happened, refresh the account by:

```javascript
client.receive(account)
    .then(updatedAccount => {
        console.log(updatedAccount) // shows the updated account
    })
```

## Success!

Given that funds were sent to the new address, the console should now list the updated balance.
