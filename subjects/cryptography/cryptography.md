# Cryptography
## Introduction
Cryptography is the science of **securing information** through mathematical algorithms and computational techniques to ensure **confidentiality**, **integrity**, and **authenticity** in digital communications.

It forms the **fundamental backbone** of modern information security and blockchain technology.

---

# Foundations & Mathematics

## Number Theory

### Prime Numbers and Primality Testing
**Prime numbers** are natural numbers greater than 1 that have no positive divisors other than 1 and themselves.

#### Key Properties
- **Fundamental Theorem of Arithmetic**: Every integer > 1 can be uniquely factored into prime numbers
- **Infinite Primes**: There are infinitely many prime numbers (Euclid's proof)
- **Prime Distribution**: Approximately n/ln(n) primes less than n (Prime Number Theorem)

#### Primality Testing Algorithms
- **Trial Division**: Test divisibility up to √n - O(√n) complexity
- **Fermat Test**: Probabilistic test using Fermat's Little Theorem
- **Miller-Rabin Test**: More robust probabilistic primality test
- **AKS Algorithm**: First deterministic polynomial-time primality test

### Modular Arithmetic
**Modular arithmetic** is arithmetic for integers where numbers "wrap around" after reaching a certain value (the modulus).

#### Fundamental Operations
```
a ≡ b (mod n) means n divides (a - b)
Addition: (a + b) mod n
Multiplication: (a × b) mod n
Exponentiation: a^k mod n (using fast exponentiation)
```

#### Properties
- **Closure**: Operations remain within the modular system
- **Associativity**: (a + b) + c ≡ a + (b + c) (mod n)
- **Commutativity**: a + b ≡ b + a (mod n)
- **Distributivity**: a(b + c) ≡ ab + ac (mod n)

### Greatest Common Divisor (GCD) Algorithms

#### Euclidean Algorithm
**Most efficient** method for computing GCD of two integers.
```
gcd(a, 0) = a
gcd(a, b) = gcd(b, a mod b)
```

#### Extended Euclidean Algorithm
Finds integers x, y such that: **ax + by = gcd(a, b)**
- **Crucial** for computing modular inverses
- **Time Complexity**: O(log min(a, b))

### Modular Inverses
The **modular multiplicative inverse** of a modulo m is an integer x such that:
```
ax ≡ 1 (mod m)
```

#### Computation Methods
- **Extended Euclidean Algorithm**: Most common method
- **Fermat's Little Theorem**: When m is prime: a^(-1) ≡ a^(p-2) (mod p)
- **Euler's Theorem**: When gcd(a,m) = 1: a^(-1) ≡ a^(φ(m)-1) (mod m)

### Important Theorems

#### Fermat's Little Theorem
If **p is prime** and **a is not divisible by p**, then:
```
a^(p-1) ≡ 1 (mod p)
```
**Applications**: Primality testing, modular exponentiation, RSA cryptosystem

#### Euler's Theorem
If **gcd(a, n) = 1**, then:
```
a^φ(n) ≡ 1 (mod n)
```
where φ(n) is **Euler's totient function** (count of integers ≤ n that are coprime to n).

#### Chinese Remainder Theorem (CRT)
Given pairwise coprime moduli m₁, m₂, ..., mₖ, the system:
```
x ≡ a₁ (mod m₁)
x ≡ a₂ (mod m₂)
...
x ≡ aₖ (mod mₖ)
```
has a **unique solution** modulo M = m₁ × m₂ × ... × mₖ.

**Applications**: RSA optimization, parallel computation, solving modular equations

## Abstract Algebra

### Group Theory
A **group** (G, ∗) is a set G with binary operation ∗ satisfying:
- **Closure**: a, b ∈ G → a ∗ b ∈ G
- **Associativity**: (a ∗ b) ∗ c = a ∗ (b ∗ c)
- **Identity Element**: ∃ e ∈ G such that e ∗ a = a ∗ e = a
- **Inverse Element**: ∀ a ∈ G, ∃ a⁻¹ such that a ∗ a⁻¹ = e

#### Cryptographic Applications
- **Diffie-Hellman Key Exchange**: Based on cyclic groups
- **Elliptic Curve Cryptography**: Uses elliptic curve groups
- **Digital Signatures**: Group operations ensure security

### Ring Theory
A **ring** (R, +, ×) has two operations satisfying:
- (R, +) forms an **abelian group**
- × is **associative** and **distributive** over +

#### Field Theory
A **field** is a ring where every non-zero element has a multiplicative inverse.
- **Finite Fields GF(p)**: Integers modulo prime p
- **Binary Fields GF(2ⁿ)**: Used in AES, error correction

### Finite Fields (Galois Fields)
**Finite fields GF(q)** where q = pⁿ (p prime, n ≥ 1) are fundamental in cryptography.

#### Properties
- **Addition and Multiplication** are closed operations
- **Every non-zero element** has a multiplicative inverse
- **Characteristic**: p (the prime)

#### Applications
- **AES Encryption**: Operations in GF(2⁸)
- **Reed-Solomon Codes**: Error correction using GF(2ᵐ)
- **Elliptic Curves**: Defined over finite fields

## Elliptic Curves
**Elliptic curves** over finite fields form the basis of modern public-key cryptography.

### Mathematical Definition
An elliptic curve over GF(p) is defined by:
```
y² ≡ x³ + ax + b (mod p)
```
where **4a³ + 27b² ≢ 0 (mod p)** (non-singular condition).

### Group Law
- **Point Addition**: Geometric/algebraic rules for adding points
- **Point Doubling**: Special case of addition
- **Identity Element**: Point at infinity (O)
- **Inverse**: (x, y) + (x, -y) = O

### Cryptographic Advantages
- **Smaller Key Sizes**: 256-bit ECC ≈ 3072-bit RSA security
- **Efficient Operations**: Faster computation
- **Lower Power Consumption**: Ideal for mobile devices

## Information Theory & Probability

### Entropy
**Shannon entropy** measures the average information content:
```
H(X) = -Σ P(xᵢ) log₂ P(xᵢ)
```

#### Cryptographic Relevance
- **Key Generation**: High entropy ensures unpredictability
- **Random Number Generation**: Entropy sources for cryptographic randomness
- **Perfect Secrecy**: One-time pad achieves maximum entropy

### Probability Theory in Cryptography
- **Birthday Paradox**: Collision probability in hash functions
- **Random Oracle Model**: Idealized cryptographic analysis
- **Probabilistic Algorithms**: Monte Carlo primality testing

## Complexity Theory

### Computational Hardness Assumptions
Modern cryptography relies on **computational problems** believed to be intractable:

#### Integer Factorization Problem
- **Problem**: Given n = pq, find p and q
- **Best Algorithm**: General Number Field Sieve - sub-exponential
- **Applications**: RSA security

#### Discrete Logarithm Problem (DLP)
- **Problem**: Given g, h, find x such that gˣ ≡ h (mod p)
- **Applications**: Diffie-Hellman, DSA, ElGamal

#### Elliptic Curve Discrete Logarithm Problem (ECDLP)
- **Problem**: Given points P, Q on elliptic curve, find k such that Q = kP
- **Hardness**: No sub-exponential algorithm known
- **Applications**: ECDSA, ECDH

---

# Classical Cryptography

## Substitution Ciphers

### Caesar Cipher
**Simplest substitution cipher** shifting each letter by fixed number of positions.

#### Algorithm
```
Encryption: C = (P + k) mod 26
Decryption: P = (C - k) mod 26
```
where k is the **shift value** (key).

#### Security Analysis
- **Key Space**: Only 25 possible keys
- **Vulnerability**: Frequency analysis, brute force
- **Historical Significance**: Foundation for understanding substitution

### Monoalphabetic Substitution
Each plaintext letter maps to **exactly one** ciphertext letter throughout the message.

#### Characteristics
- **Key Space**: 26! ≈ 4 × 10²⁶ possible keys
- **Frequency Preservation**: Letter frequencies remain unchanged
- **Vulnerability**: Statistical analysis breaks the cipher

#### Cryptanalysis
- **Frequency Analysis**: Match ciphertext frequencies to language patterns
- **Pattern Analysis**: Common words, repeated sequences
- **N-gram Analysis**: Bigrams, trigrams provide additional constraints

### Polyalphabetic Ciphers
Use **multiple substitution alphabets** to obscure frequency patterns.

#### Vigenère Cipher
Uses a **keyword** to determine shifting pattern.

**Encryption Process**:
```
For each position i:
C[i] = (P[i] + K[i mod |K|]) mod 26
```

#### Alberti Cipher
**First polyalphabetic cipher** using rotating cipher disks.
- **Innovation**: Changed substitution alphabet during encryption
- **Historical Impact**: Inspired centuries of polyalphabetic development

#### Security Improvements
- **Frequency Flattening**: Multiple alphabets reduce statistical patterns
- **Increased Key Space**: Longer keywords provide more security
- **Limitations**: Still vulnerable to advanced statistical analysis

## Transposition Ciphers

### Rail Fence Cipher
**Simple transposition** writing plaintext in zigzag pattern across multiple "rails".

#### Process
1. **Write** plaintext in zigzag pattern across n rails
2. **Read** ciphertext by concatenating each rail
3. **Decryption** reverses the process

#### Example (3 rails)
```
Plaintext: HELLO WORLD
Rail 1: H   O   R  
Rail 2:  E L   W O L
Rail 3:   L     D   
Ciphertext: HORELWOLLD
```

### Columnar Transposition
**Arrange plaintext** in rectangular grid, read columns in key-determined order.

#### Algorithm
1. **Write** plaintext in rows under keyword
2. **Number** columns by alphabetical order of keyword letters
3. **Read** columns in numerical order

#### Security Features
- **Key-dependent permutation**: Column order determined by keyword
- **Variable block size**: Rectangle dimensions affect security
- **Double transposition**: Multiple rounds increase complexity

## Historical Cipher Machines

### Enigma Machine
**German rotor-based cipher machine** used in World War II.

#### Components
- **Rotors**: Wired wheels implementing complex substitutions
- **Reflector**: Ensures encryption/decryption symmetry
- **Plugboard**: Additional substitution layer
- **Ring Settings**: Rotor position offsets

#### Operation
1. **Key press** triggers rotor advancement
2. **Electrical path** through rotors, reflector, back through rotors
3. **Output lamp** indicates encrypted letter
4. **Rotor stepping**: Creates polyalphabetic effect

#### Cryptanalysis
- **Polish Mathematicians**: Initial theoretical breakthroughs
- **Bletchley Park**: Industrial-scale codebreaking
- **Weaknesses**: Predictable rotor stepping, reflector limitations

### Lorenz Cipher
**German teleprinter cipher** for high-level communications.

#### Technical Details
- **Five-bit Baudot code**: Teleprinter character encoding
- **XOR operation**: Bitwise exclusive-or with key stream
- **Twelve rotors**: Complex key generation mechanism
- **Non-regular stepping**: More sophisticated than Enigma

## One-Time Pad

### Perfect Secrecy
**Claude Shannon proved** one-time pad provides **perfect secrecy** when:
- **Key length** equals message length
- **Key is truly random**
- **Key used only once**
- **Key kept secret**

#### Mathematical Proof
For any plaintext P and ciphertext C:
```
P(P|C) = P(P)
```
Ciphertext provides **no information** about plaintext.

#### Practical Limitations
- **Key distribution**: Secure exchange of large keys
- **Key storage**: Managing massive key quantities
- **Key synchronization**: Sender/receiver coordination
- **No authentication**: Doesn't prevent message modification

## Classical Cryptanalysis

### Frequency Analysis
**Statistical attack** exploiting letter frequency patterns in natural language.

#### English Letter Frequencies
| Letter | Frequency | Letter | Frequency |
|--------|-----------|--------|-----------|
| E | 12.7% | N | 6.7% |
| T | 9.1% | R | 6.0% |
| A | 8.2% | I | 7.0% |
| O | 7.5% | S | 6.3% |

#### Analysis Techniques
- **Single letter frequency**: Match most common letters
- **Bigram analysis**: Common two-letter combinations (TH, HE, IN)
- **Trigram patterns**: Three-letter sequences (THE, AND, ING)

### Kasiski Examination
**Method** for finding keyword length in polyalphabetic ciphers.

#### Process
1. **Identify repeated sequences** in ciphertext
2. **Measure distances** between repetitions
3. **Find GCD** of all distances
4. **Keyword length** likely divides the GCD

#### Mathematical Basis
Repeated plaintext encrypted with same key portion produces identical ciphertext.

### Index of Coincidence
**Statistical measure** of letter distribution in text.

#### Formula
```
IC = Σ(fᵢ(fᵢ-1)) / (N(N-1))
```
where fᵢ is frequency of letter i, N is text length.

#### Applications
- **Language identification**: Different languages have characteristic IC values
- **Keyword length determination**: Plot IC vs. assumed key length
- **Cipher type detection**: Monoalphabetic vs. polyalphabetic patterns

#### Typical IC Values
- **English**: ~0.067
- **Random text**: ~0.038
- **Monoalphabetic cipher**: ~0.067 (preserves distribution)
- **Polyalphabetic cipher**: Between 0.038-0.067

---

# Symmetric Key Cryptography

## Block Ciphers

### Fundamental Structures

#### Feistel Network Structure
**Feistel networks** divide data into two halves and apply round functions alternately.

**Structure**:
```
For each round i:
Lᵢ₊₁ = Rᵢ
Rᵢ₊₁ = Lᵢ ⊕ F(Rᵢ, Kᵢ)
```

**Properties**:
- **Self-inverse**: Same structure for encryption/decryption
- **Round function F**: Doesn't need to be invertible
- **Key schedule**: Generates round keys from master key
- **Examples**: DES, Blowfish, Twofish

#### Substitution-Permutation (SP) Network
**SP networks** alternate **substitution** and **permutation** layers.

**Components**:
- **S-boxes**: Non-linear substitution providing confusion
- **P-boxes**: Linear permutation providing diffusion
- **Key mixing**: XOR with round keys
- **Examples**: AES, Serpent, PRESENT

**Security Principles**:
- **Confusion**: Each ciphertext bit depends on multiple key bits
- **Diffusion**: Each plaintext bit affects multiple ciphertext bits

### Major Block Cipher Algorithms

#### Data Encryption Standard (DES)
**DES** was the first widely adopted commercial encryption standard.

**Specifications**:
- **Block size**: 64 bits
- **Key size**: 56 bits (8 parity bits)
- **Rounds**: 16 Feistel rounds
- **Structure**: Feistel network with f-function

**Key Components**:
- **Initial Permutation (IP)**: Rearranges input bits
- **S-boxes**: 8 substitution boxes (6→4 bits each)
- **P-box**: 32-bit permutation after S-boxes
- **Key schedule**: Generates 16 round keys

**Security Issues**:
- **Small key space**: 2⁵⁶ keys vulnerable to brute force
- **Known attacks**: Differential, linear cryptanalysis
- **Replacement**: Superseded by AES in 2001

#### Triple DES (3DES)
**3DES** applies DES three times to increase effective key length.

**Variants**:
- **3DES-EEE**: Encrypt-Encrypt-Encrypt with 3 keys
- **3DES-EDE**: Encrypt-Decrypt-Encrypt (most common)
- **3DES-2KEY**: EDE with K₁ = K₃

**Process** (EDE):
```
C = DES_K₃(DES⁻¹_K₂(DES_K₁(P)))
```

**Security**:
- **Effective key length**: 112 bits (2-key) or 168 bits (3-key)
- **Meet-in-the-middle attack**: Reduces 3-key to 112-bit security
- **Legacy usage**: Still used in financial systems

#### Advanced Encryption Standard (AES)
**AES** is the current symmetric encryption standard adopted in 2001.

**Specifications**:
- **Block size**: 128 bits
- **Key sizes**: 128, 192, or 256 bits
- **Rounds**: 10, 12, or 14 (depending on key size)
- **Structure**: SP network based on Rijndael

**AES Operations**:
1. **SubBytes**: S-box substitution (confusion)
2. **ShiftRows**: Row-wise left shifts (diffusion)
3. **MixColumns**: Column mixing in GF(2⁸) (diffusion)
4. **AddRoundKey**: XOR with round key

**State Matrix**:
```
[s₀₀ s₀₁ s₀₂ s₀₃]
[s₁₀ s₁₁ s₁₂ s₁₃]
[s₂₀ s₂₁ s₂₂ s₂₃]
[s₃₀ s₃₁ s₃₂ s₃₃]
```

**Security Strengths**:
- **No practical attacks**: Against full-round AES
- **Side-channel resistance**: Designed to resist timing attacks
- **Quantum resistance**: 256-bit AES provides 128-bit post-quantum security

#### Other Notable Block Ciphers

##### Blowfish
- **Key size**: Variable (32-448 bits)
- **Block size**: 64 bits
- **Structure**: 16-round Feistel network
- **Features**: Fast, patent-free, large S-boxes

##### Twofish
- **AES finalist**: Bruce Schneier's design
- **Block size**: 128 bits
- **Key sizes**: 128, 192, 256 bits
- **Features**: Key-dependent S-boxes, PHT operations

##### Serpent
- **AES finalist**: Ultra-conservative design
- **Block size**: 128 bits
- **Rounds**: 32 SP rounds
- **Security**: High security margin, slower than AES

##### IDEA (International Data Encryption Algorithm)
- **Block size**: 64 bits
- **Key size**: 128 bits
- **Operations**: XOR, addition mod 2¹⁶, multiplication mod (2¹⁶ + 1)
- **Usage**: Previously used in PGP

##### PRESENT
- **Lightweight cipher**: Designed for constrained devices
- **Block size**: 64 bits
- **Key sizes**: 80 or 128 bits
- **Rounds**: 31 SP rounds

## Block Cipher Modes of Operation

### Electronic Codebook (ECB)
**Simplest mode**: Each block encrypted independently.

```
Cᵢ = E_K(Pᵢ)
Pᵢ = D_K(Cᵢ)
```

**Characteristics**:
- **Parallel encryption/decryption**: High performance
- **No chaining**: Block errors don't propagate
- **Pattern preservation**: Identical plaintext blocks → identical ciphertext

**Security Issues**:
- **Pattern leakage**: Images, structured data reveal patterns
- **Replay attacks**: Blocks can be rearranged
- **Not recommended**: For most applications

### Cipher Block Chaining (CBC)
**Chains blocks**: Each block XORed with previous ciphertext.

```
C₀ = IV (Initialization Vector)
Cᵢ = E_K(Pᵢ ⊕ Cᵢ₋₁)
Pᵢ = D_K(Cᵢ) ⊕ Cᵢ₋₁
```

**Properties**:
- **IV requirement**: Must be random and unpredictable
- **Error propagation**: Single bit error affects two blocks
- **No parallelization**: Encryption must be sequential
- **Common usage**: TLS, file encryption

### Cipher Feedback (CFB)
**Stream cipher mode**: Encrypts in smaller units than block size.

```
C₀ = IV
Cᵢ = Pᵢ ⊕ MSB_s(E_K(Cᵢ₋₁))
```

**Features**:
- **Variable segment size**: Can encrypt s bits at a time
- **Self-synchronizing**: Recovers from bit errors
- **No padding required**: Handles arbitrary message lengths

### Output Feedback (OFB)
**Keystream generation**: Creates stream independent of plaintext.

```
S₀ = IV
Sᵢ = E_K(Sᵢ₋₁)
Cᵢ = Pᵢ ⊕ Sᵢ
```

**Advantages**:
- **Bit-level encryption**: No padding needed
- **No error propagation**: Single bit errors affect only corresponding bit
- **Parallel decryption**: Keystream can be precomputed

### Counter Mode (CTR)
**Counter-based**: Encrypts incrementing counter values.

```
Cᵢ = Pᵢ ⊕ E_K(Counter + i)
```

**Benefits**:
- **Full parallelization**: Both encryption and decryption
- **Random access**: Can decrypt any block independently
- **No padding**: Handles arbitrary lengths
- **Streaming**: Can process data as it arrives

### Galois/Counter Mode (GCM)
**Authenticated encryption**: Combines CTR mode with Galois field authentication.

**Components**:
- **Encryption**: CTR mode for confidentiality
- **Authentication**: GHASH for integrity
- **Additional data**: Can authenticate unencrypted data

**Process**:
```
Cᵢ = Pᵢ ⊕ E_K(Counter + i)
Tag = GHASH_H(A, C) ⊕ E_K(Counter)
```

**Applications**:
- **TLS 1.2/1.3**: Primary AEAD mode
- **WPA3**: WiFi security
- **IPSec**: VPN encryption

### XEX-based Tweaked-codebook mode (XTS)
**Disk encryption mode**: Designed for storage encryption.

**Features**:
- **Tweak input**: Sector/block position prevents copy attacks
- **Length-preserving**: Ciphertext same length as plaintext
- **No expansion**: Critical for disk encryption

**Process**:
```
T = E_K₂(i) · α^j  (tweak calculation)
C = E_K₁(P ⊕ T) ⊕ T
```

## Stream Ciphers

### Linear Feedback Shift Registers (LFSR)
**LFSR** forms the basis of many stream cipher designs.

#### Structure
- **Shift register**: n-bit register with feedback
- **Feedback polynomial**: Determines output sequence
- **Maximum period**: 2ⁿ - 1 for primitive polynomial

#### Properties
- **Linear operation**: XOR-based feedback
- **Predictable**: Linear equations can be solved
- **Building block**: Combined in complex designs

### RC4
**Variable-key-size stream cipher** widely used in protocols.

#### Algorithm
```
Key Scheduling:
for i = 0 to 255: S[i] = i
j = 0
for i = 0 to 255: 
    j = (j + S[i] + key[i mod keylen]) mod 256
    swap(S[i], S[j])

Pseudo-Random Generation:
i = j = 0
for each byte:
    i = (i + 1) mod 256
    j = (j + S[i]) mod 256
    swap(S[i], S[j])
    output S[(S[i] + S[j]) mod 256]
```

#### Security Issues
- **Biased outputs**: First bytes are predictable
- **Related-key attacks**: Weak key scheduling
- **WEP vulnerabilities**: Poor IV usage in WiFi
- **Deprecated**: Replaced by modern alternatives

### ChaCha20
**Modern stream cipher** designed by Daniel J. Bernstein.

#### Features
- **256-bit key**: High security margin
- **64-bit nonce**: Prevents key reuse
- **ARX operations**: Addition, Rotation, XOR
- **Quarter-round function**: Core building block

#### Advantages
- **Software efficiency**: Fast on general-purpose CPUs
- **Side-channel resistance**: Constant-time operations
- **TLS adoption**: Used in TLS 1.3
- **Cryptanalysis resistance**: No practical attacks

### Salsa20
**Predecessor to ChaCha20** with similar design principles.

#### Characteristics
- **256-bit or 128-bit keys**
- **64-bit nonce**
- **Matrix-based state**: 4×4 32-bit words
- **20 rounds**: Double rounds for security

### Lightweight Stream Ciphers

#### Grain
- **Target**: RFID and sensor networks
- **State size**: 160 bits (Grain-128)
- **LFSR + NLFSR**: Linear and non-linear components
- **Hardware efficient**: Low gate count

#### Trivium
- **eSTREAM portfolio**: Hardware-oriented cipher
- **State size**: 288 bits
- **Simple structure**: Three shift registers
- **High throughput**: Parallel implementation

## Cryptographic Hash Functions

### Properties of Cryptographic Hash Functions
A cryptographic hash function h must satisfy:

1. **Pre-image resistance**: Given h(x), hard to find x
2. **Second pre-image resistance**: Given x, hard to find x' such that h(x) = h(x')
3. **Collision resistance**: Hard to find x, x' such that h(x) = h(x')

