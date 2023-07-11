# Natural Person representing Legal Person

## Introduction

Regulation (EU) No 910/2014 (eIDAS) refers to representation of persons in Article 3 (1), explicitly stating **a natural person representing a legal person**. 

However, as in practice there may be more cases of representation, the eIDAS technical specifications have been amended to cover all scenarios of a natural persons or a legal persons representing another natural person or a legal
person. Explanation can be found in Section 2.8. NATURAL AND LEGAL PERSON REPRESENTATIVE from [eIDAS SAML Attribute Profile V1.2](https://ec.europa.eu/digital-building-blocks/wikis/download/attachments/467109280/eIDAS%20SAML%20Attribute%20Profile%20v1.2%20Final.pdf), 31 August 2019.

## Representation

In most cases, agreements in B2B ecosystems and associated processes are among about legal persons. In these processes, Relying Parties typically need to establish that the user (a natural person) has the power to represent the legal person in the electronic process in order to be able to proceed with the execution. This document is about requirements on the exchange of evidences about legal persons.

When processing requests for evidence about legal persons, the Relying Party must authenticate users acting either directly or through a representative using electronic identification means defined in Article 3(2) of Regulation (EU) 910/2014 issued under the electronic identification schemes notified in accordance with that Regulation. Even if the representative attributes MUST NOT be explicitly requested in the eIDAS Authentication request, the Online Procedure Portal MAY receive from the eIDAS service one representative attribute set in case of representation. (see 2.8 of the eIDAS SAML Attribute Profile 1.2). This means that the Online Procedure Portal may receive in case of representation two attribute sets, one for the representative and one for the represented person. The attributes for representative must follow the same specifications as defined in sections 2.2, 2.3 of the eIDAS SAML Attribute Profile 1.2 and must have the attribute’s FriendlyName prefixed with “Representative”.

When making evidence requests, the evidence requester shall include all the attribute sets obtained using eIDAS. A Data Service, when processing an evidence request, shall use all identity attributes of the user that are included in the request. The Data Service may choose to re-authenticate the user, or use the attributes sets in combination with additional security services as defined in 2.2 - OOTS eID additional security services - Q1 2023 to determine if pieces of evidence can be returned. In both cases, the Data Service must ensure that the attributes of the user and of the representative where applicable match the attributes held by it.

Please note that the current eIDAS technical specifications do not consider any constraints of representation. The scope of powers or mandates may be described in the notification process of eID schemes that concern either legal persons or natural persons representing legal persons, but this information is not available to the evidence requester and **there is no agreed syntax to encode it**.

## Certificates

following Legal Representative certificates:

- Legal Representative of a Legal Person Certificate 
    Electronic certification issued by ANF AC which links the holder with signature verification data and 
confirms their identity. They are linked to a legal person, the Signatory acts on behalf of a legal 
person as a legal representative with powers of attorney.

- Legal Representative of an Entity without Legal Personality Certificate
Electronic certification issued by ANF AC which links the holder with signature verification data and 
confirms their identity for the sole purpose of being used in the tax and other Public Administration 
fields that are expressly allowed. These certificates are issued under the terms set forth in the 
Order EHA/3256/2004, September 30, (Spanish Official Gazette Nº 246, October 12th). 
It is an entity without legal personality, the one to which article 35.4 of the Spanish General Tax 
Law and other applicable legislation refers to.
Certification Policy Certificates for electronic signature
OID 1.3.6.1.4.1.18332.3.1
Page 9 of 37

- Legal Representative of Sole and Joint and Several Directors Certificate
Electronic certification issued by ANF AC which links the holder with signature verification data and 
confirms their identity. The Signatory acts in representation of a Legal Person as a legal 
representative with his position, as sole or joint and several directors, registered in the Mercantile 
Registry.


## Other things

### Sociedades inscritas en el registro mercantil
Sociedad anónima, sociedad limitada, agrupación de interés económico, agrupación europea de interés económico, sociedad colectiva, sociedad comanditaria.


Acreditación de la identidad persona solicitante (original y en vigor):

Ciudadanía española: DNI, pasaporte o permiso de conducción.
Ciudadanía miembro UE/EEE: pasaporte o documento de identidad de su país de origen junto con Tarjeta de Identificación de Extranjero o certificado emitido por el Registro de Ciudadanos miembros de la Unión o documento oficial de concesión del NIE
Ciudadanía extracomunitaria: pasaporte junto con Tarjeta de Identificación de Extranjero o documento oficial de concesión del NIE.

Acreditación de la organización y las facultades de la persona solicitante:

Izenpe asume la verificación de la vigencia de la entidad, así como de las facultades de la persona solicitante en el caso de tener la consideración de administradora.
En los casos en los que la persona solicitante tenga,
Capacidad general de representación: aportará copia del poder.
Poder especial para solicitar y utilizar el certificado en representación de la entidad: aportará original y copia del poder notarial.
La condición de administrador mancomunado: aportará copia de la escritura notarial acreditativa de la identidad de los administradores mancomunados y su forma de actuación, junto con la solicitud de emisión firmada por los administradores mancomunados.
Si la administración de la sociedad corresponde a un Consejo de Administración, la solicitud corresponderá al Presidente.

