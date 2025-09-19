# TSP_QAOA
Traveling salesman problem using QAOA
Solving the Traveling Salesman Problem with QAOA using Qiskit
This repository contains a Jupyter Notebook demonstrating how to solve the Traveling Salesman Problem (TSP) using the Quantum Approximate Optimization Algorithm (QAOA). The implementation utilizes Python, with Qiskit for quantum circuit simulation and qiskit_optimization for problem modeling.

📝 Overview
The Traveling Salesman Problem is a notorious NP-hard problem in combinatorial optimization. The goal is to find the shortest possible route that visits a set of cities and returns to the origin city, visiting each city exactly once.

This project leverages quantum computing principles to tackle the TSP:

The problem is first defined classically using a graph structure from the NetworkX library.

It's then converted into a Quadratic Unconstrained Binary Optimization (QUBO) problem using qiskit_optimization.

This QUBO is mapped to an Ising Hamiltonian, whose ground state (lowest energy state) corresponds to the optimal solution of the TSP.

The QAOA, a hybrid quantum-classical algorithm, is used to prepare and find this ground state.

A classical optimizer (COBYLA) fine-tunes the QAOA circuit parameters to minimize the Hamiltonian's energy.

Finally, the optimized quantum circuit is run on a Qiskit AerSimulator, and the most probable result is decoded to find the shortest tour.

⚛️ The Quantum Approach: QAOA
The Quantum Approximate Optimization Algorithm (QAOA) is a hybrid algorithm designed to find approximate solutions to combinatorial optimization problems. It works by preparing a quantum state that encodes the solution through a sequence of operations guided by a classical optimizer.

The workflow is as follows:

Problem Mapping: The TSP, with its cities and distances, is translated into a cost function. This function is then mapped to an Ising Hamiltonian (H_P). The quantum state with the lowest energy (ground state) for this Hamiltonian represents the optimal path for the salesman.

QAOA Ansatz: A parameterized quantum circuit, known as an ansatz, is created. It consists of alternating layers of two operators:

Cost Hamiltonian (e 
−iγH_P
 ): Encodes the problem's cost function. The parameter γ (gamma) is optimized.

Mixer Hamiltonian (e 
−iβH_M
 ): Allows the quantum system to explore different possible solutions. The parameter β (beta) is also optimized.

Classical Optimization: A classical computer repeatedly runs the quantum circuit and measures the resulting energy. It uses an optimization algorithm (like COBYLA) to adjust the γ and β parameters, trying to find the combination that minimizes the energy.

Solution Extraction: Once the optimal parameters are found, the quantum circuit is run one final time with a large number of "shots." The most frequently measured bitstring is the most likely solution to the problem. This bitstring is then decoded back into a human-readable tour of the cities.

🚀 Getting Started
Prerequisites
Make sure you have Python 3.8 or later installed. The required libraries are listed below.
qiskit
qiskit-optimization
qiskit-aer
numpy
networkx

matplotlib

scipy
