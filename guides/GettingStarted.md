---
title: "Getting Started"
index: 0
category: "guides"
type: "content"
---


# Getting Started

Welcome! The goal of this guide is to get you set up quickly with a skeleton project and to familiarize you with a few basic concepts.  If you have any questions or difficulties, head over to [Riot](chat.uport.me) and someone will help you out.

### Requirements

* [Node.js](https://nodejs.org/en/) version 8 or higher.

## 1. Get the uPort App

The primary way this app interacts with applications is by scanning QR codes during transactions like disclosing data, verifying previously disclosed information or sharing contacts for example.

Install the latest mobile client for your smartphone: [uPort iOS](https://itunes.apple.com/us/app/uport-identity-wallet-ethereum/id1123434510?mt=8) | [uPort Android](https://play.google.com/store/apps/details?id=com.uportMobile)

## 2. Get an Application Identity

By default, an identity will be created on the `RINKEBY` Ethereum test network which this guide assumes.

Much like the uPort app is used to create your uPort identity, using our Application Manager you can also create an **application** identity.

1. Navigate to [uPort App Manager](https://appmanager.uport.me) and authenticate/connect by scanning the QR code with the mobile client and approving the request.
2. Click "**Create An App**" and scan the next QR.  Approving the next request will create a proxy contract that your application will interact with and allow you to set attributes like an app name, logo, etc.
3. At the next screen fill out your application details and save the value stored in the address field.  It is the MNID/client ID for your application.
4. Click "**Click Here for your App Code**".  The signing key will be a string passed to a SimpleSigner object like `SimpleSigner('bb10b3da70af3cccc804279f9b5085902afdb33da5fd8a55f6eb31818b94343')`.  Save this string somewhere safe.  It is your application's private key.

**Note:** *This signing (private) key should be protected.  Do not distribute it publicly.  We display the private key in our demos, guides, and tutorials for an educational purpose and recommend that you use your own signing key and application identifier (MNID) in place of the ones we provide for reference.*

## 3. Setup Dependencies

From the root of your project folder:
```bash
npm init
npm install --save uport-connect
npm install --save qrcode-terminal
```
* A. Create a vanilla node.js project.
* B. Install [uport-connect](https://github.com/uport-project/uport-connect).
* C. Install [qrcode-terminal](https://www.npmjs.com/package/qrcode-terminal).  This is not a required dependency for uport-connect.  We are using it to demonstrate QR-code functionality.

These are the minimum dependencies you'll need for this getting started guide.

## 4. Configure and Run Code

Copy/paste this code into a new javascript file in the project's directory.

```js
const uportConnect = require('uport-connect');
const qrcode = require('qrcode-terminal');

const mnidAddress = 'CLIENT_ID';
const signingKey = 'SIGNING_KEY';
const appName = 'NAME_OF_DAPP';

const uriHandler = (uri) => {
  qrcode.generate(uri, {small: true})
  console.log(uri)
}

const uport = new uportConnect.Connect(appName, {uriHandler,
    clientId: mnidAddress,
    network: 'rinkeby'
    signer: uportConnect.SimpleSigner(signingKey)
});

// Request credentials
uport.requestCredentials({
  requested: ['name'],
}).then((credentials) => {
  console.log(credentials);
})
```

Update *'CLIENT_ID'* and *'SIGNING_KEY'* with the application identifier (MNID) and private signing key that were obtained from the application manager. Replace `NAME_OF_DAPP` with a string that you want to represent the name of the application.  This name will be shown when requests are made with this application identity.

Let's break down what is happening.

```js
const uriHandler = (uri) => {
  qrcode.generate(uri, {small: true})
  console.log(uri)
}
```

Here we provide a simple function that takes a URI string and returns a QR image.  This will be passed as a handler function for the resulting URI that is generated during a request for credentials.

```js
const uport = new uportConnect.Connect('NAME_OF_DAPP', {
    uriHandler,
    clientId: mnidAddress,
    network: 'rinkeby',
    signer: uportConnect.SimpleSigner('SIGNING_KEY');
})
```

Next we create an object from the `Connect` function by passing in the application name, the handler function `uriHandler`, and an object with `mnidAddress` and `signingKey` assigned as values to `cliendId:` and `signer:`.  If a network is not specified *Rinkeby* will be the default.

```js
uport.requestCredentials({
  requested: ['name'],
})
.then((credentials) => {
  console.log(credentials);
})
```

Next we make a request with the configured connect object for a mobile user's name.  The public identifier (MNID) of the mobile identity is also requested by default.  `requestCredentials` will generate a URI and pass it to the function `uriHandler` that was utilized when creating the `uport` connect object.  Remember the `uriHandler` will take a URI display it in the form of a QR code.  The function returns a promise that will print the response to the console.

Running this example from a terminal `node <your file name>.js`, you should see a QR code.  Scan this code with the uPort mobile client or your mobile device's native scanner app to see the response returned by the request.

That's it!  Please check out our other guides and tutorials for more examples of how you can expand this code to do other things, like [Signing Transactions](https://developer.uport.me/signtransactions), or [Attesting Credentials](https://developer.uport.me/attestcredentials).

As always, if you have any questions or issues getting started please reach out to us on [Riot](chat.uport.me) or open an issue on [Github](https://github.com/uport-project).
