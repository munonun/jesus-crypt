# 📊 Project: Jesus - Benchmark Results

This document outlines the performance results of Project: Jesus  
under various conditions and test cases.

---

## 🔧 Test Environment

- **CPU**: AMD Ryzen 7 7435HS (8-core, 16-thread)
- **RAM**: 20GB DDR5
- **OS**: Windows 11 / MinGW-w64 GCC 14.2.0
- **Compiler**: g++ 14.2.0 with `-std=c++23 -O3 -flto -march=native`
- **Libraries**: libsodium, liboqs, OpenSSL

---

## 📦 Test Parameters

| Item | Value |
|------|-------|
| Test target | `benchmark.cpp` (full encrypt + decrypt)  
| Chunk size | Auto-tuned (based on hardware concurrency)  
| Dataset size | 1GB file x 100 iterations  
| Total processed | 100GB of data  
| Integrity checks | BLAKE3 hash + HMAC-SHA512  
| PQC applied | Kyber-1024 + Dilithium v3 (once per session)  

---

## 📈 Results Summary

| Batch | Time (sec) |
|-------|------------|
| #1    | 517.551  
| #2    | 516.592  
| #3    | 514.637  
| #4    | 516.970  
| #5    | 516.731  

- **Average**: `516.496s`  
- **Min**: `514.637s`  
- **Max**: `517.551s`  
- **Standard Deviation**: `±0.986s`  

---

## 📊 Interpretation

- Performance is extremely stable with <1s deviation over 5 runs  
- Parallel chunking + async processing effectively spreads CPU load  
- PQC operations (Kyber/Dilithium) have negligible impact after session init  
- MAC & hash validation overhead is bounded and consistent

---

## 📷 Visualization

> _Insert chart screenshot here if available_  
(예: `benchmark_graph.png` 그래프 이미지 첨부하면 끝)

---

## 📌 Notes

- No compression used — results reflect **raw encryption/decryption**  
- Test was repeated multiple times to eliminate cache/warm-up effects  
- All security layers (MAC, hash, PQC) were active

---
