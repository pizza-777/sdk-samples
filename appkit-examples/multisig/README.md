# How to deploy your wallet and make a transfer
In this example we use [AppKit package](https://github.com/tonlabs/appkit-js) to deploy a [multisig contract](https://github.com/tonlabs/ton-labs-contracts/blob/master/solidity/safemultisig/) into [Developer Network](https://net.ton.live/) and then make a transfer from it.  

You can update the scripts to [work with other networks](https://docs.everos.dev/ever-platform/reference/graphql-api/networks), for example, with Everscale.

## Prerequisite

* Node.js >= [14.x installed](https://nodejs.org)
* Optional [Docker](https://docs.docker.com/desktop/#download-and-install) - if you want to use local blockchain Evernode SE

## Before running the example

-   Create a project on [dashboard.evercloud.dev](https://dashboard.evercloud.dev) if you don't have one.
-   Remember its Development Network HTTPS endpoint.
-   Pass this endpoint as a parameter when running scripts.


In order to do it, perform these steps:

1. Make preparations.
2. Deploy contract.
3. Transfer tokens.
Below we describe each of the steps in more detail.

## Make preparations

You can find the source code in `preparation.js`. In order to run it, use:

```sh
npm i
node preparation.js <HTTPS_DEVNET_ENDPOINT>
```

In this step, the script will do the following:

1. Generates an seed phrase based on the dictionary and the specified number of words.
2. Generates a public/private key pair based on the seed phrase.
3. Save keys and seed phrase to files.
4. Show you the address of the future contract

After the step 4 you will need to sponsor this address with tokens in your network before proceeding with `Deploy` instruction. If you work in Developer Network, you may ask for test tokens (so-called Rubies) in mobile TON Surf version.

## Deploy contract

You can find the source code in `deploy.js`. In order to run it, use:
                                         
```sh
node deploy.js <HTTPS_DEVNET_ENDPOINT>
```

In this step we use the key pair to deploy the contract. Before performing this step you need to ensure you have
at least 0.5 tokens on your future wallet address.

## Transfer tokens

You can find the source code in `work-with-multisig.js`. In order to run it, use:
                                                     
```sh
node work-with-multisig.js <HTTPS_DEVNET_ENDPOINT>
```

In this step we:

1. Get the custodians list.
2. Send a transaction to transfer 0.1 token to pre-defined address.
3. Output sent transaction information.
