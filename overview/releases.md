---
title: "Releases"
index: 100
category: "overview"
type: "content"
announcement: "Updates required for Uport Connect and Uport JS!  Visit developers.uport.me/releases for more information."
source: "https://github.com/uport-project/docs/blob/develop/overview/releases.md"
---

## Uport Connect

### *What's New in Version [uport-connect@0.7.5](https://github.com/uport-project/uport-connect/releases/tag/v0.7.5)*

* Backward compatible Ethr-DID response support that allows communication with IDs created with the ethr-did registry in the upcoming uPort mobile client release.
* Use the networkAddress key/value received in responses for all blockchain interactions if you have not already switched from using the address key/value. A networkAddress will continue to be a MNID encoded address for the network your app is configured for. It you are using the uPort subProvider this already happens by default. Continue to use the address key/value as you have for all other interactions (i.e as the subject for attestations issued). In the transition to DIDs the address key/value in a response may be a DID or MNID, but the libraries will set this appropriately to support both new and old mobile app identities.

### *Steps to migrate*

* npm install uport-connect
* Use networkAddress key/value in response for all blockchain interactions instead of address key/value if you have not switched already. Continue to use address key/value for all other interactions (i.e attestations). This change may not be required, its dependent on your current implementation.

### *Legacy support*

* Versions _[0.7.3](https://github.com/uport-project/uport-connect/tree/v0.7.3)_ and earlier will continue to work with all uPort Mobile clients until the uPort Mobile clients with DID support are released in August (exact date listed once known).
* Once the new uPort Mobile clients are released, these clients will only work with versions 0.7.5 and later minor versions of uport-connect.
* 0.7.5 and later minor versions will remain backwards compatible, working with both current uPort Mobile clients and future releases.

## Uport JS

### *What's New in Version uport@0.6.3*

* Backward compatible Ethr-DID response support that allows communication with IDs created with the ethr-did registry in the upcoming uPort mobile client release.
* Use the networkAddress key/value received in responses for all blockchain interactions if you have not already switched from using the address key/value. A networkAddress will continue to be a MNID encoded address for the network your app is configured for. It you are using the uPort subProvider this already happens by default. Continue to use the address key/value as you have for all other interactions (i.e as the subject for attestations issued). In the transition to DIDs the address key/value in a response may be a DID or MNID, but the libraries will set this appropriately to support both new and old mobile app identities.


### *Steps to migrate*

* npm install uport
* Use networkAddress key/value in response for all blockchain interactions instead of address key/value if you have not switched already. Continue to use address key/value for all other interactions (i.e attestations). This change may not be required, its dependent on your current implementation.

### *Legacy support*

* Versions _[version 0.6.2](https://github.com/uport-project/uport-js/tree/v0.6.2)_ and earlier will continue to work with all uPort Mobile clients until the uPort Mobile clients with DID support are released in August (exact date listed once known).
* Once the new uPort Mobile clients are released, these clients will only work with versions 0.6.3 and later minor versions of uport-connect.
* 0.6.3 and later minor versions will remain backwards compatible, working with both current uPort Mobile clients and future releases.
