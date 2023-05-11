v1.1.3

This release contains a reference implementation of [FIDO Device Onboard (FDO) Specification](https://fidoalliance.org/specs/FDO/FIDO-Device-Onboard-PS-v1.1-20220419/).

It includes 4 components:
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
  * Test: [test-fidoiot](https://github.com/fido-device-onboard/test-fidoiot) implements a test-suite that gets executed as part of continuous integration pipeline.

### New Features

**client-sdk-fidoiot**, **pri-fidoiot**: Support for full X5 Chain public key support has been implemented

**client-sdk-fidoiot**, **pri-fidoiot**: Support for Mutual TLS has been implemented. 

**pri-fidoiot**: There is an option for the users to create an Alpine image for the docker in addition to Ubuntu image

### Changes to existing features

**client-sdk-fidoiot**, **pri-fidoiot**: The key stores can now be stored in database and file system. APIs are documented in the readme.

**client-sdk-fidoiot**, **pri-fidoiot**: The default database is now configured to be MariaDB. Users can switch to H2 with the steps provided in the readme.  

**client-sdk-fidoiot**, **pri-fidoiot**: The solution is secure by default and allows only CA signed certificates by default. Workaround to enable self signed certificate has been documented in readme.

### Known Issues

**pri-fidoiot**: Read permission needs to be added to server-key.pem file while configuring database secrets.  
 This is tracked through the GitHub issue [pri-fidoiot#551](https://github.com/fido-device-onboard/pri-fidoiot/issues/551).

**pri-fidoiot**: Starting a component with an invalid port number or with a port already in use gives an exception.  
 This is tracked through the GitHub issue [pri-fidoiot#467](https://github.com/fido-device-onboard/pri-fidoiot/issues/467).
 
**pri-fidoiot**: RVDelaySec is currently not considered during TO0 and TO1.
 This is tracked through the GitHub issue [pri-fidoiot#468](https://github.com/fido-device-onboard/pri-fidoiot/issues/468).

**pri-fidoiot**: Proxy settings for owner to be set explicitly when using a proxy.
 This is tracked through the GitHub issue [pri-fidoiot#476](https://github.com/fido-device-onboard/pri-fidoiot/issues/476).

### SHA256 checksum for release binaries

*Following SHA256 checksum is calculated using sha256sum tool*
```
06fa4c6b7aa74160d3c2fb70e7ea60cc28d9fff71b51a60dd91b6c1182599776 - client-sdk-fidoiot-v1.1.3.tar.gz
22473ea112225928541307ae9766fa739c9a39b70502bfea85f4f269ad134587 - pri-fidoiot-v1.1.3.tar.gz
d058130cf45ea84728b6a5a3824d1cccd53c0ab9f5247e982c40070b91a16177 - NOTICES-v1.1.3.tar.gz
5cf498b0d5ef3972bd645ed5e984ced08268e6220d5eead6652cd038405f5503 - third-party-components.tar.gz
```

### Documentation

https://fido-device-onboard.github.io/docs-fidoiot/1.1.3

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*

