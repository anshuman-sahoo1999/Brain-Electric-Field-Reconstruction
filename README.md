# 🧠 Electro-Diffusion Physics-Informed Neural Network (ED-PINN)  
### for 3D Brain Electric Field Reconstruction from EEG Signals

**Author:**  
**Anshuman Sahoo**  
M.Tech — Computer Science & Engineering  
School of Engineering & Technology, DRIEMS University, India  
R&D Division, Ecometrix Consultants Pvt. Ltd.  
📧 *anshuman.sahoo1999@gmail.com*

---

## 📄 Thesis Title
**“Electro-Diffusion Physics-Informed Neural Network for 3D Brain Electric Field Reconstruction from EEG Signals”**

---

## 🧩 Abstract
Accurate reconstruction of brain electric potentials from scalp EEG signals remains a fundamental challenge in computational neuroengineering due to the ill-posed nature of the EEG inverse problem and the heterogeneous conductivity of head tissues.  
This work proposes a **Physics-Informed Neural Network (PINN)** architecture that embeds the **quasi-static Maxwell electro-diffusion equation**:

\[
\nabla \cdot (\sigma \nabla \phi) = -I
\]

within a deep neural model. The proposed **Electro-Diffusion PINN (ED-PINN)** directly learns the mapping between 3D spatial coordinates and electric potential values while enforcing physical consistency through PDE residuals, boundary conditions, and measured electrode data losses.

The system reconstructs volumetric potential fields (ϕ) and identifies localized neuronal sources (I) from sparse EEG measurements. Synthetic training data are generated using a realistic multi-layer spherical head model (brain, skull, scalp) and validated on open **PhysioNet EEG** datasets.  

Implemented entirely in **Google Colab (PyTorch)**, the ED-PINN framework provides interpretable, physics-consistent brain activity reconstructions—offering new potential for **seizure localization**, **brain-computer interfaces**, and **computational neurodiagnostics**.

---

## ⚙️ Methodology Overview
| Stage | Description |
|--------|--------------|
| 1. **Forward Model** | Simulated 3D head geometry (multi-layer conductivity) solved for ground-truth potentials via Poisson equation. |
| 2. **Data Generation** | Synthetic Gaussian dipole sources; EEG electrode potentials sampled on scalp surface. |
| 3. **Neural Network** | SIREN-based coordinate MLP mapping (x, y, z) → ϕ(x,y,z). |
| 4. **Physics Losses** | Combines electrode MSE, PDE residual, and Neumann boundary condition losses. |
| 5. **Training** | Hybrid Adam + autograd-based gradient computation with adaptive loss weighting. |
| 6. **Evaluation** | L² potential error, electrode fit, and source localization accuracy. |

---

## 🧠 Key Equation
\[
\nabla \cdot (\sigma(\mathbf{x}) \nabla \phi(\mathbf{x},t)) = -I(\mathbf{x},t)
\]
where  
- \( \sigma(\mathbf{x}) \): spatially varying conductivity (brain, skull, scalp)  
- \( \phi(\mathbf{x},t) \): electric potential field  
- \( I(\mathbf{x},t) \): impressed current source density  

---

## 🧮 Implementation
**Language:** Python 3 (Google Colab)  
**Framework:** PyTorch  
**Dependencies:** `torch`, `numpy`, `scipy`, `matplotlib`, `tqdm`  
**Dataset:** Synthetic spherical head simulation + PhysioNet EEG (optional)

---

## 🚀 How to Run
1. Open the notebook `ED_PINN_Brain_Reconstruction.ipynb` in Google Colab.  
2. Execute all cells sequentially:  
   - Cell 0–4: Environment setup and data generation  
   - Cell 5–6: Sampling electrodes and collocation points  
   - Cell 7–9: Model definition and training  
   - Cell 10–11: Evaluation and visualization  
3. (Optional) Save results to Google Drive.  

Outputs include:
- `phi_true.npy` → ground truth potential  
- `phi_pred_grid.npy` → reconstructed potential  
- `s_est.npy` → estimated source map  
- Visualization PNGs for slices, scalp fits, and residuals.

---

## 📊 Sample Results
- Achieved relative potential reconstruction error **< 0.12** on 32³ grid.  
- Source localization error **< 6 mm** after extended training.  
- Demonstrated robustness under 5% Gaussian noise on EEG measurements.  

---

## 📘 Citation
If you use or reference this work, please cite as:

> **A. Sahoo**, *“Electro-Diffusion Physics-Informed Neural Network for 3D Brain Electric Field Reconstruction from EEG Signals,”* M.Tech Thesis, School of Engineering & Technology, DRIEMS University, India, 2025.

---

## 📚 References
1. Raissi, M., Perdikaris, P., & Karniadakis, G. E. (2019). *Physics-informed neural networks: A deep learning framework for solving forward and inverse problems involving nonlinear PDEs.* Journal of Computational Physics.  
2. Hämäläinen, M., et al. (1993). *Magnetoencephalography—Theory, instrumentation, and applications to noninvasive studies of the working human brain.* Rev. Mod. Phys.  
3. Gramfort, A., et al. (2013). *MEG and EEG data analysis with MNE-Python.* Frontiers in Neuroscience.  

---

## 🧭 License
© 2025 **Anshuman Sahoo**  
This project is released for academic research use only. Reuse or publication requires author acknowledgment.

---
