# Getting Started

Welcome to the uPort usage guide!

Here we will walk you through all the necessary steps to get up and running with your first dapp.

Web 3.0 and decentralized applications _require a fundamental rethinking_ of the moving parts of the web so it is important to read everything or you may miss some important elements around the design decisions of what you are working with.

**Also please note**: these libraries are in progress and are subject to change. Gitter is a great place for the community to congregate and help each other. Lets get started.

## Download the Mobile App

Firstly, we will download the uPort mobile app.

The mobile app is where your [ECDSA private keys](https://blog.cloudflare.com/ecdsa-the-digital-signature-algorithm-of-a-better-internet/) are held (inside the secure enclave that's unlocked with your fingerprint). These keys are what controls the administrative layer between your device and the blockchain.

You will also have locally stored data in the app that is relevant to you such as your contacts and verified credentials. Essentially, the phone is an extension of you, and uPort is your internet native passport to the secure, decentralized web.

You can download the mobile app with one of the links below.

[uPort iOS](https://itunes.apple.com/us/app/uport-identity-wallet-ethereum/id1123434510?mt=8) | [uPort Android](https://play.google.com/store/apps/details?id=com.uportMobile)

Once you have downloaded the app, go ahead and create an identity. This identity will be resident on the `RINKEBY` Ethereum test network. You can create more identities on the same netowrk or on other Ethereum networks (`ROPSTEN` and `KOVAN`) in the settings menu so you can test counterparty interactions on the **same network**.

## Register your App

Next we shall regsiter an application on the blockchain.

When a users interacts with an app, they will desire to see relevant information, a picture, and any other helpful indicators on their transacation cards that this is the correct endpoint they wish to interact with. This registration process will create an identity for your app so that this becomes possible, and for your frontend to know where to listen to changes on the blockchain.

Let's go create an app over at the [uPort App Manager](https://developer.uport.me/myapps.html).

**Make sure to save the signing key somewhere secure! This will not be stored in browser for you for security reasons**.

## Install the Library/SDK

We now have the mobile uPort app and a registered application. Let's install the library in our project.

**Please make sure you have Node.Js and NPM installed**

uPort and its depending libraries are dependent on the Node.Js ecosystem.

_Native (iOS & Android) Application libraries are in the works._

Go to your Terminal and `cd` to your project folder.

```bash
npm install --save uport-connect
```

## Add your Keys

Now that we have the needed dependency, lets go grab our keys from the app manager.

**You may copy the code with the injected keys in the accordion at the bottom of your created app's page to help you get started quickly or you can follow the directions below.**

We need to instantiate the uPort object with an app's identity.

Lets create an object from the `Connect` function and feed in the App's name, id, and signing key.

```js
const uport = new Connect('NAME_OF_DAPP', {
  clientId: 'CLIENT_ID',
  signer: SimpleSigner('SIGNING KEY')
})
```

The clientID is the public address of your app and the signer (wrapped with the SimpleSigner function) is the signing key of your app that you will help create JWT tokens. These bits of information are given to you after registering an application.

**We should also export the `web3` and `MNID` objects from the resulting uport object for signing transactions later.**

```js
const web3 = uport.getWeb3()
export { web3, uport, MNID }
```          
