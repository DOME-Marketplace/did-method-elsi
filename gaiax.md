The credential will include a claim like this:

```
<https://www.goodair.com/employee/{employeeSerialNumber}?hl=zQmWvQxTqbG2Z9HPJgG57jjwR154cKhbtJenbyYTWkjgF3e> dvp:isRepresentativeFor <https://www.goodair.com/.wellknown/VATES-12345678?hl=zQhdud7ud7wdnwd9n6de6dhee6e6eje6j>
```

And the signature/seal of the credential is done with an eIDAS certificate (either a certificate for ESeal or a certificate for ESig).

## A little bit about eIDAS certificates for ESeal and ESign

Those certificates have several fields which are relevant for the verifications that will be explained later.

An example of fields about the subject for a certificate of representation (certificate for ESig issued to a natural person acting as representative of a legal person):

```
cn = 56565656V Jesus Ruiz
serialNumber = 56565656V
givenName = Jesus
sn = Ruiz
2.5.4.97 = VATES-12345678
o = GoodAir
c = ES
2.5.4.13 = Notary:Juan Lopez/Protocol Num:7172/Date:07-06-2021
```

And an example of a certificate for ESeal:

```
2.5.4.97 = VATDE-170173453
CN = DRV QC 11 MA CA 2017ca
OU = QC 11 Mitarbeiter CA
O = Deutsche Rentenversicherung Westfalen
C = DE
```

In both types of certificates the number `2.5.4.97` is the official OID for the unique `organizationIdentifier` of the target legal person (the Participant).

In the case of a certificate of representation, the certificate includes additionally information about the legal representative (the `cn`, `sn`, `givenName` and `serialNumber` fields above).

Before issuing a certificate like the ones above, the QTSP has to perform some validations (typically in the official business trade register of the relevant country) to ensure that in the official source of truth there is already registered information about the legal entity and the legal representative (in the case of certificates of representation).

Given the special role of QTSPs in the eIDAS framework and the properties of eIDAS advanced/qualified signatures and seals, a document signed/sealed with such signatures enjoys the **presumption of non-repudiation** in the sense that the validity of the signature/seal can not be challenged in the courts, providing a high level of legal certainty. In other words, using eIDAS certificates avoids things like this: [Canadian judge rules thumbs-up emoji can represent contract agreement](https://www.theguardian.com/world/2023/jul/06/canada-judge-thumbs-up-emoji-sign-contract).

That means that those documents are legally bound to the real-world entities with the unique identifier `organizationIdentifier`, and they can not repudiate them.

## About the ODRL statement inside the credential

Let's assume that the credential includes a claim like:

```
<https://www.goodair.com/employee/{employeeSerialNumber}?hl=zQmWvQxTqbG2Z9HPJgG57jjwR154cKhbtJenbyYTWkjgF3e> dvp:isRepresentativeFor <https://www.goodair.com/.wellknown/VATES-12345678?hl=zQhdud7ud7wdnwd9n6de6dhee6e6eje6j>
```

Where the first therm is the [Cryptographic Hyperlink](https://w3c-ccg.github.io/hashlink/) of the credential resolved at the associated URL corresponding to the specific employee in the rule, with the given `serialNumber`.

And the third term is the Cryptographic Hyperlink of the credential resolved at the associated URL corresponding to a specific legal entity.

The third term in the ODRL rule inside the credential has the following URI about the issuer (the same entity that signs the credential with the eIDAS certificate):

```
https://www.goodair.com/.wellknown/VATES-12345678?hl=zQhdud7ud7wdnwd9n6de6dhee6e6eje6j
```

The parameter `hl` is the hash of the document retrieved when the URL is resolved.
The last part of the path MUST be equal to the `organizationIdentifier` inside the certificate used to sign the credential.
Only the entity controlling the private key of the eIDAS certificate can make both organizationIdentifiers identical (the one in the path and the one in the certificate that signed/sealed the credential)

The above statement is saying:

1. The entity controlling the eIDAS certificate with organizationIdentifier `VATES-12345678` states that the natural person identified in the first term is a representative of the entity with `organizationIdentifier` equal to `VATES-12345678`. Only the the real-world entity with the given `organizationIdentifier` can make goth identifiers the same.
2. A credential located at that URL contains information about the legal entity, and it was attested to be true at the time of the signature by the legal entity signing the credential (this is a legally binding statement).

The Cryptographic hyperlinks ensure that the linked credentials have not been modified since the main credential was signed, and are effectively includes in the legally binding statement.

Note: In order to fully comply with the eIDAS2 regulation, the signature has to be performed using the JAdES format (JSON Advanced Electronic Signature), but in Gaia-X the signatures are using LD-Proofs. In any case, the important thing is that inside the credential, signed with the certificate, there is a claim with the right information.