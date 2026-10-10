# Future Proofs Tech
# Cryptography Research & Systems Architecture

Independent development and formal analysis of post-quantum cryptographic primitives and zero-knowledge proving systems. Focused on zero-dependency, constant-time, and adversarial-resilient implementations from first principles.

---

### Current Projects & Implementations

#### 1. RMD-Q: Restricted Module Decoding with Quadratic Constraint
* **Theoretical Grounding:** A novel post-quantum hardness assumption jointly coupling a noisy module-linear relation over Rq = Zq[X]/(X^n + 1) with a sparse multivariate-quadratic constraint P(s) = 0.
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

#### 5. 0l0 — Post-Quantum Confidential Transfers on Lattice Proofs
**0l0** is a next-generation cryptographic system that enables **anonymous, secure, and quantum-resistant transactions**. Instead of speculative projections, it delivers a benchmarked, end-to-end architecture split into two core layers:
* **`sq-pq`** – A post-quantum Zero-Knowledge (ZK) proof engine built over a Lyubashevsky core on polynomial rings.
* **`sq-chain`** – A confidential statement layer handling notes, nullifiers, wallet transactions, and fail-closed validation.
* **Ultra-Fast Verification**: Validating a full 2-in-2-out confidential transfer takes **only ≈ 2 ms**. This scales to **~500 TPS per core**, making it highly viable for production ledgers.
* **Compact Proof Sizes**: Base ZK proofs (`R*` and `R_bin`) are optimized down to just **3,545 bytes**, minimizing blockchain bloat and storage requirements.
* **Measured Data Only**: Every performance figure is directly measured on an Intel i5-14400F release build. There are **zero projections** or theoretical estimates here.
* **Hardened Security**: 
  * Full memory safety verified via Miri and backed by **over 9.3 million libFuzzer runs** with 0 crashes.
  * Side-channel resilience ensured by a branchless core (asm-verified) and dudect harnesses.
  * Mathematical correctness cross-verified with an independent Python model producing **byte-identical proofs**.

---

### Project Support
Contributions to support independent, self-funded cryptographic research are accepted at the following sovereign addresses:
* **Ethereum (ETH / ERC-20):** `0xAE0ac3296f7b6DDc5921913DbdC5c80E119a1DC3`
* **Bitcoin (BTC):** `bc1qvd7yz2n7nnjumrygr0q77cr589sf6ztp6erl85`

