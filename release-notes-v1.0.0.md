v1.0.0

This release contains a reference implementation of [FIDO Device Onboard (FDO) Specification](https://fidoalliance.org/specs/FDO/fido-device-onboard-v1.0-ps-20210323/).

It includes 4 components:
  * Protocol Reference Implementation (PRI): [pri-fidoiot](https://github.com/fido-device-onboard/pri-fidoiot) is a JAVA based implementation of all the components specified in the FDO Specification. It supports the following cryptographic modes.
    * Signing keys: ECDSA NIST P-256, ECDSA NIST P-384, RSA2048RESTR, and Intel EPID 1.1.
    * Key Exchanges: ECDH256, ECDH384, ASYMKEX2048, ASYMKEX3072, DHKEXid14, and DHKEXid15.
    * Ciphers: AES128/CTR/HMAC-SHA256, AES128/CBC/HMAC-SHA256, AES256/CTR/HMAC-SHA384, AES256/CBC/HMAC-SHA384, AES-CCM-64-128-128, AES-CCM-64-128-256, AES128GCM, AES256GCM, and RSA/NONE/OAEPWithSHA256AndMGF1Padding.
    * Public Key Encoding: Crypto, X509, and COSEX509.
    * COSE Signature Types: ES256, ES384, RS256, and RS384.

  * Client SDK: [client-sdk-fidoiot](https://github.com/fido-device-onboard/client-sdk-fidoiot) is a C based implementation for the device component specified in the FDO Specification. Additionally, it supports an implementation of the device that uses the TPM infrastructure. It supports the following cryptographic modes.
    * Signing keys: ECDSA NIST P-256, and ECDSA NIST P-384
    * Key Exchanges: ECDH256, and ECDH384
    * Ciphers: AES-CCM-64-128-128, AES-CCM-64-128-256, AES128GCM, and AES256GCM.
    * Public Key Encoding: COSEX509.
    * COSE Signature Types: ES256, and ES384.

  * EPID Verification Service: [epid-verification-service](https://github.com/fido-device-onboard/epid-verification-service) is a wrapper service written on top of the EPID SDK to assist the FDO Rendezvous service and FDO Owner service to perform device signature verification for EPID based devices.
  * Test: [test-fidoiot](https://github.com/fido-device-onboard/test-fidoiot) implements a test-suite that gets executed as part of continuous integration pipeline.

### New Features

**client-sdk-fidoiot**, **pri-fidoiot**: The test credentials (attestation keystores, SSL keystores,
truststore) has been removed from source code. A script 'keys_gen.sh' is provided to generate test
credentials for demo usage.

**client-sdk-fidoiot**, **pri-fidoiot**: New end-points are created in PRI services to receive
Error-Type255 messages. The Client implementation was updated to send message number in the
Error-Type255 messages.

**client-sdk-fidoiot**, **pri-fidoiot**: Client implementations were updated to support DI operation
over HTTPs protocol.

**client-sdk-fidoiot**, **pri-fidoiot**: ServiceInfo modules were updated to process and send
modname:active messages.

**epid-verification-service**, **pri-fidoiot**: Docker based build scripts are provided for building the source code.

**client-sdk-fidoiot**: The URL for Manufacturer service is now passed through a single file
'manufacturer_addr.bin'. This includes the protocol details, DNS/IP details and port details.

**pri-fidoiot**: A new component 'aio' (All-in-one Demo) is included. It implements all the FDO
services witin a single container. REST APIs are provided to configure the component.

**pri-fidoiot**: The API in Manufacturer is updated to take the RendezvousInfo blob as input. A
script 'get-cbor-bytes.sh' is provided to generate the CBOR blob in required format.

**pri-fidoiot**: Both HTTP and HTTPS support is enabled for all the PRI services by default.

**pri-fidoiot**: SLF4J based logging infrastructure is developed. In default configuration, INFO
messages are redirected to console and DEBUG messages are redirected to a log file.

### Changes to existing features

**client-sdk-fidoiot**, **pri-fidoiot**: Several security issues found during secure code review
were fixed. These fixes include - updating L value in KDF to specify the number of bits of generated
key, improving input validation, removing usage of deprecated packages, etc.

**client-sdk-fidoiot**, **pri-fidoiot**: Credential REUSE feature is disabled in default PRI Owner
implementation. This can be re-enabled for demonstration purpose.

**client-sdk-fidoiot**, **pri-fidoiot**: COSE signature generation method is fixed to include
Protected Header in signature payload.

**client-sdk-fidoiot**: Support for AES-GCM and AES-CCM modes has been included and support for
AES-CBC and AES-CTR modes has been removed. Support for ASYMKEX and Diffie-Hellman key exchange as
well as use of RSA for device key attestation has also been removed.

**pri-fidoiot**: Diffie-Hellman key exchange support is added.

**pri-fidoiot**: SoftHSM support has been removed from 'Manufacturer' and 'Reseller' components.

**pri-fidoiot**: The ServiceInfo module is refactored to support MTU size as low as 256 bytes. The
maximum supported ServiceInfo MTU size is 60000 bytes (supported by only PRI device).

### Known Issues

**pri-fidoiot**, **client-sdk-fidoiot**: Section 3.3.2 defines hashtype as 'uint8', but the values
for SHA256 and SHA384 are negative. In the implementation, the 'hashtype' is considered as 'int8'.
 This is tracked through GitHub issue
 [client-sdk-fidoiot#150](https://github.com/fido-device-onboard/client-sdk-fidoiot/issues/150).

**pri-fidoiot**, **client-sdk-fidoiot**: The following RVVariable entries are ignored -
RVSvCertHash, RVClCertHash, RVUserInput, RVWifiSsid, RVWifiPw, RVMedium, RVExtRV. The following
RVProtocolValue entries are ignored - RVProtRest, RVProtTcp, RVProtCoapTcp and RVProtCoapUdp. This
is tracked through GitHub issue
[client-sdk-fidoiot#151](https://github.com/fido-device-onboard/client-sdk-fidoiot/issues/151).

**client-sdk-fidoiot**: Maximum supported value for RVDelaySec is 3600s. If no RVDelaySec is
provided, a delay of 3 seconds is used while trying successive RendezvousDirectives and a delay of
120 seconds is used while retrying the RendezvousInfo. The delay is not randomized by +/-30s. This
is tracked through GitHub issue
[client-sdk-fidoiot#152](https://github.com/fido-device-onboard/client-sdk-fidoiot/issues/152).

**client-sdk-fidoiot**: IPAddress.ip6 is not supported. This is tracked through GitHub issue
[client-sdk-fidoiot#156](https://github.com/fido-device-onboard/client-sdk-fidoiot/issues/156).

**client-sdk-fidoiot**: Error code values are not implemented as per section 5.1. Generic error code '100'
and '500' are sent to the servers. This is tracked through GitHub issue
[client-sdk-fidoiot#153](https://github.com/fido-device-onboard/client-sdk-fidoiot/issues/153).

**client-sdk-fidoiot**: The key 'devmod:modules' and its corresponding value cannot be broken into
multiple message based on the maximum MTU size indicated by the Owner, and is sent in a single
message. Addition of ServiceInfo modules to this key requires manual change in the source. This is
tracked through GitHub issue
[client-sdk-fidoiot#154](https://github.com/fido-device-onboard/client-sdk-fidoiot/issues/154).

**client-sdk-fidoiot**: Only the 'devmod' module is supported as a Device ServiceInfo module.
Support for adding additional Device ServiceInfo modules and subsequent response framework to the
Owner, has not yet been implemented. This is tracked through GitHub issue
[client-sdk-fidoiot#155](https://github.com/fido-device-onboard/client-sdk-fidoiot/issues/155).

**pri-fidoiot**: RVDelaySec is not honoured for TO0 retries with RendezvousInfo, due to possible
conflicts with the TO0Scheduler. This is tracked through GitHub issue
[pri-fidoiot#346](https://github.com/fido-device-onboard/pri-fidoiot/issues/346).

**pri-fidoiot**: The maven build occasionally fails while running the unit tests. The issue happens
rarely and is often fixed during successive retries. This is tracked through GitHub issue
[pri-fidoiot#347](https://github.com/fido-device-onboard/pri-fidoiot/issues/347).

**pri-fidoiot**: get-cbor-bytes.sh script uses cbor.me website for generating the RendezvousInfo
CBOR bytes. This site should be accessible from the local machine while generating RendezvousInfo
for different configurations. This is tracked through GitHub issue
[pri-fidoiot#348](https://github.com/fido-device-onboard/pri-fidoiot/issues/348).

### SHA256 checksum for release binaries

*Following SHA256 checksum is calculated using sha256sum tool*
```
61250074c052cada285cab2b2336a6984ac2337a84689d48be6fafcd8f64f85b - client-sdk-fidoiot-v1.0.0.tar.gz
f0c0b93857b07a7e5c19aeada5c7c0fb221fb1234f2b10d4c7232e46084b5428 - epid-verification-service-v1.0.0.tar.gz
31e1e95431cbf025502cf7c2671477ed792ec82bec31aee58b2d81b998e4f848 - pri-fidoiot-v1.0.0.tar.gz
2efd9e5c37230c878f1e8253144c912de04f6287b9041d65a596fe1bcd0074fa - NOTICES-v1.0.0.tar.gz
```

### Documentation

https://fido-device-onboard.github.io/docs-fidoiot/1.0.0

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*

