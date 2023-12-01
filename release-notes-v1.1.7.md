v1.1.7

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

  
### New Features

**client-sdk-fidoiot**: Option to update manufacturer address through command line argument during DI added.

**client-sdk-fidoiot**: Compile time option to fetch serial number of the device from BIOS added.

**pri-fidoiot**: Support for FIDO Service Info Module (FSIM) added. This is only a preview release.

### Changes to existing features

**client-sdk-fidoiot**, **pri-fidoiot**: Changes to Owner Exec, Fetch now fetches file and enables saving on owner.

### Fixed Issues

**pri-fidoiot**: The version of third-party dependencies have been updated.


### Known Issues

**client-sdk-fidoiot**: Sporadic failure with continuous, repeated usage of CSDK built with Intel® CSE without pause. 
 This is tracked through the GitHub issue [client-sdk-fidoiot#226](https://github.com/fido-device-onboard/client-sdk-fidoiot/issues/226).
**pri-fidoiot**: Given this is a preview release of FSIM, we recommend enabling either FSIM or FDO_SYS at any time.

### SHA256 checksum for release binaries

*Following SHA256 checksum is calculated using sha256sum tool*
```
87b2f0aebfe9fd3745945b5dc1247a72301b03cda8acdf6569b7aaa7a6a7b1c8 - client-sdk-fidoiot-v1.1.7.tar.gz
231439d8a3fddf33dd2f88eb12cd68fb3df99eae28deb6d649bf5e7e803623bb - pri-fidoiot-v1.1.7.tar.gz
036b79df7485ec14dfbc5953dd7f5ad6bf7ae8b0dbc60e63bbba42254583c692 - NOTICES-v1.1.7.tar.gz
b74eb98bfc1e8e020b392f132f9f17036f564eb4f03ad228ddbaba90a3b83beb - third-party-components.tar.gz
```

### Documentation

https://fido-device-onboard.github.io/docs-fidoiot/1.1.7

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*

