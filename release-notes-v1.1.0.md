v1.1.0

This release contains a reference implementation of [FIDO Device Onboard (FDO) Specification](https://fidoalliance.org/specs/FDO/FIDO-Device-Onboard-RD-v1.1-20211214/).

It includes 4 components:
  * Protocol Reference Implementation (PRI): [pri-fidoiot](https://github.com/fido-device-onboard/pri-fidoiot) is a JAVA based implementation of all the components specified in the FDO Specification. It supports the following cryptographic modes.
    * Signing keys: ECDSA NIST P-256, ECDSA NIST P-384, RSA2048RESTR, and Intel EPID 1.1.
    * Key Exchanges: ECDH256, ECDH384, ASYMKEX2048, ASYMKEX3072, DHKEXid14, and DHKEXid15.
    * Ciphers: AES128/CTR/HMAC-SHA256, AES128/HMAC-SHA256, AES256/CTR/HMAC-SHA384, AES256/HMAC-SHA384, AES-CCM-64-128-128, AES-CCM-64-128-256, AES128GCM, AES256GCM, and RSA/NONE/OAEPWithSHA256AndMGF1Padding.
    * Public Key Encoding: Crypto, X509, and COSEKey.
    * COSE Signature Types: ES256, ES384, RS2048.

  * Client SDK: [client-sdk-fidoiot](https://github.com/fido-device-onboard/client-sdk-fidoiot) is a C based implementation for the device component specified in the FDO Specification. Additionally, it supports an implementation of the device that uses the TPM infrastructure. It supports the following cryptographic modes.
    * Signing keys: ECDSA NIST P-256, and ECDSA NIST P-384
    * Key Exchanges: ECDH256, and ECDH384
    * Ciphers: AES-CCM-64-128-128, AES-CCM-64-128-256, AES128GCM, and AES256GCM.
    * Public Key Encoding:  X509.
    * COSE Signature Types: ES256, and ES384.

  * EPID Verification Service: [epid-verification-service](https://github.com/fido-device-onboard/epid-verification-service) is a wrapper service written on top of the EPID SDK to assist the FDO Rendezvous service and FDO Owner service to perform device signature verification for EPID based devices.
  * Test: [test-fidoiot](https://github.com/fido-device-onboard/test-fidoiot) implements a test-suite that gets executed as part of continuous integration pipeline.

### New Features

**client-sdk-fidoiot**, **pri-fidoiot**: Multiple device / owner ServiceInfo modules can be enabled and disabled through configuration. 

**client-sdk-fidoiot**, **pri-fidoiot**: Keep-alive feature has been implemented in fdo_sys module for long running onboarding scripts. 

**client-sdk-fidoiot**, **pri-fidoiot**: Support for Red Hat OS has been enabled. 

**client-sdk-fidoiot**, **pri-fidoiot**: The FDO solution currently supports the [FDO 1.1 Spec](https://fidoalliance.org/specs/FDO/FIDO-Device-Onboard-RD-v1.1-20211214/#functional-changes)
 
**client-sdk-fidoiot**, **pri-fidoiot**: Database access is via Hibernate Core which enables changing backend database without code changes. 


### Changes to existing features

**client-sdk-fidoiot**, **pri-fidoiot**: The key stores are now stored in database and APIs have been added to access them. 

**client-sdk-fidoiot**, **pri-fidoiot**: The Reseller public keys are not stored in the database but are accessible via API.
Ownership Voucher extension APIs for Manufacturer / Reseller have been changed

**client-sdk-fidoiot**, **pri-fidoiot**: H2 UI is standalone and not integrated into Tomcat. 

**client-sdk-fidoiot**, **pri-fidoiot**: New APIs added. Refer readme (aio) for more details. 

**pri-fidoiot**: The REST APIs are now in human-readable format and not CBOR encoded as in the previous release. 

**pri-fidoiot**:  The maximum supported ServiceInfo MTU size is 64K bytes (supported by only PRI device).

**pri-fidoiot**: OnDie certificate import into the PRI has changed from individual files to a single .zip file. 

### Known Issues

**pri-fidoiot**: Starting a component with an invalid port number or with a port already in use gives an exception.  
 This is tracked through the GitHub issue [pri-fidoiot#467](https://github.com/fido-device-onboard/pri-fidoiot/issues/467).

**pri-fidoiot**: RVDelaySec is currently not considered during TO0 and TO1 and will be fixed in the next release.
 This is tracked through the GitHub issue [pri-fidoiot#468](https://github.com/fido-device-onboard/pri-fidoiot/issues/468).

**pri-fidoiot**: Proxy settings for owner to be set explicitly when using a proxy.
 This is tracked through the GitHub issue [pri-fidoiot#476](https://github.com/fido-device-onboard/pri-fidoiot/issues/476).

### SHA256 checksum for release binaries

*Following SHA256 checksum is calculated using sha256sum tool*
```
6a6f7a37924f9b204dfc317d0621f8ca8cfe92498339906ee07b8568c5d4702e  pri-fidoiot-v1.1.0.tar.gz
762fc4b0336ae571208a2f72ebaae68bacb298184b186b2c0d75b00acd52ca51  NOTICES-v1.1.0.tar.gz
6e8197dcc08b1abbe69d1c70a6cf6fc94fa317ccd99265d4241d42e64a03379f  epid-verification-service-v1.1.0.tar.gz
e36cc1c45e02ebf6d6157af3fccd627033f49a45119b452e79c5b962264612c9  client-sdk-fidoiot-v1.1.0.tar.gz
```

### Documentation

https://fido-device-onboard.github.io/docs-fidoiot/1.1.0

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*

