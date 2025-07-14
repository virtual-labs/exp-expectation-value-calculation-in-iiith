### Theory

#### 1. What is Quantum Computing?

Quantum computing is a field of computing that uses principles of quantum mechanics to perform calculations. Unlike classical computers, which use bits as the smallest unit of information (0 or 1), quantum computers use *qubits*, which can exist in a combination (superposition) of both 0 and 1.

Quantum computing is powerful because:
- Qubits can exist in superpositions
- Multiple qubits can be *entangled*, sharing information instantly
- It enables new algorithms that are faster than classical ones for certain problems (e.g., Shor’s algorithm, Grover’s algorithm)

This experiment focuses on the basic concept of measuring a qubit and understanding what the outcome means through the **expectation value**.



#### 2. What is a Qubit?

A qubit is the fundamental unit of quantum information. It is a two-level quantum system that can be in state |0⟩, |1⟩, or any linear combination of the two.

Mathematically, a qubit can be written as:

\[
|\psi\rangle = \alpha |0\rangle + \beta |1\rangle
\]

Where:
- \( \alpha \) and \( \beta \) are complex numbers
- \( |\alpha|^2 + |\beta|^2 = 1 \), to satisfy normalization

In matrix form:
- \( |0\rangle = \begin{bmatrix}1 \\ 0\end{bmatrix} \)
- \( |1\rangle = \begin{bmatrix}0 \\ 1\end{bmatrix} \)

This superposition is a key difference from classical bits, which are either 0 or 1 — but not both.



#### 3. Qubit on the Bloch Sphere

Every pure qubit state can be represented on the surface of a sphere called the **Bloch Sphere**.

The general form using spherical coordinates is:

\[
|\psi\rangle = \cos\left(\frac{\theta}{2}\right)|0\rangle + e^{i\phi}\sin\left(\frac{\theta}{2}\right)|1\rangle
\]

Where:
- \( \theta \) is the angle from the z-axis
- \( \phi \) is the angle in the x-y plane
- This form helps visualize the state in 3D

This is useful for understanding quantum operations as rotations on the sphere.



#### 4. Measurement in Quantum Computing

Quantum measurement collapses the qubit to one of the basis states:
- Measuring in the standard basis means the outcomes will be either |0⟩ or |1⟩.
- The probability of getting |0⟩ is \( |\alpha|^2 \), and for |1⟩ is \( |\beta|^2 \)

In practice, we often represent measurement using an operator or matrix, called an **observable**.
#### 5. Observable Operators (Measurement Basis)

In quantum mechanics, observables are physical quantities we can measure, such as spin or energy. Mathematically, observables are represented using **Hermitian matrices**, which have **real eigenvalues** and **orthogonal eigenstates**.



##### What Are Eigenvalues and Eigenstates?

When an observable is applied to a quantum state, the only possible measurement outcomes are its **eigenvalues**. The system will collapse into the corresponding **eigenstate** after measurement.

Mathematically:

\[
A|\psi\rangle = \lambda|\psi\rangle
\]

- \( A \) is the observable (such as a Pauli matrix)
- \( |\psi\rangle \) is the eigenstate
- \( \lambda \) is the eigenvalue (the result you observe)

This means:
- If the system is already in an eigenstate of \( A \), measuring \( A \) will return \( \lambda \) with certainty.
- If the system is not in an eigenstate, the outcome will be probabilistic, and the state will collapse to one of the eigenstates.




##### Pauli-Z Operator (Z)

This is the standard measurement basis (computational basis). It measures whether the qubit is in the state |0⟩ or |1⟩.

\[
Z = \begin{bmatrix}1 & 0 \\ 0 & -1\end{bmatrix}
\]

- If the qubit is in state |0⟩, measurement gives +1  
- If in |1⟩, measurement gives -1  
- Any superposition of |0⟩ and |1⟩ gives an average (expectation value) between -1 and +1

**Z** measures the **spin along the Z-axis** of the Bloch sphere.



##### Pauli-X Operator (X)

The Pauli-X matrix is often called the **quantum NOT gate**. It flips |0⟩ to |1⟩ and vice versa. When used as an observable, it measures in the **X-basis** (|+⟩ and |−⟩ states):

\[
X = \begin{bmatrix}0 & 1 \\ 1 & 0\end{bmatrix}
\]

- \( |+\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) \) → eigenvalue +1  
- \( |-\rangle = \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle) \) → eigenvalue -1

So, measuring with **X** tells us whether the qubit is aligned along the **X-axis**.



##### Pauli-Y Operator (Y)

The Pauli-Y matrix introduces a phase difference and is related to rotation and spin in the Y direction:

\[
Y = \begin{bmatrix}0 & -i \\ i & 0\end{bmatrix}
\]

Its eigenstates are complex combinations of |0⟩ and |1⟩:

- \( \frac{1}{\sqrt{2}}(|0\rangle + i|1\rangle) \) → eigenvalue +1  
- \( \frac{1}{\sqrt{2}}(|0\rangle - i|1\rangle) \) → eigenvalue -1

Measuring with **Y** gives the projection along the **Y-axis** on the Bloch sphere.



| Operator | Matrix | Measures Along |
|----------|--------|----------------|
| Pauli-Z  | \(\begin{bmatrix}1 & 0 \\ 0 & -1\end{bmatrix}\) | Z-axis |
| Pauli-X  | \(\begin{bmatrix}0 & 1 \\ 1 & 0\end{bmatrix}\) | X-axis |
| Pauli-Y  | \(\begin{bmatrix}0 & -i \\ i & 0\end{bmatrix}\) | Y-axis | 

Each operator defines a different measurement basis and can give different expectation values depending on the state of the qubit.





#### 6. Expectation Value

The expectation value of an observable A in a quantum state \( |\psi\rangle \) is the average value we expect after many measurements of the same system:

\[
\langle A \rangle = \langle \psi | A | \psi \rangle
\]

This gives a number between -1 and 1 when measuring a single qubit with Pauli matrices.



#### 7. How to Calculate It

To calculate the expectation value:

1. Represent the state \( |\psi\rangle \) as a column vector.
2. Take its conjugate transpose to form \( \langle \psi | \)
3. Multiply using the formula:  
   \( \langle \psi | A | \psi \rangle \)

**Example:**

If the qubit is in state:

\[
|\psi\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) = \begin{bmatrix} \frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} \end{bmatrix}
\]

And the observable is Pauli-Z:

\[
Z = \begin{bmatrix}1 & 0 \\ 0 & -1\end{bmatrix}
\]

Then the expectation value is:

\[
\langle Z \rangle = 
\begin{bmatrix} \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} \end{bmatrix}
\begin{bmatrix}1 & 0 \\ 0 & -1\end{bmatrix}
\begin{bmatrix} \frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} \end{bmatrix}
= 0
\]

So, even though each measurement gives +1 or -1, the average of many measurements is 0 — meaning equal probability of |0⟩ and |1⟩.



#### 8. Interpretation of Expectation Value

The expectation value tells you about the balance between |0⟩ and |1⟩ in the qubit state.

- \( \langle Z \rangle = 1 \) → qubit is completely in |0⟩
- \( \langle Z \rangle = -1 \) → qubit is completely in |1⟩
- \( \langle Z \rangle = 0 \) → qubit is an equal mix of |0⟩ and |1⟩

This value is helpful to visualize the state on the Bloch Sphere (z-axis position).


