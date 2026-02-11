# 🧬 Quantum-Enhanced LABS Optimization — Team Beerantum

> **NVIDIA iQuHACK 2026 Challenge Submission**
> Hybrid quantum-classical approach to the Low Autocorrelation Binary Sequences (LABS) problem using NVIDIA CUDA-Q

[![CUDA-Q](https://img.shields.io/badge/CUDA--Q-v0.13.0-76B900?style=flat&logo=nvidia)](https://nvidia.github.io/cuda-quantum/latest/)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)](https://python.org)
[![iQuHACK 2026](https://img.shields.io/badge/iQuHACK-2026-purple.svg)](https://github.com/iQuHACK/2026-NVIDIA)
[![Fork](https://img.shields.io/badge/Fork_of-iQuHACK%2F2026--NVIDIA-blue.svg)](https://github.com/iQuHACK/2026-NVIDIA)

---

## Overview

This is **Team Beerantum's** official submission fork for the [NVIDIA iQuHACK 2026 Challenge](https://github.com/iQuHACK/2026-NVIDIA) at MIT. All deliverables are located in the [`team-submissions/`](./team-submissions) directory.

The challenge tackles the **Low Autocorrelation Binary Sequences (LABS)** problem — a notoriously hard combinatorial optimization problem with critical applications in radar systems and telecommunications. Our approach evolves the classical state-of-the-art **Memetic Tabu Search (MTS)** into a **hybrid quantum-enhanced workflow**, where quantum algorithm samples seed the classical MTS population, accelerated end-to-end with **NVIDIA CUDA-Q** and GPU compute.

## The LABS Problem

Given a binary sequence $S = \{s_1, s_2, \dots, s_N\}$ where $s_i \in \{-1, +1\}$, the goal is to minimize the **energy function** (sum of squared autocorrelations):

$$E(S) = \sum_{k=1}^{N-1} C_k^2, \quad \text{where} \quad C_k = \sum_{i=1}^{N-k} s_i \cdot s_{i+k}$$

Equivalently, we maximize the **merit factor**:

$$F(S) = \frac{N^2}{2E(S)}$$

Finding optimal sequences is computationally intractable for large $N$ — the search space grows as $2^N$ and the problem is known to be NP-hard.

## Approach

Our hybrid strategy combines quantum sampling with classical local search:

1. **Quantum Seed Generation** — Use quantum algorithms (implemented in CUDA-Q) to produce diverse, high-quality initial candidate sequences that explore the solution landscape more broadly than random initialization.
2. **Classical Memetic Tabu Search** — Feed quantum-generated seeds into an enhanced MTS algorithm that performs deep local search with tabu constraints to avoid cycling.
3. **GPU Acceleration** — Leverage NVIDIA GPUs to accelerate both the quantum circuit simulation and the classical search components, enabling scaling to larger sequence lengths.

## Submission Structure

All team deliverables are in the `team-submissions/` directory:

```
team-submissions/
│
├── Phase 1/                                        # Prototyping & CPU validation (qBraid)
│   ├── auxiliary_files/                             # Supporting data and helper files
│   ├── images/
│   │   └── 01_quantum_enhanced_optimization_LABS/   # Figures and plots from the tutorial
│   ├── 01_quantum_enhanced_optimization_LABS_complete_final_Beerantum.ipynb
│   │                                                # Main notebook: completed LABS tutorial
│   └── PRD-Beerantum.md                             # Product Requirements Document / research plan
│
├── Phase 2/                                         # GPU acceleration & deployment (Brev)
│   ├── auxiliary_files/                              # Supporting data and helper files
│   ├── Step A.ipynb                                  # Quantum algorithm implementation
│   ├── Step C GPU Acceleration of the classical algorithm.ipynb
│   │                                                 # GPU-accelerated MTS implementation
│   ├── GPU Acceleration and Hardware Migration.ipynb  # Brev migration & hardware benchmarks
│   ├── tests.py                                      # Unit tests and validation suite
│   ├── Beerantum_Presentation.pptx                   # Final showcase presentation
│   ├── AI_REPORT.md                                  # AI-driven workflow report
│   ├── message_AI_report_complementary.txt            # Supplementary AI workflow notes
│   ├── Drive and material.md                          # Links to shared resources and materials
│   └── README.md                                      # Phase 2 specific documentation
│
└── README.md                                         # Deliverables checklist (original)
```

### Phase 1 — Prototyping on qBraid

Milestones completed during this phase:

- **Ramp Up**: Completed the scaffolded LABS tutorial (`01_quantum_enhanced_optimization_LABS_complete_final_Beerantum.ipynb`), mastering the state-of-the-art Memetic Tabu Search algorithm and the LABS optimization landscape.
- **Research & Plan**: Produced a detailed Product Requirements Document (`PRD-Beerantum.md`) outlining our quantum strategy, ansatz selection, parameter optimization approach, and GPU deployment architecture.

### Phase 2 — GPU Acceleration on Brev

Milestones completed during this phase:

- **Build**: Implemented the hybrid quantum-enhanced algorithm across multiple notebooks — quantum algorithm design (`Step A.ipynb`), GPU-accelerated classical search (`Step C GPU Acceleration of the classical algorithm.ipynb`), and hardware migration to NVIDIA Brev (`GPU Acceleration and Hardware Migration.ipynb`). Validated with automated tests (`tests.py`).
- **Showcase & Retrospective**: Delivered a final presentation (`Beerantum_Presentation.pptx`), documented the AI-assisted development workflow (`AI_REPORT.md`), and compiled performance benchmarks across GPU architectures (L4, T4, A100).

## Tech Stack

| Component | Technology |
|-----------|------------|
| Quantum Programming | [NVIDIA CUDA-Q](https://nvidia.github.io/cuda-quantum/latest/) v0.13.0 |
| Prototyping Platform | [qBraid](https://account-v2.qbraid.com/) |
| GPU Deployment | [NVIDIA Brev](https://brev.nvidia.com/) |
| Language | Python 3.10+ |
| Notebooks | Jupyter |

## Getting Started

### Prerequisites

- Python 3.10+
- NVIDIA CUDA-Q v0.13.0+
- (Optional) Access to NVIDIA GPU for accelerated simulation

### Running Locally

```bash
# Clone the repository
git clone https://github.com/Akri-A/2026-NVIDIA.git
cd 2026-NVIDIA/team-submissions

# Install CUDA-Q (see https://nvidia.github.io/cuda-quantum/latest/install.html)
pip install cuda-quantum

# Navigate to the desired phase and open the notebooks
jupyter notebook
```

### Running on qBraid

1. Visit [qBraid](https://account-v2.qbraid.com/) and create an account.
2. Clone this repo in the qBraid environment.
3. Ensure the `CUDA-Q (v0.13.0)` environment is installed.
4. Set the notebook kernel to `Python 3 [cuda q-v0.13.0]`.

## Team Beerantum 🍺⚛️

We are **Beerantum Research** — a quantum computing team passionate about pushing the boundaries of hybrid quantum-classical optimization.

## Challenge Context

This project was developed during **MIT iQuHACK 2026** (January 31 – February 1, 2026), the seventh edition of MIT's interdisciplinary quantum computing hackathon. The NVIDIA challenge emphasized an agentic, AI-assisted development workflow where teams operated as Technical Leadership — decomposing the problem, delegating across team members and AI agents, and verifying results.

This repository is a fork of the [official NVIDIA challenge repo](https://github.com/iQuHACK/2026-NVIDIA), with our team's deliverables added to the `team-submissions/` directory as required by the submission guidelines.

## Acknowledgments

- **NVIDIA** for designing the LABS challenge and providing CUDA-Q, Brev GPU resources, and mentorship.
- **qBraid** for the zero-setup quantum development environment.
- **MIT iQuHACK** organizers for hosting an outstanding event.

## References

- Bernasconi, J. (1987). *Low autocorrelation binary sequences: statistical mechanics and configuration space analysis.* Journal de Physique, 48(4), 559–567.
- Gallardo, J. E., Cotta, C., & Fernández, A. J. (2009). *Finding low autocorrelation binary sequences with memetic algorithms.* Applied Soft Computing, 9(4), 1252–1262.
- [NVIDIA CUDA-Q Documentation](https://nvidia.github.io/cuda-quantum/latest/)
- [iQuHACK 2026 NVIDIA Challenge Repository](https://github.com/iQuHACK/2026-NVIDIA)

---

<p align="center">
  Built with ⚛️ and 🍺 by Team Beerantum at MIT iQuHACK 2026
</p>
