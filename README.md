
# Hybrid Quantum-Classical Path Optimization for Multi-Drone Gas Leak Detection

This repository hosts a hybrid AI framework designed for rapid gas leak detection using autonomous UAV (drone) fleets. By combining **Quantum-Inspired Heuristics** with **Classical Path Planning**, the system optimizes for **Time-to-Detection (TTD)** over standard area coverage.



---

## 🛠 Project Overview
Traditional drone monitoring focuses on uniform area coverage, which is often too slow for emergency response. This framework uses a **Hybrid Partition-and-Routing** approach:
1.  **Quantum-Inspired Clustering (QUBO)**: Partitioning the search space based on hazard intensity.
2.  **Classical 2-Opt TSP**: Rapidly routing drones through high-risk waypoints.

---

## 🧪 Stage I: Synthetic Validation (Proof of Concept)
In the initial development phase, the framework was validated using a controlled synthetic environment to benchmark the **Quadratic Unconstrained Binary Optimization (QUBO)** formulation against standard random walk and greedy heuristics.

### Synthetic Environment Parameters
* **Area Size**: $1000m \times 1000m$
* **Target Distribution**: Multi-modal Gaussian hotspots.
* **Drone Fleet**: 3 to 5 drones with limited endurance.

### Performance on Synthetic Data
| Algorithm | Avg. Compute Time (s) | Path Efficiency | Convergence Rate |
| :--- | :--- | :--- | :--- |
| Random Walk | 0.01s | 12.5% | N/A |
| Classical Greedy | 0.45s | 78.2% | 100% |
| **Hybrid QUBO (Simulated)** | **0.12s** | **89.5%** | **98.4%** |

---

## 📈 Stage II: Real-World Proxy Validation (GPLA-12)
To simulate a real-world industrial environment, the system utilizes the **GPLA-12 Acoustic Dataset**. While the routing is "payload-agnostic," the acoustic data provides a realistic distribution of leak severities and noise interference.



### The "M3" Baseline Comparison
A critical addition to our research was **Method 3 (M3)**: an Intensity-Weighted K-Means algorithm. This ensured the Hybrid Q-C model was compared against the strongest possible classical heuristic.

| Metric | M1 (Random) | M2 (K-Means) | M3 (IW K-Means) | **Hybrid Q-C** |
| :--- | :--- | :--- | :--- | :--- |
| **Mean TTD (s)** | 66.2s | 45.1s | 43.9s | **10.0s** |
| **HR Leak TTD (s)** | 64.8s | 42.1s | 40.7s | **9.4s** |
| **Compute Time** | 0.02s | 1.80s | 2.67s | **0.21s** |
| **Speedup vs M3** | - | - | 1.0x | **12.7x** |

### Statistical Rigor
* **$p$-values**: All results are statistically significant ($p \le 0.0002$ via Mann-Whitney U tests).
* **Reproducibility**: Fixed seeds (`numpy=42`, `tensorflow=42`) ensure consistent results across runs.

---

## 🚁 Drone Mission Visualization
The system generates a dynamic mission map where drone responsibilities are divided using a **Quantum-inspired Voronoi** partition.



> **Figure 1**: The background heatmap represents normalized leak intensity. White lines represent the boundaries of the Voronoi cells calculated via QUBO, and the colored paths show the optimized 2-opt TSP routes for the 7-drone fleet.

---

## 🔑 Key Features
* **Trainable Quantum-Inspired Classifier**: Achieves **89.05% accuracy** using angle encoding and variational layers.
* **QUBO Scaling**: Analyzes problem growth from 2,052 to 13,680 binary variables.
* **Payload-Agnostic Routing**: Compatible with optical, electrochemical, or acoustic sensors.
* **Real-time Animation**: Automatically generates `drone_mission_animation.gif` for mission debriefing.

---

## 🚀 Installation & Usage

### 1. Clone the Repo
```bash
git clone https://github.com/yourusername/hybrid-gas-leak-detection.git
cd hybrid-gas-leak-detection
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the Simulation
You can run the full pipeline (from data loading to animation) via the main script:
```python
python hybrid_gas_leakage_system.py
```

---
**Disclaimer**: This project is for research purposes. All "Quantum" results are produced using classical simulation of quantum heuristics.
