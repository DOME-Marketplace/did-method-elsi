# DID ETSI Legal person Semantic Identifier Method Specification (`did:elsi`)

This repository contains the `did:elsi` DID Method Specification.

This is a DID method for **legal persons**, bridging the world of the eIDAS regulation with the world of W3C Verifiable Credentials, maximising at the same time regulatory compliance and decentralisation.

> **Note**
> Natural persons MUST not use this DID method, or for that matter, any DID method that registers anything related to personal information in any type of Verifiable Registry or shared data store.
>
> A good DID method for natural persons is `did:key` which is a perfect complement to `did:elsi` to build ecosystems that maximise privacy, regulatory compliance, safety, scalability, and decentralisation. 

Any legal person than can operate in the digital economy and that can digitally sign a document using an advanced or qualified e-seal valid in the EU (like an invoice or a contract) has already a DID identifier under the `did:elsi` method without any further action and which can be used without any intervention by any third party.

The identifiers in this DID method are based on the unique identifiers that are already used in the eIDAS certificates that comply to the relevant ETSI standards for electronic signatures and seals. This is in contrast to most other did methods, which invent identifiers and mechanims that are not well integrated with the legal framework and which are not in general legally recognised in the EU for economic transactions (e.g., that can be used in electronic invoices across the EU).

The `did:elsi` method is intented to be used in W3C Verifiable Credentials which, when signed using JAdES digital signatures, can be used to meet the requirements of electronic signatures, advanced electronic signatures, qualified electronic signatures, electronic seals, advanced electronic seals, and qualified electronic seals as defined in Regulation (EU) No 910/2014 (eIDAS).

Whith this approach, SSI ecosystems can use W3C Verifiable Credentials that have the same legal status as any other document which uses advanced or qualified digital signatures and seals, and so can replace easily other documents in less efficient formats, like signed PDFs.

## Documentation

The online document is available at https://DOME-Marketplace.github.io/did-method-elsi/ and the source for the document is in [index.rite](index.rite) in this repository.

The document is written in [`rite`](https://hesusruiz.github.io/rite/), a simple way to write specifications based on ReSpec.

We encourage contributions preferably via the creation of issues and pull requests in the GitHub repository.