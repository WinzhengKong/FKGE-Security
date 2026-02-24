
# Unveiling and Mitigating Untargeted Poisoning Attacks on Federated Knowledge Graph Embedding

[![Conference](https://img.shields.io/badge/WWW-2026-brightgreen)](https://www2026.thewebconf.org/)
[![License](https://img.shields.io/badge/License-CC%20BY%204.0-blue.svg)](https://creativecommons.org/licenses/by/4.0/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.5.0-orange)](https://pytorch.org/)

This repository contains the official implementation of the paper **"Unveiling and Mitigating Untargeted Poisoning Attacks on Federated Knowledge Graph Embedding"**, accepted by **The Web Conference 2026 (WWW '26)**.

## 📝 Abstract

Federated Knowledge Graph Embedding (FKGE) enables collaborative learning across distributed knowledge graphs (KGs) while preserving privacy. However, its decentralized nature exposes vulnerabilities to client-side attacks, particularly **untargeted poisoning attacks**, which remain underexplored.

In this work, we present the first systematic investigation of untargeted poisoning attacks on FKGE. We propose three novel attacks targeting both data and embedding levels:
1.  **Similarity-based Replacement (SR):** A data-level attack that replaces entities in triples with their least similar counterparts.
2.  **Add Noise (AN):** An embedding-level attack that injects controlled noise into uploaded embeddings.
3.  **Random Noise (RN):** An embedding-level attack that completely replaces embeddings with random noise.

To counter these threats, we propose a **Learning-based Defense Mechanism (LDM)**. LDM leverages embedding density and anomaly detection (e.g., ECOD, Isolation Forest) to identify malicious clients and employs a retention mechanism to mitigate performance degradation.


## 🚀 Quick Start

### 1. Installation

Our code is based on **Python 3.9.20** and **PyTorch 2.5.0**.

```bash
# Clone the repository
git clone [https://github.com/WinzhengKong/FKGE-Security.git](https://github.com/WinzhengKong/FKGE-Security.git)
cd FKGE-Security

# Install dependencies
pip install -r requirements.txt

```

**Key Dependencies:**

* `numpy==1.26.4`
* `scipy==1.13.1`
* `torch==2.5.0`
* `networkx==3.2.1`
* `scikit_learn==1.5.2`
* `python_Levenshtein==0.26.0`

### 2. Datasets

We use the **FB15k-237** dataset, partitioned into federated settings:

* **FB15k-237-R5**: Partitioned for 5 clients.
* **FB15k-237-R10**: Partitioned for 10 clients.

Please ensure the data is placed in the `./data` directory. Detailed statistics can be found in the paper (Appendix D.1).

## 🏃 Running Experiments

We provide scripts to replicate the attacks and defense mechanisms on **FedE**, **FedEC**, and **FedLU**.

### 1. Attack Implementation

We support three attack types:

**SR (Data Poisoning):** Replaces entities based on cosine similarity.


**AN (Embedding Poisoning):** Adds scaled noise $\delta_i \sim \mathcal{U}(-\beta, \beta)$ to embeddings.


**RN (Embedding Poisoning):** Replaces embeddings with random noise.


**Example: Running FedE with AN Attack**

```bash
./run_FedE.sh --attack_type AN --malicious_ratio 0.4 --noise_scale 0.5
```

* `--attack_type`: `SR`, `AN`, or `RN`.
* `--malicious_ratio`: Ratio of malicious clients (e.g., `0.2`, `0.4`).
* `--noise_scale` ($\alpha$): Noise scaling factor for AN (default: 0.5).


### 2. Defense Implementation (LDM)

The **Learning-based Defense Mechanism (LDM)** integrates anomaly detection (e.g., ECOD, IF, LOF) to filter malicious clients.

**Example: Running FedEC with LDM Defense**

```bash
./run_FedEB.sh --model FedEC --defense LDM --detector ECOD
```

* `--defense`: Enable `LDM`.
* `--detector`: Choose `ECOD`, `IF` (Isolation Forest), or `LOF`.


## 📍 Citation

If you use this code or findings in your research, please cite our WWW '26 paper:

```bibtex
@inproceedings{jiang2026unveiling,
  author    = {Jiang, Wenzheng and Liang, Ke and Huang, Wenke and others},
  title     = {Unveiling and Mitigating Untargeted Poisoning Attacks on Federated Knowledge Graph Embedding},
  booktitle = {Proceedings of the ACM Web Conference 2026 (WWW '26)},
  year      = {2026},
  month     = {April},
  publisher = {ACM},
  address   = {Dubai, United Arab Emirates},
  doi       = {10.1145/3774904.3792117}
}

```

## ✉️ Contact

For any questions, please contact the corresponding authors:

**Wenzheng Jiang**: [jiangwenzheng@nudt.edu.cn](mailto:jiangwenzheng@nudt.edu.cn) 

