v1.0.0

### Components

This release contains a reference implementation of [FIDO Device Onboard (FDO) Specification](https://fidoalliance.org/specs/FDO/fido-device-onboard-v1.0-ps-20210323/).

It includes 4 components:
  * Protocol Reference Implementation (PRI): [pri-fidoiot](https://github.com/secure-device-onboard/pri-fidoiot) is a JAVA based implementation of all the components specified in the FDO Specification.
  * Client SDK: [client-sdk-fidoiot](https://github.com/secure-device-onboard/client-sdk-fidoiot) is a C based implementation for the device component specified in the FDO Specification. Additionally, it supports an implementation of the device that uses TPM infrastructure.
  * EPID Verification Service: [epid-verification-service](https://github.com/secure-device-onboard/epid-verification-service) is a wrapper service written on top of EPID SDK to assist FDO Rendezvous service and FDO Owner service to perform device signature verification for EPID based devices.
  * Test: [test-fidoiot](https://github.com/secure-device-onboard/test-fidoiot) implements a test-suite that gets executed as part of continuous integration pipeline.

### New Features

pending

### Supported Cryptographic Modes

**pri-fidoiot** supports following cryptographic modes.

* For device attestation, it supports Intel EPID keys based on StEPID10 and StEPID11 and ECC keys
based on SECP256R1 and SECP384R1 curves.

* For key exchange, it supports DHKEXid14, DHKEXid15, ASYMKEX2048, AESYMKEX3072, ECDH256 and ECDH384
  modes.

* For session encryption, it supports following AES modes - AES-CTR-128, AES-CTR-256, AES-CBC-128,
  AES-CBC-256, A128GCM, A256GCM, AES-CCM-64-128-128 and AES-CCM-64-128-256.

* For public key encoding, it supports Crypto, X509 as well as COSEX509 encoding. (section 3.3.4)

* For COSE signatures, ES512 signature type is not supported. (section 3.3.5)

**client-sdk-fidoiot**: It supports a only a subset of the cryptographic modes.

* For device attestation, ECC keys based on SECP256R1 and SECP384R1 are supported.

* For Key Exchange, ECDH256 and ECDH384 modes are supported.

* For session encryption, it supports following AES modes - A128GCM, A256GCM, AES-CCM-64-128-128 and
AES-CCM-64-128-256.

* For public key encoding, COSEX509 encoding is used. (section 3.3.4).

* For COSE signatures, ES512, RS256 and RS384 signature types are not supported. (section 3.3.5)

### Implementation Notes

**pri-fidoiot**, **client-sdk-fidoiot**: Section 3.3.2 defines hashtype as 'uint8', but the values
for SHA256 and SHA384 are negative. In the implementation, the 'hashtype' is considered as 'int8'.

**pri-fidoiot**, **client-sdk-fidoiot**: The following RVVariable entries are ignored -
RVSvCertHash, RVClCertHash, RVUserInput, RVWifiSsid, RVWifiPw, RVMedium, RVExtRV.

**pri-fidoiot**, **cient-sdk-fidoiot**: The following RVProtocolValue entries are ignored -
RVProtRest, RVProtTcp, RVProtCoapTcp and RVProtCoapUdp.

**client-sdk-fidoiot**: Maximum supported values for RVDelaySec is 3600s. If no RVDelaySec is
provided, a delay of 3 seconds is used while trying successive RendezvousDirectives and a delay of
120 seconds is used while retrying the RendezvousInfo. The delay is not randomized by +/-30s.

**pri-fidoiot**: RVDelaySec is not honored for TO0 retries with RendezvousInfo, due to possible
conflicts with the TO0Scheduler.

**client-sdk**: IPAddress.ip6 is not supported. (section 3.3.9)

### Known Issues

**client-sdk-fidoiot**: Error code values are not implemented as per section 5.1. Generic error code '100'
and '500' are sent to the servers. [issue #](URL)

**pri-fidoiot**: The maven build occasionally fails while running the unit tests. The issue happens
rarely and is often fixed during successive retries. [issue #](URL)

**pri-fidoiot**: get-cbor-bytes.sh script uses cbor.me website for generating the RendezvousInfo
CBOR bytes. This site should be accessible from the local machine while generating RendezvousInfo
for different configurations. [issue #](URL)

### Changes to existing features

pending

### Discontinued features

**client-sdk-fidoiot** AES-CTR and AES-CBC modes are no longer supported.

### Fixed Issues

None

### Known Issues

**client-sdk-fidoiot**: The device ServiceInfo message is not broken down into multiple messages
based on the maximum MTU size indicated by the Owner. (devmod SVI message is always sent as a single
message). The message to send [modname:active, false] for unsupported modules is also not broken
down to multiple messages even if the ServiceInfo message size exceeds the maximum MTU value sent by
the Owner in msg/67.

### SHA256 checksum for release binaries

*Following SHA256 checksum is calculated using sha256sum tool*
```
```

### Documentation

https://secure-device-onboard.github.io/docs/1.0.0

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*

