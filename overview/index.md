# uPort

## Overview

uPort is an interoperable identity network for a secure, private, decentralized web.

uPort provides open protocols for decentralized identity and interoperable messaging that enable trusted source attribution for all web communication. By allowing message recipients to trust message senders without centralized servers, we can create an entirely new framework for building applications.

uPort returns ownership of identity to individuals. uPort's open identity network allows users to register their own identity on Ethereum independent from any centralized authority. This decentralized model of identity forms the foundation for a user-centric data network, where users own and manage their personal data in privacy. On uPort, users are always in control of their data and they are free to share it with whomever they choose.

uPort provides a standard interface to decentralized identity that bridges networks to create a universal, public-private web-of-trust. uPort identities are simply defined as addresses registered on public, permissionless networks. These addresses are controlled by private keys that sign messages, which can be sent to any destination. Identities are further expressed by a combination of publicly and privately available data. This simple model enables multi-network interoperability and identity standards compliance.

uPort makes it easy to build with decentralized identity on Ethereum. uPort's open source components are simple to use and can support a variety of use case architectures. uPort has been designed to meet demanding usability, flexibility, and interoperability requirements.

uPort decentralizes identity control from centralized custodians and data silos to the edges of the network. In doing so, uPort lays the foundation for a radically free, equitable, p2p, user-centric internet society. Applications, networks, and societies that value decentralization, privacy, or security should consider integrating with the uPort network.


## Components

#### PROTOCOLS

uPort consists of identity and messaging protocols that together form an interoperable identity layer for the decentralized web. uPort Identity Protocol describes a generalized identity model capable of expressing humans, businesses, applications, IoT devices, AI, and more. uPort Claims Protocol describes a standard message format that enables source attribution and that facilitates interoperability between various blockchain and identity networks. Together, these protocols form a common architecture and interface for decentralized identity that is capable of becoming a universal web standard.

**uPort Identity Protocol**

* Identities: An address on a decentralized network, controlled by a private signing key.
* PKI: Decentralized public key infrastructure (PKI) that enables signature validation.

**uPort Claims Protocol**

* Message Format: Standards for constructing claims messages.
* Statements: Message payload data formats. Currently supports JWTs and Ethereum transactions.

The uPort Protocol is compatible with the Decentralized Identifier (DID) specification created through the Rebooting Web of Trust workshops as well as the identity related standardization efforts by the Decentralized Identity Foundation and the W3C Credentials Community group.

_What's not included?_
Specifications on where identity data and private keys are stored, and more. We don't include them in the core uPort protocols because we believe these features can be implemented as modules that support the underlying standards. Our platform, detailed below, provides simple solutions for private key and data management.



#### PLATFORM

The uPort Platform is our implementation of the uPort Protocol designed to make decentralized identities on Ethereum easy to create and use for developers and users. uPort's modular, open-source components can easily support any Ethereum network, and are available for you to use today.

**Ethereum Identity Components:** Decentralized identity infrastructure for the Ethereum network, implemented as smart contracts.

* _[Identities](https://github.com/uport-project/uport-identity)_: uPort IDs and accounts on the Ethereum network. Current version is a Proxy Contract.

* _[Identity Manager](https://github.com/uport-project/uport-identity/blob/develop/docs/identityManager.md):_ Exists to provide a simple way to create and manage identities on Ethereum. Current version is called MetaIdentityManager.

* _[Claims Registry](https://github.com/ethereum/EIPs/issues/780):_ A general purpose registry where identities can send claims messages for permanent public record. Registry contracts provide a PKI mechanism for identities to publicly claim their official uPort Document, containing critical PKI information and other metadata, in a way that can be publicly searched and discovered by other participants on the network. Actually, registry contracts can be used to store any kind of public claim. Current version is called the Ethereum Claims Registry and we submitted it for consideration as an Ethereum standard in ERC 780.


**Network Microservices:** Hosted web services that make using the uPort network simpler. The goal is for these services to be replaced by decentralized alternatives as they become more feasible.

* _Nodes:_ Cloud node infrastructure required to access various decentralized networks. Improves usability for end users. Operated by Infura (http://infura.io/), another ConsenSys project.

* _[Messaging](https://github.com/uport-project/specs/blob/65c1b3171aa1a83ae918fbf3b57d90c24e779bc0/transports/index.md#messaging-server):_ Message service that allows communication between uPort clients. Current implementations are called Chasqui (message queue), and Pututu (mobile push).

* _Fueling:_ Background service that funds network transactions without the user needing to interact with network fees, such as gas. Solves a major onboarding and usability hurdle for mainstream adoption. Current implementation is called Sensui.

* _Backup:_ Exists to provide a secure backup solution to private identity data. Current implementation is called Caleuche.

* _Identity Creation:_ Exists to provide an easy way to create uPort identities on the network. Current implementation is called Unnu.


**Libraries:** Open source libraries for developers to quickly start integrating with the uPort network.

* _[uPort Connect](https://github.com/uport-project/uport-connect)_: Enables web applications to communicate with uPort Wallet. Desktop web applications transport messages via QR codes and push notifications, while mobile web applications use applinks.

* _[uPort Identity](https://github.com/uport-project/uport-registry):_ Provides a library of uPort identity code including identities, identity managers, and more.

* _[uPort Credentials](https://github.com/uport-project/uport-js):_ Makes it easy to generate JWT Statements, including request tokens and credentials. This is currently wrapped in the uPort JS library.

* _[uPort JWT](https://github.com/uport-project/uport-js):_ Makes it easy to verify signatures against the uPort PKI. This is currently wrapped in the uPort JS library.

* _uPort Mobile SDK:_ Native mobile libraries for uPort-enabled mobile applications. Coming soon.


**Clients (apps)**

Allow users, developers, and applications to interact with the uPort platform.

* _[uPort Mobile Wallet](https://itunes.apple.com/us/app/uport-id/id1123434510):_ Secure mobile self-sovereign identity wallet for end users to create their identity, manage their data, and approve requests.

* _[uPort App Manager](http://developer.uport.me/myapps.html):_ Web client for developers to manage the uPort identity of their applications.

* _[uPort JS Client](https://github.com/uport-project/uport-js-client):_ JavaScript client for developers to interact with the uPort Platform. Built for testing and development. Can create identities, handle messages, execute signatures, and more.
