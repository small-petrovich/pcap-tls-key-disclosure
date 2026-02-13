# Security Assessment Report

## Executive Summary

During analysis of the provided network capture, a critical misconfiguration was identified: a private RSA key was exposed via HTTP without authentication.

Due to the use of TLS without Perfect Forward Secrecy, full TLS session decryption was successfully demonstrated.

This represents a complete compromise of confidentiality.

---

## Technical Findings

### F-01 — Private Key Disclosure  
Severity: Critical  
CVSS v3.1: 9.8  

Endpoint `/k3y` on port 1337 exposes a private RSA key in PEM format over HTTP without authentication.

---

### F-02 — TLS Without Perfect Forward Secrecy  
Severity: Critical  

Cipher suite used:
`TLS_RSA_WITH_AES_256_CBC_SHA`

Key exchange: RSA  
No ECDHE/DHE → No PFS  

This allows TLS decryption if the private key is compromised.

---

### F-03 — Deprecated TLS Version  
Severity: High  

TLS 1.0 is deprecated and vulnerable to known attacks.

---

## Proof of Exploitation

1. Extracted private RSA key.
2. Imported key into Wireshark.
3. Successfully decrypted TLS session.
4. Observed HTTP request inside TLS:
   GET /file
5. Extracted PNG file containing secret message.

---

## Recommendations

- Immediately revoke exposed key.
- Reissue TLS certificate.
- Enforce TLS 1.2 or TLS 1.3.
- Use ECDHE cipher suites.
- Remove sensitive files from web-accessible directories.
