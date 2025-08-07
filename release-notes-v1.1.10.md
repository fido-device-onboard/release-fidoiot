v1.1.10

This release includes critical security fixes, library upgrades, and enhancements across all core FDO components.
## Components
### Protocol Reference Implementation (PRI)

[pri-fidoiot](https://github.com/fido-device-onboard/pri-fidoiot) is a Java-based implementation of the components defined in the [FIDO Device Onboard Specification](https://fidoalliance.org/specs/FDO/FIDO-Device-Onboard-PS-v1.1-20220419/).

**Supported Cryptographic Modes:**
- **Signing Keys:** ECDSA NIST P-256, ECDSA NIST P-384, RSA2048RESTR, Intel EPID 1.1  
- **Key Exchanges:** ECDH256, ECDH384, ASYMKEX2048, ASYMKEX3072, DHKEXid14, DHKEXid15  
- **Ciphers:** AES128/CTR/HMAC-SHA256, AES128/HMAC-SHA256, AES256/CTR/HMAC-SHA384, AES256/HMAC-SHA384, AES-CCM-64-128-128, AES-CCM-64-128-256, AES128GCM, AES256GCM, RSA/NONE/OAEPWithSHA256AndMGF1Padding  
- **Public Key Encoding:** Crypto, X509, COSEKey, X5 Chain  
- **COSE Signature Types:** ES256, ES384, RS2048  

---

### Client SDK
[client-sdk-fidoiot](https://github.com/fido-device-onboard/client-sdk-fidoiot) is a C-based implementation of the FDO device component. It also supports a variant using TPM infrastructure.
**Supported Cryptographic Modes:**
- **Signing Keys:** ECDSA NIST P-256, ECDSA NIST P-384  
- **Key Exchanges:** ECDH256, ECDH384  
- **Ciphers:** AES-CCM-64-128-128, AES-CCM-64-128-256, AES128GCM, AES256GCM  
- **Public Key Encoding:** X509  
- **COSE Signature Types:** ES256, ES384  

---

## New Features

### pri-fidoiot

- Skip TLS SAN checks for self-signed certificates.
- Improved Diffie-Hellman key exchange handling.
- Updated `service.yml` and bug reporting links in README.

### client-sdk-fidoiot

- Build compatibility with FDO GO server.
- Upgraded OpenSSL to v3.0.14 and curl to v8.8.0.

---

## 🛠 Fixed Issues

### pri-fidoiot
- **Security Fixes:**
  - [CVE-2024-34750](https://nvd.nist.gov/vuln/detail/CVE-2024-34750)
  - [CVE-2024-50379](https://nvd.nist.gov/vuln/detail/CVE-2024-50379)
  - [CVE-2024-47554](https://nvd.nist.gov/vuln/detail/CVE-2024-47554)

- **Dependency Updates:**
  - Upgraded MySQL, Protobuf, and Commons-IO
  - Updated GitHub Actions and build workflows

- **Other Fixes:**
  - Reverted incorrect `service.yml` changes

### client-sdk-fidoiot
- Fixed build with FDO GO server
- Workflow dependency upgrades

### test-do
- Changed `docker-compose` command to `docker compose`

---

## Known Issues
---

## SHA256 Checksums   

83aaad1...... - client-sdk-fidoiot-v1.1.10.tar.gz
3f5c8d....... - pri-fidoiot-v1.1.10.tar.gz
036b79....... - NOTICES-v1.1.10.tar.gz
b74eb9....... - third-party-components.tar.gz
Documentation

https://fido-device-onboard.github.io/docs-fidoiot/1.1.10

Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.