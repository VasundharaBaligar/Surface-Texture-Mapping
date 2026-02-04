# Surface Texture Mapping & Neural Mesh Transfer

![Status](https://img.shields.io/badge/Status-Research_Showcase-blue)
![Domain](https://img.shields.io/badge/Domain-Medical_Imaging_%7C_3D_Vision-green)
![Tech](https://img.shields.io/badge/Tech-Neural_Fields_%7C_Python-orange)

> **Note:** This repository serves as a documentation and result showcase for a research project on 3D surface mapping. Due to intellectual property constraints and the reliance on proprietary medical datasets, the source code is not publicly available.

## 📄 Abstract

Surface texture mapping is a critical task in computer graphics and medical imaging, allowing for the transfer of surface properties (appearance, texture, and fine geometry) from a source model to a target model. This project investigates and implements advanced parametrization-free techniques to solve the mapping problem between non-isometric shapes.

Specifically, we compare **Adaptive Triangularization** against **Mesh Draping (Neural Mesh Transfer)**. While traditional methods struggle with complex topologies, this research demonstrates the efficacy of Neural Fields (specifically Progressive Positional Encodings) in transferring fine-grained geometric details onto anatomical structures, such as **Brain Ventricles**.

## 🔬 Methodology

We explored two distinct approaches to solving the surface mapping problem:

### 1. Adaptive Triangularization (Geometry-Based)
* **Concept:** Computes bijective maps between genus-0 surfaces using common triangulations.
* **Process:** Discretizes maps while maintaining bijective correspondence via spherical embeddings.
* **Limitation:** Computationally expensive for high-resolution meshes and struggles with highly non-isometric deformations.

### 2. Mesh Draping (Deep Learning-Based)
* **Concept:** A parametrization-free method that "drapes" a source mesh over a target using a neural network.
* **Core Architecture:** Utilizes **Implicit Neural Representations** and **Progressive Positional Encodings (PE)**.
* **Advantage:** The progressive PE allows the network to capture high-frequency details (tiny geometric features) that standard fully connected networks often smooth over.

![Methodology Comparison](assets/methodology_diagram.png)
*Figure 1: Visual comparison of the Adaptive Triangularization pipeline vs. the Neural Mesh Draping workflow.*

---

## 🧠 Application: Medical Anatomy

The primary contribution of this research was the application of these techniques to **Artificial Human Organ Modeling**.

* **Dataset:** 3D Meshes of Human Brain Ventricles.
* **Goal:** Map the surface texture and anomalies of a *known/scanned* ventricle model onto a *generic/artificial* ventricle model.
* **Implementation:** * Automated the key-point mapping process between Source (Incomplete Ventricle) and Target.
    * Optimized the neural network to minimize distortion during the transfer of ventricle walls.

## 📊 Results

We evaluated the performance on both standard graphical objects (ShapeNet) and medical data.

### 1. General Shape Transfer
Comparison of texture transfer on standard non-rigid shapes.

| Source Mesh | Target Mesh | Result (Mesh Draping) |
| :---: | :---: | :---: |
| ![Plane Source](assets/plane_source.png) | ![Plane Target](assets/plane_target.png) | ![Plane Result](assets/plane_result.png) |

### 2. Brain Ventricle Mapping
Transferring surface details from a specific patient scan to a generic model.

| Source (Patient Scan) | Target (Template) | Draped Output |
| :---: | :---: | :---: |
| ![Ventricle Source](assets/ventricle_source.png) | ![Ventricle Target](assets/ventricle_target.png) | ![Ventricle Result](assets/ventricle_result.png) |

*Figure 2: The Neural Mesh Draping method successfully preserves the local curvature of the brain ventricle while adhering to the target topology.*

---

## 🛠️ Key Contributions

* **Comparative Analysis:** Conducted a rigorous comparison between geometry-based remeshing and neural-based draping.
* **Pipeline Optimization:** Implemented an automated key-point saving mechanism in the Mesh Draping codebase to streamline the iterative training process.
* **Medical Adaptation:** Successfully tuned the frequency bands of the Positional Encoding to handle the smooth, organic curvature of biological tissues (ventricles) rather than just sharp mechanical objects.

## 📚 References

This work is based on and extends the following papers:

1.  **Mesh Draping:** Hertz, A., Perel, O., Giryes, R., Sorkine-Hornung, O., & Cohen-Or, D. (2022). *Mesh Draping: Parametrization-Free Neural Mesh Transfer*.
2.  **Adaptive Triangularization:** Schmidt, P., Pieper, D., & Kobbelt, L. (2023). *Surface Maps via Adaptive Triangulations*.

## 📬 Contact

For inquiries regarding the implementation details or the medical dataset usage, please contact:

**Vasundhara V. Baligar** [Your Email / LinkedIn Link]
