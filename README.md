# Caesar Cipher Breaker using Grover's Algorithm in Quantum Computing
<p align="center">
  <img 
    src="https://github.com/user-attachments/assets/a87b2a9f-acdc-4f58-bccb-3575572d8fad" 
    alt="Quantum_image" 
    width="384" 
    height="256"
    style="
        border-radius: 15px;
        box-shadow: 0 4px 12px rgba(0,0,0,0.25);
        transition: transform 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
      "
    onmouseover="this.style.transform='scale(1.03)'; this.style.boxShadow='0 6px 20px rgba(0,0,0,0.35)';"
    onmouseout="this.style.transform='scale(1.0)'; this.style.boxShadow='0 4px 12px rgba(0,0,0,0.25)';"
  />
</p>

## 📌 Project Overview

This project implements a quantum search algorithm using Grover’s Algorithm to determine the key used in a Caesar Cipher encryption.
Unlike classical brute-force methods—which try all possible shifts—Grover’s algorithm achieves a quadratic speedup, making the search exponentially more powerful as key space grows.

The project demonstrates:

- How plaintext and ciphertext are represented in quantum states

- How quantum modular addition circuits act as encryption

- How the oracle flips the phase of the correct key

- How the diffusion operator amplifies the amplitude of the solution

- How to fully construct and invert circuits in Qiskit

- How to measure the key qubits to retrieve the shift value

This is a complete, working quantum implementation of Caesar cipher key search.

## 🧠 Project Structure
### 1. Encoding Plaintext & Ciphertext

Plaintext and ciphertext characters are converted into bitstrings and loaded into quantum registers:

- |p⟩ → plaintext qubits

- |k⟩ → key qubits

### 2. Modular Adder Circuit (ADD_k)

To simulate Caesar cipher encryption:

$$∣p⟩∣k⟩→∣p+kmod26⟩∣k⟩$$


Implemented using controlled additions and reversible logic.

### 3. Oracle Construction

The oracle checks:

$$(p + k mod 26) = c$$

If correct:

$$∣kcorrect​⟩→−∣kcorrect​⟩$$

#### Oracle components:

- Apply modular addition

- Compare encrypted value to ciphertext

- Apply phase flip

- Apply inverse adder to remove entanglement

### 4. Diffusion Operator

The diffusion operator amplifies the marked key:

$$D=2∣s⟩⟨s∣−I$$

#### Steps:

1. Apply H to all key qubits

2. Apply phase flip on $∣0…0⟩$

3. Apply H again

### 5. Grover Iteration

Each iteration performs:

- Oracle

- Uncompute adder (adder†)

- Diffusion operator

This amplifies the amplitude of the correct key while suppressing others.

### *Full Circuit👇*

<div align="center"> <img width="700" alt="output" src="https://github.com/user-attachments/assets/0b6491ef-f6fe-4f30-8ddd-24b370f9dbd4" /> </div>

### 6. Simulation & Result Extraction

Measured the key register after running the circuit:

**$$Result=Correct Caesar Cipher Key$$**

### *Simulator Output👇*

<div align="center"> <img width="500"  alt="Simulator_output" src="https://github.com/user-attachments/assets/4c442af7-3cf9-4013-b0fa-f4030d6c2ad1" /></div>

### *IBM Output👇*
<div align="center"><img width="500"  alt="real_ibm_output" src="https://github.com/user-attachments/assets/78890435-f0d3-426b-b806-56c1c00e8e7f" /></div>

### ⚙️ Technologies Used

- Qiskit

- Python

- Quantum Modular Arithmetic

- Grover’s Algorithm

- Reversible Circuits

- Statevector Simulations


