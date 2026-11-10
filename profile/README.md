<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/OmniTrustILM/ilm/main/logo/ot-white.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/OmniTrustILM/ilm/main/logo/ot-color.svg">
  <img alt="OTPKI — OmniTrust PKI" src="https://raw.githubusercontent.com/OmniTrustILM/ilm/main/logo/ot-color.svg" width="400">
</picture>

## OmniTrust PKI

OTPKI is an open-source certificate authority and enrollment platform from OmniTrust, built for real HSM deployments, with first-class support for hardware security modules, post-quantum cryptography, and the protocols devices actually speak: SCEP, EST, ACME, CMP, Microsoft AutoEnrollment, and REST.

Released under the [Apache License 2.0](https://github.com/otpki/otpki-ce/blob/main/LICENSE).

### Key Capabilities

- **Certificate Issuance** — x509 CA with configurable profiles and policy enforcement
- **Enrollment** — SCEP, EST, ACME, CMP, Microsoft AutoEnrollment, and REST APIs for device and workload identity
- **HSM-first** — PKCS #11 v3.2 key driver, remote HSM brokering via `pkcs11-proxy`
- **Post-quantum** — ML-DSA, ML-KEM, and SLH-DSA support through a CIRCL-integrated Go toolchain
- **Validation** — OCSP and CRL services for certificate status checking

### Key Repositories

| Repository                                                | What it is                                                                                                                                          |
| --------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| [otpki-ce](https://github.com/otpki/otpki-ce)             | Certificate issuance, enrollment, and validation services (Community Edition)                                                                       |
| [pkcs11](https://github.com/otpki/pkcs11)                 | Go client for PKCS #11 v3.2, plus `pkcs11-proxy`: a remote HSM broker with route-per-token discovery, active-active replicas, and signed audit logs |
| [iogo](https://github.com/otpki/iogo)                     | Standalone Go toolchain fork with post-quantum crypto (CIRCL) integration                                                                           |
| [otpki-pkg](https://github.com/otpki/otpki-pkg)           | Shared Go libraries for OTPKI services                                                                                                              |
| [otpki-protobuf](https://github.com/otpki/otpki-protobuf) | Protobuf definitions                                                                                                                                |
| [otpki-keycloak](https://github.com/otpki/otpki-keycloak) | Keycloak image and theme for OTPKI                                                                                                                  |
| [otpki-docs](https://github.com/otpki/otpki-docs)         | Documentation site                                                                                                                                  |

### Forks

We maintain downstream forks where OTPKI needs changes upstream projects have not taken. Upstream licenses, attribution, and CI are preserved.

| Repository                              | Upstream                                                | License                                   |
| --------------------------------------- | ------------------------------------------------------- | ----------------------------------------- |
| [circl](https://github.com/otpki/circl) | [cloudflare/circl](https://github.com/cloudflare/circl) | BSD-3-Clause + Apache-2.0 for our changes |
| [pkcs7](https://github.com/otpki/pkcs7) | [smallstep/pkcs7](https://github.com/smallstep/pkcs7)   | MIT + Apache-2.0 for our changes          |
| [scep](https://github.com/otpki/scep)   | [smallstep/scep](https://github.com/smallstep/scep)     | MIT + Apache-2.0 for our changes          |

### Contributing

We welcome contributions from everyone. To get started:

- Read the [Contributing Guide](https://github.com/otpki/.github/blob/main/CONTRIBUTING.md) for workflow, commit conventions, and issue guidelines
- Look for issues labeled [`good first issue`](https://github.com/search?q=org%3Aotpki+label%3A%22good+first+issue%22+is%3Aopen&type=issues) to find a good starting point
- Found a bug? File an issue in the relevant repository
- Found a vulnerability? **Do not open a public issue** — report it privately through the affected repository's Security tab, or see our [security policy](https://github.com/otpki/.github/blob/main/SECURITY.md)

### Resources & Community

- [Documentation](https://docs.otpki.com) — guides and deployment instructions
- [OmniTrust](https://www.omnitrust.com) — company website
- [Support](https://github.com/otpki/.github/blob/main/SUPPORT.md) — where to get help

### License

OTPKI projects are released under the [Apache License 2.0](https://github.com/otpki/otpki-ce/blob/main/LICENSE), forks keep their upstream licenses.
