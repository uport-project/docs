---
title: "Getting Started"
index: 0
category: "guides"
type: "content"
---


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

Once you have downloaded the app, go ahead and create an identity. This identity will be resident on the `RINKEBY` Ethereum test network. You can create more identities on the same network or on other Ethereum networks (`ROPSTEN`, `KOVAN` and `MAINNET`) in the settings menu so you can test counterparty interactions on the **same network**.

## Register your App

Next we shall register an application on the blockchain.

When a users interacts with an app, they will desire to see relevant information, a picture, and any other helpful indicators on their transacation cards that this is the correct endpoint they wish to interact with. This registration process will create an identity for your app so that this becomes possible, and for your frontend to know where to listen to changes on the blockchain.

Let's go create an app over at the [uPort App Manager](https://appmanager.uport.me).

**Make sure to save the signing key somewhere secure! This will not be stored in browser for you for security reasons**.

## Install the Library/SDK

We now have the mobile uPort app and a registered application. Let's install the (uport-connect)[https://github.com/uport-project/uport-connect] and (mnid)[https://github.com/uport-project/mnid] libraries in our project.

**Please make sure you have (Node.js)[https://nodejs.org/en/] version 8 or higher installed**

uPort and its depending libraries are dependent on the Node.js ecosystem.

_Native (iOS & Android) Application libraries are in the works._

Go to your Terminal and `cd` to the root directory of your project folder.

From the root directory, install the two libraries with the Terminal commands below.

```bash
npm install --save uport-connect
```
```bash
npm install --save mnid
```

## Quickstart

Copy and paste this code into a new file.

```js
// index.js
const MNID = require('mnid')
const uportConnect = require('uport-connect');

const uport = new uportConnect.Connect('NAME_OF_DAPP', {
    clientId: 'CLIENT_ID',
    signer: uportConnect.SimpleSigner('SIGNING_KEY');
})

const web3 = uport.getWeb3()

export { web3, uport, MNID }
```

Next, go grab our keys from the [uPort App Manager](https://appmanager.uport.me).

**You may copy the code with the injected keys in the accordion at the bottom of your created app's page to help you get started quickly or you can follow the directions below.**

Update 'CLIENT_ID' and 'SIGNING_KEY' with our unique keys. 'NAME_OF_DAPP' can be changed to anything we would like.

Let's break down what is happening.

1.
```js
// index.js
const MNID = require('mnid')
const uportConnect = require('uport-connect');
```
We import the two require libraries, 'mnid' and 'uport-connect', that we installed and assign them variable names MNID and uportConnect respectively.

More information about the 'mnid' library can be found [here](https://github.com/uport-project/mnid)

2.
We need to instantiate the uPort object with an app's identity.

We then create an object from the `Connect` function and feed in the 'NAME_OF_DAPP', 'CLIENT_ID', and 'SIGNING_KEY'.

```js
const uport = new uportConnect.Connect('NAME_OF_DAPP', {
    clientId: 'CLIENT_ID',
    signer: uportConnect.SimpleSigner('SIGNING_KEY');
})
```
The clientID is the public address of your app and the signer (wrapped with the SimpleSigner function) is the signing key of your app that you will help create JWT tokens. These bits of information are given to you after registering an application.

3.

```js
const web3 = uport.getWeb3()
```

From the new uport connect object that we created in step 2, we access the web3 object which is used for interacting with the ethereum blockchain.

4.
```js
export { web3, uport, MNID }
```

Lastly, we export these objects from to be used later.

