---
title: "Protocols"
index: 3
chapter: "Protocol"
cover: "https://unsplash.it/400/300/?random?BoldMage"
date: "01/01/2017"
category: "overview"
type: "content"
tags:
    - programming
    - stuff
    - other
---


# PROTOCOLS

uPort consists of identity and messaging protocols that together form an interoperable identity layer for the decentralized web. uPort Identity Protocol describes a generalized identity model capable of expressing humans, businesses, applications, IoT devices, AI, and more. uPort Claims Protocol describes a standard message format that enables source attribution and that facilitates interoperability between various blockchain and identity networks. Together, these protocols form a common architecture and interface for decentralized identity that is capable of becoming a universal web standard.

## **uPort Identity Protocol**

* Identities: An address on a decentralized network, controlled by a private signing key.
* PKI: Decentralized public key infrastructure (PKI) that enables signature validation.

## **uPort Claims Protocol**

* Message Format: Standards for constructing claims messages.
* Statements: Message payload data formats. Currently supports JWTs and Ethereum transactions.

The uPort Protocol is compatible with the Decentralized Identifier (DID) specification created through the Rebooting Web of Trust workshops as well as the identity related standardization efforts by the Decentralized Identity Foundation and the W3C Credentials Community group.

_What's not included?_
Specifications on where identity data and private keys are stored, and more. We don't include them in the core uPort protocols because we believe these features can be implemented as modules that support the underlying standards. Our platform, detailed below, provides simple solutions for private key and data management.
