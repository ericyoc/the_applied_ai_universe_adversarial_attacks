# The Applied AI Universe: Adversarial Attacks Coding Guide
### *Breaking Every Model in the AI Universe*

[![Open Classical Notebook In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ericyoc/the_applied_ai_universe_adversarial_attacks/blob/main/Adversarial_Attacks_Classical.ipynb)
[![Open Quantum Notebook In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ericyoc/the_applied_ai_universe_adversarial_attacks/blob/main/Adversarial_Attacks_Hybrid_Quantum.ipynb)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)](https://tensorflow.org/)
[![ART](https://img.shields.io/badge/ART-adversarial--robustness--toolbox-red.svg)](https://github.com/Trusted-AI/adversarial-robustness-toolbox)
[![PennyLane](https://img.shields.io/badge/PennyLane-quantum-blueviolet.svg)](https://pennylane.ai/)
[![HuggingFace](https://img.shields.io/badge/HuggingFace-models-yellow.svg)](https://huggingface.co/)

---

<p align="center">
  <em>Book 1 builds the models. Book 2 breaks them. Book 3 hardens them — sharing one model zoo.</em>
</p>

---

## Overview

This repository is **Book 2** of *The Applied AI Universe* series. Where Book 1 (*The Applied AI Universe Coding Guide*) builds every model in the concentric-ring taxonomy of artificial intelligence, Book 2 **attacks** each one. Every victim is reconstructed from its exact Book 1 specification — same dataset, same architecture, same hyperparameters — then subjected to the attack matched to its class.

Each cell follows a consistent loop: **reconstruct the Book 1 victim → run the attack → measure clean vs. adversarial performance → score it → visualize → preview the mitigation** (which Book 3 delivers in full). Results and a master leaderboard are written to Google Drive.

| Notebook | Coverage |
|---|---|
| **`Adversarial_Attacks_Classical.ipynb`** | 27 victims across Modules 1–6: symbolic AI, classical ML, neural networks, deep learning, generative models |
| **`Adversarial_Attacks_Hybrid_Quantum.ipynb`** | 6 hybrid/quantum victims on the `default.qubit` simulator: QAOA, VQC, Hybrid QNN, VQE, Quantum-Kernel SVM, QGAN |

---

## Disclaimer

This repository is intended for **educational and defensive-research purposes only**. It demonstrates how AI and quantum models fail under adversarial conditions so that practitioners can recognize, measure, and ultimately defend against those failures (see Book 3). The techniques here are applied **only** to the author's own models on publicly available benchmark datasets; they must not be used against systems you do not own or have explicit permission to test. Results, accuracy metrics, and attack-success rates vary with runtime environment, library versions, and hardware. Quantum circuit simulations run entirely on classical hardware using software simulators (PennyLane `default.qubit`) — no physical quantum hardware is used. This work reflects the views of the author and not those of California Polytechnic State University, San Luis Obispo, or any affiliated institution.

---

## Interactive Notebooks

> GitHub may time out rendering large notebooks. Use the Colab badges to open and run them directly, or view them via nbviewer below.

### Classical Adversarial Attacks (Modules 1–6)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ericyoc/the_applied_ai_universe_adversarial_attacks/blob/main/Adversarial_Attacks_Classical.ipynb)
[![nbviewer](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.org/github/ericyoc/the_applied_ai_universe_adversarial_attacks/blob/main/Adversarial_Attacks_Classical.ipynb)

### Hybrid & Quantum Adversarial Attacks

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ericyoc/the_applied_ai_universe_adversarial_attacks/blob/main/Adversarial_Attacks_Hybrid_Quantum.ipynb)
[![nbviewer](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.org/github/ericyoc/the_applied_ai_universe_adversarial_attacks/blob/main/Adversarial_Attacks_Hybrid_Quantum.ipynb)

---

## Attack Catalog — Classical Notebook

Every victim is reconstructed faithfully from Book 1 (dataset and architecture noted), then attacked.

### Module 1 — Symbolic AI

| Victim | Book 1 Model | Attack |
|---|---|---|
| Planning | A* on a 10×10 grid | Obstacle injection → goal made unreachable |
| Expert System | Rule-based diagnosis | Knowledge-base poisoning (rule injection) |
| Fuzzy Logic | Mamdani controller | Membership-function shift |

### Module 2 — Machine Learning

| Victim | Book 1 Model | Attack |
|---|---|---|
| Supervised | Iris · 6 classifiers (DT/SVM/RF/GB/KNN/LogReg) | FGSM (white-box) + HopSkipJump (black-box) evasion |
| Feature Pipeline | Breast Cancer · RandomForest(200) | Label-flip data poisoning |
| Regression | Linear & Polynomial (degree 3) | Adversarial input perturbation |
| Semi-Supervised | Digits · LabelSpreading (kNN) | Pseudo-label poisoning |
| Unsupervised | Iris · K-Means (k=3) + PCA | Centroid poisoning |
| Ensemble | make_classification · Voting (DT/RF/GB/AdaBoost) | Black-box evasion + transfer to standalone RF |

### Module 3 — Neural Networks

| Victim | Book 1 Model | Attack |
|---|---|---|
| Perceptron | From-scratch unit (AND gate) | Decision-boundary perturbation |
| MLP | MNIST · 784→256→128→64→10 | FGSM ε-sweep + PGD (GradientTape) |
| CNN | MNIST · 3 conv blocks | FGSM ε-sweep + PGD |
| LSTM/RNN | Sine wave · seq_len 50 | Sequence perturbation |
| SOM | Iris · MiniSom(10×10) | Best-matching-unit shift |

### Module 4 — Deep Learning

| Victim | Book 1 Model | Attack |
|---|---|---|
| DNN | CIFAR-10 · flattened dense net | FGSM ε-sweep + PGD |
| Transfer Learning | MobileNetV2 · CIFAR-10 · 96×96 · [−1,1] | PGD in the model's own input space |
| GAN | MNIST · dense generator/discriminator | Membership inference |
| Attention | Scaled dot-product (random Q/K/V) | Key-matrix perturbation |
| Dropout | MNIST · with/without dropout | FGSM (regularization vs. robustness) |
| Reinforcement Learning | Q-Learning · 5×5 GridWorld (goal +10, traps −5) | Reward poisoning |
| CapsNet | Dynamic-routing capsule network | FGSM |
| DBN | RBM×2 + LogReg pipeline | Evasion |

### Modules 5–6 — Generative AI

| Victim | Book 1 Model | Attack |
|---|---|---|
| N-gram LM | Trigram language model | Out-of-vocabulary token injection |
| Transformer | Multi-head self-attention block | Token-substitution perturbation |
| Pretrained NLU | HuggingFace sentiment pipeline | Homoglyph substitution |
| Retrieval Chatbot | TF-IDF + cosine retrieval | Query perturbation |
| RLHF | Proxy reward model | Reward hacking (length exploit) |
| Diffusion (DDPM) | U-Net denoiser | Membership inference |
| LoRA / PEFT | GPT-2 + LoRA adapter | Backdoored adapter (trigger token) |
| Mamba / SSM | Selective state-space model | Long-sequence token perturbation |

---

## Attack Catalog — Quantum Notebook

| Victim | Book 1 Model | Attack | Result |
|---|---|---|---|
| QAOA | MaxCut on a 4-cycle | Parameter poisoning | cut 2.77 → 2.00 / 4.0 |
| VQC | AngleEmbedding + StronglyEntanglingLayers | Quantum FGSM (input gradient) | acc 0.89 → 0.78 |
| Hybrid QNN | BasicEntanglerLayers | FGSM | acc 0.56 → 0.38 |
| VQE | Ising / H₂ Hamiltonian | Parameter-noise injection | E −1.414 → −0.985 |
| Quantum-Kernel SVM | Quantum kernel + SVC | Kernel-boundary evasion | acc 0.70 → 0.05 |
| QGAN | Variational generator | Generator weight poisoning | gen μ 0.47 → 0.38 |

---

## Metrics & Visualization

Every attack reports a standard **Scorecard**: clean accuracy, robust (post-attack) accuracy, attack-success rate (ASR), and L∞/L₂ perturbation norms. Image attacks render a three-row figure — **CLEAN** (green, correctly classified), **ADVERSARIAL** (red, fooled), and **PERTURBATION** (amplified) — so the imperceptible-yet-fooling nature of L∞ attacks is visible. Parameter/weight attacks (QAOA, VQE, QGAN) report `NaN` for L∞/L₂ because there is no input-space perturbation to measure. Each cell closes with a **Mitigation Preview** pointing to its Book 3 defense.

## Drive Outputs

```
AI_Universe_Adversarial_Attacks/            # classical figures + leaderboard_classical.csv
AI_Universe_Adversarial_Attacks_Quantum/    # quantum figures + leaderboard_quantum.csv
```

Victim weights are reconstructed from Book 1 code and cached to Drive on first run. Run the **engine/setup cell at the top of each notebook once per session** — it defines `Scorecard`, `log`, `savefig`, and the Drive paths that every attack cell uses.

## Technologies Used

| Area | Stack |
|---|---|
| Classical ML | scikit-learn |
| Deep learning | TensorFlow / Keras (GradientTape attacks) |
| Attack toolkit | Adversarial Robustness Toolbox (ART) |
| NLP / generative | HuggingFace Transformers, PEFT, PyTorch |
| Quantum / hybrid | PennyLane (`default.qubit`) |

## Further Reading

| Topic | Reference |
|---|---|
| Adversarial examples | Goodfellow et al., *Explaining and Harnessing Adversarial Examples* |
| PGD / robustness | Madry et al., *Towards Deep Learning Models Resistant to Adversarial Attacks* |
| Black-box attacks | Chen et al., *HopSkipJumpAttack* |
| Data poisoning | Biggio & Roli, *Wild Patterns* |
| Quantum adversarial ML | Lu et al., *Quantum Adversarial Machine Learning* |

---

**Topics:** `adversarial-attacks` `adversarial-examples` `machine-learning-security` `fgsm` `pgd` `data-poisoning` `membership-inference` `model-evasion` `tensorflow` `pennylane` `quantum-machine-learning` `ai-security` `adversarial-robustness-toolbox` `huggingface` `lora` `backdoor-attacks` `red-team` `mlsecops` `cybersecurity` `educational`

---

*Built for CSC-3201 — California Polytechnic State University, San Luis Obispo*
