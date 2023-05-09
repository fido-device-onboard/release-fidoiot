v1.0.2

### Fixed Issues

**test-fidoiot**, **epid-verification-service**: The version of third-party dependencies have been updated to resolve [CVE-2021-44832](https://nvd.nist.gov/vuln/detail/CVE-2021-44832) vulnerability.
**pri-fidoiot**: The version of third-party dependencies have been updated to resolve  [CVE-2021-44832](https://nvd.nist.gov/vuln/detail/CVE-2021-44832), [CVE-2021-42392](https://github.com/advisories/GHSA-h376-j262-vhq6), [CVE-2021-23463](https://github.com/advisories/GHSA-7rpj-hg47-cx62) vulnerabilities.
**client-sdk-fidoiot**: There are no changes from previous release.  

### Known Issues
**pri-fidoiot**: Upgrading from H2 1.4.200 to 2.X.X version resulted in a few incompatibilities. See this [GitHub issue](https://github.com/fido-device-onboard/pri-fidoiot/issues/401) for more details.

The tag v1.0.2 and the branches 1.0-rel, 1.10-rel points to the same commit ( #991abd4, Version rollover to 1.0.2 Release). In build/build.sh script, the remote branch points to 1.10-rel, which is same as the 1.0-rel branch and v1.0.2 tag.

### SHA256 checksum for release binaries

*Following SHA256 checksum is calculated using sha256sum tool*
```
5a03afe073e1c511a2b1d4aa3c6442d62c78b725e93a8d5027a42ecd719fb549 client-sdk-fidoiot-v1.0.2.tar.gz
fe043cadf87909a51a103560e4c2f21f2f22a91ce6a4a48386f1c827c2a98564 epid-verification-service-v1.0.2.tar.gz
bf249081c65f8b8c9e6bd531cdeaac8751777f883d87d6b8bde63cb851d6f0e1 pri-fidoiot-v1.0.2.tar.gz
25536c464796c2107550428d9711836c01d3e0404f0388a135d3f1b354be160a NOTICES-v1.0.2.tar.gz
```


### Documentation

https://fido-device-onboard.github.io/docs-fidoiot/1.0.0

*Please ignore Source code zip/tar.gz files. These are default artifacts generated during GitHub Release process.*

