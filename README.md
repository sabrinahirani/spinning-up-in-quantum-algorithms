## Spinning Up in Quantum Algorithms

### Quantum States

In quantum mechanics, the state of a quantum system is described by a vector, known as a *ket*, in a complex vector space (Hilbert Space). The simplest quantum system is a qubit, represented by a two-dimensional vector:

$$
\ket{\psi} = \alpha \ket{0} + \beta \ket{1}
$$

where \$\alpha\$ and \$\beta\$ are complex numbers satisfying the normalization condition:

$$
|\alpha|^2 + |\beta|^2 = 1
$$

These coefficients represent the *probability amplitudes* for measuring the qubit in states \$\ket{0}\$ or \$\ket{1}\$.

### Measurement and Superposition

In quantum mechanics, measurement collapses a quantum state into one of the basis states, with probabilities determined by the state's coefficients. If a qubit is in a superposition state:

$$
\ket{\psi} = \alpha \ket{0} + \beta \ket{1}
$$

the probability of measuring the qubit in state \$\ket{0}\$ is given by *Born's Rule*:

$$
P(\ket{0}) = |\alpha|^2, \quad P(\ket{1}) = |\beta|^2
$$

Here, \$|\alpha|^2\$ and \$|\beta|^2\$ are the probabilities of observing \$\ket{0}\$ and \$\ket{1}\$, respectively, and the total probability must sum to 1.

In superposition, the qubit can be in a combination of states until measured, at which point it collapses to one of the basis states, reflecting the probabilistic nature of quantum mechanics. This is a key distinction between classical and quantum systems, where quantum states can exist in a superposition of multiple possibilities.

### Composite Systems

For systems with more than one qubit, the total quantum state is described by the *tensor product* of individual qubits. For example, two qubits in states \$\ket{\psi\_1} = \alpha\_1 \ket{0} + \beta\_1 \ket{1}\$ and \$\ket{\psi\_2} = \alpha\_2 \ket{0} + \beta\_2 \ket{1}\$ form the composite state:

$$
\ket{\psi_1} \otimes \ket{\psi_2} = \alpha_1 \alpha_2 \ket{00} + \alpha_1 \beta_2 \ket{01} + \beta_1 \alpha_2 \ket{10} + \beta_1 \beta_2 \ket{11}
$$

### Entanglement (Mathematically Demonstrated)

Entanglement is a phenomenon where qubits in a composite system are correlated in such a way that the state of each qubit cannot be described independently. Consider two qubits in the Bell state:

$$
\ket{\Phi^+} = \frac{1}{\sqrt{2}} (\ket{00} + \ket{11})
$$

To see why this is an entangled state, observe that there are no individual qubit states \$\ket{\psi\_1}\$ and \$\ket{\psi\_2}\$ such that:

$$
\ket{\Phi^+} = \ket{\psi_1} \otimes \ket{\psi_2}
$$

This means the state \$\ket{\Phi^+}\$ cannot be factored into two separate qubit states. Measuring the first qubit will instantly determine the state of the second qubit. For example:

- If you measure the first qubit to be \$\ket{0}\$, the second qubit must also be \$\ket{0}\$.
- If you measure the first qubit to be \$\ket{1}\$, the second qubit must also be \$\ket{1}\$.

This non-local correlation demonstrates quantum entanglement, where the state of the entire system is inseparable, even if the qubits are physically distant.

### Quantum Gates

Quantum gates are unitary operations that transform the state of qubits. They are analogous to classical logic gates but operate on quantum states, which allows for more complex transformations.

For a single qubit, quantum gates are represented by 2x2 unitary matrices. Multi-qubit gates act on composite systems, represented by tensor products of matrices.

### Common Quantum Gates

- **Hadamard Gate (H):** Creates superposition from a basis state.

$$
H = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}
$$

This transforms \$\ket{0}\$ into \$\frac{1}{\sqrt{2}}(\ket{0} + \ket{1})\$, and \$\ket{1}\$ into \$\frac{1}{\sqrt{2}}(\ket{0} - \ket{1})\$.

- **Pauli-X Gate (X):** Equivalent to the classical NOT gate, flipping \$\ket{0} \leftrightarrow \ket{1}\$.

$$
X = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}
$$

- **Pauli-Y Gate (Y):** Applies a phase flip combined with a bit flip.

$$
Y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}
$$

- **Pauli-Z Gate (Z):** Applies a phase flip to \$\ket{1}\$, leaving \$\ket{0}\$ unchanged.

$$
Z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
$$

