---
title: "PKCS #8 Private-Key Information Content Types"
abbrev: "PKCS #8 PrivateKeyInfo Content Types"
category: std

docname: draft-mandel-lamps-pkcs8-prikeyinfo-contenttypes-latest
submissiontype: IETF
number:
date:
consensus: true
v: 3
area: Security
workgroup: LAMPS Working Group
keyword:
 - 
venue:
  group: WG
  type: LAMPS
  mail: spasm@ietf.org
  arch: https://mailarchive.ietf.org/arch/browse/spasm/
  github: mandelj7/pkcs8-PriKeyInfoCt
  latest: https://github.com/mandelj7/pkcs8-PriKeyInfoCt

author:
- name: Joe Mandel
  org: AKAYLA, Inc.
  abbrev: AKAYLA
  email: joe@akayla.com
- name: Russ Housley
  org: Vigil Security, LLC
  abbrev: Vigil Security
  email: housley@vigilsec.com
- name: Sean Turner
  org: sn3rd, llc
  abbrev: sn3rd
  email: sean@sn3rd.com

normative:
  RFC5208:
  RFC5958:
  RFC5911:
informative:


--- abstract

This document defines PKCS #8 content types for use with
PrivateKeyInfo and EncryptedPrivateKeyInfo as specified in
{{RFC5958}}.

--- middle

# Introduction {#intro}

The syntax for private-key information was originally described in {{RFC5208}} and
later obsoleted by {{RFC5958}}. This document defines PKCS #8 content types for
use with PrivateKeyInfo and EncryptedPrivateKeyInfo.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

# Private-Key Information Content Types {#ContentTypes}

This section defines a content type for private-key information and
encrypted private-key information.

The PrivateKeyInfo content type is identified by the following object identifier:

~~~
id-ct-privateKeyInfo OBJECT IDENTIFIER ::= { iso(1)
 member-body(2) us(840) rsadsi(113549) pkcs(1) pkcs-9(9)
 smime(16) ct(1) TBD1 }
~~~

The EncryptedPrivateKeyInfo content type is identified by the following object identifier:

~~~
id-ct-encrPrivateKeyInfo OBJECT IDENTIFIER ::= { iso(1)
 member-body(2) us(840) rsadsi(113549) pkcs(1) pkcs-9(9)
 smime(16) ct(1) TBD2 }
~~~

# Security Considerations

The security considerations in {{RFC5958}} apply here.


# IANA Considerations

For the private key info content types defined in section {{ContentTypes}},
IANA is requested to assign an object identifier (OID) for each of the content types. The
OIDs for the content types should be alloacted in the "SMI Security for S/MIME CMS Content Type"
registry (1.2.840.113549.1.9.16.1), and the description should be set to id-ct-privateKeyInfo (TDB1)
and id-ct-encrPrivateKeyInfo (TBD2).

For the ASN.1 Module in {{asn1-mod}}, IANA is requested to assign an
object identifier (OID) for the module identifier. The OID for the module
should be allocated in the "SMI Security for S/MIME Module Identifier"
registry (1.2.840.113549.1.9.16.0), and the Description for the new OID should be set
to "id-mod-pkcs8ContentType".

# ASN.1 Module {#asn1-mod}

~~~ asn.1
PrivateKeyInfoContentTypes
 { iso(1) member-body(2) us(840) rsadsi(113549) pkcs(1)
   pkcs-9(9) smime(16) modules(0) id-mod-pkcs8ContentType(TBD0) }

DEFINITIONS IMPLICIT TAGS ::=
BEGIN

-- EXPORTS ALL

IMPORTS

CONTENT-TYPE
 FROM CryptographicMessageSyntax-2009 -- in [RFC5911]
   { iso(1) member-body(2) us(840) rsadsi(113549) pkcs(1)
     pkcs-9(9) smime(16) modules(0) id-mod-cms-2004-02(41) }

PrivateKeyInfo, EncryptedPrivateKeyInfo
 FROM AsymmetricKeyPackageModuleV1 -- in [RFC5958]
    { iso(1) member-body(2) us(840) rsadsi(113549) pkcs(1)
      pkcs-9(9) smime(16) modules(0)
      id-mod-asymmetricKeyPkgV1(50) }  ;


PrivateKeyInfoContentTypes CONTENT-TYPE ::= {
 ct-privateKeyInfo | ct-encrPrivateKeyInfo,
 ... -- Expect additional content types --  }

ct-privateKeyInfo CONTENT-TYPE ::= { PrivateKeyInfo
 IDENTIFIED BY id-ct-privateKeyInfo }

id-ct-privateKeyInfo OBJECT IDENTIFIER ::= { iso(1)
 member-body(2) us(840) rsadsi(113549) pkcs(1) pkcs-9(9)
 smime(16) ct(1) TBD1 }

ct-encrPrivateKeyInfo CONTENT-TYPE ::= { EncryptedPrivateKeyInfo
 IDENTIFIED BY id-ct-encrPrivateKeyInfo }

id-ct-encrPrivateKeyInfo OBJECT IDENTIFIER ::= { iso(1)
 member-body(2) us(840) rsadsi(113549) pkcs(1) pkcs-9(9)
 smime(16) ct(1) TBD2 }

END
~~~
--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.

