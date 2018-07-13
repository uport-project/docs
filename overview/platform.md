---
title: "Platform"
index: 2
category: "overview"
type: "content"
source: "https://github.com/uport-project/docs/blob/develop/overview/platform.md"
---

# PLATFORM

The uPort Platform is our implementation of the uPort Protocol designed to make decentralized identities on Ethereum easy to create and use for developers and users. uPort's modular, open-source components can easily support any Ethereum network, and are available for you to use today.

## **Ethereum Identity Components**:
Decentralized identity infrastructure for the Ethereum network, implemented as smart contracts.

* _[Identities](https://github.com/uport-project/uport-identity)_: uPort IDs and accounts on the Ethereum network. Current version is a Proxy Contract.

* _[Identity Manager](https://github.com/uport-project/uport-identity/blob/develop/docs/identityManager.md):_ Exists to provide a simple way to create and manage identities on Ethereum. Current version is called MetaIdentityManager.

* _[Claims Registry](https://github.com/ethereum/EIPs/issues/780):_ A general purpose registry where identities can send claims messages for permanent public record. Registry contracts provide a PKI mechanism for identities to publicly claim their official uPort Document, containing critical PKI information and other metadata, in a way that can be publicly searched and discovered by other participants on the network. Actually, registry contracts can be used to store any kind of public claim. Current version is called the Ethereum Claims Registry and we submitted it for consideration as an Ethereum standard in ERC 780.


## **Network Microservices**:
Hosted web services that make using the uPort network simpler. The goal is for these services to be replaced by decentralized alternatives as they become more feasible.

* _Nodes:_ Cloud node infrastructure required to access various decentralized networks. Improves usability for end users. Operated by Infura (http://infura.io/), another ConsenSys project.

* _[Messaging](https://github.com/uport-project/specs/blob/65c1b3171aa1a83ae918fbf3b57d90c24e779bc0/transports/index.md#messaging-server):_ Message service that allows communication between uPort clients. Current implementations are called Chasqui (message queue), and Pututu (mobile push).

* _Fueling:_ Background service that funds network transactions without the user needing to interact with network fees, such as gas. Solves a major onboarding and usability hurdle for mainstream adoption. Current implementation is called Sensui.

* _Backup:_ Exists to provide a secure backup solution to private identity data. Current implementation is called Caleuche.

* _Identity Creation:_ Exists to provide an easy way to create uPort identities on the network. Current implementation is called Unnu.


## **Libraries**:
Open source libraries for developers to quickly start integrating with the uPort network.

* _[uPort Connect](https://github.com/uport-project/uport-connect)_: Enables web applications to communicate with uPort Wallet. Desktop web applications transport messages via QR codes and push notifications, while mobile web applications use applinks.

* _[uPort Identity](https://github.com/uport-project/uport-registry):_ Provides a library of uPort identity code including identities, identity managers, and more.

* _[uPort Credentials](https://github.com/uport-project/uport-js):_ Makes it easy to generate JWT Statements, including request tokens and credentials. This is currently wrapped in the uPort JS library.

* _[uPort JWT](https://github.com/uport-project/uport-js):_ Makes it easy to verify signatures against the uPort PKI. This is currently wrapped in the uPort JS library.

* _uPort Mobile SDK:_ Native mobile libraries for uPort-enabled mobile applications. Coming soon.
