# Attack Diagram

HTTP 1337 → /k3y → PRIVATE KEY  
        ↓  
TLS 1338 (TLS_RSA, TLS 1.0, no PFS)  
        ↓  
Import private key  
        ↓  
Decrypt TLS  
        ↓  
GET /file  
        ↓  
PNG with secret message
