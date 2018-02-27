---
title: "Attesting Credentials"
lesson: 1
chapter: "Attesting Credentials"
cover: "https://unsplash.it/400/300/?random?BoldMage"
date: "01/01/2017"
category: "guides"
type: "lesson"
tags:
    - programming
    - stuff
    - other
---

# Attesting Credentials

One of the core needs of Web 3.0 is to build trust in a self-sovereign world. We establish facts which are not mathematically derived by social consensus. To create social consensus, actors must attest to things being true. We can do this with uPort using the `uport.attestCredentials` function.

**NOTE:** Currently only one credential can be pushed at a time. We are working to fix this soon.

## Calling the attest method

```js
uport.attestCredentials({
  sub: 'THE_RECEIVING_UPORT_ID',
  claim: { CUSTOM_PROPERTY: PROPERTY_VALUE },
})
```

## Setting an expiration date

We can also optionally add an expiration date.

```js
uport.attestCredentials({
  sub: 'THE_RECEIVING_UPORT_ID',
  claim: { CUSTOM_PROPERTY: PROPERTY_VALUE },
  exp: new Date().getTime() + 30 * 24 * 60 * 60 * 1000,  // Optional expiration
})
```

## Attesting multiple credentials

**Under construction**
