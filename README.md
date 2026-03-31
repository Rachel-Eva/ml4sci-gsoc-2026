# ML4SCI GSoC 2026 — Evaluation Tasks

Evaluation test submissions for the **QML-HEP** projects under ML4SCI Google Summer of Code 2026.

## Projects Applied To

- **Q-MAML** — Quantum Model-Agnostic Meta-Learning for Variational Quantum Algorithms for High Energy Physics Analysis at the LHC
- **Automated Scientific Discovery of Quantum Machine Learning Architectures**

## Tasks Completed

| Task | Description | File |
|------|-------------|------|
| Task I | Quantum circuit implementation with PennyLane — Hadamard, CNOT, SWAP, RX gates + SWAP test circuit | `task_i.ipynb` |
| Task II | Classical GNN for quark/gluon jet classification — GCN and TreeNiN-style RvNN (Louppe et al. 2019) with level-batching | `task_ii.ipynb` |
| Task III | Written commentary on QML, VQAs, barren plateaus, PennyLane, and proposed methods | `task_iii` |
| Task VI | Quantum representation learning with contrastive loss on MNIST — SWAP test circuit + Q-MAML (Lee et al. AAAI 2025) meta-learning | `task_vi.ipynb` |
| Task XI | MLP + PQC for quantum state preparation from normally distributed data — MSE loss on statevectors + Q-MAML Learner | `task_xi.ipynb` |
| Task XII | Task XI extended with PPO reinforcement learning — RL agent adjusts PQC parameters using −MSE as reward signal | `task_xii.ipynb` |

## Dependencies

All notebooks are self-contained with install cells. Core dependencies:

```
pennylane
pennylane-lightning
torch
energyflow        # Task II only
scikit-learn
matplotlib
numpy
```

## Running

All notebooks are designed for **Google Colab (T4 GPU)**. Open any notebook in Colab and run cells top to bottom. Google Drive mounting is used in Task II for caching the jet dataset and model checkpoints.

## Key Results

**Task II — Quark/Gluon Jet Classification**
- GCN: AUC = 0.8319
- TreeNiN RvNN (level-batched, Louppe et al.): AUC = 0.8605
- RvNN outperforms GCN — physics-motivated kt clustering tree provides stronger inductive bias than geometric kNN graph

**Task VI — Quantum Representation Learning**
- Baseline (contrastive circuit): 96.5% accuracy, fidelity gap 0.331
- Q-MAML few-shot adaptation on held-out digit pair: 93% vs 87% (small init) vs 83% (random init)

**Task XI — Quantum State Preparation**
- Q-MAML Learner init: fidelity 0.8152 vs small init 0.6768 vs random 0.7996
- Key finding: small initialisation hurts for state preparation (circuit needs large rotations away from identity)

**Task XII — PPO Quantum Control**
- PPO agent learns to navigate PQC parameter space using −MSE reward
- Comparison against direct gradient descent on held-out target states
