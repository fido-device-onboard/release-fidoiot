v0.3.0

### New features

This release contains a reference implementation of [FIDO IoT draft spec](https://fidoalliance.org/specs/fidoiot/FIDO-IoT-spec-v1.0-wd-20200730.html). This implementation inherits the initial code from the protocol-next branch of [PRI](https://github.com/secure-device-onboard/pri) repository.

* The core protocol implementation supports "list of crypto algorithms", "list of key-exchange protocols".
* Protocol-samples are added to help developers validate core protocol implementation. These samples
use hard-coded values.
* Component-samples for manufacturer, reseller, rendezvous service, owner and device are provided. These samples can be used to realize different use-case scenarios.
* REST end-points are provided to perform necessary operations on component databases to realize various use-cases.

### Changes to existing features

None  

### Discontinued features

None  

### Fixed Issues

None

### Known Issues

None  

### Supported hardware platforms

**client-sdk**:  
X86 (source and binary)  
ARM-SE, ARM M4, ARM A7 (source only)  

### Documentation

https://secure-device-onboard.github.io/docs/  

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*  

