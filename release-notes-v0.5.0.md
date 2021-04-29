v0.5.0

### Components

This release contains a reference implementation of [FIDO Device Onboard (FDO) Proposed Standard](https://fidoalliance.org/specs/FDO/fido-device-onboard-v1.0-ps-20210323/).

It includes 4 components:
  * Protocol Reference Implementation (PRI): [pri-fidoiot](https://github.com/secure-device-onboard/pri-fidoiot) is a JAVA based implementation of all the components specified in the FDO Proposed Standard.
  * Client SDK: [client-sdk-fidoiot](https://github.com/secure-device-onboard/client-sdk-fidoiot) is a C based implementation for the device component specified in the FDO Proposed Standard. Additionally, it supports an implementation of the device that uses TPM infrastructure.
  * EPID Verification Service: [epid-verification-service](https://github.com/secure-device-onboard/epid-verification-service) is a wrapper service written on top of EPID SDK to assist FDO Rendezvous service and FDO Owner service to perform device signature verification for EPID based devices.
  * Test: [test-fidoiot](https://github.com/secure-device-onboard/test-fidoiot) implements a test-suite that gets executed as part of continuous integration pipeline.

### New Features

**pri-fidoiot**: The core protocol implementation supports the following cryptographic algorithms:
  * Signing keys: ECDSA NIST P-256, ECDSA NIST P-384, RSA2048RESTR, Intel EPID 1.1
  * Key Exchanges: ECDH256, ECDH384, ASYMKEX2048
  * Ciphers: AES128/CTR/HMAC-SHA256, AES128/CBC/HMAC-SHA256, AES256/CTR/HMAC-SHA384, AES256/CBC/HMAC-SHA384, AES-CCM-64-128-128, AES-CCM-64-128-256, AES128GCM, AES256GCM, and RSA/NONE/OAEPWithSHA256AndMGF1Padding

**client-sdk**: The core protocol implementation supports the following cryptographic algorithms:
  * Signing keys: ECDSA NIST P-256, ECDSA NIST P-384
  * Key Exchanges: ECDH256, ECDH384
  * Ciphers: AES128/CTR/HMAC-SHA256, AES128/CBC/HMAC-SHA256, AES256/CTR/HMAC-SHA384, AES256/CBC/HMAC-SHA384

**pri-fidoiot**, **client-sdk-fidoiot**: A new ServiceInfo module (fdo_sys) has been implemented. The maximum number of bytes that can be sent in a single ServiceInfo message is configurable.

**pri-fidoiot**, **client-sdk-fidoiot**: Implemented RVBypass feature wherein the TO0 and TO1 protocols are skipped and the device connects to the owner for TO2 protocol using the URLs provided in Rendezvous Directives.

**pri-fidoiot**: Packages have been renamed from org.fido.iot.xxx to org.fidoalliance.fdo.xxx.

**pri-fidoiot**: The owner service can now provide a different owner key that can be used as the manufacturer key after resale.

**pri-fidoiot**: Support for Intel OnDie ECDSA based device attestation has been included.

**epid-verification-service**: It exposes the following REST end-points.
  * Endpoints to retrieve EPID resources such as privrl, sigrl, public key
  * Endpoints to get EPID signature verification proof result
  * Endpoints to download crypto material tarball and crypto material signature files

**epid-verification-service**: Provides Docker Compose based scripts to deploy the services.

**test-fidoiot**: Provides the TestNG based test-suite that is executed for validating the pull requests raised for `pri-fidoiot` and `client-sdk-fidoiot` repositories.

### Changes to existing features

**pri-fidoiot**: Source code has been refactored to separate core protocol implementation and example implementations.

**pri-fidoiot**: TLS support has been enabled for the Docker containers provided within `components-samples\demo`.

### Discontinued features

None

### Fixed Issues

None

### Known Issues

* The REST end-point call for uploading ServiceInfo files to the 'owner' database occasionally fails. This is tracked through GitHub issue [pri-fidoiot#117](https://github.com/secure-device-onboard/pri-fidoiot/issues/117).

### SHA256 checksum for release binaries

*Following SHA256 checksum is calculated using sha256sum tool*
```
5228781026fc2ea3d90d87c57e254cd4e85b570bc3b858a691141ba0af6b05f2 - client-sdk-fidoiot-v0.5.0.tar.gz
9024db7e51957b9a1f4392a06fafc11e6284adcc3e9fc7106ac335d30abd6ec3 - pri-fidoiot-v0.5.0.tar.gz
```

### Documentation

https://secure-device-onboard.github.io/docs/

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*

