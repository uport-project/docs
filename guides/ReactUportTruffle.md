---
title: "React-Uport Truffle Box"
index: 3
category: "tutorials"
type: "content"
source: "https://github.com/uport-project/docs/blob/develop/guides/ReactUportTruffle.md"
---

# React-uport Truffle box

This a short tutorial to requesting credentials and signing attestations with uPort.  We will be leveraging the [react-uport truffle box](http://truffleframework.com/boxes/react-uport) which provides a powerful framework and tools for getting started.

## Setup React Truffle Box

Download react-uport truffle box and follow instructions on [http://truffleframework.com/boxes/react-uport](http://truffleframework.com/boxes/react-uport) to set up.

If everything is working correctly, we should see the homepage load when running the project locally.

## Create the necessary uport-connect objects

The first thing we need to do is create an instance of the uport-connect object for signing transactions and issuing attestations.

Open up the connectors.js file found in 'src/util/connectors.js'.

From the [uPort AppManager](https://appmanager.uport.me/), copy and paste the import statement and the code for creating the uport-connect object. 'NAME_OF_APP', 'YOUR_ADDRESS' and 'YOUR_SIGNING_KEY' in the example below will come pre-populated.

Next, specify the network we will use. The code allows you to choose from 'rinkeby or ropsten or kovan'. We will use 'rinkeby'.

Lastly, export the newly created uport-connect object so we can access it later from other components in the project.

After making the modifications, the connectors.js file should look like this.

```js

import { Connect, SimpleSigner } from 'uport-connect'

export const uport = new Connect('NAME_OF_APP', {
  clientId: 'YOUR_ADDRESS',
  network: 'rinkeby or ropsten or kovan',
  signer: SimpleSigner('YOUR_SIGNING_KEY')
})

```

## Request a user's information

The react-uport truffle box already makes a call to the uPort requestCredentials function to login.

Code to reference can be found in 'src/user/ui/loginbutton/LoginButtonActions.js'.

```js

import { uport } from './../../../util/connectors.js'
import { browserHistory } from 'react-router'

export const USER_LOGGED_IN = 'USER_LOGGED_IN'
function userLoggedIn(user) {
  return {
    type: USER_LOGGED_IN,
    payload: user
  }
}

export function loginUser() {
  return function(dispatch) {
    // UPort and its web3 instance are defined in ./../../../util/wrappers.
    // Request uPort persona of account passed via QR
    uport.requestCredentials().then((credentials) => {
      dispatch(userLoggedIn(credentials))

      // Used a manual redirect here as opposed to a wrapper.
      // This way, once logged in a user can still access the home page.
      var currentLocation = browserHistory.getCurrentLocation()

      if ('redirect' in currentLocation.query)
      {
        return browserHistory.push(decodeURIComponent(currentLocation.query.redirect))
      }

      return browserHistory.push('/dashboard')
    })
  }
}

```

Now that we have exported the uport-connect object in the connectors.js file, this code should work.

Run the project on localhost and try logging in with the [uport mobile app](https://developer.uport.me/clients#u-port-mobile-wallet) on the top right.

## Create an Attestation

Creating an attestation requires two parts. First, we must request information from the user. This allows us to identify the uport identity to send the attestation to. We can also perform multiple checks here to verify this user should receive the attestation. After verifying the user, we can then create an attestation and pass it along to them.

We will be creating a new react component for this functionality. Create a new file in 'src/user/ui' and call it AttestButton.js.

First, import react and the uport-connect object we created previously.

```js

import React, { Component } from 'react'
import { uport } from './../../../util/connectors.js'

```

Next, create the component structure and add a button to the render method. We are adding an onClick action to run the attest method which will hold our code for requesting and attesting.

```js

class AttestButton extends Component {
    attest(){
    }

    render(){
        return(
            <a href="#" className="pure-menu-link" onClick={this.attest()}>Attest</a>
          )
    }
}
export default AttestButton

```

In the attest method, create a request for a user's uport identity information

```js

attest(){
    uport.requestCredentials().then((credentials) => {
        // Can verify the uport user is verified with the returned 'credentials' object.
    })
}

```

After verifying the uport users identity, we can issue an attestation. For this example, we will issue an attestation confirming a uport users attendance to an event. Add the additional code below into the callback of the requestCredentials function.

```js

attest(){
    uport.requestCredentials().then((credentials) => {
        // Can verify the uport user is verified with the returned 'credentials' object.
        var d = new Date();
        var month = ['Jan', 'Feb','Mar','Apr','May','June','July','Aug','Sept','Oct','Nov', 'Dec'];
        uport.attestCredentials({
          sub: credentials.address,
          claim: {
            "Event": "Ethereal Summit Conference",
            "Date": month[d.getMonth()] + " " + d.getDate() + "," + d.getFullYear(),
            "Details": "Proof of Attendance"
          }
        })
      })
}

```

For this demo, we will include the component we just created on the home page.

Navigate to 'src/layouts/home/Home.js'. At the top, we can add the following line of code to import our new component.

```js

import AttestButton from './../../user/ui/AttestButton'

```

Include the component somewhere on the page with '<AttestButton/>'.

## Wrapping it up

We now have a component that can request information and issue attestations. Two of the core features of the uport platform. For more details about uport libraries [explore our documentation](https://developer.uport.me/gettingstarted).
