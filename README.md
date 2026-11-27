# Future Proofs Tech
# Cryptography Research & Systems Architecture

Independent development and formal analysis of post-quantum cryptographic primitives and zero-knowledge proving systems. Focused on zero-dependency, constant-time, and adversarial-resilient implementations from first principles.

---

### Current Projects & Implementations

#### 1. [z0p — Zero-Knowledge STARK & IVC Stack](https://github.com/FutureProofsTech/z0p)
* **Architecture:** From-scratch, zero-dependency zero-knowledge proving stack implemented in 100% safe Rust. Utilizes binary tower fields, an NTT-friendly prime field, BLAKE3, and an arity-4 FRI polynomial commitment scheme.
* **Recursion:** Features a post-quantum, hash-folded Incrementally Verifiable Computation (IVC) mechanism.
* **Security & Performance:** Formally hardened against proof malleability and transcript-poisoning vectors via strict domain separation. Validated through an adversarial test suite covering 970+ hostile vectors (FRI surgery, leaf/node confusion, fold tampering) with zero panics. Prover runtime measures ~6.4s for 2²⁰ rows on a 16-core CPU.

#### 2. [CA-PQ — Post-Quantum Hybrid KEM Framework](https://github.com/FutureProofsTech/CA-PQ)
* **CA-PQ** is a post-quantum cryptography framework that refuses the usual trade-offs. Instead of choosing between battle-tested classical ECDH and larger post-quantum KEMs, it combines both—plus a deterministic chaotic-stream layer—under a single transcript, in a single dependency-free Rust tree where every primitive is hand-written and every claim is tested.
* **Two PQ profiles** (ML-KEM-768 at NIST level 3, ML-KEM-512 at level 1) feed two hybrid combiners alongside a hand-written X25519 leg.
* **The result** on commodity hardware: ∼17k PQ encapsulations per second, ∼2.7k hybrid pairs per second, 828–1 148-byte ciphertexts, zero third-party code.

#### 3. [HypG — Complete Post-Quantum Cryptographic Suite](https://github.com/FutureProofsTech/HypG)
* **HypG** is a from-scratch post-quantum cryptographic suite written in 100% safe Rust with zero dependencies: a Module-LWE key-encapsulation mechanism, BLAKE3-based hashing, ChaCha20 / keyed-BLAKE3 authenticated encryption (one-shot and streaming), and state-less hash-based signatures.
* **The suite** is a frozen research prototype (v1.0): every construction is implemented, deterministically tested, adversarially exercised, and fully gated in CI.


#### 4. [SiCaS — Side-Channel Attenuation & Leakage Assessment](https://github.com/FutureProofsTech/SiCaS)
* **SiCaS** helps engineers build and test software that is harder to attack by measuring the unintended power and electromagnetic signals a chip gives off while it runs, so weaknesses can be found before deployment. SiCaS is a safe Rust, zero runtime dependency workspace that combines first order Boolean-masked primitives and a masked ChaCha20 reference implementation with a leakage-assessment harness for TVLA, CPA, DPA, and timing analysis.

#### 5. [Sirus — Binary-Level x86-64 Code Virtualizer](https://github.com/FutureProofsTech/Sirus)
- **Architecture:** Post-compilation binary virtualizer for ELF64 and PE32+ images. Lifts a strict subset of x86-64 into a typed IR, flattens control flow, expands arithmetic via MBA identities, and compiles into a per-build randomized encrypted ISA executed by a freestanding `no_std`, zero-dependency, 100% safe Rust VM.
- **Hardening & Modes:** Enforces fail-closed binary translation, constant-time execution profiles, and an optional `unsafe` hardened boundary for anti-debug and self-integrity checks.

#### 6. [qWp — Versioned Post-Quantum Hash-Based Signature Family](https://github.com/FutureProofsTech/qWp)
- **Architecture:** From-scratch, zero-dependency post-quantum hash-based signature toolkit implemented in 100% safe Rust (`#![forbid(unsafe_code)]`) with a `no_std` cryptographic core. Built on in-tree BLAKE3 (256-bit and 512-bit modes) and hand-written Ed25519/SHA-512 primitives with strict version separation across all wire formats.
- **Profiles & Trade-offs:** Covers stateful WOTS/Merkle schemes (`QHS-1` through `QHS-3.1` with tree caching), stateless FORS/hypertree variants (`QHS-4` through `QHS-4.2` with parallel signing), a 512-bit-margin construction (`QHS-5`), an Ed25519 classical hybrid (`QHS-6`), and a verifier-only embedded profile (`QHS-E`) for constrained MCUs and bootloaders.
- **Verification & Evidence:** Backed by an evidence-first verification suite including 308 release tests, 20 adversarial attack groups, exhaustive signature bit sweeps, Kani/Creusot/Frama-C formal checks, ~47M libFuzzer runs, constant-time validation (`dudect` max `|t| ≤ 1.07`), and multi-hour soak runs.

---

### Project Support
Contributions to support independent, self-funded cryptographic research are accepted at the following sovereign addresses:
* **Ethereum (ETH / ERC-20):** `0xAE0ac3296f7b6DDc5921913DbdC5c80E119a1DC3`
* **Bitcoin (BTC):** `bc1qvd7yz2n7nnjumrygr0q77cr589sf6ztp6erl85`