### MD5 (Message Digest 5)
**128-bit hash function** designed by Ron Rivest.

#### Specifications
- **Block size**: 512 bits
- **Output size**: 128 bits
- **Rounds**: 64 operations in 4 rounds
- **Operations**: Modular addition, bitwise operations

#### Security Status
- **Collision attacks**: Practical attacks exist (2004)
- **Chosen-prefix attacks**: Can create meaningful colliding documents
- **Deprecated**: Not suitable for security applications
- **Legacy usage**: Still used for checksums (non-cryptographic)

### SHA-1 (Secure Hash Algorithm 1)
**160-bit hash function** designed by NSA.

#### Design
- **Block size**: 512 bits
- **Output size**: 160 bits
- **Rounds**: 80 rounds in 4 groups
- **Based on MD4**: Improved design

#### Security Issues
- **Theoretical attacks**: Collision complexity reduced
- **SHAttered attack** (2017): Practical collision demonstration
- **Deprecated**: Major organizations phasing out
- **Timeline**: NIST deprecated for digital signatures (2011)

### SHA-2 Family
**Family of hash functions** with different output sizes.

#### Variants
| Function | Output Size | Block Size | Word Size |
|----------|-------------|------------|-----------|
| SHA-224 | 224 bits | 512 bits | 32 bits |
| SHA-256 | 256 bits | 512 bits | 32 bits |
| SHA-384 | 384 bits | 1024 bits | 64 bits |
| SHA-512 | 512 bits | 1024 bits | 64 bits |

