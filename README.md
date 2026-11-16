# Hybrid Mail test certificates

Public test certificates for [Hybrid Mail](https://github.com/ve7jtb/hybrid-mail), published by ve7jtb. These are the current certificates used in the successful Beta0 YubiKey PKCS#11 S/MIME tests on 2026-11-16.

Only public X.509 certificates are included. Private keys remain on the YubiKey. No PINs, passwords, PKCS#12 identity files, device serials or mail messages are included.

## Certificates

| Certificate | Public-key algorithm | PEM | DER |
|---|---|---|---|
| pure-signing | `ML-DSA-65` | [pure-signing.pem](pure-signing.pem) | [pure-signing.cer](pure-signing.cer) |
| pure-encryption | `ML-KEM-768` | [pure-encryption.pem](pure-encryption.pem) | [pure-encryption.cer](pure-encryption.cer) |
| hybrid-signing | `MLDSA65-RSA3072-PSS-SHA512` | [hybrid-signing.pem](hybrid-signing.pem) | [hybrid-signing.cer](hybrid-signing.cer) |
| hybrid-encryption | `MLKEM768-ECDH-P256-SHA3-256` | [hybrid-encryption.pem](hybrid-encryption.pem) | [hybrid-encryption.cer](hybrid-encryption.cer) |

All certificates identify `beta0@example.test`, a demonstration address, not a deliverable mailbox. The pure and hybrid signing certificates are self-signed. Each encryption certificate is signed by the corresponding signing identity. They are local test credentials, not certificates issued by a publicly trusted CA. Composite formats follow the Bouncy Castle revision pinned by Hybrid Mail.

Use signing certificates to verify or pin test signatures, and encryption certificates as recipients for test encryption. Do not use the signing certificate as an encryption recipient. Only the owner of the corresponding private keys can decrypt. Both certificate signatures and PEM/DER byte equivalence were checked with the app's Bouncy Castle build before publication.

## SHA-256 certificate fingerprints

Fingerprints cover the DER certificate bytes (not the PEM text).

- **pure-signing**: `7c3bcab62805c001e58a3945fa7e6d2a4669bb1aad36c253c85e512da5bc26ad`
  Validity: 2026-11-16T23:03:36Z through 2027-11-16T23:04:36Z.
- **pure-encryption**: `663bc2711296fc72ecb161dd2cf60c9af403eb031de6888a1e895555b45d971d`
  Validity: 2026-11-16T23:21:00Z through 2027-11-16T23:22:00Z.
- **hybrid-signing**: `5061de6ab8698785b7c71dc5c5e7a46fefdd6858a6a1e8eff05a2a7baf3aed13`
  Validity: 2026-11-16T23:03:59Z through 2027-11-16T23:04:59Z.
- **hybrid-encryption**: `a4245b6f1ef4713fc3f6402b83b49ffebf24823ad3df4655aa51fe3602962dd2`
  Validity: 2026-11-16T23:21:41Z through 2027-11-16T23:22:41Z.

`SHA256SUMS` contains file hashes for all eight certificate files. On macOS, run `shasum -a 256 -c SHA256SUMS`; on Linux, run `sha256sum -c SHA256SUMS`.
