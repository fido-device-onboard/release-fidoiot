v0.3.0

### New features

This release contains a reference implementation of [FIDO IoT draft spec](https://fidoalliance.org/specs/fidoiot/FIDO-IoT-spec-v1.0-wd-20200730.html). This implementation inherits the initial code from the protocol-next branch of [PRI](https://github.com/fido-device-onboard/pri/tree/protocol-next) repository.

* The core protocol implementation supports the following cryptographic algorithms:
  * Signing keys: ECDSA NIST P-256, ECDSA NIST P-384, RSA2048RESTR, RSA3072, Intel EPID 1.1
  * Key Exchanges: ECDH256, ECDH384, ASYMKEX2048, ASYMKEX3072
  * Ciphers: AES128/CTR/HMAC-SHA256, AES128/CBC/HMAC-SHA256, AES256/CTR/HMAC-SHA384, AES256/CBC/HMAC-SHA384, RSA/NONE/OAEPWithSHA256AndMGF1Padding
* Protocol-samples are provided to help developers validate core protocol implementation. These samples use hard-coded values.
* Component-samples for manufacturer, reseller, rendezvous service, owner and device are provided. These samples can be used to realize different use-case scenarios.
* REST end-points are provided to perform necessary operations on component databases to realize various use-cases.
* Docker container scripts are provided under demo folder for out-of-box execution of different components.

### Changes to existing features

None  

### Discontinued features

None  

### Fixed Issues

None  

### Known Issues

* The REST end-point call for uploading ServiceInfo files to the 'owner' database occasionally fails. This is tracked through GitHub issue [pri-fidoiot#117](https://github.com/fido-device-onboard/pri-fidoiot/issues/117).

### Documentation

https://fido-device-onboard.github.io/docs/  

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*  

