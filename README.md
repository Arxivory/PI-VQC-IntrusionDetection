# Physics-Informed Variational Quantum Machine Learning for Network Intrusion Detection

## A Hybrid Quantum-Classical Approach via IBM Qiskit

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1k3qWls2NLjX-xKvWPJAfDbXn9ymmPf2Y?usp=sharing)
### 🏆 Champion Project – Quantum Computing Society of the Philippines XQubit Technical Applications Competition

## Abstract

This project demonstrates a **Physics-Informed Variational Quantum Classifier (PI-VQC)** for network intrusion detection, a submission for the **Quantum Computing Society of the Philippines' XQubit Competition**, addressing the limitations of classical machine learning in handling high-dimensional, nonlinear cybersecurity data under real-time and adversarial conditions. The approach implements a **hybrid quantum-classical pipeline** using **IBM Qiskit**.

### Key Components:
*   **Quantum feature encoding:** Angle embedding of preprocessed network features into a $2^n$-dimensional Hilbert space.
*   **Physics-informed ansatz:** A parameterized quantum circuit structurally inspired by the Ising spin Hamiltonian, encoding interaction-based priors.
*   **Variational quantum optimization:** Parameter-shift gradient descent over a cost landscape defined by observable expectation values.
*   **Hybrid inference:** Quantum circuit outputs feed into a classical softmax layer for binary classification (normal vs. intrusion).

This pipeline is evaluated on the **UNSW-NB15 network intrusion dataset** using Qiskit's AerSimulator. The project aims to show that the physics-informed circuit structure provides an inductive bias that regularizes the quantum model, potentially mitigating the barren plateau problem and improving trainability for cybersecurity classification tasks.

## Research Objectives

| # | Objective |
|---|-----------|
| O1 | Design and implement a PI-VQC pipeline using the transverse-field Ising Hamiltonian as ansatz prior |
| O2 | Derive all mathematical components from first principles: angle encoding, ZZ decomposition, parameter-shift gradients |
| O3 | Train and evaluate the PI-VQC on the UNSW-NB15 dataset using IBM Qiskit AerSimulator |
| O4 | Implement a Quantum Kernel SVM (QKSVM) baseline using fidelity-based quantum kernels |
| O5 | Simulate NISQ noise (depolarising + readout errors) and quantify performance degradation |
| O6 | Compare PI-VQC (ideal + noisy) against QKSVM and classical SVM under identical preprocessing |
| O7 | Demonstrate that the Ising ansatz produces larger gradient norms than generic circuits, supporting the barren plateau mitigation claim |

## Key Findings

*   **Physics-informed structure aids trainability:** The Ising ansatz produces larger gradient norms than generic circuits of equal depth, consistent with barren plateau mitigation theory.
*   **NISQ degradation is measurable but bounded:** Performance degradation at realistic gate error rates ($p_2 = 0.05$) is observed, with potential for recovery using error mitigation techniques.
*   **Quantum kernel matches classical SVM:** The QKSVM achieves competitive accuracy, validating the fidelity kernel framework on this dataset.
*   **Quantum advantage not demonstrated at this scale:** At $n \leq 4$ qubits, classical SVM performance matches or exceeds quantum models. True quantum advantage for such tasks typically requires a fault-tolerant regime with a significantly higher number of qubits.

## Setup and Installation

To run this notebook, you will need the following Python packages. You can install them by uncommenting and running the first code cell in the notebook:

```bash
!pip install qiskit qiskit-aer qiskit-machine-learning scikit-learn
!pip install pandas matplotlib seaborn imbalanced-learn pylatexenc
```

# Dataset
The project uses the **UNSW-NB15** dataset.  
The notebook includes a Kaggle Hub integration to automatically download the dataset.  
If you prefer to load it manually, ensure `UNSW_NB15_training-set.csv` is in the same directory as the notebook and update the `DATASET_PATH` variable in the `load_dataset` function accordingly.

---

# Usage
The notebook is structured into several chapters:

- **Chapter 0: Environment Setup & Imports**  
  Initializes necessary libraries and global configurations.

- **Chapter 1: Dataset Loading, EDA & PCA Preprocessing**  
  Loads the UNSW-NB15 dataset, performs exploratory data analysis, handles categorical features with one-hot encoding, and applies PCA for dimensionality reduction and data scaling. It also uses SMOTE for handling class imbalance.

- **Chapter 2: Quantum Circuit Construction**  
  Details the angle encoding strategy and constructs the physics-informed Ising ansatz, explaining its components and physical interpretation.

- **Chapter 3: Variational Training Loop (Parameter-Shift + ADAM)**  
  Implements the parameter-shift rule for gradient calculation and trains the PI-VQC using the ADAM optimizer with mini-batch training.

- **Chapter 4: Quantum Kernel SVM Baseline**  
  Establishes a quantum kernel SVM baseline for comparison, alongside a classical SVM.

- **Chapter 5: Noise Simulation (NISQ Realism)**  
  Introduces a NISQ noise model (depolarizing and readout errors) and evaluates the PI-VQC's performance under noisy conditions.

- **Chapter 6: Results, Plots & Comparison Table**  
  Presents training convergence plots, confusion matrices, a comprehensive comparison table of all models, and a decision boundary visualization.

- **Chapter 7: Discussion & Conclusions**  
  Summarizes findings, revisits research gaps, discusses limitations, and outlines future work.

Execute the cells sequentially to reproduce the analysis and results.

---

# Disclaimer
This notebook incorporates **Artificial Intelligence (AI)** tools to assist with research, data exploration, and mathematical analysis.  
While AI can enhance productivity, all results, interpretations, and conclusions presented remain the responsibility of the author.  
Users are encouraged to independently verify any outputs.
