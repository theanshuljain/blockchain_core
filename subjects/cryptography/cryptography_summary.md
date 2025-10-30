# Cryptography Quiz Summary

## 🔑 Key Concepts

### Number Theory & Math Foundations
- **Prime Numbers**: Basis for RSA, primality testing (Miller-Rabin)
- **Modular Arithmetic**: a ≡ b (mod n), crucial for all crypto
- **Euler's Theorem**: a^φ(n) ≡ 1 (mod n) when gcd(a,n) = 1
- **Chinese Remainder Theorem**: Solve systems of modular equations

### Classical Cryptography
- **Caesar Cipher**: Shift by k positions
- **Vigenère**: Polyalphabetic substitution
- **One-Time Pad**: Perfect secrecy (key = message length, truly random, used once)
- **Frequency Analysis**: Breaking substitution ciphers

## 🔐 Symmetric Cryptography

### Block Ciphers
- **AES**: 128-bit blocks, 128/192/256-bit keys, SP network
- **DES**: 64-bit blocks, 56-bit keys (broken)
- **Feistel Networks**: Self-inverse structure (DES, Blowfish)

### Modes of Operation
- **ECB**: Each block independent (patterns leak)
- **CBC**: Chain blocks with IV (sequential)
- **CTR**: Counter mode (parallel, streaming)
- **GCM**: Authenticated encryption (CTR + GHASH)

### Stream Ciphers
- **RC4**: Deprecated due to biases
- **ChaCha20**: Modern, fast, secure
- **One-Time Pad**: Theoretically perfect

### Hash Functions
- **Properties**: Pre-image resistance, collision resistance
- **SHA-256**: 256-bit output, Merkle-Damgård construction
- **SHA-3**: Keccak, sponge construction
- **HMAC**: Hash-based MAC using nested hashing

## 🔑 Asymmetric Cryptography

### RSA
- **Key Gen**: n = p×q, e = 65537, d = e^(-1) mod φ(n)
- **Encrypt**: C = M^e mod n
- **Decrypt**: M = C^d mod n
- **Security**: Integer factorization problem

### Elliptic Curve Cryptography (ECC)
- **Curve**: y² = x³ + ax + b (mod p)
- **ECDSA**: Digital signatures on elliptic curves
- **Advantages**: Smaller keys, same security (256-bit ECC ≈ 3072-bit RSA)
- **Ed25519**: Fast, secure curve for signatures

### Digital Signatures
- **RSA Signatures**: S = H(M)^d mod n
- **DSA/ECDSA**: Based on discrete log problem
- **Properties**: Authentication, non-repudiation, integrity

## 🎯 Advanced Cryptography

### Zero-Knowledge Proofs
- **Properties**: Completeness, soundness, zero-knowledge
- **zk-SNARKs**: Succinct, non-interactive (Zcash)
- **zk-STARKs**: Transparent setup, post-quantum secure
- **Bulletproofs**: Range proofs without trusted setup

### Blockchain Cryptography
- **Merkle Trees**: Binary tree of hashes, O(log n) proofs
- **Hash Functions**: SHA-256 for Bitcoin, Keccak for Ethereum
- **Digital Signatures**: ECDSA standard, EdDSA emerging
- **Ring Signatures**: Anonymous signatures (Monero)

### Post-Quantum Cryptography
- **Threat**: Quantum computers break RSA/ECC
- **NIST Standards**: Kyber (KEM), Dilithium (signatures)
- **Based on**: Lattices, codes, multivariate equations

## ⚠️ Common Attacks

### Classical Attacks
- **Frequency Analysis**: Statistical attack on substitution
- **Birthday Attack**: Find collisions in √n operations
- **Meet-in-the-Middle**: Reduce key space for double encryption

### Modern Attacks
- **Side-Channel**: Timing, power analysis
- **Padding Oracle**: Exploit padding validation
- **Chosen Plaintext/Ciphertext**: Active attacks

## 🔧 Practical Applications

### TLS/SSL
- **Handshake**: Key exchange + authentication
- **Cipher Suites**: Key exchange + auth + encryption + MAC
- **Perfect Forward Secrecy**: Ephemeral keys

### PKI (Public Key Infrastructure)
- **Certificate Authority**: Issues certificates
- **X.509 Certificates**: Standard format
- **Certificate Chain**: Root → Intermediate → End entity

## 📊 Key Algorithms Summary

| Algorithm | Type | Key Size | Security Level |
|-----------|------|----------|----------------|
| AES-128 | Symmetric | 128-bit | High |
| RSA-2048 | Asymmetric | 2048-bit | Medium |
| ECDSA-256 | Signature | 256-bit | High |
| SHA-256 | Hash | - | High |
| ChaCha20 | Stream | 256-bit | High |

## 🎓 Quiz Tips
- Know the difference between symmetric vs asymmetric
- Understand hash function properties
- Remember RSA key generation steps
- Know ECC advantages over RSA
- Understand zero-knowledge proof properties
- Remember blockchain cryptography basics