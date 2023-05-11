v1.1.3.1

This release contains a reference implementation of [FIDO Device Onboard (FDO) Specification](https://fidoalliance.org/specs/FDO/FIDO-Device-Onboard-RD-v1.1-20211214/).


### Fixed Issues

**client-sdk-fidoiot** : Curl installation instructions are updated in linux.md and tpm.md to fix the issue with accessing hosted RV servers (https connections). 

**epid-verification-service** : The versions of third-party dependencies are updated. 

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
94952b31877343254febfb2920300437e61437ea933274254ed47587dabe2887  client-sdk-fidoiot-v1.1.3.1.tar.gz
b4f0f026bda5aad2a0238f410c389f2d5a8ad01df1a001006a7ce73c90a65e03  epid-verification-service-v1.1.3.1.tar.gz
d058130cf45ea84728b6a5a3824d1cccd53c0ab9f5247e982c40070b91a16177  NOTICES-v1.1.3.tar.gz
5cf498b0d5ef3972bd645ed5e984ced08268e6220d5eead6652cd038405f5503  third-party-components.tar.gz
```

### Documentation

https://fido-device-onboard.github.io/docs-fidoiot/1.1.3

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*

