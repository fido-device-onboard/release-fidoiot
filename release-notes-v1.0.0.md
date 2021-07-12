v1.0.0

### Components

This release contains a reference implementation of [FIDO Device Onboard (FDO) Specification](https://fidoalliance.org/specs/FDO/fido-device-onboard-v1.0-ps-20210323/).

It includes 4 components:
  * Protocol Reference Implementation (PRI): [pri-fidoiot](https://github.com/secure-device-onboard/pri-fidoiot) is a JAVA based implementation of all the components specified in the FDO Specification.
  * Client SDK: [client-sdk-fidoiot](https://github.com/secure-device-onboard/client-sdk-fidoiot) is a C based implementation for the device component specified in the FDO Specification. Additionally, it supports an implementation of the device that uses TPM infrastructure.
  * EPID Verification Service: [epid-verification-service](https://github.com/secure-device-onboard/epid-verification-service) is a wrapper service written on top of EPID SDK to assist FDO Rendezvous service and FDO Owner service to perform device signature verification for EPID based devices.
  * Test: [test-fidoiot](https://github.com/secure-device-onboard/test-fidoiot) implements a test-suite that gets executed as part of continuous integration pipeline.

### New Features




### Known Issues



### Changes to existing features


### Discontinued features

None

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

