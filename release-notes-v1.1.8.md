v1.1.8

This release contains a reference implementation of [FIDO Device Onboard (FDO) Specification](https://fidoalliance.org/specs/FDO/FIDO-Device-Onboard-PS-v1.1-20220419/).

It includes the below components:
  * Protocol Reference Implementation (PRI): [pri-fidoiot](https://github.com/fido-device-onboard/pri-fidoiot) is a JAVA based implementation of all the components specified in the FDO Specification. It supports the following cryptographic modes.
    * Signing keys: ECDSA NIST P-256, ECDSA NIST P-384, RSA2048RESTR, and Intel EPID 1.1.
    * Key Exchanges: ECDH256, ECDH384, ASYMKEX2048, ASYMKEX3072, DHKEXid14, and DHKEXid15.
    * Ciphers: AES128/CTR/HMAC-SHA256, AES128/HMAC-SHA256, AES256/CTR/HMAC-SHA384, AES256/HMAC-SHA384, AES-CCM-64-128-128, AES-CCM-64-128-256, AES128GCM, AES256GCM, and RSA/NONE/OAEPWithSHA256AndMGF1Padding.
    * Public Key Encoding: Crypto, X509, COSEKey , X5 Chain.
    * COSE Signature Types: ES256, ES384, RS2048.

  * Client SDK: [client-sdk-fidoiot](https://github.com/fido-device-onboard/client-sdk-fidoiot) is a C based implementation for the device component specified in the FDO Specification. Additionally, it supports an implementation of the device that uses the TPM infrastructure. It supports the following cryptographic modes.
    * Signing keys: ECDSA NIST P-256, and ECDSA NIST P-384
    * Key Exchanges: ECDH256, and ECDH384
    * Ciphers: AES-CCM-64-128-128, AES-CCM-64-128-256, AES128GCM, and AES256GCM.
    * Public Key Encoding:  X509.
    * COSE Signature Types: ES256, and ES384.

  * EPID Verification Service: [epid-verification-service](https://github.com/fido-device-onboard/epid-verification-service) is a wrapper service written on top of the EPID SDK to assist the FDO Rendezvous service and FDO Owner service to perform device signature verification for EPID based devices.
  
### New Features

**client-sdk-fidoiot**: Support for FIDO Service Info Module (FSIM) added.

### Changes to existing features

**client-sdk-fidoiot**: Storage of credentials in TPM has been modified to be compliant with the TPM spec. Please note that the [FIDO Alliance specification "Securing FDO Credentials in the TPM"](https://fidoalliance.org/specs/FDO/securing-fdo-in-tpm-v1.0-rd-20231010/securing-fdo-in-tpm-v1.0-rd-20231010.html) has been published as a Review Draft by the FIDO Alliance, and is still subject to comment and change. With respect to [section 4.2, Handles for FDO Credentials](https://fidoalliance.org/specs/FDO/securing-fdo-in-tpm-v1.0-rd-20231010/securing-fdo-in-tpm-v1.0-rd-20231010.html#Handles_LABEL), Trusted Computing Group (TCG) has allocated the NVRAM addresses referenced, and is moving towards approval of the persistent object handles.

**pri-fidoiot**: Added REST API support to update the replacement RV information.

**client-sdk-fidoiot**, **pri-fidoiot** **epid-verification-service**: Updated the required third party dependencies to be complaint with FIPS.

*Use of Bouncy Castle FIPS as Security Provider in FDO Project
 The PRI FIDO IOT component uses Bouncy Castle FIPS as the primary security provider for all cryptographic operations within the project with the exception of the KDF.
 The KDF implementation is compliant with the FIDO specification and is not based on the Bouncy Castle FIPS.*

### Fixed Issues
 
**client-sdk-fidoiot**: Cross attestation between CSDK client and PRI services are fixed.

**client-sdk-fidoiot**, **pri-fidoiot** **epid-verification-service**: The version of third-party dependencies have been updated.

### Known Issues

**client-sdk-fidoiot**: Sporadic failure with continuous, repeated usage of CSDK built with Intel® CSE without pause. 
 This is tracked through the GitHub issue [client-sdk-fidoiot#226](https://github.com/fido-device-onboard/client-sdk-fidoiot/issues/226).

### SHA256 checksum for release binaries

*Following SHA256 checksum is calculated using sha256sum tool*
```
ad34d3b74483915fe11fbad6e3d45cda44264546f0571b1e03160121c88a1fff - client-sdk-fidoiot-v1.1.8.tar.gz
5fa5685ee74bb906915b9c231f2d5f7c4bf8ca917fc124a45ec0772467db9d81 - epid-verification-service-v1.1.8.tar.gz
49c07b1d124ced6932e728536173943cd2a079bf29441984eb62fd006c63bfed - pri-fidoiot-v1.1.8.tar.gz
036b79df7485ec14dfbc5953dd7f5ad6bf7ae8b0dbc60e63bbba42254583c692 - NOTICES-v1.1.8.tar.gz
b74eb98bfc1e8e020b392f132f9f17036f564eb4f03ad228ddbaba90a3b83beb - third-party-components.tar.gz
```

### Documentation

https://fido-device-onboard.github.io/docs-fidoiot/1.1.8

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*