- **CNOT Gate (Controlled-NOT):** A two-qubit gate that flips the second qubit (target) if the first qubit (control) is \$\ket{1}\$.

$$
CNOT = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}
$$

This gate is crucial for creating entangled states like the Bell states.

- **SWAP Gate:** A two-qubit gate that swaps the states of two qubits.

$$
SWAP = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}
$$

- **Toffoli Gate (CCNOT):** A three-qubit gate that flips the third qubit (target) if the first two qubits (controls) are both \$\ket{1}\$.

$$
Toffoli = \begin{pmatrix}
1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\
0 & 0 & 0 & 0 & 0 & 0 & 1 & 0
\end{pmatrix}
$$

The Toffoli gate is universal for classical computation, as it can be used to construct any Boolean circuit.

---

## Benefits of Quantum Algorithms:

### Quantum Teleportation

Quantum teleportation transmits a quantum state from one location to another using entanglement and classical communication.

**Protocol Steps:**

1. Alice and Bob share an entangled Bell pair: \$\ket{\Phi^+} = \frac{1}{\sqrt{2}} (\ket{00} + \ket{11})\$.
2. Alice has a qubit in state \$\ket{\psi} = \alpha \ket{0} + \beta \ket{1}\$.
3. She performs a Bell-state measurement on her qubit and one from the entangled pair.
4. She sends the result (2 classical bits) to Bob.
5. Bob applies a corresponding Pauli correction to recover \$\ket{\psi}\$.

**Circuit Diagram:**

```
|ψ⟩──■───────H───M───┐
      │               ├──(classical to Bob)
|0⟩──X──■────────M───┘
         │
|0⟩──────X─────────────Z^a X^b (by Bob)
```

### Superdense Coding

Superdense coding allows sending 2 classical bits using only 1 qubit, leveraging entanglement.

**Protocol Steps:**

1. Alice and Bob share a Bell pair.
2. Alice applies one of four Pauli operations (\$I\$, \$X\$, \$Z\$, \$XZ\$) to encode 2 bits.
3. She sends her qubit to Bob.
4. Bob applies a Bell measurement and recovers the 2 bits.

**Circuit Diagram:**

```
|0⟩──H──■───────┐         
        │       │        
|0⟩─────X───────■───Bell measurement
       Alice encodes       Bob decodes
```

### The CHSH Game

The CHSH game is a two-player game testing quantum non-locality. Players win with probability >75% using entanglement.

**Game:**

- Alice and Bob receive random bits \$x\$ and \$y\$.
- They output bits \$a\$ and \$b\$.
- Win if \$a \oplus b = x \cdot y\$.

**Quantum Strategy:**

- Share the Bell state \$\ket{\Phi^+}\$.
- Measure at angles depending on \$x\$ and \$y\$.
- Achieves success probability \~\$85.4%\$.

**Circuit Diagram:**

```
|0⟩──H──■───Measure at θₐ(x)────a
        │                     
|0⟩─────X───Measure at θ_b(y)────b
```

---

## Quantum Algorithms

### What Is Phase Kickback?

Phase kickback is a phenomenon where a phase applied to a target qubit affects the control qubit instead. It's crucial in phase estimation and the quantum Fourier transform.

Example: In a controlled-U operation, applying \$U\$ to \$\ket{1}\$ causes the control to "receive" the phase.

### Quantum Fourier Transform

The quantum Fourier transform (QFT) maps computational basis states to their Fourier-transformed equivalents. It's essential in Shor’s and phase estimation algorithms.

**QFT for 2 Qubits:**

```
|q0⟩──H─────●─────R2───H
            │
|q1⟩────────X───────────
```

### Quantum Phase Estimation

Estimates the eigenvalue \$e^{2\pi i \phi}\$ of a unitary \$U\$ such that \$U \ket{u} = e^{2\pi i \phi} \ket{u}\$.

**Steps:**

1. Prepare \$t\$ control qubits in \$\ket{0}\$ and one eigenvector \$\ket{u}\$.
2. Apply Hadamards to control.
3. Apply controlled-\$U^{2^j}\$ gates.
4. Inverse QFT on control qubits.
5. Measure to estimate \$\phi\$.

### Shor's Algorithm

Shor’s algorithm factors large integers exponentially faster than the best-known classical algorithms.

**Outline:**

1. Choose a random base \$a\$ coprime to \$N\$.
2. Use quantum phase estimation to find the period \$r\$ of \$a^x \mod N\$.
3. Use \$r\$ to compute factors of \$N\$.

**Key Quantum Subroutine:** Period finding via phase estimation.

---