#### Design Principles
- **Merkle–Damgård construction**: Iterative design
- **Compression function**: Based on modified SHACAL block cipher
- **Message schedule**: Expands 16 words to 64/80 words
- **Security**: No practical attacks against full versions

#### Applications
- **Bitcoin**: SHA-256 for proof-of-work
- **TLS**: Certificate signatures
- **Password hashing**: With proper salting
- **HMAC**: Message authentication

### SHA-3 (Keccak)
**Latest NIST standard** using different construction than SHA-2.

#### Sponge Construction
```
Absorption: XOR input with state
Permutation: Apply Keccak-f function
Squeezing: Extract output bits
```

#### Advantages
- **Different design**: Sponge vs. Merkle–Damgård
- **Security margin**: Large internal state
- **Flexibility**: Variable output length
- **Quantum resistance**: Better post-quantum security

#### Variants
- **SHA3-224, SHA3-256, SHA3-384, SHA3-512**: Fixed outputs
- **SHAKE128, SHAKE256**: Extendable output functions

### BLAKE2/BLAKE3
**High-performance hash functions** designed for modern applications.

#### BLAKE2 Features
- **Speed**: Faster than MD5, SHA-1, SHA-2
- **Security**: Based on ChaCha stream cipher
- **Flexibility**: Configurable output length, personalization
- **Variants**: BLAKE2b (64-bit), BLAKE2s (32-bit)

#### BLAKE3 Improvements
- **Parallelization**: Tree-based design
- **Unlimited parallelism**: Scales with available cores
- **Incremental updates**: Efficient re-hashing
- **Unified algorithm**: One algorithm for all use cases

### Hash-based Message Authentication Code (HMAC)

#### Construction
```
HMAC(K, m) = H((K ⊕ opad) || H((K ⊕ ipad) || m))
```

where:
- **K**: Secret key (adjusted to block length)
- **opad**: Outer padding (0x5c repeated)
- **ipad**: Inner padding (0x36 repeated)
- **H**: Underlying hash function

#### Security Properties
- **Pseudorandom function**: Under suitable assumptions
- **Key recovery resistance**: Even with many MAC values
- **Forgery resistance**: Cannot create valid MACs without key

#### Applications
- **TLS**: Record authentication
- **IPSec**: Packet authentication
- **JWT**: Token signatures
- **API authentication**: Request signing

---

# Asymmetric Key Cryptography

## Integer Factorization Based Cryptography

### RSA Cryptosystem
**RSA** is the most widely used public-key cryptosystem, based on the difficulty of factoring large integers.

#### Mathematical Foundation
RSA security relies on the **Integer Factorization Problem**: Given n = pq (where p, q are large primes), finding p and q is computationally hard.

#### RSA Key Generation
1. **Choose primes**: Select two large primes p and q (typically 1024+ bits each)
2. **Compute modulus**: n = p × q
3. **Calculate totient**: φ(n) = (p-1)(q-1)
4. **Choose public exponent**: e such that gcd(e, φ(n)) = 1 (commonly e = 65537)
5. **Compute private exponent**: d ≡ e⁻¹ (mod φ(n))
6. **Public key**: (n, e)
7. **Private key**: (n, d) or (p, q, d)

#### RSA Encryption/Decryption
**Encryption** (with public key):
```
C ≡ M^e (mod n)
```

**Decryption** (with private key):
```
M ≡ C^d (mod n)
```

