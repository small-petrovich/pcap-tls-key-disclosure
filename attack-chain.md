# Attack Chain

1. Identify service on port 1337
2. Discover `/k3y` endpoint
3. Extract private RSA key
4. Identify TLS service on port 1338
5. Confirm absence of PFS
6. Import key into Wireshark
7. Decrypt TLS session
8. Extract `/file`
9. Recover secret message
