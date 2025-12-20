# Quantum Random Number Generator (QRNG)

A practical implementation of a quantum random number generator using IBM's Qiskit framework, demonstrating true randomness through quantum superposition and measurement.

## Overview

This project leverages quantum mechanics to generate truly random numbers—fundamentally unpredictable even in principle. Unlike classical pseudo-random number generators that use deterministic algorithms, this QRNG harnesses quantum superposition to produce randomness guaranteed by the laws of physics.

**Achieved Results:**
- **Shannon Entropy:** 4.9966 bits (99.93% of theoretical maximum)
- **Bit Balance:** All qubits within 49.3-50.8% (near-perfect 50/50)
- **Performance:** Matches/exceeds cryptographic-grade classical RNGs

## How It Works

### Quantum Circuit Design
1. **Initialize:** 5 qubits in state |0⟩
2. **Superposition:** Apply Hadamard gates to create equal superposition: 
      $H|0⟩ = (|0⟩+|1⟩)/√2$
3. **Measurement:** Collapse each qubit randomly to 0 or 1
4. **Iteration:** Execute circuit 4,096 times for statistical reliability

### Why Quantum?
- **Classical RNGs:** Use mathematical formulas (predictable if algorithm/seed is known)
- **Quantum RNGs:** Use measurement collapse (fundamentally unpredictable by quantum mechanics)

The Debian OpenSSL bug (2008) showed the dangers of weak randomness—reducing encryption keys from 2^128 to just 32,768 possibilities, affecting millions of systems worldwide. Quantum randomness provides physics-guaranteed unpredictability.

## Statistical Validation

This project validates randomness through five comprehensive tests:

### 1. Bit-Balance Test
Verifies each qubit produces ~50% zeros and ~50% ones.
```
Qubit 0: 50.83% | Qubit 1: 50.34% | Qubit 2: 49.44%
Qubit 3: 50.61% | Qubit 4: 49.29%
```

### 2. Shannon Entropy
Measures unpredictability (0 = predictable, 5 = perfect randomness for 5 qubits).
```
Result: 4.9966 bits (99.93% perfect)
```

### 3. Distribution Uniformity
All 32 possible 5-bit integers (0-31) appear roughly equally (110-140 times each).

### 4. Classical Comparison
Benchmarked against Python's random number generators:
```
Quantum RNG:     4.9966 bits ✓✓
secrets module:  4.9952 bits ✓
random module:   4.9946 bits ✓
```

### 5. Von Neumann Debiasing
Industry-standard bias removal technique:
```
Original bits:  20,480
Debiased bits:   5,129
Efficiency:      25.0% (matches theory)
```

## Quick Start

### Prerequisites
```bash
pip install qiskit qiskit-aer numpy matplotlib
```

### Basic Usage
```python
from qiskit import QuantumCircuit
from qiskit_aer import AerSimulator

# Create 5-qubit quantum circuit
qc = QuantumCircuit(5, 5)

# Apply Hadamard gates (superposition)
qc.h(range(5))

# Measure all qubits
qc.measure(range(5), range(5))

# Run simulation
sim = AerSimulator()
job = sim.run(qc, shots=4096)
result = job.result()
counts = result.get_counts()

print(counts)
```

### Full Implementation
See `qrng.ipynb` for complete code including:
- Entropy calculation
- Statistical analysis
- Visualization
- Von Neumann debiasing

## 📈 Results Visualization

The project includes visualizations for:
- Per-qubit bit-balance bar charts
- Shannon entropy comparison graphs
- Distribution histograms (all 32 outcomes)
- Debiased bit distribution analysis

## Real-World Applications

### 1. Cybersecurity & Post-Quantum Cryptography
- Unbreakable encryption key generation
- Protection against quantum computer attacks
- "Harvest now, decrypt later" threat mitigation

### 2. Blockchain & Web3
- Verifiable randomness for smart contracts
- Fair NFT drops and lottery systems
- Decentralized consensus mechanisms

### 3. Fair Gaming
- Provably fair online casinos
- Transparent lottery systems
- Regulatory compliance

### 4. Scientific Research
- Monte Carlo simulations
- Clinical trials and drug testing
- Physics simulations and climate modeling

### 5. National Security
- Military-grade encryption
- Classified communications
- Intelligence operations

## Future Work

### Short-Term
- [ ] Test on real IBM quantum hardware (vs simulator)
- [ ] Apply full NIST Statistical Test Suite
- [ ] Scale to 10-20 qubits
- [ ] Implement quantum error mitigation

### Long-Term
- [ ] Build web application for on-demand quantum RNG
- [ ] One-time pad encryption demonstration
- [ ] Alternative algorithms (Bell states, quantum walks)
- [ ] Integration with blockchain protocols

## Security Context

### The Quantum Threat
Current encryption methods (RSA, ECC) are vulnerable to quantum attacks:
- **Shor's algorithm** can break RSA in polynomial time
- **"Harvest now, decrypt later"** attacks are already happening
- Need for quantum-resistant cryptography is urgent

### Why QRNG Matters
- Foundation for post-quantum security systems
- Provides provably unpredictable randomness
- Essential for next-generation cryptographic protocols

## Technical Details

**Framework:** Qiskit 1.0+  
**Simulator:** AerSimulator (Qiskit Aer)  
**Qubits:** 5 (32 possible outcomes)  
**Shots:** 4,096 measurements  
**Entropy:** 4.9966 / 5.0 bits (99.93%)  
**Language:** Python 3.8+

## Contributing

Contributions welcome! Areas of interest:
- Real hardware testing and error mitigation
- Additional statistical tests (NIST suite)
- Alternative quantum algorithms
- Performance optimizations

## References

1. Nielsen & Chuang (2010). *Quantum Computation and Quantum Information*
2. IBM Quantum. *Qiskit Documentation*. https://qiskit.org
3. Von Neumann, J. (1951). *Various Techniques Used in Connection with Random Digits*
4. Herrero-Collantes & Garcia-Escartin (2017). *Quantum Random Number Generators*. Reviews of Modern Physics.
5. Python Software Foundation. *random — Pseudorandom Number Generation*

## License

[- MIT recommended for open source]

## Author

**Blessed-Agboola Jesujoba Jemimah**  
HeGUTTS Fellowship 2025  
jblessedagboola@gmail.com | 
https://www.linkedin.com/in/ba-jesujoba

---

*"Harnessing the fundamental randomness of quantum mechanics to generate numbers that even a supercomputer with perfect knowledge couldn't predict."*
