# 🔐 Network Traffic Analysis — TLS Key Disclosure & Decryption

## 📌 Overview

This repository contains a full security analysis of the provided network traffic capture (`cap3.pcapng`).

The analysis demonstrates full TLS session decryption caused by private key disclosure and lack of Perfect Forward Secrecy.

---

## 🔎 Key Findings

- Private RSA key exposed via HTTP endpoint `/k3y`
- TLS service running on port 1338
- Cipher suite: `TLS_RSA_WITH_AES_256_CBC_SHA`
- No Perfect Forward Secrecy (PFS)
- Deprecated TLS 1.0 protocol
- Successful TLS session decryption
- Extraction of protected resource `/file`

---

## 💣 Result

The combination of private key exposure and insecure TLS configuration allowed full decryption of the encrypted session and extraction of sensitive data.

---

## 📂 Repository Structure

- report.md — Full technical security report
- attack-chain.md — Exploitation sequence
- diagram.md — Attack diagram
- screenshots/ — Wireshark evidence
- artifacts/ — Extracted file

---

## 👤 Author

Kirill M8v 
Information Security
