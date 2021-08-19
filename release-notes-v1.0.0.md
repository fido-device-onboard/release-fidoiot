v1.0.0

This release contains a reference implementation of [FIDO Device Onboard (FDO) Specification](https://fidoalliance.org/specs/FDO/fido-device-onboard-v1.0-ps-20210323/).

It includes 4 components:
  * Protocol Reference Implementation (PRI): [pri-fidoiot](https://github.com/secure-device-onboard/pri-fidoiot) is a JAVA based implementation of all the components specified in the FDO Specification.
  * Client SDK: [client-sdk-fidoiot](https://github.com/secure-device-onboard/client-sdk-fidoiot) is a C based implementation for the device component specified in the FDO Specification. Additionally, it supports an implementation of the device that uses the TPM infrastructure.
  * EPID Verification Service: [epid-verification-service](https://github.com/secure-device-onboard/epid-verification-service) is a wrapper service written on top of the EPID SDK to assist the FDO Rendezvous service and FDO Owner service to perform device signature verification for EPID based devices.
  * Test: [test-fidoiot](https://github.com/secure-device-onboard/test-fidoiot) implements a test-suite that gets executed as part of continuous integration pipeline.

### New Features

**client-sdk-fidoiot**, **pri-fidoiot**: The test credentials (attestation keystores, SSL keystores,
truststore) has been removed from source code. A script 'keys_gen.sh' is provided to generate test
credentials for demo usage.

**pri-fidoiot**: A new component 'aio' (All-in-one Demo) is included. It implements all the FDO
services witin a single container. REST APIs are provided to configure the component.

**pri-fidoiot**: The API in Manufacturer is updated to take the RendezvousInfo blob as input. A
script 'get-cbor-bytes.sh' is provided to generate the CBOR blob in required format.

**client-sdk-fidoiot**, **pri-fidoiot**: New end-points are created in PRI services to receive
Error-Type255 messages. The Client implementation was updated to send message number in the
Error-Type255 messages.

**pri-fidoiot**: Both HTTP and HTTPS support is enabled for all the PRI services by default.

**client-sdk-fidoiot**, **pri-fidoiot**: Client implementations were updated to support DI operation
over HTTPs protocol.

**client-sdk-fidoiot**: The URL for Manufacturer service is now passed through a single file
'manufacturer_addr.bin'. This includes the protocol details, DNS/IP details and port details.

**client-sdk-fidoiot**, **pri-fidoiot**: ServiceInfo modules were updated to process and send
modname:active messages.

**pri-fidoiot**: SLF4J based logging infrastructure is developed. In default configuration, INFO
messages are redirected to console and DEBUG messages are redirected to a log file.

**epid-verification-service**, **pri-fidoiot**: Docker based build scripts are provided for building the source code.

### Changes to existing features

**pri-fidoiot**: Diffie-Hellman key exchange support is added.

**pri-fidoiot**: SoftHSM support has been removed from 'Manufacturer' and 'Reseller' components.

**pri-fidoiot**: The ServiceInfo module is refactored to support MTU size as low as 256 bytes. The
maximum supported ServiceInfo MTU size is 60000 bytes (supported by only PRI device).

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

### Supported Cryptographic Modes

**pri-fidoiot** supports the following cryptographic modes.

* For device attestation, it supports Intel EPID keys based on EPID 1.0/EPID 1.1 and ECC keys
based on SECP256R1 and SECP384R1 curves.

* For key exchange, it supports DHKEXid14, DHKEXid15, ASYMKEX2048, AESYMKEX3072, ECDH256 and ECDH384
  modes.

* For session encryption, it supports the following AES modes - AES-CTR-128, AES-CTR-256,
  AES-CBC-128, AES-CBC-256, A128GCM, A256GCM, AES-CCM-64-128-128 and AES-CCM-64-128-256.

* For public key encoding, it supports Crypto, X509 as well as COSEX509 encoding. (section 3.3.4)

* For COSE signatures, ES256, ES384, RS256 and RS384 signature types are supported. (section 3.3.5)

**client-sdk-fidoiot**: It supports a subset of the above cryptographic modes.

* For device attestation, ECC keys based on SECP256R1 and SECP384R1 are supported.

* For Key Exchange, ECDH256 and ECDH384 modes are supported.

* For session encryption, it supports following AES modes - A128GCM, A256GCM, AES-CCM-64-128-128 and
AES-CCM-64-128-256.

* For public key encoding, COSEX509 encoding is used. (section 3.3.4).

* For COSE signatures, ES256 and ES384 signature types are supported. (section 3.3.5)

### Known Issues

**pri-fidoiot**, **client-sdk-fidoiot**: Section 3.3.2 defines hashtype as 'uint8', but the values
for SHA256 and SHA384 are negative. In the implementation, the 'hashtype' is considered as 'int8'.
 Refer to [issue](https://github.com/secure-device-onboard/client-sdk-fidoiot/issues/150) for
 more details.

**pri-fidoiot**, **client-sdk-fidoiot**: The following RVVariable entries are ignored -
RVSvCertHash, RVClCertHash, RVUserInput, RVWifiSsid, RVWifiPw, RVMedium, RVExtRV. The following
RVProtocolValue entries are ignored - RVProtRest, RVProtTcp, RVProtCoapTcp and RVProtCoapUdp. Refer
to [issue](https://github.com/secure-device-onboard/client-sdk-fidoiot/issues/151) for more
details.

**client-sdk-fidoiot**: Maximum supported value for RVDelaySec is 3600s. If no RVDelaySec is
provided, a delay of 3 seconds is used while trying successive RendezvousDirectives and a delay of
120 seconds is used while retrying the RendezvousInfo. The delay is not randomized by +/-30s. Refer
to [issue](https://github.com/secure-device-onboard/client-sdk-fidoiot/issues/152) for more
details.

**pri-fidoiot**: RVDelaySec is not honoured for TO0 retries with RendezvousInfo, due to possible
conflicts with the TO0Scheduler. Refer to
[issue](https://github.com/secure-device-onboard/pri-fidoiot/issues/346) for more details.

**client-sdk-fidoiot**: IPAddress.ip6 is not supported. Refer to
[issue](https://github.com/secure-device-onboard/client-sdk-fidoiot/issues/156) for more details.

**client-sdk-fidoiot**: Error code values are not implemented as per section 5.1. Generic error code '100'
and '500' are sent to the servers. Refer to
[issue](https://github.com/secure-device-onboard/client-sdk-fidoiot/issues/153) for more details.

**pri-fidoiot**: The maven build occasionally fails while running the unit tests. The issue happens
rarely and is often fixed during successive retries. Refer to
[issue](https://github.com/secure-device-onboard/pri-fidoiot/issues/347) for more details.

**pri-fidoiot**: get-cbor-bytes.sh script uses cbor.me website for generating the RendezvousInfo
CBOR bytes. This site should be accessible from the local machine while generating RendezvousInfo
for different configurations. Refer to
[issue](https://github.com/secure-device-onboard/pri-fidoiot/issues/348) for more details.

**client-sdk-fidoiot**: The key 'devmod:modules' and its corresponding value cannot be broken into
multiple message based on the maximum MTU size indicated by the Owner, and is sent in a single
message. Addition of ServiceInfo modules to this key requires manual change in the source. Refer to
[issue](https://github.com/secure-device-onboard/client-sdk-fidoiot/issues/154) for more details.

**client-sdk-fidoiot**: Only the 'devmod' module is supported as a Device ServiceInfo module.
Support for adding additional Device ServiceInfo modules and subsequent response framework to the
Owner, has not yet been implemented. Refer to
[issue](https://github.com/secure-device-onboard/client-sdk-fidoiot/issues/155) for more details.

### SHA256 checksum for release binaries

*Following SHA256 checksum is calculated using sha256sum tool*
```
```

### Documentation

https://secure-device-onboard.github.io/docs/1.0.0

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*

