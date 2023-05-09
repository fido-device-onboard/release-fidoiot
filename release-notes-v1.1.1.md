v1.1.1

### New Features

**client-sdk-fidoiot**, **pri-fidoiot**, **epid-verification-service**: Adding support for Ubuntu 22.04 and Debian 11.4, as host operating system. 

### Known Issues

**client-sdk-fidoiot**: Binaries built on different systems with different openssl versions fail to execute in certain scenarios with different platforms. 
 This is tracked through the GitHub issue [client-sdk-fidoiot#189](https://github.com/fido-device-onboard/client-sdk-fidoiot/issues/189).
**epid-verification-service**: Need to manually update the build context in epid verification service on RedHat. 
 This is tracked through the GitHub issue [epid-verification-service#38](https://github.com/fido-device-onboard/epid-verification-service/issues/38).
**epid-verification-service**: Support for Ubuntu 22.04 needs to be enabled on epid verification service. 
 This is tracked through the GitHub issue [epid-verification-service#39](https://github.com/fido-device-onboard/epid-verification-service/issues/39).
### SHA256 checksum for release binaries

*Following SHA256 checksum is calculated using sha256sum tool*
```
f7489f640bbe7f9dae1e0a9bc75dbed839795f69ca4b354b8a686f902722128f client-sdk-fidoiot-v1.1.1.tar.gz
01b0b1ffcfcf987d3a05dbf566f1d25e41e628030f3bd3f9efa86b0ed46a6006 NOTICES-v1.1.1.tar.gz
acf149208a72b6f6fb615a9ba490fafb9202d2929067bdb43b269ef9f3e9d68b pri-fidoiot-v1.1.1.tar.gz
5cf498b0d5ef3972bd645ed5e984ced08268e6220d5eead6652cd038405f5503 third-party-components.tar.gz
```

### Documentation

https://fido-device-onboard.github.io/docs-fidoiot/1.1.1

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*

