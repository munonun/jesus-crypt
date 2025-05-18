# jesus-crypt

> Quantum-Resistant Parallel Authenticated Encryption Stack  
> (XChaCha ×4 · AES-512-CTR · Kyber-1024 · Dilithium v3 · HMAC-SHA512 · BLAKE3)

---

## ✨ About

**jesus-crypt** is a high-assurance encryption stack designed for maximum resilience under post-quantum threat models.  
Built for those who prioritize **security over speed**, and **control over compromise**.

---

## 🔐 Components

- **XChaCha20 × 4** layered symmetric encryption
- **AES-512-CTR** block-layer encryption (dual IV)
- **HMAC-SHA512** message authentication
- **BLAKE3** hashing for integrity
- **Kyber-1024** (NIST PQC KEM)
- **Dilithium v3** (NIST PQC signature)

---

## 🚀 Benchmark

**1GB x 100 Encrypt/Decrypt**
- Average Time: `516.5s`
- Min: `514.6s`, Max: `517.5s`, Std Dev: `±1.5s`

See [`BENCHMARK.md`](./BENCHMARK.md) for graphs.

---

## 🛠️ .c conversion command

```bash
g++ -std=c17 -O3 -flto -msse2 "-msse4.1" -mavx2 -mavx512f -mavx512vl -c blake3_dispatch.c blake3_portable.c blake3_sse2.c blake3_sse41.c blake3_avx2.c blake3_avx512.c
```
## 🛠️ build

```bash
g++ -std=c++23 -O3 -flto -march=native benchmark.cpp blake3.c blake3_dispatch.o blake3_portable.o blake3_sse2.o blake3_sse41.o blake3_avx2.o blake3_avx512.o -IC:/vcpkg/installed/x64-windows/include -LC:/vcpkg/installed/x64-windows/lib -lsodium -lssl -lcrypto -loqs -o benchmark.exe
```
