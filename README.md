# Kolmogorov–Arnold Networks (KAN)

This repository collects research, code, and results on **Kolmogorov–Arnold Networks (KANs)**.  
KANs place learnable univariate basis functions on edges and have emerged as a promising alternative to MLPs and PINNs, showing advantages in accuracy, convergence, and interpretability across tasks such as regression, function approximation, and PDE solving.

---

## 📂 Repository Structure

The repository is organized into modules. Each folder contains a self-contained project with its own documentation, results, and code.

- `choose-your-kan/`  
  Companion materials for the review paper *“Choose–Your–KAN”*, including figures, results, references, and a practical guide to basis functions, accuracy/efficiency improvements, and convergence studies.

- `chebykan/` *(planned)*  
  Implementations and experiments with **Chebyshev-based KANs**, including recurrence forms, grid-based designs, finite-basis expansions, and PDE applications.


---

## 📊 Comparison of Basis Functions in KANs

| Name                | Support | Equation Form                                                           | Grid Required | Basis / Activation              | Reference      |
|---------------------|---------|------------------------------------------------------------------------|---------------|---------------------------------|----------------|
| **B-spline**        | Local   | $\sum_n c_n B_n^{(k)}(x)$                                              | Yes           | B-spline (Tanh, Sigmoid)        | Liu (2024)     |
| **Chebyshev**       | Global  | $\sum_k c_k T_k(\tanh(x))$                                             | No            | Chebyshev + Tanh                | SS (2024)      |
| **Chebyshev (grid)**| Global  | $\sum_k c_k T_k\left(\tfrac{1}{m}\sum_i \tanh(w_i x + b_i)\right)$     | Yes           | Chebyshev + averaged Tanh grid  | Toscano (2024) |
| **ReLU-KAN**        | Local   | $\sum_i w_i R_i(x)$                                                    | Yes           | Squared ReLU                    | Qiu (2024)     |
| **HRKAN**           | Local   | $\mathrm{ReLU}^m(x)\cdot \mathrm{ReLU}^m(e-x)$                         | Yes           | Polynomial ReLU                 | So (2024)      |
| **Adaptive ReLU-KAN** | Local | HRKAN + adaptive grid                                                  | Yes           | Adaptive ReLU                   | Rigas (2024)   |
| **fKAN (Jacobi)**   | Global  | $J_n^{(\alpha,\beta)}(\phi_\gamma(\sigma(x)))$                         | No            | Jacobi (via Sigmoid)            | Aghaei (2024)  |
| **rKAN (Padé/Jacobi)** | Global | Rational Jacobi compositions                                          | No            | Rational + Jacobi               | Aghaei (2024)  |
| **Jacobi-KAN**      | Global  | $\sum_i \lambda_i P_i^{(\alpha,\beta)}(\tanh(x))$                      | No            | Jacobi + Tanh                   | Kashefi (2025) |
| **FourierKAN**      | Global  | $\sum_k a_k \cos(kx) + b_k \sin(kx)$                                   | No            | Fourier (trigonometric)         | Xu (2025)      |
| **KAF**             | Global  | $\alpha\,\mathrm{GELU}(x)+\beta\,V\,\psi_{\mathrm{RFF}}(x)$            | No            | RFF + GELU hybrid               | Zhang (2025)   |
| **Gaussian**        | Local   | $\sum_i w_i \exp\left(-\left(\tfrac{x-g_i}{\varepsilon}\right)^2\right)$ | Yes           | Gaussian RBF                    | Li (2024)      |
| **CVKAN**           | Local   | $\sum_{u,v} w_{uv} \exp\left(-\lvert z - g_{uv}\rvert^2\right)$      | Yes           | Complex Gaussian (CSiLU)        | Wolff (2025)   |
| **BSRBF-KAN**       | Local   | $w_b b(x) + w_s \left(BS(x) + RBF(x)\right)$                           | Yes           | B-spline + Gaussian             | Ta (2024)      |
| **Wav-KAN**         | Local   | $\psi_s\left(\tfrac{x-\tau}{s}\right)$                                 | No            | Wavelet (DoG, Morlet, etc.)     | Bozorgasl (2024) |
| **FBKAN**           | Local   | $\sum_j \omega_j(x) K_j(x)$                                            | Yes           | Cosine + B-spline               | Howard (2024)  |
| **SincKAN**         | Global  | $\sum c_i \,\mathrm{Sinc}\left(\tfrac{\pi}{h}(x - ih)\right)$          | Yes           | Sinc                            | Yu (2024)      |
| **Poly-KAN**        | Global  | $\sum_i w_i P_i(x)$                                                    | No            | Polynomial (Jacobi, Meixner)    | Seydi (2024)   |

---

## 🚀 Getting Started

Clone the repository:
```bash
git clone https://github.com/AmirNoori68/KAN.git
cd KAN
