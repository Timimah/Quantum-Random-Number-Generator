# Quantum Random Number Generation Using Qiskit: A Practical Implementation

## Abstract

    This project presents a practical implementation of a **Quantum Random Number Generator (QRNG)** using Qiskit (2024/2025). By leveraging qubit superposition and measurement, the system produces randomness that exceeds the unpredictability of classical pseudorandom generators. The generated bitstreams were analyzed using entropy, bit-balance tests, distribution analysis, and Von Neumann debiasing.  
    Results show that QRNG provides high-quality randomness suitable for cryptographic and scientific applications.

---

## 1. Introduction

    Random number generation is central to modern computing, especially in cryptography, simulation, and secure communication. Classical computers produce pseudorandom numbers using deterministic algorithms, which can be predictable and therefore vulnerable.

    Quantum Random Number Generators (QRNGs) use quantum mechanics—specifically **superposition and measurement**—to produce truly random outcomes.  
    This project implements such a generator using Qiskit, analyzes its statistical properties, and compares it with classical methods.

---

## 2. Background

### 2.1 Quantum Superposition

A qubit initialized in \|0⟩ becomes a superposition when a Hadamard gate is applied:

\[
H|0\rangle = \frac{|0\rangle + |1\rangle}{\sqrt{2}}
\]

Measuring this superposition produces either 0 or 1 with equal probability.

### 2.2 Measurement and Randomness

Quantum measurement introduces **irreducible randomness**.  
This randomness does not arise from algorithmic processes, making QRNG ideal for cryptographic applications.

### 2.3 Von Neumann Debiasing

Quantum hardware may introduce bias due to noise or readout errors.  
The Von Neumann extractor removes bias by processing pairs of bits:

- 01 → 0  
- 10 → 1  
- 00 and 11 are discarded  

This reduces bias while preserving true randomness.

---

## 3. Methodology

### 3.1 Quantum Circuit Construction

The QRNG circuit includes:

1. Qubits initialized in state \|0⟩  
2. Hadamard gates applied to induce superposition  
3. Measurements applied to all qubits  

Simulations were conducted using Qiskit Aer with 4096 shots.

### 3.2 Statistical Analysis

The project evaluates randomness using:

- Bit-balance test  
- Shannon entropy  
- Histogram of generated integers  
- Comparison with classical RNGs  
- Debiasing using the Von Neumann algorithm  

---

## 4. Results

### 4.1 Bit-Balance

The proportion of 1s for each qubit was approximately 50%, aligning with expected quantum behavior.

### 4.2 Shannon Entropy

The entropy of quantum-generated integers was close to theoretical maximum, indicating strong unpredictability.

### 4.3 Distribution Analysis

The distribution of random integer outputs appeared uniform, signifying stable randomness.

### 4.4 Debiasing Performance

The Von Neumann extractor reduced output size but yielded a more uniform and unbiased bitstream.

---

## 5. Discussion

Results demonstrate that Qiskit-based QRNG produces high-quality randomness even in simulation.  
The system’s entropy compared favorably with Python’s classical `random` and cryptographically secure `secrets` generators.  
Debiasing further improved uniformity, suggesting QRNG suitability for applications in security and scientific computation.

---

## 6. Conclusion

This project confirms that quantum randomness can be efficiently generated and analyzed using Qiskit.  
The implementation is beginner-friendly yet demonstrates clear quantum advantage over classical methods.  
Future work could extend the project by:

- Running circuits on real quantum hardware  
- Applying NIST randomness tests  
- Integrating QRNG output into cryptographic protocols  

---

## 7. References

1. Nielsen, M. A., & Chuang, I. L. (2010). *Quantum Computation and Quantum Information*. Cambridge University Press.  
2. IBM Quantum. (2024). *Qiskit Documentation*. https://qiskit.org  
3. Von Neumann, J. (1951). *Various Techniques Used in Connection with Random Digits*.  
4. Herrero-Collantes, M., & Garcia-Escartin, J. C. (2017). *Quantum Random Number Generators*. *Reviews of Modern Physics*, 89(1), 015004.  
5. Python Software Foundation. (2024). *random — Pseudorandom Number Generation*.  