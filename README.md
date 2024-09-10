## Spinning Up in Quantum Algorithms

### Quantum States
In quantum mechanics, the state of a quantum system is described by a vector, known as a *ket*, in a complex vector space (Hilbert Space). The simplest quantum system is a qubit, represented by a two-dimensional vector:

$$
\ket{\psi} = \alpha \ket{0} + \beta \ket{1}
$$

where $\alpha$ and $\beta$ are complex numbers satisfying the normalization condition:

$$
|\alpha|^2 + |\beta|^2 = 1
$$

These coefficients represent the *probability amplitudes* for measuring the qubit in states $\ket{0}$ or $\ket{1}$.

### Measurement and Superposition
In quantum mechanics, measurement collapses a quantum state into one of the basis states, with probabilities determined by the state's coefficients. If a qubit is in a superposition state:

$$
\ket{\psi} = \alpha \ket{0} + \beta \ket{1}
$$

the probability of measuring the qubit in state $\ket{0}$ is given by *Born's Rule*:

$$
P(\ket{0}) = |\alpha|^2, \quad P(\ket{1}) = |\beta|^2
$$

Here, $|\alpha|^2$ and $|\beta|^2$ are the probabilities of observing $\ket{0}$ and $\ket{1}$, respectively, and the total probability must sum to 1.

In superposition, the qubit can be in a combination of states until measured, at which point it collapses to one of the basis states, reflecting the probabilistic nature of quantum mechanics. This is a key distinction between classical and quantum systems, where quantum states can exist in a superposition of multiple possibilities.

### Composite Systems
For systems with more than one qubit, the total quantum state is described by the *tensor product* of individual qubits. For example, two qubits in states $\ket{\psi_1} = \alpha_1 \ket{0} + \beta_1 \ket{1}$ and $\ket{\psi_2} = \alpha_2 \ket{0} + \beta_2 \ket{1}$ form the composite state:

$$
\ket{\psi_1} \otimes \ket{\psi_2} = \alpha_1 \alpha_2 \ket{00} + \alpha_1 \beta_2 \ket{01} + \beta_1 \alpha_2 \ket{10} + \beta_1 \beta_2 \ket{11}
$$

### Entanglement (Mathematically Demonstrated)
Entanglement is a phenomenon where qubits in a composite system are correlated in such a way that the state of each qubit cannot be described independently. Consider two qubits in the Bell state:

$$
\ket{\Phi^+} = \frac{1}{\sqrt{2}} (\ket{00} + \ket{11})
$$

To see why this is an entangled state, observe that there are no individual qubit states $\ket{\psi_1}$ and $\ket{\psi_2}$ such that:

$$
\ket{\Phi^+} = \ket{\psi_1} \otimes \ket{\psi_2}
$$

This means the state $\ket{\Phi^+}$ cannot be factored into two separate qubit states. Measuring the first qubit will instantly determine the state of the second qubit. For example:
- If you measure the first qubit to be $\ket{0}$, the second qubit must also be $\ket{0}$.
- If you measure the first qubit to be $\ket{1}$, the second qubit must also be $\ket{1}$.

This non-local correlation demonstrates quantum entanglement, where the state of the entire system is inseparable, even if the qubits are physically distant.

### Quantum Gates
Quantum gates are unitary operations that transform the state of qubits. They are analogous to classical logic gates but operate on quantum states, which allows for more complex transformations.

For a single qubit, quantum gates are represented by 2x2 unitary matrices. Multi-qubit gates act on composite systems, represented by tensor products of matrices.

### Common Quantum Gates
- **Hadamard Gate (H):** Creates superposition from a basis state.

$$
H = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}
$$

This transforms $\ket{0}$ into $\frac{1}{\sqrt{2}}(\ket{0} + \ket{1})$, and $\ket{1}$ into $\frac{1}{\sqrt{2}}(\ket{0} - \ket{1})$.

- **Pauli-X Gate (X):** Equivalent to the classical NOT gate, flipping $\ket{0} \leftrightarrow \ket{1}$.

$$
X = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}
$$

- **Pauli-Y Gate (Y):** Applies a phase flip combined with a bit flip.

$$
Y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}
$$

- **Pauli-Z Gate (Z):** Applies a phase flip to $\ket{1}$, leaving $\ket{0}$ unchanged.

$$
Z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
$$

- **CNOT Gate (Controlled-NOT):** A two-qubit gate that flips the second qubit (target) if the first qubit (control) is $\ket{1}$.

$$
CNOT = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 1 & 0 \end{pmatrix}
$$

This gate is crucial for creating entangled states like the Bell states.

- **SWAP Gate:** A two-qubit gate that swaps the states of two qubits.

$$
SWAP = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}
$$

The SWAP gate exchanges the states of the two qubits: $\ket{00} \to \ket{00}$, $\ket{01} \to \ket{10}$, $\ket{10} \to \ket{01}$, and $\ket{11} \to \ket{11}$.

- **Toffoli Gate (CCNOT):** A three-qubit gate that flips the third qubit (target) if the first two qubits (controls) are both $\ket{1}$.

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

### Quantum Teleporation

TODO

### Superdense Coding

TODO

From the above, we observe a multiple bit to single qubit equivalence ratio. This implies... TODO

### The CHSH Game

TODO

---

## Quantum ALgorithms

### What Is Phase Kickback?

TODO

### Quantum Fourier Transform

TODO

### Quantum Phase Estimation

TODO

### Shor's Algorithm

TODO

---

