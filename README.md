
# Hybrid Quantum-Classical Path Optimization for Multi-Drone Gas Leak Detection

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

This repository implements a **Hybrid Partition-and-Routing Heuristic** that combines classical machine learning with quantum-inspired optimization (QUBO) to coordinate drone fleets for industrial gas leak detection. 

The framework optimizes for **Time-to-Detection (TTD)**, significantly outperforming standard coverage-based methods in emergency response scenarios.

---

## 🛠 System Architecture

The system follows a modular hybrid pipeline:

1.  **Quantum-Inspired Classifier**: Uses **Angle Encoding** and variational circuits to identify leak severity from raw sensor data.
2.  **Quantum Voronoi Partitioning**: Formulates a **Quadratic Unconstrained Binary Optimization (QUBO)** problem to assign drone deployment sites based on the severity heatmap.
3.  **Classical Path Generation**: Utilizes a **2-Opt TSP** heuristic to plan the exact flight path for each drone within its assigned partition.

---

## 📊 Data Sources & Methodology

This project utilizes a two-tier validation strategy to transition from theoretical optimization to industrial application.

### 1. Stage I: Synthetic Validation
Initial benchmarking was performed using a synthetic "Hazard Topology" in a simulated $1000m \times 1000m$ environment. 
* **Purpose:** To isolate the performance of the QUBO solver and verify convergence across different fleet sizes (5–20 drones).
* **Generation:** Multi-modal Gaussian distributions create "ground truth" leak intensities.

### 2. Stage II: Real-World Proxy (GPLA-12)
Final validation uses the **GPLA-12 Acoustic Signal Dataset** to provide realistic hazard inputs.
* **Source:** Collected by researchers at the University of Adelaide. [Reference: Li & Yao, 2021]
* **Composition:** 684 samples across 12 classes simulating various pipeline pressures and leakage types.
* **Role:** Acoustic signals are processed through the hybrid ensemble to generate the severity scores that drive the spatial optimization.

---

## 📈 Performance Results

The framework was benchmarked against three classical baselines. **Method 3 (M3)** is a high-performance, intensity-weighted K-Means algorithm used to ensure a fair comparison with the proposed model.

### Comparative Analytics (7-Drone Fleet)

| Metric | M1 (Random) | M2 (K-Means) | M3 (IW K-Means) | **Hybrid Q-C (Ours)** |
| :--- | :--- | :--- | :--- | :--- |
| **Mean TTD (s)** | 66.2s | 45.1s | 43.9s | **10.0s** |
| **High-Risk TTD (s)** | 64.8s | 42.1s | 40.7s | **9.4s** |
| **Compute Time (s)** | 0.02s | 1.80s | 2.67s | **0.21s** |
| **Speedup vs M3** | - | - | 1.0x | **12.7x** |

**Statistical Note:** Results are averaged over $n=10$ runs with fixed seeds (`numpy=42`, `tensorflow=42`). The speedup is statistically significant ($p \le 0.0002$ via Mann-Whitney U tests).

---

## 📽 Visualizations

The system provides several layers of visualization to interpret the optimization results:

* **Hazard Heatmaps**: Visualizes the density of the GPLA-12 derived leak spots.
* **Voronoi Cells**: Displays the QUBO-derived boundaries for drone responsibility.
* **Mission Animation**: A real-time `.gif` showing drones traversing optimized paths.

*(Note: In the provided source code, animations are saved as `drone_mission_animation.gif` for mission debriefing.)*

---

## 🚀 Installation & Usage

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/hybrid-gas-leakage-detection.git
cd hybrid-gas-leakage-detection
```

### 2. Install Requirements
```bash
pip install -r requirements.txt
```

### 3. Run the Simulation
The full end-to-end pipeline (data processing → optimization → animation) is contained in the main script:
```python
python hybrid_gas_leakage_system.py
```

---

## 📜 Citations & Credits

### Original Dataset
If you use the GPLA-12 data, please cite:
> Li, J., & Yao, L. (2021). **GPLA-12: An Acoustic Signal Dataset of Gas Pipeline Leakage.** arXiv preprint arXiv:2106.10277. [Source](https://arxiv.org/abs/2106.10277)

---

## ⚠️ Disclaimer
This project is an **algorithmic proof-of-concept**. All "Quantum" components are currently executed via **classical simulation** of quantum heuristics. It is intended for academic research and is not certified for deployment in safety-critical industrial infrastructure.

## 📄 License
This project is licensed under the **MIT License**. See the `LICENSE` file for details.