**Correctness proof**:
```
C^d ≡ (M^e)^d ≡ M^(ed) ≡ M^1 ≡ M (mod n)
```
(by Euler's theorem, since ed ≡ 1 (mod φ(n)))

#### RSA Digital Signatures
**Signing** (with private key):
```
S ≡ H(M)^d (mod n)
```

**Verification** (with public key):
```
H(M) ≟ S^e (mod n)
```

#### RSA-PSS (Probabilistic Signature Scheme)
**Improved RSA signature** scheme with better security properties.

**Features**:
- **Randomized padding**: Prevents signature forgery attacks
- **Provable security**: Tight security reduction
- **Standard compliance**: PKCS#1 v2.1, RFC 3447

**Process**:
1. **Hash message**: H = Hash(M)
2. **Generate salt**: Random salt value
3. **Create padded hash**: MGF-based padding with salt
4. **Sign**: Apply RSA private key operation

#### Rabin Cryptosystem
**Alternative to RSA** with equivalent security to factoring.

**Key Generation**:
- Choose primes p, q ≡ 3 (mod 4)
- Public key: n = pq
- Private key: (p, q)

**Encryption**:
```
C ≡ M² (mod n)
```

**Decryption**:
- Compute square roots modulo p and q
- Use Chinese Remainder Theorem to find M

**Security Advantage**: Breaking Rabin is **provably equivalent** to factoring n.

## Discrete Logarithm Based Cryptography

### Diffie-Hellman Key Exchange
**First public-key protocol** enabling secure key establishment over insecure channels.

#### Protocol
**Public parameters**: Prime p, generator g of multiplicative group ℤₚ*

1. **Alice generates**: Private key a, public key A = gᵃ mod p
2. **Bob generates**: Private key b, public key B = gᵇ mod p
3. **Key exchange**: Alice and Bob exchange A and B
4. **Shared secret**: K = Aᵇ mod p = Bᵃ mod p = gᵃᵇ mod p

#### Security
- **Computational DH assumption**: Computing gᵃᵇ from g, gᵃ, gᵇ is hard
- **Decision DH assumption**: Distinguishing gᵃᵇ from random is hard
- **Vulnerability**: Man-in-the-middle attacks (solved by authentication)

### ElGamal Encryption
**Probabilistic public-key encryption** based on discrete logarithm problem.

#### Key Generation
- Choose prime p, generator g
- Private key: x ∈ ℤₚ₋₁
- Public key: (p, g, y = gˣ mod p)

#### Encryption
For message M:
1. **Choose random**: k ∈ ℤₚ₋₁
2. **Compute ciphertext**: (c₁, c₂) where:
   ```
   c₁ = gᵏ mod p
   c₂ = M · yᵏ mod p
   ```

#### Decryption
```
M = c₂ · (c₁ˣ)⁻¹ mod p
```

**Properties**:
- **Semantic security**: Randomized encryption
- **Ciphertext expansion**: 2× message size
- **Malleable**: Multiplicatively homomorphic

### Digital Signature Algorithm (DSA)
**NIST standard** for digital signatures based on discrete logarithms.

#### Parameters
- **Prime modulus**: p (1024-3072 bits)
- **Prime divisor**: q divides (p-1), typically 160-256 bits
- **Generator**: g of order q in ℤₚ*

#### Key Generation
- **Private key**: x ∈ {1, ..., q-1}
- **Public key**: y = gˣ mod p

#### Signature Generation
For message M:
1. **Choose random**: k ∈ {1, ..., q-1}
2. **Compute**: r = (gᵏ mod p) mod q
3. **Compute**: s = k⁻¹(H(M) + xr) mod q
4. **Signature**: (r, s)

#### Signature Verification
1. **Compute**: w = s⁻¹ mod q
2. **Compute**: u₁ = H(M) · w mod q, u₂ = r · w mod q
3. **Verify**: r ≟ (gᵘ¹ · yᵘ² mod p) mod q

## Elliptic Curve Cryptography (ECC)

### Mathematical Foundation
**Elliptic curves** over finite fields provide the same security as integer-based systems with much smaller key sizes.

#### Curve Equation
Over prime field 𝔽ₚ:
```
y² ≡ x³ + ax + b (mod p)
```

#### Point Addition
For points P = (x₁, y₁) and Q = (x₂, y₂):

**Case 1** (P ≠ Q):
```
λ = (y₂ - y₁) · (x₂ - x₁)⁻¹ mod p
x₃ = λ² - x₁ - x₂ mod p
y₃ = λ(x₁ - x₃) - y₁ mod p
```

**Case 2** (P = Q, point doubling):
```
λ = (3x₁² + a) · (2y₁)⁻¹ mod p
x₃ = λ² - 2x₁ mod p
y₃ = λ(x₁ - x₃) - y₁ mod p
```

### Elliptic Curve Digital Signature Algorithm (ECDSA)
**Elliptic curve version** of DSA with smaller key sizes.

#### Domain Parameters
- **Curve**: E(𝔽ₚ) defined by y² = x³ + ax + b
- **Base point**: G of order n
- **Cofactor**: h = #E(𝔽ₚ)/n

#### Key Generation
- **Private key**: d ∈ {1, ..., n-1}
- **Public key**: Q = dG

#### Signature Generation
1. **Choose random**: k ∈ {1, ..., n-1}
2. **Compute point**: (x₁, y₁) = kG
3. **Compute**: r = x₁ mod n
4. **Compute**: s = k⁻¹(H(M) + dr) mod n
5. **Signature**: (r, s)

#### Security Advantages
- **Smaller keys**: 256-bit ECC ≈ 3072-bit RSA
- **Faster operations**: Especially on mobile devices
- **Lower bandwidth**: Smaller signatures and certificates

### Elliptic Curve Diffie-Hellman (ECDH)
**Key agreement** protocol using elliptic curve arithmetic.

#### Protocol
1. **Alice**: Private key dₐ, public key Qₐ = dₐG
2. **Bob**: Private key dᵦ, public key Qᵦ = dᵦG
3. **Shared secret**: K = dₐQᵦ = dᵦQₐ = dₐdᵦG

### EdDSA (Edwards-curve Digital Signature Algorithm)
**Modern signature scheme** using Edwards curves with improved performance and security.

#### Edwards Curve Form
```
x² + y² = 1 + dx²y²
```

#### Ed25519 (Popular EdDSA Variant)
- **Curve**: Edwards25519 over 𝔽₂²⁵⁵₋₁₉
- **Key size**: 256 bits
- **Signature size**: 512 bits
- **Performance**: Very fast signing and verification

#### Advantages
- **Complete addition formulas**: No special cases
- **Deterministic**: No random number generation during signing
- **Resilience**: Resistant to side-channel attacks
- **Batch verification**: Multiple signatures verified efficiently

### Schnorr Signatures
**Simple and elegant** signature scheme with excellent properties.

#### Basic Schnorr Scheme
**Key Generation**:
- Private key: x ∈ ℤₚ₋₁
- Public key: y = gˣ mod p

**Signature Generation**:
1. Choose random r ∈ ℤₚ₋₁
2. Compute R = gʳ mod p
3. Compute e = H(M || R)
4. Compute s = r + ex mod (p-1)
5. Signature: (R, s)

**Verification**:
Check if R ≟ gˢy⁻ᵉ mod p

#### Properties
- **Provable security**: Under discrete log assumption
- **Linear**: Enables efficient multi-signatures
- **Non-malleable**: Cannot modify signatures
- **Batch verification**: Multiple signatures verified together

## Lattice-Based Cryptography

### Learning With Errors (LWE)
**Fundamental problem** underlying most lattice-based cryptography.

#### LWE Problem
Given samples (aᵢ, bᵢ) where:
```
bᵢ = ⟨aᵢ, s⟩ + eᵢ mod q
```
- **aᵢ**: Random vectors in ℤₚⁿ
- **s**: Secret vector
- **eᵢ**: Small error terms
- **Goal**: Recover s

#### Security
- **Worst-case to average-case reduction**: LWE hardness implies lattice problem hardness
- **Quantum resistance**: No known efficient quantum algorithms
- **Parameter selection**: Balance security, efficiency, and correctness

### Ring-LWE
**Structured variant** of LWE using polynomial rings for efficiency.

#### Ring Structure
- **Polynomial ring**: R = ℤ[x]/(xⁿ + 1) where n is power of 2
- **Quotient ring**: Rq = R/qR
- **Advantage**: More efficient operations via FFT

#### Applications
- **Key exchange**: Ring-LWE based Diffie-Hellman
- **Encryption**: More compact than standard LWE
- **Signatures**: Basis for lattice signatures

### Post-Quantum Algorithms

#### Kyber (Key Encapsulation)
**NIST selected** algorithm for key encapsulation mechanism.

**Features**:
- **Based on**: Module-LWE (generalization of Ring-LWE)
- **Key sizes**: Kyber512, Kyber768, Kyber1024
- **Security levels**: Equivalent to AES-128, AES-192, AES-256
- **Performance**: Efficient implementation on various platforms

#### Dilithium (Digital Signatures)
**NIST selected** algorithm for post-quantum signatures.

**Design**:
- **Based on**: Module-LWE and FIAT-Shamir transform
- **Security levels**: Dilithium2, Dilithium3, Dilithium5
- **Signature technique**: Rejection sampling for security
- **Advantages**: Strong security proofs, reasonable signature sizes

#### NTRUEncrypt
**Alternative lattice** cryptosystem with different structure.

**Key Features**:
- **NTRU lattice**: Special structure for efficiency
- **Operations**: Polynomial multiplication in truncated ring
- **Decryption failures**: Small probability, managed by parameters
- **Legacy**: One of oldest post-quantum proposals

## Other Post-Quantum Approaches

### Multivariate Cryptography
**Based on** difficulty of solving systems of multivariate polynomial equations.

#### Mathematical Problem
Solve system:
```
f₁(x₁, ..., xₙ) = y₁
f₂(x₁, ..., xₙ) = y₂
...
fₘ(x₁, ..., xₙ) = yₘ
```
over finite field 𝔽q.

#### Examples
- **HFE (Hidden Field Equations)**: Uses field extension
- **Rainbow**: Layered construction
- **UOV (Unbalanced Oil and Vinegar)**: Variable separation technique

### Code-Based Cryptography

#### McEliece Cryptosystem
**Based on** error-correcting codes and syndrome decoding problem.

**Construction**:
- **Generator matrix**: G for linear code C
- **Scrambling**: S (invertible), P (permutation)
- **Public key**: G' = SGP
- **Private key**: (S, G, P) and decoding algorithm

**Security**: Syndrome decoding is NP-complete for random linear codes.

**Challenges**:
- **Large key sizes**: Public keys can be very large
- **Code selection**: Finding suitable error-correcting codes
- **Constant ciphertext expansion**: 2× message size

### Supersingular Isogeny Cryptography

#### SIDH (Supersingular Isogeny Diffie-Hellman)
**Based on** walks in supersingular isogeny graphs.

**Mathematical Objects**:
- **Supersingular elliptic curves**: Special class of curves
- **Isogenies**: Morphisms between curves
- **Key exchange**: Parallel walks in isogeny graph

**Status**: Recently broken (2022) but sparked research in isogeny cryptography.

### Hash-Based Signatures

#### Merkle Signatures
**One-time signatures** built into tree structure for multiple uses.

**Construction**:
1. **Generate** many one-time signature keypairs
2. **Build Merkle tree** with public keys as leaves
3. **Root**: Single public key for entire scheme
4. **Signing**: Use one OTS keypair + authentication path

#### Advantages
- **Minimal assumptions**: Only requires secure hash functions
- **Quantum resistance**: Hash functions believed quantum-resistant
- **Provable security**: Security reduces to hash function properties

#### Modern Variants
- **XMSS**: Extended Merkle Signature Scheme
- **SPHINCS+**: Stateless hash-based signatures
- **LMS**: Leighton-Micali Signatures

#### Trade-offs
- **Large signatures**: Include authentication paths
- **Signing complexity**: More computation than traditional schemes
- **State management**: Some schemes require state tracking

## Post-Quantum Transition Challenges

### Migration Considerations
- **Hybrid approaches**: Combine classical and post-quantum
- **Key size increases**: Larger storage and bandwidth requirements
- **Performance impact**: Generally slower operations
- **Standardization**: NIST post-quantum cryptography standards

### Implementation Security
- **Side-channel attacks**: New vulnerabilities in PQC algorithms
- **Constant-time implementations**: Critical for practical security
- **Parameter selection**: Balancing security, performance, and sizes

---

# Cryptographic Protocols

## Key Management

### Key Generation
**Secure key generation** is fundamental to cryptographic security.

#### Requirements
- **Entropy sources**: Hardware random number generators, OS entropy pools
- **Seeding**: Proper initialization of pseudorandom generators
- **Key quality**: Statistical randomness tests
- **Domain parameters**: Proper selection of cryptographic parameters

#### Key Generation Methods
- **True random generation**: Hardware entropy sources
- **Cryptographically secure PRNGs**: HMAC-DRBG, CTR-DRBG
- **Deterministic generation**: From passwords using KDFs
- **Distributed generation**: Multi-party key generation

### Key Distribution
**Secure delivery** of cryptographic keys to authorized parties.

#### Key Distribution Problem
- **Scalability**: n² key pairs needed for n parties
- **Initial key exchange**: Bootstrap problem
- **Secure channels**: Authenticated and confidential delivery

#### Distribution Methods
- **Pre-shared keys**: Manual distribution
- **Key distribution centers**: Trusted third party
- **Public key cryptography**: Eliminates pre-sharing requirement
- **Key escrow**: Recovery mechanisms for lost keys

### Key Exchange Protocols

#### Diffie-Hellman Variants
**Enhanced versions** addressing various security requirements.

##### Ephemeral Diffie-Hellman (DHE)
- **Forward secrecy**: New keys for each session
- **Session keys**: Deleted after use
- **Long-term authentication**: Separate from key exchange

##### Station-to-Station (STS) Protocol
1. **A → B**: g^a
2. **B → A**: g^b, Sign_B(g^b, g^a)
3. **A → B**: Sign_A(g^a, g^b)

**Features**: Mutual authentication, key confirmation

### Key Agreement Protocols

#### Multi-Party Key Agreement
**Protocols** for establishing shared keys among multiple parties.

##### Burmester-Desmedt Protocol
**Efficient** key agreement for groups.
1. **Round 1**: Each party broadcasts g^xi
2. **Round 2**: Each party computes and broadcasts intermediate values
3. **Key computation**: All parties derive same group key

#### Authenticated Key Agreement
- **Mutual authentication**: Both parties verify identities
- **Key confirmation**: Proof of shared key possession
- **Forward secrecy**: Past sessions remain secure
- **Known key security**: Compromise of one key doesn't affect others

### Key Storage
**Secure storage** of cryptographic keys.

#### Storage Requirements
- **Confidentiality**: Encryption of stored keys
- **Integrity**: Detection of unauthorized modifications
- **Availability**: Reliable access when needed
- **Access control**: Authorization mechanisms

#### Storage Methods
- **Hardware Security Modules (HSMs)**: Tamper-resistant hardware
- **Trusted Platform Modules (TPMs)**: Chip-level security
- **Software keystores**: OS-protected storage
- **Key wrapping**: Encryption of keys with master keys

### Public Key Infrastructure (PKI)

#### PKI Components
- **Certificate Authority (CA)**: Issues and manages certificates
- **Registration Authority (RA)**: Verifies identity before certificate issuance
- **Certificate Repository**: Stores and distributes certificates
- **Certificate Revocation List (CRL)**: Lists revoked certificates

#### X.509 Certificates
**Standard format** for public key certificates.

**Certificate Structure**:
```
Certificate:
  Version
  Serial Number
  Signature Algorithm
  Issuer
  Validity Period
  Subject
  Subject Public Key Info
  Extensions
```

**Key Extensions**:
- **Key Usage**: Defines permitted key operations
- **Extended Key Usage**: Application-specific usage
- **Subject Alternative Name**: Additional identities
- **Authority Key Identifier**: Links to issuing CA

#### Certificate Chain Validation
1. **Path building**: Construct chain to trusted root
2. **Signature verification**: Verify each certificate signature
3. **Validity checking**: Ensure certificates not expired
4. **Revocation checking**: Check CRL or OCSP status
5. **Policy validation**: Verify certificate policies

### Web of Trust
**Decentralized** trust model alternative to PKI.

#### PGP Web of Trust
- **Self-signed certificates**: Users create own certificates
- **Cross-certification**: Users sign each other's certificates
- **Trust levels**: Levels of confidence in signatures
- **Trust propagation**: Transitive trust relationships

**Advantages**:
- **No central authority**: Distributed trust model
- **User control**: Direct trust decisions
- **Resilience**: No single point of failure

**Challenges**:
- **Scalability**: Trust relationships grow complex
- **Usability**: Difficult for average users
- **Trust evaluation**: Complex trust calculations

## Authentication Protocols

### Challenge-Response Protocols
**Interactive authentication** using cryptographic challenges.

#### Basic Challenge-Response
1. **Verifier**: Sends random challenge C
2. **Prover**: Computes response R = F(C, secret)
3. **Verifier**: Checks if R is correct response to C

#### Examples
- **Password-based**: R = Hash(C || password)
- **Public key**: R = Sign_private(C)
- **Symmetric key**: R = MAC_key(C)

### Zero-Knowledge Proofs
**Protocols** proving knowledge without revealing information.

#### Properties
- **Completeness**: Honest prover convinces honest verifier
- **Soundness**: Cheating prover cannot convince verifier
- **Zero-knowledge**: Verifier learns nothing beyond validity

#### Schnorr Identification Protocol
**Zero-knowledge proof** of discrete logarithm knowledge.

**Setup**: Public key y = g^x, secret key x

1. **Commitment**: Prover sends a = g^r (random r)
2. **Challenge**: Verifier sends random challenge e
3. **Response**: Prover sends z = r + ex
4. **Verification**: Check if g^z = a · y^e

### Multi-Factor Authentication (MFA)
**Multiple authentication factors** for enhanced security.

#### Authentication Factors
- **Something you know**: Password, PIN
- **Something you have**: Token, smart card, phone
- **Something you are**: Biometric identifiers
- **Somewhere you are**: Location-based authentication

#### Implementation Methods
- **SMS codes**: Text message delivery
- **TOTP**: Time-based one-time passwords
- **Push notifications**: App-based authentication
- **Hardware tokens**: Dedicated authentication devices

### Kerberos
**Network authentication protocol** using symmetric cryptography.

#### Components
- **Key Distribution Center (KDC)**: Authentication server + Ticket-granting server
- **Authentication Server (AS)**: Verifies user credentials
- **Ticket-Granting Server (TGS)**: Issues service tickets
- **Service Server (SS)**: Target service requiring authentication

#### Protocol Flow
1. **AS_REQ**: Client requests authentication
2. **AS_REP**: AS returns TGT encrypted with user's key
3. **TGS_REQ**: Client requests service ticket using TGT
4. **TGS_REP**: TGS returns service ticket
5. **AP_REQ**: Client presents service ticket to server
6. **AP_REP**: Server optionally authenticates to client

### OAuth 2.0
**Authorization framework** for secure API access delegation.

#### Roles
- **Resource Owner**: Entity controlling protected resource
- **Resource Server**: Server hosting protected resources
- **Client**: Application requesting resource access
- **Authorization Server**: Issues access tokens

#### Grant Types
- **Authorization Code**: Server-side applications
- **Implicit**: Client-side applications (deprecated)
- **Resource Owner Password**: Direct credential exchange
- **Client Credentials**: Service-to-service authentication

## Secure Communication Protocols

### Transport Layer Security (TLS)
**Cryptographic protocol** providing secure communication over networks.

#### TLS Handshake Process
1. **ClientHello**: Supported cipher suites, random value
2. **ServerHello**: Selected cipher suite, server random
3. **Certificate**: Server's certificate chain
4. **ServerKeyExchange**: Additional key exchange parameters
5. **ClientKeyExchange**: Client key exchange contribution
6. **Finished**: Handshake completion verification

#### TLS 1.3 Improvements
- **Reduced handshake**: Fewer round trips
- **Forward secrecy**: Mandatory ephemeral key exchange
- **Simplified cipher suites**: AEAD-only encryption
- **Zero-RTT**: Optional resumed session optimization

#### Security Features
- **Authentication**: Server (and optionally client) identity verification
- **Confidentiality**: Symmetric encryption of application data
- **Integrity**: MAC protection against tampering
- **Replay protection**: Sequence numbers prevent replay attacks

### Internet Protocol Security (IPsec)
**Security framework** for IP layer protection.

#### Components
- **Authentication Header (AH)**: Provides authentication and integrity
- **Encapsulating Security Payload (ESP)**: Provides confidentiality, authentication, integrity
- **Internet Key Exchange (IKE)**: Key management protocol

#### Modes
- **Transport mode**: Protects payload only
- **Tunnel mode**: Protects entire IP packet

#### Security Associations (SA)
- **Unidirectional**: Separate SAs for each direction
- **Parameters**: Algorithms, keys, sequence numbers
- **Database**: Security Policy Database (SPD), Security Association Database (SAD)

### Pretty Good Privacy (PGP/GPG)
**Email encryption** and digital signature system.

#### Operations
- **Encryption**: Hybrid cryptosystem using RSA + symmetric cipher
- **Digital signatures**: RSA or DSA signatures with hash
- **Compression**: Optional data compression before encryption
- **ASCII armor**: Base64 encoding for email transmission

#### Trust Model
- **Web of trust**: Decentralized certificate validation
- **Key signing**: Users validate and sign each other's keys
- **Trust levels**: Levels of confidence in key ownership

---

# Advanced Cryptographic Concepts

## Zero-Knowledge Proofs

### Interactive Proof Systems
**Mathematical framework** for zero-knowledge protocols.

#### Complexity Classes
- **IP**: Interactive Polynomial-time
- **NP**: Non-deterministic Polynomial-time
- **PSPACE**: Polynomial Space
- **Relationship**: NP ⊆ IP = PSPACE

#### Perfect vs Statistical vs Computational ZK
- **Perfect ZK**: Information-theoretic indistinguishability
- **Statistical ZK**: Negligible statistical difference
- **Computational ZK**: Computationally indistinguishable

### Non-Interactive Zero-Knowledge (NIZK)
**Zero-knowledge proofs** without interaction rounds.

#### Common Reference String (CRS)
- **Trusted setup**: Generation of public parameters
- **Structured CRS**: Specific mathematical structure
- **Random oracle model**: Idealized hash function assumption

#### Fiat-Shamir Transform
**Converts** interactive proofs to non-interactive.
- **Replace verifier**: Hash function provides challenges
- **Security**: Requires random oracle model
- **Efficiency**: Eliminates interaction rounds

### zk-SNARKs
**Zero-Knowledge Succinct Non-Interactive Arguments of Knowledge**

#### Properties
- **Succinct**: Proof size independent of statement size
- **Non-interactive**: Single proof message
- **Sound**: Computationally sound argument
- **Zero-knowledge**: Reveals no information about witness

#### Construction Components
- **Quadratic Arithmetic Programs (QAPs)**: Circuit representation
- **Elliptic curve pairings**: Bilinear map operations
- **Trusted setup**: Generates proving and verification keys
- **Polynomial commitments**: Commit to polynomial evaluations

#### Applications
- **Zcash**: Privacy-preserving cryptocurrency
- **Blockchain scaling**: Layer 2 rollup solutions
- **Private computation**: Verifiable computation without revealing inputs

### zk-STARKs
**Zero-Knowledge Scalable Transparent Arguments of Knowledge**

#### Advantages over SNARKs
- **Transparent setup**: No trusted parameter generation
- **Post-quantum security**: Relies only on hash functions
- **Scalability**: Proof generation scales better
- **Quantum resistance**: No elliptic curve assumptions

#### Technical Foundation
- **Fast Reed-Solomon Interactive Oracle Proofs (FRI)**: Polynomial commitment scheme
- **Air traces**: Algebraic intermediate representation
- **Merkle trees**: Commitment to trace polynomials

### Bulletproofs
**Range proofs** and arithmetic circuit proofs without trusted setup.

#### Features
- **Logarithmic size**: O(log n) proof size
- **No trusted setup**: Uses only standard group assumptions
- **Batch verification**: Multiple proofs verified together efficiently
- **Aggregation**: Multiple range proofs combined

#### Applications
- **Confidential transactions**: Hide transaction amounts
- **Private smart contracts**: Zero-knowledge contract execution
- **Audit systems**: Prove compliance without revealing data

## Secure Multi-Party Computation (MPC)

### Secret Sharing

#### Shamir's Secret Sharing
**Threshold scheme** using polynomial interpolation.

**Sharing Process**:
1. **Choose polynomial**: P(x) = s + a₁x + ... + aₜ₋₁x^(t-1)
2. **Evaluate points**: Share i is (i, P(i))
3. **Distribution**: Give each party one share

**Reconstruction**:
- **Lagrange interpolation**: Recover P(0) = s from t shares
- **Threshold property**: Any t shares can reconstruct secret
- **Privacy**: Fewer than t shares reveal no information

#### Verifiable Secret Sharing
**Enhancement** with share verification capability.
- **Commitment verification**: Shares verified against commitments
- **Cheating detection**: Invalid shares detected
- **Robust reconstruction**: Works despite some invalid shares

### Yao's Garbled Circuits
**Two-party computation** protocol for arbitrary functions.

#### Construction
1. **Circuit garbling**: Replace truth table with encrypted values
2. **Label assignment**: Random labels for wire values
3. **Oblivious transfer**: Receiver gets input labels
4. **Circuit evaluation**: Decrypt gates using obtained labels

#### Security Properties
- **Privacy**: Neither party learns other's input
- **Correctness**: Both parties learn correct output
- **Semi-honest security**: Assumes parties follow protocol

### Homomorphic Encryption

#### Partially Homomorphic Encryption
**Encryptions** supporting one operation type.

**Examples**:
- **RSA**: Multiplicatively homomorphic
  ```
  E(m₁) · E(m₂) = E(m₁ · m₂)
  ```
- **ElGamal**: Multiplicatively homomorphic
- **Paillier**: Additively homomorphic
  ```
  E(m₁) · E(m₂) = E(m₁ + m₂)
  ```

#### Fully Homomorphic Encryption (FHE)
**Holy grail** supporting arbitrary computations on encrypted data.

**Gentry's Construction**:
1. **Somewhat homomorphic**: Limited depth circuits
2. **Bootstrapping**: Refresh ciphertext to reduce noise
3. **Fully homomorphic**: Unlimited depth via bootstrapping

**Modern FHE Schemes**:
- **BFV/BGV**: Integer-based schemes
- **CKKS**: Approximate arithmetic for real numbers
- **TFHE**: Fast bootstrapping for boolean circuits

#### Applications
- **Cloud computing**: Compute on encrypted data
- **Privacy-preserving analytics**: Statistical analysis without data exposure
- **Secure outsourcing**: Delegate computation while maintaining privacy

## Privacy-Enhancing Technologies

### Ring Signatures
**Anonymous signatures** hiding signer identity within group.

#### Construction
- **Ring formation**: Ad-hoc group of possible signers
- **Signature creation**: Proves one member signed without revealing which
- **Verification**: Confirms signature from someone in ring

#### Properties
- **Unconditional anonymity**: Computationally impossible to identify signer
- **Unforgeability**: Cannot create signatures without private key
- **No group manager**: No trusted authority needed

### Group Signatures
**Anonymous signatures** with designated group manager.

#### Components
- **Group manager**: Manages group membership and revocation
- **Group members**: Can create anonymous signatures
- **Verification**: Anyone can verify group signatures

#### Features
- **Anonymity**: Signatures unlinkable to specific members
- **Traceability**: Group manager can identify signers
- **Revocation**: Members can be excluded from group

### Blind Signatures
**Signatures on blinded messages** preserving message privacy.

#### Chaum's Blind Signature
1. **Blinding**: Client blinds message m → m'
2. **Signing**: Server signs blinded message → s'
3. **Unblinding**: Client unblinds signature → s
4. **Verification**: Signature s valid on original message m

#### Applications
- **Anonymous credentials**: Blind issuance of certificates
- **Digital cash**: Untraceable electronic payments
- **Anonymous voting**: Blind signature on vote choices

### Mix Networks
**Communication systems** providing sender anonymity.

#### Chaum Mix
**Single mix** providing unlinkability.
1. **Batching**: Collect multiple encrypted messages
2. **Decryption**: Remove one encryption layer
3. **Shuffling**: Reorder messages randomly
4. **Forwarding**: Send messages to next hop

#### Mixnet Variants
- **Cascade mixnets**: Sequential chain of mixes
- **Pool mixnets**: Messages delayed randomly
- **Stop-and-go mixnets**: Variable delay distribution

### Differential Privacy
**Statistical privacy** for database queries.

#### Definition
Algorithm M satisfies (ε, δ)-differential privacy if:
```
Pr[M(D₁) ∈ S] ≤ e^ε · Pr[M(D₂) ∈ S] + δ
```
for adjacent databases D₁, D₂ differing by one record.

#### Mechanisms
- **Laplace mechanism**: Add Laplace noise to numeric queries
- **Exponential mechanism**: Select from discrete outputs
- **Gaussian mechanism**: Add Gaussian noise (for approximate DP)

#### Applications
- **Census data**: Government statistical releases
- **Location privacy**: Geostatistical services
- **Machine learning**: Privacy-preserving model training

### Anonymous Credentials
**Privacy-preserving authentication** systems.

#### Features
- **Selective disclosure**: Reveal only necessary attributes
- **Unlinkability**: Multiple uses cannot be linked
- **Unforgeability**: Cannot create fake credentials

#### Implementations
- **Idemix**: IBM's anonymous credential system
- **U-Prove**: Microsoft's credential technology
- **BBS+ signatures**: Pairing-based anonymous credentials

### Private Information Retrieval (PIR)
**Database queries** without revealing query pattern.

#### Single-Server PIR
- **Computational PIR**: Based on cryptographic assumptions
- **Homomorphic encryption**: Query encrypted database
- **Oblivious RAM**: Hide access patterns

#### Multi-Server PIR
- **Information-theoretic security**: Perfect privacy guarantee
- **Secret sharing**: Distribute database across servers
- **Query splitting**: Queries reveal nothing individually

#### Applications
- **Patent databases**: Private patent searches
- **Medical records**: Confidential medical queries
- **Location services**: Anonymous location queries

---

# Cryptanalysis

## Attack Types

### Classical Attack Models

#### Ciphertext-only Attacks
**Passive attacks** where adversary has access only to intercepted ciphertext.

**Attack Scenarios**:
- **Statistical analysis**: Frequency analysis on substitution ciphers
- **Pattern recognition**: Identifying repetitive structures
- **Brute force**: Exhaustive key search when key space is small
- **Known algorithm**: Exploit weaknesses in cipher design

**Historical Examples**:
- **Breaking Enigma**: Using statistical patterns and cribs
- **DES brute force**: Exhaustive search of 56-bit key space
- **Stream cipher attacks**: Keystream reuse vulnerabilities

#### Known-plaintext Attacks
**Adversary knows** some plaintext-ciphertext pairs.

**Attack Strategies**:
- **Key recovery**: Derive encryption key from known pairs
- **Differential analysis**: Compare plaintext/ciphertext differences
- **Linear relationships**: Find linear approximations in cipher
- **Algebraic methods**: Set up equation systems to solve for key

**Examples**:
- **Linear cryptanalysis**: Statistical bias in XOR relationships
- **Differential cryptanalysis**: Probability of difference propagation
- **Correlation attacks**: Statistical correlation in stream ciphers

#### Chosen-plaintext Attacks (CPA)
**Adversary can choose** plaintexts and observe corresponding ciphertexts.

**Capabilities**:
- **Oracle access**: Query encryption oracle with chosen inputs
- **Adaptive queries**: Select subsequent plaintexts based on previous results
- **Pattern analysis**: Identify cipher structure through controlled inputs

**Attack Applications**:
- **Block cipher analysis**: Chosen plaintexts reveal cipher properties
- **Public key attacks**: RSA with poor padding schemes
- **Hash function collision**: Birthday attack with chosen messages

#### Chosen-ciphertext Attacks (CCA)
**Adversary can choose** ciphertexts and observe decryption results.

**Attack Variants**:
- **CCA1 (Lunchtime attack)**: Decryption queries before seeing challenge
- **CCA2 (Adaptive attack)**: Decryption queries even after challenge
- **Padding oracle**: Exploit padding validation information

**Notable Attacks**:
- **PKCS#1 v1.5**: Padding oracle against RSA
- **Bleichenbacher attack**: Adaptive chosen-ciphertext against RSA
- **CBC padding oracle**: Decrypt without key using padding information

### Side-Channel Attacks
**Exploit physical implementation** characteristics rather than mathematical weaknesses.

#### Timing Attacks
**Analyze execution time** to extract secret information.

**Attack Mechanisms**:
- **Variable execution time**: Operations depend on secret data
- **Cache timing**: Memory access patterns reveal information
- **Network timing**: Response time analysis in protocols

**Mitigation Strategies**:
- **Constant-time algorithms**: Fixed execution time regardless of input
- **Blinding techniques**: Randomize intermediate calculations
- **Timing noise**: Add random delays to obscure patterns

#### Power Analysis Attacks
**Monitor power consumption** during cryptographic operations.

##### Simple Power Analysis (SPA)
- **Visual inspection**: Identify operations from power traces
- **Pattern recognition**: Distinguish different operations
- **Single trace**: Extract information from one execution

##### Differential Power Analysis (DPA)
- **Statistical analysis**: Correlate power consumption with intermediate values
- **Multiple traces**: Average over many executions
- **Hypothesis testing**: Test key guesses against power measurements

**Countermeasures**:
- **Masking**: Randomize intermediate values
- **Power balancing**: Constant power consumption
- **Noise injection**: Add random power fluctuations

#### Fault Attacks
**Induce computational errors** to extract secrets.

**Fault Injection Methods**:
- **Voltage glitching**: Temporary power supply manipulation
- **Clock glitching**: Timing disruption
- **Laser attacks**: Precise bit flipping
- **Electromagnetic pulses**: EMI-induced faults

**Attack Examples**:
- **RSA-CRT fault attack**: Induce errors in Chinese Remainder Theorem
- **AES fault attack**: Differential fault analysis on round operations
- **ECC fault attacks**: Invalid curve attacks using faulty computations

### Mathematical Cryptanalysis

#### Differential Cryptanalysis
**Analyze propagation** of differences through cipher rounds.

**Methodology**:
1. **Choose input difference**: Specific XOR difference in plaintexts
2. **Trace propagation**: Follow difference through cipher rounds
3. **Identify characteristics**: High-probability difference paths
4. **Key recovery**: Use output differences to determine round keys

**Applications**:
- **DES analysis**: Biham-Shamir differential attack
- **AES variants**: Reduced-round differential attacks
- **Hash functions**: Collision attacks using differentials

#### Linear Cryptanalysis
**Find linear approximations** in cipher operations.

**Linear Approximation**:
```
P[i₁] ⊕ P[i₂] ⊕ ... ⊕ C[j₁] ⊕ C[j₂] ⊕ ... ⊕ K[k₁] ⊕ K[k₂] ⊕ ... = 0
```
with probability ≠ 1/2

**Attack Process**:
1. **Find linear hull**: Combine linear approximations across rounds
2. **Collect data**: Many plaintext-ciphertext pairs
3. **Statistical test**: Bias indicates key bit values
4. **Key recovery**: Determine key bits from biased equations

#### Integral Cryptanalysis
**Higher-order differential** attack on block ciphers.

**Integral Property**:
- **Multiset analysis**: Study how sets of inputs transform
- **Balance property**: XOR of outputs equals zero
- **Square attack**: Special case for Square cipher

**Process**:
1. **Choose integral**: Set of plaintexts with specific pattern
2. **Partial encryption**: Encrypt through partial rounds
3. **Distinguish**: Detect non-random behavior
4. **Key recovery**: Extract key information from distinguisher

### Network-Based Attacks

#### Man-in-the-Middle Attacks
**Interception and manipulation** of communications.

**Attack Scenarios**:
- **Key exchange**: Intercept and replace public keys
- **Certificate substitution**: Replace legitimate certificates
- **Protocol downgrade**: Force use of weaker algorithms
- **Session hijacking**: Take over established connections

**Countermeasures**:
- **Certificate pinning**: Validate expected certificates
- **Perfect forward secrecy**: Limit impact of key compromise
- **Mutual authentication**: Both parties authenticate
- **Secure channels**: Use authenticated key exchange

#### Replay Attacks
**Retransmit valid messages** to achieve unauthorized actions.

**Attack Types**:
- **Authentication replay**: Reuse authentication credentials
- **Transaction replay**: Duplicate financial transactions
- **Timestamp exploitation**: Old messages replayed later

**Defenses**:
- **Nonces**: One-time random values
- **Timestamps**: Time-based message validity
- **Sequence numbers**: Ordered message numbering
- **Challenge-response**: Dynamic authentication

## Cryptanalysis Techniques

### Brute Force Attacks
**Exhaustive search** of entire key space.

#### Complexity Analysis
- **Time complexity**: O(2^(k-1)) average, O(2^k) worst case
- **Space complexity**: O(1) for key search
- **Parallelization**: Easily distributed across multiple processors

#### Optimization Techniques
- **Meet-in-the-middle**: Reduce search space through time-memory tradeoff
- **Rainbow tables**: Pre-computed hash chains
- **GPU acceleration**: Parallel processing for hash computations
- **FPGA/ASIC**: Specialized hardware for specific algorithms

### Dictionary Attacks
**Use lists of likely passwords** instead of exhaustive search.

#### Dictionary Sources
- **Common passwords**: Most frequently used passwords
- **Leaked databases**: Previously compromised password lists
- **Language dictionaries**: Words from various languages
- **Pattern-based**: Common substitution patterns (a→@, o→0)

#### Hybrid Attacks
- **Dictionary + rules**: Apply transformation rules to dictionary words
- **Markov chains**: Generate passwords based on statistical models
- **Neural networks**: ML-generated password candidates

### Rainbow Tables
**Time-memory tradeoff** for password cracking.

#### Construction
1. **Reduction function**: Map hash output to potential input
2. **Chain generation**: H(P₀) → R → P₁ → H → R → P₂ → ...
3. **Table storage**: Store only endpoints (start, end) of chains
4. **Chain length**: Balance time vs. space requirements

#### Usage
1. **Hash target**: Compute hash of target password
2. **Reduction chain**: Apply reduction functions to find chain
3. **Chain lookup**: Search for ending point in table
4. **Chain regeneration**: Recreate chain to find password

**Countermeasures**:
- **Salt**: Unique random value per password
- **Iterated hashing**: Multiple hash iterations (PBKDF2, scrypt)
- **Memory-hard functions**: Argon2, bcrypt

### Advanced Attack Techniques

#### Boomerang Attacks
**Combine two short differential characteristics** to attack more rounds.

**Structure**:
1. **Upper characteristic**: Rounds 1 to r₁
2. **Middle rounds**: Rounds r₁+1 to r₂  
3. **Lower characteristic**: Rounds r₂+1 to total rounds

**Amplified Boomerang**:
- **Multiple middle differences**: Increase success probability
- **Adaptive queries**: Adjust based on intermediate results

#### Impossible Differential Attacks
**Exploit characteristics** with zero probability.

**Methodology**:
1. **Find impossible differential**: Input/output difference with probability 0
2. **Partial encryption/decryption**: Work from both ends
3. **Wrong key elimination**: Discard keys producing impossible differential
4. **Key recovery**: Remaining keys after elimination

#### Slide Attacks
**Exploit self-similarity** in cipher structure.

**Requirements**:
- **Periodic key schedule**: Repeating pattern in round keys
- **Similar round functions**: Identical or related round operations

**Attack Process**:
1. **Identify slid pairs**: Plaintexts related by key periodicity
2. **Slide relation**: P₂ = f_k(P₁), C₂ = f_k(C₁)
3. **Key recovery**: Extract key information from slide relations

---

# Applied Cryptography

## Blockchain & Cryptocurrencies

### Merkle Trees
**Binary tree structure** providing efficient and secure verification of large data structures.

#### Construction
```
For leaves: H(data)
For internal nodes: H(left_child || right_child)
Root: Single hash representing entire tree
```

#### Properties
- **Integrity verification**: Any change detectable via root hash
- **Efficient proofs**: O(log n) proof size for membership
- **Incremental updates**: Add new leaves without rebuilding entire tree
- **Parallelizable**: Tree construction can be parallelized

#### Applications in Blockchain
- **Block structure**: Transactions organized in Merkle tree
- **SPV clients**: Lightweight verification without full blockchain
- **State commitments**: Commit to entire blockchain state
- **Cross-chain verification**: Prove transaction inclusion across chains

### Patricia Merkle Trees
**Radix tree** combining Merkle tree security with compressed trie efficiency.

#### Structure
- **Radix trie**: Compressed prefix tree for key-value storage
- **Merkle hashing**: Each node contains hash of subtree
- **Path compression**: Nodes with single child compressed
- **Branch optimization**: Efficient representation of sparse trees

#### Ethereum Usage
- **State trie**: Account balances, nonces, contract storage
- **Storage trie**: Contract storage variables
- **Transaction trie**: Transactions in block
- **Receipt trie**: Transaction execution receipts

### Consensus Algorithm Cryptography

#### Verifiable Random Functions (VRF)
**Cryptographic primitive** providing publicly verifiable randomness.

**Properties**:
- **Pseudorandomness**: Output indistinguishable from random
- **Uniqueness**: Each input produces unique output
- **Verifiability**: Anyone can verify output correctness
- **Unpredictability**: Output unpredictable before computation

**Construction** (RSA-based):
```
VRF_prove(SK, x) = x^SK mod N, π (proof)
VRF_verify(PK, x, y, π) = verify y = x^SK using proof π
```

**Blockchain Applications**:
- **Leader election**: Randomly select block proposers
- **Committee selection**: Choose validation committees
- **Randomness beacons**: Provide public randomness source

#### Verifiable Delay Functions (VDF)
**Functions requiring** sequential computation but fast verification.

**Properties**:
- **Sequential computation**: Cannot be parallelized effectively
- **Fast verification**: Result verified much faster than computation
- **Deterministic**: Same input always produces same output
- **Public verifiability**: Anyone can verify correctness

**Applications**:
- **Timestamping**: Prove passage of time
- **Randomness extraction**: Generate unbiased randomness
- **Leader election**: Prevent grinding attacks
- **Proof of elapsed time**: Consensus mechanism component

### Privacy-Preserving Transactions

#### Ring Confidential Transactions (RingCT)
**Monero's privacy protocol** hiding sender, receiver, and amount.

**Components**:
1. **Ring signatures**: Hide transaction sender among group
2. **Stealth addresses**: Hide transaction receiver
3. **Confidential transactions**: Hide transaction amounts
4. **Range proofs**: Prove amounts are positive without revealing values

**RingCT Construction**:
- **Pedersen commitments**: Commit to transaction amounts
- **Ring signatures**: Prove spending authority without revealing key
- **Bulletproofs**: Efficient range proofs for hidden amounts

#### Atomic Swaps
**Cross-chain transactions** without trusted intermediaries.

**Hash Time-Locked Contracts (HTLC)**:
```
If (hashlock verified AND timelock not expired):
    Allow spending with preimage
Else if (timelock expired):
    Allow refund to original owner
```

**Swap Protocol**:
1. **Alice locks**: Coins in HTLC on Chain A
2. **Bob locks**: Coins in HTLC on Chain B (same hash)
3. **Alice claims**: Bob's coins by revealing preimage
4. **Bob claims**: Alice's coins using revealed preimage

### Layer 2 Scaling Solutions

#### zk-Rollups
**Layer 2 scaling** using zero-knowledge proofs for validation.

**Architecture**:
- **Off-chain execution**: Transactions processed off main chain
- **State commitment**: Merkle root of account states
- **Validity proofs**: zk-SNARK proves correct state transition
- **Data availability**: Transaction data posted on-chain

**Benefits**:
- **High throughput**: Thousands of transactions per second
- **Security**: Inherits base layer security
- **Fast finality**: Immediate finality after proof verification
- **Capital efficiency**: No dispute resolution delays

#### Optimistic Rollups
**Layer 2 scaling** assuming transactions valid unless challenged.

**Mechanism**:
- **Optimistic execution**: Assume state transitions correct
- **Challenge period**: Time window for disputing invalid transitions
- **Fraud proofs**: Cryptographic proof of invalid state transition
- **Slashing**: Penalize operators submitting invalid states

**Trade-offs**:
- **Withdrawal delays**: Must wait for challenge period
- **Lower security assumptions**: Requires honest challengers
- **Higher throughput**: No proof generation overhead

## Secure Storage

### Disk Encryption
**Full-disk encryption** protecting data at rest.

#### Block-Level Encryption
- **Transparent operation**: Applications unaware of encryption
- **Sector-based**: Each disk sector encrypted independently
- **Key management**: Master key protects sector encryption keys
- **Boot security**: Pre-boot authentication required

#### Common Standards
- **AES-XTS**: NIST-approved mode for storage encryption
- **BitLocker**: Microsoft's full-disk encryption
- **FileVault**: macOS disk encryption
- **LUKS**: Linux Unified Key Setup

### Format-Preserving Encryption (FPE)
**Encryption maintaining** original data format and length.

#### Requirements
- **Format preservation**: Ciphertext matches plaintext format
- **Length preservation**: No expansion of encrypted data
- **Security**: Standard encryption security properties
- **Deterministic**: Same plaintext produces same ciphertext

#### FF1/FF3 Algorithms
**NIST-standardized** FPE modes using Feistel networks.

**Applications**:
- **Database encryption**: Encrypt sensitive fields in-place
- **Legacy systems**: Encrypt without changing data formats
- **Compliance**: Meet regulatory requirements without system changes
- **Credit card numbers**: Encrypt while maintaining format

### Searchable Encryption
**Enable search** on encrypted data without decryption.

#### Symmetric Searchable Encryption (SSE)
- **Keyword search**: Search for specific keywords in encrypted documents
- **Index encryption**: Encrypted search index construction
- **Query privacy**: Search queries themselves encrypted
- **Result privacy**: Search results don't reveal other document content

#### Property-Preserving Encryption
- **Order-preserving**: Maintains ordering relationships
- **Equality-preserving**: Enables equality queries
- **Range queries**: Support for range-based searches
- **Frequency analysis**: Vulnerable to statistical attacks

## Hardware Cryptography

### Hardware Security Modules (HSM)
**Tamper-resistant hardware** for cryptographic operations.

#### Security Features
- **Secure key storage**: Keys never exist in plaintext outside HSM
- **Tamper evidence**: Physical intrusion detection
- **Tamper response**: Key deletion on unauthorized access
- **Performance**: Hardware-accelerated cryptographic operations

#### HSM Types
- **Network-attached**: Shared across multiple systems
- **PCIe cards**: Direct integration into servers
- **USB tokens**: Portable security devices
- **Cloud HSMs**: HSM-as-a-Service offerings

### Trusted Platform Module (TPM)
**Hardware security chip** providing trusted computing base.

#### TPM Capabilities
- **Root of trust**: Hardware-based trust anchor
- **Key generation**: Cryptographically secure key creation
- **Platform attestation**: Verify system integrity
- **Sealed storage**: Encrypt data bound to platform state

#### TPM Operations
- **PCR extension**: Measure and record system state
- **Quote operation**: Sign PCR values for remote attestation
- **Seal/Unseal**: Encrypt/decrypt based on platform state
- **Key certification**: Prove keys generated in TPM

### Physical Unclonable Functions (PUF)
**Hardware primitives** exploiting manufacturing variations.

#### PUF Properties
- **Uniqueness**: Each device produces unique responses
- **Unclonability**: Practically impossible to duplicate
- **Unpredictability**: Responses cannot be predicted
- **Reliability**: Consistent responses under normal conditions

#### PUF Applications
- **Device authentication**: Unique device fingerprinting
- **Key generation**: Derive keys from physical properties
- **Anti-counterfeiting**: Verify hardware authenticity
- **Secure boot**: Hardware-based boot verification

### White-box Cryptography
**Software implementation** resistant to white-box attacks.

#### Threat Model
- **Full access**: Attacker has complete control over execution environment
- **Key extraction**: Goal to extract cryptographic keys
- **Code analysis**: Static and dynamic analysis capabilities
- **Instrumentation**: Ability to modify and monitor execution

#### Protection Techniques
- **Key hiding**: Embed keys in complex computations
- **Control flow obfuscation**: Hide program logic
- **Data obfuscation**: Obscure intermediate values
- **Tamper resistance**: Detect and respond to modifications

#### Applications
- **DRM systems**: Content protection in untrusted environments
- **Mobile applications**: Protect keys in client software
- **Payment systems**: Secure payment processing
- **Licensing**: Software licensing and activation systems

#### Limitations
- **Theoretical impossibility**: Provably secure white-box crypto impossible
- **Practical attacks**: Many schemes broken by cryptanalysis
- **Performance overhead**: Significant computational cost
- **Code size**: Large increase in program size

---

# Cryptographic Standards & Implementation

## Standardization Bodies

### NIST Standards
**National Institute of Standards and Technology** develops US federal cryptographic standards.

#### Key Publications
- **Advanced Encryption Standard (AES)**: FIPS 197 - Rijndael block cipher
- **Secure Hash Standard (SHS)**: FIPS 180-4 - SHA-2 family
- **Digital Signature Standard (DSS)**: FIPS 186-5 - DSA, RSA, ECDSA
- **Random Number Generation**: SP 800-90A - Deterministic random bit generators

#### Post-Quantum Cryptography Standardization
**NIST PQC Competition** (2016-2022):
- **Selected algorithms**: Kyber (KEM), Dilithium (signatures), Falcon (signatures), SPHINCS+ (signatures)
- **Alternate candidates**: BIKE, HQC, Classic McEliece
- **Migration timeline**: Preparation for quantum computer threat

#### Special Publications (SP 800 Series)
- **SP 800-38**: Block cipher modes of operation
- **SP 800-56**: Key derivation and agreement schemes
- **SP 800-57**: Key management recommendations
- **SP 800-63**: Digital identity guidelines

### ISO/IEC Standards
**International Organization for Standardization** develops global cryptographic standards.

#### ISO/IEC 18033 Series - Encryption Algorithms
- **Part 1**: General principles and framework
- **Part 2**: Asymmetric ciphers (RSA, ElGamal, ECC)
- **Part 3**: Block ciphers (AES, 3DES, modes of operation)
- **Part 4**: Stream ciphers
- **Part 5**: Identity-based encryption

#### ISO/IEC 14888 - Digital Signatures
- **RSA signatures**: PKCS#1 v1.5 and PSS
- **DSA signatures**: Original and elliptic curve variants
- **Certificate-based signatures**: Integration with PKI

#### ISO/IEC 19790 - Security Requirements for Cryptographic Modules
- **Security levels**: Level 1 (software) to Level 4 (tamper-active)
- **Physical security**: Tamper evidence and response requirements
- **Operational environment**: Trusted vs. non-trusted environments

### IETF RFCs
**Internet Engineering Task Force** standards for internet cryptography.

#### Core Cryptographic RFCs
- **RFC 8446**: Transport Layer Security (TLS) 1.3
- **RFC 5246**: TLS 1.2 specification
- **RFC 4253**: SSH Transport Layer Protocol
- **RFC 3447**: PKCS#1 v2.1 - RSA cryptography standard

#### Key Management and PKI
- **RFC 5280**: X.509 certificate and CRL profile
- **RFC 6960**: Online Certificate Status Protocol (OCSP)
- **RFC 7296**: Internet Key Exchange (IKEv2) protocol
- **RFC 5652**: Cryptographic Message Syntax (CMS)

### FIPS Publications
**Federal Information Processing Standards** for US government use.

#### Security Requirements
- **FIPS 140-3**: Cryptographic module validation program
- **FIPS 199**: Information categorization standards
- **FIPS 200**: Minimum security requirements

#### Validation Programs
- **CAVP**: Cryptographic Algorithm Validation Program
- **CMVP**: Cryptographic Module Validation Program
- **Testing labs**: Accredited testing laboratories worldwide

### Common Criteria
**International standard** for computer security certification.

#### Evaluation Assurance Levels (EAL)
- **EAL1**: Functionally tested
- **EAL2**: Structurally tested
- **EAL3**: Methodically tested and checked
- **EAL4**: Methodically designed, tested, and reviewed
- **EAL5-7**: Higher assurance levels for critical systems

## Implementation Considerations

### Cryptographic Agility
**Design systems** to adapt to evolving cryptographic requirements.

#### Design Principles
- **Algorithm independence**: Separate crypto logic from application logic
- **Modular architecture**: Pluggable cryptographic components
- **Configuration-driven**: External configuration of algorithms
- **Version negotiation**: Protocol support for multiple algorithm versions

#### Implementation Strategies
- **Crypto abstraction layers**: Hide algorithm details from applications
- **Factory patterns**: Runtime algorithm selection
- **Capability negotiation**: Dynamic algorithm agreement
- **Graceful degradation**: Fallback to secure alternatives

### Algorithm Selection
**Choose appropriate** cryptographic algorithms for specific use cases.

#### Selection Criteria
- **Security level**: Match security requirements to threat model
- **Performance requirements**: Latency, throughput, power consumption
- **Compatibility**: Interoperability with existing systems
- **Standardization**: Use of recognized standards and implementations

#### Algorithm Comparison Matrix
| Use Case | Symmetric | Asymmetric | Hash | Key Exchange |
|----------|-----------|------------|------|--------------|
| **High Performance** | AES-GCM | ECC | BLAKE2 | ECDH |
| **IoT/Constrained** | ChaCha20 | Ed25519 | SHA-256 | X25519 |
| **Legacy Support** | AES-CBC | RSA-2048 | SHA-256 | DHE |
| **Post-Quantum** | AES-256 | Kyber | SHA-3 | Kyber |

### Performance Optimization

#### Hardware Acceleration
- **AES-NI**: Intel/AMD AES instruction sets
- **ARM Crypto Extensions**: Dedicated crypto instructions
- **GPU acceleration**: Parallel hash computations
- **Specialized hardware**: Crypto accelerator cards

#### Software Optimization
- **Vectorization**: SIMD instructions for parallel operations
- **Cache optimization**: Memory access pattern optimization
- **Loop unrolling**: Reduce loop overhead
- **Lookup table optimization**: Balance speed vs. cache pressure

### Secure Implementation Practices

#### Constant-time Implementation
**Eliminate timing side channels** through careful programming.

**Requirements**:
- **Data-independent execution**: Control flow independent of secret data
- **Constant memory access**: Access patterns independent of secrets
- **Uniform operations**: Same operations regardless of input values

**Techniques**:
- **Bitwise operations**: Use XOR, AND, OR instead of conditional branches
- **Arithmetic masking**: Blind secret values during computation
- **Table-based approaches**: Access all table entries uniformly

#### Secure Memory Management
- **Memory zeroing**: Clear sensitive data after use
- **Secure allocation**: Use secure memory allocation functions
- **Memory locking**: Prevent swapping of sensitive data
- **Stack protection**: Prevent buffer overflow attacks

#### Secure Random Number Generation
**Critical foundation** for cryptographic security.

**Entropy Sources**:
- **Hardware sources**: TRNG, CPU instruction (RDRAND)
- **OS entropy pools**: /dev/urandom, CryptGenRandom()
- **Environmental noise**: Timing variations, interrupt patterns
- **User input**: Mouse movements, keystroke timing

**PRNG Requirements**:
- **Cryptographic strength**: Computationally secure output
- **Proper seeding**: Sufficient entropy for initialization
- **State protection**: Secure internal state management
- **Forward security**: Past outputs don't compromise future outputs

#### Cryptographic Library Design

**Security-First Design**:
- **Fail-safe defaults**: Secure default configurations
- **Input validation**: Rigorous parameter checking
- **Error handling**: Secure error handling without information leakage
- **API design**: Hard-to-misuse interfaces

**Example Secure API Design**:
```c
// Bad: Easy to misuse
int encrypt(char* plaintext, char* key, char* output);

// Good: Clear ownership and error handling
crypto_result_t encrypt(
    const uint8_t* plaintext, size_t plaintext_len,
    const uint8_t* key, size_t key_len,
    uint8_t* ciphertext, size_t* ciphertext_len,
    const uint8_t* nonce, size_t nonce_len
);
```

---

# Specialized Topics

## Quantum Cryptography

### Quantum Key Distribution (QKD)
**Theoretically secure** key establishment using quantum mechanics.

#### Quantum Mechanical Principles
- **No-cloning theorem**: Quantum states cannot be perfectly copied
- **Heisenberg uncertainty**: Measurement disturbs quantum states
- **Quantum entanglement**: Correlated quantum states across distance
- **Superposition**: Quantum states exist in multiple states simultaneously

### BB84 Protocol
**First practical QKD protocol** developed by Bennett and Brassard.

#### Protocol Steps
1. **Preparation**: Alice randomly chooses bits and bases (+, ×)
2. **Transmission**: Alice sends photons in chosen polarizations
3. **Measurement**: Bob randomly chooses measurement bases
4. **Sifting**: Alice and Bob discard measurements with different bases
5. **Error checking**: Sample subset to detect eavesdropping
6. **Privacy amplification**: Extract shorter, more secure key

#### Security Analysis
- **Information-theoretic security**: Security based on physics laws
- **Eavesdropping detection**: Quantum disturbance reveals Eve's presence
- **Error rates**: Acceptable error rates vs. security thresholds
- **Practical limitations**: Channel noise, detector efficiency, distance limits

### E91 Protocol
**Entanglement-based QKD** using Einstein-Podolsky-Rosen pairs.

#### Entangled States
- **Bell states**: Maximally entangled two-qubit states
- **Correlation measurements**: Statistical correlations violate Bell inequalities
- **Security proof**: Bell inequality violation guarantees security
- **Device independence**: Security independent of implementation details

### Post-Quantum Cryptography Transition
**Preparing for quantum computer threat** to current cryptography.

#### Timeline Considerations
- **Quantum computer development**: Current state and projections
- **Cryptographic lifetimes**: Long-term data protection requirements
- **Migration complexity**: Infrastructure and protocol updates
- **Hybrid approaches**: Combining classical and post-quantum algorithms

#### Migration Strategies
- **Risk assessment**: Evaluate quantum computing threat timeline
- **Inventory assessment**: Catalog current cryptographic usage
- **Priority ranking**: Critical systems requiring immediate attention
- **Testing programs**: Validate post-quantum implementations

## Lightweight Cryptography

### Resource-Constrained Environments
**Cryptography for devices** with limited computational resources.

#### Constraints
- **Processing power**: Limited CPU capabilities
- **Memory**: Restricted RAM and storage
- **Energy**: Battery-powered operation
- **Communication**: Low bandwidth, high latency
- **Cost**: Manufacturing cost sensitivity

#### Design Principles
- **Efficiency**: Minimize computational overhead
- **Simplicity**: Reduce implementation complexity
- **Flexibility**: Adaptable to different constraint profiles
- **Security**: Maintain adequate security levels

### IoT Cryptography
**Security for Internet of Things** devices and networks.

#### Threat Model
- **Physical access**: Devices may be physically accessible
- **Network attacks**: Wireless communication vulnerabilities
- **Resource exhaustion**: DoS attacks through resource consumption
- **Supply chain**: Manufacturing and distribution security

#### Lightweight Block Ciphers
- **PRESENT**: 64-bit block, 80/128-bit keys, hardware-optimized
- **CLEFIA**: 128-bit block, multiple key sizes, software-friendly
- **LED**: 64-bit block, related to AES structure
- **SIMON/SPECK**: NSA designs optimized for hardware/software

#### Lightweight Hash Functions
- **PHOTON**: Sponge construction for constrained devices
- **SPONGENT**: Lightweight sponge-based hash family
- **Quark**: Ultra-lightweight hash function family

### RFID Security
**Radio Frequency Identification** security challenges and solutions.

#### RFID Constraints
- **No battery**: Passive tags powered by reader RF energy
- **Extreme limitations**: ~1000-10000 logic gates
- **Real-time requirements**: Millisecond response times
- **Cost sensitivity**: Pennies per tag in volume

#### Security Protocols
- **Challenge-response**: Lightweight authentication protocols
- **Distance bounding**: Prevent relay attacks
- **Key updating**: Forward security for long-term deployments
- **Privacy protection**: Prevent tracking and profiling

## Biometric Cryptography

### Fuzzy Extractors
**Extract consistent keys** from noisy biometric data.

#### Problem Statement
- **Biometric variability**: Measurements never exactly identical
- **Key consistency**: Cryptographic keys must be exactly reproducible
- **Privacy**: Biometric templates must be protected
- **Revocability**: Need ability to "change" biometric credentials

#### Construction
1. **Secure sketch**: Helper data enabling error correction
2. **Privacy amplification**: Extract uniform randomness from biometric
3. **Error correction**: Reed-Solomon or BCH codes
4. **Randomness extraction**: Universal hash functions

#### Security Properties
- **Entropy preservation**: Maintain biometric entropy
- **Privacy**: Helper data reveals minimal information
- **Robustness**: Handle expected biometric variations
- **Security**: Resist attacks on helper data

### Biometric Template Protection
**Protect stored biometric templates** from compromise.

#### Protection Techniques
- **Cancelable biometrics**: Transform biometrics with secret parameters
- **Biometric cryptosystems**: Bind cryptographic keys to biometrics
- **Template encryption**: Encrypt stored biometric templates
- **Homomorphic encryption**: Enable matching on encrypted templates

#### Applications
- **Access control**: Biometric authentication systems
- **Identity verification**: Government and commercial ID systems
- **Forensics**: Criminal identification databases
- **Healthcare**: Patient identification and medical records

## Visual Cryptography

### Secret Sharing with Images
**Share secrets** using visual patterns requiring no computation to decode.

#### (k, n) Visual Secret Sharing
- **Secret image**: Divided into n shares
- **Reconstruction**: Any k shares reveal secret when overlaid
- **Visual decoding**: Human visual system performs decoding
- **No computation**: No mathematical operations required

#### Construction Example (2, 2) Scheme
- **White pixel**: Each share gets random pattern, identical patterns
- **Black pixel**: Each share gets random pattern, complementary patterns
- **Overlay**: White pixels remain light, black pixels become dark

### Applications
- **Physical security**: Tamper-evident seals and documents
- **Authentication**: Visual verification of authenticity
- **Copyright protection**: Hidden watermarks in images
- **Access control**: Visual key cards and tokens

## DNA Cryptography

### Biological Computing Approaches
**Use DNA properties** for information security applications.

#### DNA Properties for Cryptography
- **Information density**: Extremely high storage capacity
- **Parallel processing**: Massive parallelism in biological reactions
- **Self-assembly**: Autonomous structure formation
- **Error correction**: Natural biological error correction mechanisms

#### Cryptographic Applications
- **Data storage**: Long-term archival storage in DNA
- **Steganography**: Hide information in biological sequences
- **One-time pads**: Generate keys from DNA sequences
- **Computation**: DNA-based cryptographic operations

#### Challenges
- **Synthesis costs**: Expensive DNA synthesis and sequencing
- **Error rates**: Higher error rates than electronic systems
- **Speed**: Slower than electronic computation
- **Practicality**: Limited to specialized applications

---

# Historical & Theoretical Foundations

## History of Cryptography

### Ancient Civilizations
**Early cryptographic techniques** developed for military and diplomatic use.

#### Mesopotamian Cryptography
- **Cuneiform encryption**: Modified cuneiform writing systems
- **Substitution techniques**: Character replacement methods
- **Steganography**: Hidden messages in clay tablets

#### Egyptian Cryptography
- **Hieroglyphic substitution**: Modified hieroglyphic symbols
- **Religious texts**: Encrypted religious and magical texts
- **Tomb inscriptions**: Protected sacred information

#### Greek and Roman Cryptography
- **Scytale**: Spartan transposition cipher using wooden rod
- **Polybius Square**: 5×5 grid cipher for Greek alphabet
- **Caesar Cipher**: Julius Caesar's shift cipher (shift by 3)
- **Military communication**: Battlefield message protection

### Medieval Cryptography
**Islamic Golden Age** contributions to cryptographic science.

#### Al-Kindi's Contributions (9th century)
- **Frequency analysis**: First systematic cryptanalysis technique
- **"Manuscript on Deciphering Cryptographic Messages"**
- **Statistical methods**: Letter frequency analysis
- **Breaking substitution ciphers**: Systematic approach to cryptanalysis

#### European Developments
- **Trithemius**: "Polygraphiae" (1518) - systematic cryptography
- **Vigenère cipher**: Polyalphabetic substitution (1553)
- **Great Cipher**: Louis XIV's diplomatic encryption
- **Diplomatic cryptography**: Renaissance court communication

### World War II Cryptography
**Industrial-scale cryptography** and mechanized codebreaking.

#### Enigma Machine
**German rotor cipher machine** used throughout WWII.

**Technical Details**:
- **Rotor mechanics**: 3-4 rotors with complex wiring
- **Plugboard**: Additional substitution layer
- **Daily settings**: Rotor positions, plugboard connections
- **Key space**: Approximately 10²³ possible configurations

**Cryptanalysis**:
- **Polish contributions**: Initial theoretical breakthroughs (1932-1939)
- **Bletchley Park**: Industrial codebreaking operation
- **Bombe machines**: Electromechanical Enigma breakers
- **Ultra intelligence**: Strategic impact on war

#### Japanese Cryptography
- **Purple cipher**: Japanese diplomatic encryption
- **JN-25**: Japanese naval code
- **Magic intelligence**: US codebreaking program
- **Battle of Midway**: Cryptanalytic intelligence success

### Venona Project
**US/UK effort** to decrypt Soviet diplomatic communications.

#### Project Details
- **Timeline**: 1943-1980 (declassified 1995)
- **Target**: Soviet diplomatic and intelligence communications
- **One-time pads**: Attacked due to pad reuse
- **Success**: Identified numerous Soviet agents
- **Historical impact**: Cold War intelligence revelations

## Theoretical Limits of Cryptography

### Perfect Secrecy
**Information-theoretic security** providing absolute protection.

#### Shannon's Definition
A cryptosystem has perfect secrecy if:
```
P(M = m | C = c) = P(M = m)
```
for all messages m and ciphertexts c.

#### One-Time Pad
**Only known perfectly secure** encryption system.

**Requirements**:
- **Key length**: Key at least as long as message
- **Random key**: Truly random key generation
- **One-time use**: Each key used exactly once  
- **Secure distribution**: Secure key sharing

**Shannon's Theorem**: Any perfectly secure cryptosystem requires key length ≥ message length.

### Provable Security
**Formal security** definitions and reduction-based proofs.

#### Security Definitions
- **Semantic security**: Ciphertext reveals no partial information
- **IND-CPA**: Indistinguishability under chosen-plaintext attack
- **IND-CCA**: Indistinguishability under chosen-ciphertext attack
- **NM-CPA**: Non-malleability under chosen-plaintext attack

#### Reduction-Based Proofs
1. **Assume adversary** breaks cryptosystem
2. **Construct algorithm** solving hard mathematical problem
3. **Show contradiction**: Would solve presumed hard problem
4. **Conclude**: Cryptosystem secure if hard problem is hard

### Cryptographic Models

#### Random Oracle Model
**Idealized model** treating hash functions as random oracles.

**Properties**:
- **Perfect randomness**: Oracle returns truly random outputs
- **Consistency**: Same input always produces same output
- **Accessibility**: All parties can query oracle
- **Unstructured**: No exploitable mathematical structure

**Limitations**:
- **Idealization**: Real hash functions have structure
- **Impossibility results**: Some ROM-secure schemes impossible in reality
- **Implementation gap**: ROM proofs don't guarantee real-world security

#### Standard Model
**Security proofs** without random oracle assumptions.

**Advantages**:
- **Realistic assumptions**: Use only well-studied mathematical assumptions
- **Stronger guarantees**: More confidence in real-world security
- **Composability**: Better security under protocol composition

**Challenges**:
- **Efficiency**: Often less efficient constructions
- **Complexity**: More complex security proofs
- **Assumptions**: May require stronger or more numerous assumptions

### Indistinguishability Games
**Game-based framework** for defining cryptographic security.

#### Game Structure
1. **Setup**: Challenger generates keys, parameters
2. **Phase 1**: Adversary makes queries (adaptive)
3. **Challenge**: Challenger presents challenge instance
4. **Phase 2**: Adversary makes additional queries
5. **Output**: Adversary outputs guess

#### Security Definition
Cryptosystem is secure if no polynomial-time adversary has non-negligible advantage in the security game.

**Advantage Function**:
```
Adv = |P(Adversary wins) - 1/2|
```

#### Examples
- **IND-CPA game**: Distinguish encryptions of chosen messages
- **EUF-CMA game**: Forge signatures after seeing valid signatures
- **PRF game**: Distinguish pseudorandom function from random function