# Neural Mesh Draping for Anatomical Completion

![Status](https://img.shields.io/badge/Status-Research_Showcase-blue)
![Domain](https://img.shields.io/badge/Domain-Medical_Imaging_%7C_3D_Vision-green)
![Tech](https://img.shields.io/badge/Tech-Neural_Fields_%7C_Python-orange)

> **Note:** This repository showcases a research project on completing partial 3D medical scans. Due to the confidential nature of the medical datasets and pending publication, the source code is not publicly available.

## 🎯 Problem Statement: The "Impossible" Replication
Replicating and analyzing human anatomical structures—specifically **Brain Ventricles**—is notoriously difficult. 
* **The Challenge:** Medical scans (MRI/CT) often result in **incomplete meshes** or "partial point clouds" due to occlusion, scanning noise, or complex organic geometries.
* **The Goal:** We needed a way to take a **broken/incomplete patient scan** and "complete" it by mapping it onto a pristine anatomical template, without losing the patient-specific deformities.

## 💡 Solution: Neural Mesh Draping
Standard geometric methods fail here because they require perfect, watertight meshes to work. We instead utilized **Mesh Draping (Neural Mesh Transfer)**.

This technique uses a **parametrization-free neural network** to "drape" the incomplete source geometry over a complete target template. It essentially "learns" the missing topology from the template while preserving the fine surface details of the patient.

---

## 📸 Research Results

### 1. Brain Ventricle Completion
The core success of this project was recovering the full shape of a human brain ventricle from partial data.

* **Input (Source):** An incomplete/broken mesh of a patient's ventricle.
* **Target (Template):** A generic, complete ventricle model.
* **Output:** A fully reconstructed, water-tight ventricle that retains the patient's specific surface features.

![Brain Ventricle Completion](assets/ventricle_results.png)
*(Figure: The Neural Mesh Draping pipeline successfully completing the missing regions of the brain ventricle scan.)*

### 2. Proof of Concept (ShapeNet)
Before applying the method to medical data, we validated the "draping" capability on standard non-rigid shapes to ensure high-frequency detail preservation.

![Standard Shape Validation](assets/draping_results.png)
*(Figure: Validating the transfer of fine geometric details (e.g., feathers, engines) on standard 3D objects.)*

---

## 🛠️ Methodology & Contributions

### Why Mesh Draping?
We moved away from traditional algorithms (like Adaptive Triangularization, which we surveyed but discarded) because they struggle with **non-isometric shapes** and **incomplete topology**.

**My Technical Contributions:**
1.  **Automated Key-Point Mapping:**
    * The original Mesh Draping implementation required manual alignment for every new pair of shapes.
    * I engineered an automated routine to detect, save, and map key correspondence points between the medical source and the template. This allowed us to run the pipeline on multiple patient scans without manual intervention.
2.  **Medical Domain Adaptation:**
    * Tuned the **Progressive Positional Encodings (PE)** to handle the smooth, organic curvature of biological tissue, ensuring the network didn't introduce artificial "sharpness" or noise into the medical model.

## 📚 References
This work builds upon the architecture proposed in:
* Hertz, A., et al. (2022). *Mesh Draping: Parametrization-Free Neural Mesh Transfer*.

## 👥 Contributors
* **Vasundhara Baligar**
* **Pratham Shanbhag**
* **Guidance:** Prof. Subodh Kumar, Mr. Sukhraj Singh
