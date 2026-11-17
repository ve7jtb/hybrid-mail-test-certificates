# Hybrid Mail test certificates

Public test certificates for [Hybrid Mail](https://github.com/ve7jtb/hybrid-mail), published by ve7jtb. These certificates were issued on 2026-11-16 (Pacific time) for the test mailbox using the same Beta0 YubiKey keys as the successful pure/composite PKCS#11 S/MIME tests. All four new certificate signatures were produced by the packaged desktop app and independently verified with Bouncy Castle. The original beta0@example.test certificates remain available in Git history.

Only public X.509 certificates are included. Private keys remain on the YubiKey. No PINs, passwords, PKCS#12 identity files, device serials or mail messages are included.

## Certificates

| Certificate | Public-key algorithm | PEM | DER |
|---|---|---|---|
| pure-signing | `ML-DSA-65` | [pure-signing.pem](pure-signing.pem) | [pure-signing.cer](pure-signing.cer) |
| pure-encryption | `ML-KEM-768` | [pure-encryption.pem](pure-encryption.pem) | [pure-encryption.cer](pure-encryption.cer) |
| hybrid-signing | `MLDSA65-RSA3072-PSS-SHA512` | [hybrid-signing.pem](hybrid-signing.pem) | [hybrid-signing.cer](hybrid-signing.cer) |
| hybrid-encryption | `MLKEM768-ECDH-P256-SHA3-256` | [hybrid-encryption.pem](hybrid-encryption.pem) | [hybrid-encryption.cer](hybrid-encryption.cer) |

All current certificates have subject `CN=ve7jtb@gmail.com` and Subject Alternative Name `rfc822Name:ve7jtb@gmail.com`. These are self-issued test credentials for that mailbox, not a claim of CA-validated mailbox ownership. The pure and hybrid signing certificates are self-signed. Each encryption certificate is signed by the corresponding signing identity. They are local test credentials, not certificates issued by a publicly trusted CA. Composite formats follow the Bouncy Castle revision pinned by Hybrid Mail.

Use signing certificates to verify or pin test signatures, and encryption certificates as recipients for test encryption. Do not use the signing certificate as an encryption recipient. Only the owner of the corresponding private keys can decrypt. Both certificate signatures and PEM/DER byte equivalence were checked with the app's Bouncy Castle build before publication.

## SHA-256 certificate fingerprints

Fingerprints cover DER certificate bytes (not PEM text).

- **pure-signing**: `1fd7a5f11c36bc0b9c33f78f586c9c2bd367d3b51ca743474dab09f4190b5440`
  Validity: 2026-11-16T23:58:41Z through 2027-11-16T23:59:41Z.
- **pure-encryption**: `db8b6088ed8b8877b44bcc2efaa402767d8ddd5d5fa919d421b9dc67be22c9b4`
  Validity: 2026-11-17T00:01:14Z through 2027-11-17T00:02:14Z.
- **hybrid-signing**: `78e165e75787beb21e86c9e3961ed28a9545165314b4a22dca1f9cc5ce005094`
  Validity: 2026-11-17T00:01:25Z through 2027-11-17T00:02:25Z.
- **hybrid-encryption**: `5aa7704bd2481067106aa9ae16e352ef8094d80a1fe08889bf108d355e1b2cf7`
  Validity: 2026-11-17T00:01:46Z through 2027-11-17T00:02:46Z.

`SHA256SUMS` contains hashes for all eight certificate files. On macOS, run `shasum -a 256 -c SHA256SUMS`; on Linux, run `sha256sum -c SHA256SUMS`.
