v1.1.4

This release contains a reference implementation of [FIDO Device Onboard (FDO) Specification](https://fidoalliance.org/specs/FDO/FIDO-Device-Onboard-PS-v1.1-20220419/).

It includes 4 components:
  * Protocol Reference Implementation (PRI): [pri-fidoiot](https://github.com/secure-device-onboard/pri-fidoiot) is a JAVA based implementation of all the components specified in the FDO Specification. It supports the following cryptographic modes.
    * Signing keys: ECDSA NIST P-256, ECDSA NIST P-384, RSA2048RESTR, and Intel EPID 1.1.
    * Key Exchanges: ECDH256, ECDH384, ASYMKEX2048, ASYMKEX3072, DHKEXid14, and DHKEXid15.
    * Ciphers: AES128/CTR/HMAC-SHA256, AES128/HMAC-SHA256, AES256/CTR/HMAC-SHA384, AES256/HMAC-SHA384, AES-CCM-64-128-128, AES-CCM-64-128-256, AES128GCM, AES256GCM, and RSA/NONE/OAEPWithSHA256AndMGF1Padding.
    * Public Key Encoding: Crypto, X509, COSEKey , X5 Chain.
    * COSE Signature Types: ES256, ES384, RS2048.

  * Client SDK: [client-sdk-fidoiot](https://github.com/secure-device-onboard/client-sdk-fidoiot) is a C based implementation for the device component specified in the FDO Specification. Additionally, it supports an implementation of the device that uses the TPM infrastructure. It supports the following cryptographic modes.
    * Signing keys: ECDSA NIST P-256, and ECDSA NIST P-384
    * Key Exchanges: ECDH256, and ECDH384
    * Ciphers: AES-CCM-64-128-128, AES-CCM-64-128-256, AES128GCM, and AES256GCM.
    * Public Key Encoding:  X509.
    * COSE Signature Types: ES256, and ES384.

  * EPID Verification Service: [epid-verification-service](https://github.com/secure-device-onboard/epid-verification-service) is a wrapper service written on top of the EPID SDK to assist the FDO Rendezvous service and FDO Owner service to perform device signature verification for EPID based devices.
  * Test: [test-fidoiot](https://github.com/secure-device-onboard/test-fidoiot) implements a test-suite that gets executed as part of continuous integration pipeline.

### New Features

**pri-fidoiot**: Support for additional databases - MySQL, PostgreSQL - have been implemented. 

### Security Enhancement 

**pri-fidoiot**: pri-fdo-rv doesn't allow replacing redirect entry with a different owner key. 

### Known Issues

**pri-fidoiot**: Read permission needs to be added to server-key.pem file while configuring database secrets.  
 This is tracked through the GitHub issue [pri-fidoiot#551](https://github.com/secure-device-onboard/pri-fidoiot/issues/551).
 
**pri-fidoiot**: RVDelaySec is currently not considered during TO0 and TO1.
 This is tracked through the GitHub issue [pri-fidoiot#468](https://github.com/secure-device-onboard/pri-fidoiot/issues/468).

**pri-fidoiot**: Proxy settings for owner to be set explicitly when using a proxy.
 This is tracked through the GitHub issue [pri-fidoiot#476](https://github.com/secure-device-onboard/pri-fidoiot/issues/476).

### SHA256 checksum for release binaries

*Following SHA256 checksum is calculated using sha256sum tool*
```
87af7e5d1f257b509981b08e5dd5ed670e3278e52d3060acc94036ae14ed1c9e - client-sdk-fidoiot-v1.1.4.tar.gz
a147d5ae8606ca894ec5bc10c141517066e82adf151f01dd68a7979e36d2ac31 - pri-fidoiot-v1.1.4.tar.gz
59b44861642df6f93c88582f014bf874424b1755bfde3f6508f61649632e00b3 - NOTICES-v1.1.4.tar.gz
b74eb98bfc1e8e020b392f132f9f17036f564eb4f03ad228ddbaba90a3b83beb - third-party-components.tar.gz
```

### Documentation

https://secure-device-onboard.github.io/docs-fidoiot/1.1.4

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*
