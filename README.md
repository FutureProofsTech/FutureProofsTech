# Future Proofs Tech
# Cryptography Research & Systems Architecture

Independent development and formal analysis of post-quantum cryptographic primitives and zero-knowledge proving systems. Focused on zero-dependency, constant-time, and adversarial-resilient implementations from first principles.

---

### Current Projects & Implementations

#### 1. RMD-Q: Restricted Module Decoding with Quadratic Constraint
* **Theoretical Grounding:** A novel post-quantum hardness assumption jointly coupling a noisy module-linear relation over \(R_q = \mathbb{Z}_q[X]/(X^n + 1)\) with a sparse multivariate-quadratic constraint P(s) = 0.
* **Constructions:** Co-designed Fujisaki-Okamoto Key-Encapsulation Mechanism (KEM) and Fiat-Shamir signature scheme sharing a unified ring arithmetic core.
* **Implementation & Verification:** Optimized constant-time C implementation (~3.9 KB core codebase) with proven Barrett reduction. Byte-for-byte validated against an independent Python reference. Verified clean under Valgrind and compiler sanitizers.

#### 2. Zero-Knowledge STARK & IVC Stack
* **Architecture:** From-scratch, zero-dependency zero-knowledge proving stack implemented in 100% safe Rust. Utilizes binary tower fields, an NTT-friendly prime field, BLAKE3, and an arity-4 FRI polynomial commitment scheme.
* **Recursion:** Features a post-quantum, hash-folded Incrementally Verifiable Computation (IVC) mechanism.
* **Security & Performance:** Formally hardened against proof malleability and transcript-poisoning vectors via strict domain separation. Validated through an adversarial test suite covering 970+ hostile vectors (FRI surgery, leaf/node confusion, fold tampering) with zero panics. Prover runtime measures ~6.4s for 2²⁰ rows on a 16-core CPU.

#### 3. CA-PQ — Post-Quantum Hybrid KEM Framework
* **CA-PQ** is a post-quantum cryptography framework that refuses the usual trade-offs. Instead of choosing between battle-tested classical ECDH and larger post-quantum KEMs, it combines both—plus a deterministic chaotic-stream layer—under a single transcript, in a single dependency-free Rust tree where every primitive is hand-written and every claim is tested.
* **Two PQ profiles** (ML-KEM-768 at NIST level 3, ML-KEM-512 at level 1) feed two hybrid combiners alongside a hand-written X25519 leg.
* **The result** on commodity hardware: ∼17k PQ encapsulations per second, ∼2.7k hybrid pairs per second, 828–1 148-byte ciphertexts, zero third-party code.

#### 4. HypG — Complete Post-Quantum Cryptographic Suite in Safe Rust
* **HypG** is a from-scratch post-quantum cryptographic suite written in 100% safe Rust with zero dependencies: a Module-LWE key-encapsulation mechanism, BLAKE3-based hashing, ChaCha20 / keyed-BLAKE3 authenticated encryption (one-shot and streaming), and state-less hash-based signatures.
* **The suite** is a frozen research prototype (v1.0): every construction is implemented, deterministically tested, adversarially exercised, and fully gated in CI.

---

### Project Support
Contributions to support independent, self-funded cryptographic research are accepted at the following sovereign addresses:
* **Ethereum (ETH / ERC-20):** `0xAE0ac3296f7b6DDc5921913DbdC5c80E119a1DC3`
* **Bitcoin (BTC):** `bc1qvd7yz2n7nnjumrygr0q77cr589sf6ztp6erl85`

