# Specs

 _[uPort Platform Specifications](https://github.com/uport-project/specs):_ uPort's platform specification repository.

## **Flows**
 _[uPort Request Flows](https://github.com/uport-project/specs/blob/develop/flows/index.md):_
 * _[Selective Disclosure Flow](https://github.com/uport-project/specs/tree/develop/flows/selectivedisclosure.md)_
 * _[Send Verification Flow](https://github.com/uport-project/specs/tree/develop/flows/verification.md)_
 * _[Ethereum Transaction Request Flow](https://github.com/uport-project/specs/tree/develop/flows/tx.md)_
 * _[Private Chain Provisioning Flow](https://github.com/uport-project/specs/tree/develop/flows/privatechain.md)_


## **Messages**
 _[Off-chain messages](https://github.com/uport-project/specs/blob/develop/messages/index.md):_ There are several standard message types that the uPort mobile app knows how to handle or create
 * _[Selective Disclosure Request](https://github.com/uport-project/specs/blob/develop/messages/sharereq.md):_ for asking private data from a user
 * _[Selective Disclosure Response](https://github.com/uport-project/specs/blob/develop/messages/shareresp.md):_ signed by the app as a response to a Selective Disclosure Request
 * _[Verification](https://github.com/uport-project/specs/blob/develop/messages/verification.md):_ signed claim by one party about another party
 * _[Private Chain Provisioning Message](https://github.com/uport-project/specs/blob/develop/messages/privatechain.md):_ for provisioning an identity on a private Ethereum chain


## **PKI**
  _[uPort PKI](https://github.com/uport-project/specs/blob/develop/pki/index.md):_ uPort implements a simple yet general purpose decentralized PKI system, making it easy to create and verify off-chain JWT messages.
  * _[Identity Document](https://github.com/uport-project/specs/blob/develop/pki/identitydocument.md):_ The Identity document is stored on IPFS and tied to the address using the uport registry


## **Rest APIs**
  * _[Fuel Server](https://github.com/uport-project/specs/blob/develop/rest-apis/fuel-server.md):_ We support a transaction fueling service, which will be called if the users account does not have enough funds available to fuel the transaction
  * _[Relay Server](https://github.com/uport-project/specs/blob/develop/rest-apis/relay-server.md)_ We support meta transactions which allows a 3rd party transaction fueling service to fund and relay transactions without requiring pre-funding the users account.


## **Transports**
 * _[Request/Response Transports](https://github.com/uport-project/specs/blob/develop/transports/index.md#requestresponse-transports):_ Requests always consist of URLs that are handled by the mobile app. Responses are sent to the callback url included with the Request.
 * _[Push Notification Transport](https://github.com/uport-project/specs/blob/develop/transports/push.md):_ Push notifications is a transport for sending requests to users.
