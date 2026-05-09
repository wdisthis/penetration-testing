# SageMath Detail Guide
> Sistem matematika open-source yang sangat kuat untuk kriptografi modern.

## Contoh Kasus di CTF
1. **Discrete Logarithm Problem:**
   ```python
   sage: g = mod(7, 101)
   sage: h = mod(42, 101)
   sage: x = h.log(g)
   ```
2. **Elliptic Curve Cryptography (ECC):**
   ```python
   sage: E = EllipticCurve(GF(101), [0, 0, 0, 1, 1])
   sage: P = E(1, 4)
   sage: Q = 15 * P
   ```
3. **Lattice-based Crypto (LLL Algorithm):**
   Digunakan untuk memecahkan RSA jika kita punya bit bocor (Coppersmith's attack).

## Tip
Anda tidak perlu install penuh jika hanya ingin tes cepat, gunakan [SageMathCell](https://sagecell.sagemath.org/) secara online.
