# Neural Mesh Draping for Anatomical Completion

![Status](https://img.shields.io/badge/Status-Research_Showcase-blue)
![Domain](https://img.shields.io/badge/Domain-Medical_Imaging_%7C_3D_Vision-green)
![Tech](https://img.shields.io/badge/Tech-Neural_Fields_%7C_Python-orange)

> **Note:** This repository showcases a research project conducted during my summer internship at **IIT Delhi** (Department of Computer Science & Engineering). Due to lab protocols and pending publication, the source code is currently private.

## 🎯 Problem Statement: The "Impossible" Replication
Replicating and analyzing human anatomical structures, specifically **Brain Ventricles** is notoriously difficult. 
* **The Challenge:** Medical scans (MRI/CT) often result in **incomplete meshes** or "partial point clouds" due to occlusion, scanning noise, or complex organic geometries.
* **The Goal:** We needed a way to take a **broken/incomplete scan** and "complete" it by mapping it onto a pristine anatomical template, without deformations.

## 💡 Solution: Neural Mesh Draping
Standard geometric methods fail here because they require perfect, watertight meshes to work. We instead utilized **Mesh Draping (Neural Mesh Transfer)**.

This technique uses a **parametrization-free neural network** to "drape" the incomplete source geometry over a complete target template. It essentially "learns" the missing topology from the template while preserving the fine surface details of the patient.

---

## 📸 Research Results

### 1. Brain Ventricle Completion
The core success of this project was recovering the full shape of a human brain ventricle from partial data.

* **Input (Source):** An incomplete/broken mesh of ventricle.
* **Target (Template):** A generic, complete ventricle model.
* **Output:** A fully reconstructed, water-tight ventricle that retains the specific surface features.

## 📸 Research Results: Anatomical Completion

### 1. Input: Incomplete Source Mesh
The raw input mesh often contains missing geometry and broken topology, making standard analysis impossible.

![Input Scan](ip.png)

### 2. Output: Neural Reconstruction
Our **Mesh Draping** pipeline "drapes" the template over the incomplete input. It adapts the geometry and recovers the full shape while perfectly preserving the unique curvature and fine details of the original source.

![Output Result](op.png)

---

## 🛠️ Methodology & Contributions

### Why Mesh Draping?
We moved away from traditional algorithms (like Adaptive Triangularization, which we surveyed but discarded) because they struggle with **non-isometric shapes** and **incomplete topology**.

## Extensions

We augmented the baseline *Mesh Draping* implementation to address the specific constraints of medical imaging:

1.  **Automated Key-Point Registration:** To overcome the bottleneck of manual alignment in the original implementation, we integrated a routine that automatically maps and persists correspondence points between the source scan and the template.
2.  **Scalability:**
    This addition allows the pipeline to generalize across multiple patient datasets without requiring "human-in-the-loop" annotation for each iteration.


## 📚 References
This work builds upon the architecture proposed in:
* Hertz, A., et al. (2022). *Mesh Draping: Parametrization-Free Neural Mesh Transfer*.
