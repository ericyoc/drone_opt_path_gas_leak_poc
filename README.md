# Hybrid Classical-Quantum Gas Leakage Detection with Drone Path Optimization

This repository implements a complete hybrid AI system combining classical machine learning and quantum-inspired optimization to detect gas pipeline leakages and coordinate drone response paths. The system leverages synthetic acoustic signals based on the GPLA-12 dataset and includes visualization, analytics, and animation.


## Motivating Research
J. Li and L. Yao, “Gpla-12: An acoustic signal dataset of gas pipeline leakage,” 2021.

https://www.researchgate.net/publication/354802112_GPLA-12_An_Acoustic_Signal_Dataset_of_Gas_Pipeline_Leakage 

## Why This Is Important

Gas leaks in pipelines can be hazardous to human health, safety, and the environment. Traditional manual inspection is time-consuming and lacks scalability. This hybrid system enables:

* **Scalable Automation**: Detect and respond to leaks across large areas using autonomous drones.
* **Early Warning Systems**: Rapid classification of high-pressure acoustic anomalies.
* **AI-Driven Efficiency**: Quantum-inspired TSP and Voronoi path planning improve coverage and reduce drone travel cost.
* **Explainable Intelligence**: Classical feature extraction ensures transparency and model interpretability.

---

## Use Cases

| Domain                | Application                                                                 |
| --------------------- | --------------------------------------------------------------------------- |
| Smart Infrastructure  | Monitor gas pipelines, sewer systems, and pressurized conduits              |
| Environmental Safety  | Detect methane or hazardous gas emissions in remote or urban environments   |
| Disaster Response     | Coordinate UAVs for leak inspection after earthquakes or industrial failure |
| Precision Agriculture | Detect toxic gas or irrigation system leaks                                 |
| Research & Simulation | Benchmark quantum-inspired optimization in AI safety systems                |

---

![Drone Mission Animation](drone_mission_animation.gif "Drone executing autonomous mission")

---

## Results Summary

**Best Test Accuracy**: 93.43% (Classical Neural Network)
**Hybrid Architecture**: 60% Classical + 40% Quantum
**Sample Count**: 684 synthetic acoustic samples across 12 classes

---

## Key Features

* End-to-end pipeline from data simulation to drone path animation
* Feature-rich classical models: Random Forest, SVM, Neural Network
* Quantum-inspired models for classification and drone optimization
* Quantum Voronoi-based drone region assignment
* Animated visualization of multi-drone mission paths

---

## Installation

This project is designed to run in Google Colab or locally with Python 3.8+.

```bash
git clone https://github.com/yourusername/hybrid-gas-leakage-detection.git
cd hybrid-gas-leakage-detection
pip install -r requirements.txt
```

---

## Running the System

```python
python hybrid_gas_leakage_system.py
```

Steps executed:

1. Mount Google Drive (if in Colab)
2. Download or generate the GPLA-12 synthetic dataset
3. Extract classical and quantum features
4. Train models and evaluate performance
5. Generate drone paths using quantum Voronoi + quantum TSP
6. Create animations and visual comparisons

---

## System Architecture

| Component          | Type      | Purpose                                                       |
| ------------------ | --------- | ------------------------------------------------------------- |
| Feature Extraction | Classical | Time, frequency, wavelet, and statistical feature engineering |
| Classification     | Classical | Random Forest, SVM, Neural Network                            |
| Classification     | Quantum   | Quantum-Inspired Classifier using angle encoding + circuits   |
| Drone Optimization | Quantum   | Quantum Voronoi site placement and TSP path planning          |

---

## Animation Generation

The system produces a **step-by-step animation of the drone mission** using Matplotlib’s animation module. The animation illustrates:

* Drone deployment to Voronoi-partitioned zones
* Individual waypoints and paths for each drone
* Leak intensity represented as background scatter
* Total mission progression over time

The animation is saved to Google Drive (if in Colab) as:

```
/content/drive/MyDrive/datasets/drone_mission_animation.gif
```

This visual output is essential for debugging drone path logic, analyzing quantum optimization convergence, and presenting mission dynamics clearly in academic or industrial reports.

---

## Performance Summary

| Model             | Type      | Test Accuracy |
| ----------------- | --------- | ------------- |
| ClassicalNN       | Classical | 93.43%        |
| SVM               | Classical | 89.05%        |
| Random Forest     | Classical | 87.59%        |
| QuantumClassifier | Quantum   | 11.68%        |
| HybridEnsemble    | Hybrid    | 91.97%        |

---

## Dataset: Synthetic GPLA-12

* 684 synthetic acoustic samples
* 1024-length signals simulating real gas pipeline leakage
* 12 classes derived from combinations of pressure, noise, and microphone

Each signal includes:

* Modulated base frequencies
* Harmonics
* Noise perturbations
* Microphone-specific adjustments

---

## Visual Outputs

* Model training curves (accuracy & loss)
* Bar charts of model comparison
* Quantum optimization convergence plots
* Voronoi region mapping and drone waypoints
* Real-time drone animation


## Disclaimer
This project is intended for academic and research purposes only.
It is not certified or approved for real-world deployment in safety-critical infrastructure or commercial drone navigation systems.
Use at your own risk and ensure compliance with local regulations and safety standards when adapting this code for testing or experimentation.

---

## License

MIT License

---

