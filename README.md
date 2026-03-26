# Cdataset: Drug–Disease Interaction Dataset from PREDICT

## 📌 Overview

**Cdataset** is a benchmark dataset for **drug–disease interaction prediction**, derived from the PREDICT framework proposed by Gottlieb et al. (2011).

The dataset integrates drug similarity, disease similarity, and known drug–disease associations, making it suitable for machine learning approaches such as:

* Graph Neural Networks (GNNs)
* Matrix factorization
* Contrastive learning

---

## 📊 Dataset Statistics

| Item                   | Value |
| ---------------------- | ----- |
| Number of drugs        | 663   |
| Number of diseases     | 409   |
| Number of proteins     | 993   |
| Number of interactions | 2532  |

---

## 🧬 Data Source

This dataset is derived from:

```id="q2n4op"
@article{gottlieb2011predict,
  title={PREDICT: a method for inferring novel drug indications with application to personalized medicine},
  author={Gottlieb, Assaf and Stein, Gideon Y and Ruppin, Eytan and Sharan, Roded},
  journal={Molecular Systems Biology},
  volume={7},
  number={1},
  pages={496},
  year={2011}
}
```

The original data combines multiple biomedical sources including:

* DrugBank
* OMIM
* KEGG

---

## 🏗 Dataset Structure

```id="s0x1fm"
Cdataset/
 ├── DiDrA.csv        # Drug–Disease associations
 ├── DrugSim.csv      # Drug similarity matrix
 ├── DiseaseSim.csv   # Disease similarity matrix
```

---

## 📄 File Description

### 1. DiDrA.csv

* Contains known drug–disease associations
* Format:

```
drug_id, disease_id
```

* Each row represents a **positive interaction**

---

### 2. DrugSim.csv

* Drug–drug similarity matrix
* Typically computed based on:

  * Chemical structure
  * Molecular fingerprints

---

### 3. DiseaseSim.csv

* Disease–disease similarity matrix
* Based on:

  * Phenotypic similarity
  * Semantic similarity (e.g., ontology-based)

---

## ⚙️ Usage

### 🔹 Task

Given:

* Drug similarity matrix **S_d**
* Disease similarity matrix **S_s**
* Known interactions **A**

Predict unknown drug–disease associations.

---

### 🔹 Example (Python)

```python id="m2r8q1"
import pandas as pd

interactions = pd.read_csv("DiDrA.csv")
drug_sim = pd.read_csv("DrugSim.csv", index_col=0)
disease_sim = pd.read_csv("DiseaseSim.csv", index_col=0)

print(interactions.head())
```

---

## 🧠 Task Formulation

The problem can be formulated as:

* **Link Prediction** in a bipartite graph
* **Matrix Completion** problem

Goal:
Predict missing entries in interaction matrix **A ∈ R^(|D| × |S|)**

---

## 📈 Evaluation Protocol

Common evaluation metrics:

* AUC (Area Under ROC Curve)
* AUPR (Area Under Precision-Recall Curve)

Evaluation strategies:

* K-fold cross-validation
* Leave-one-out validation

---

## ⚠️ Notes

* The dataset is **sparse** (few known interactions vs. many unknown pairs)
* Negative samples are not explicitly provided
* Common practice:

  * Generate negatives via random sampling
  * Ensure no information leakage

---

## 🚀 Recommended Use Cases

* Drug repurposing
* Biomedical link prediction
* Heterogeneous graph learning
* Contrastive representation learning

---

## 📜 License

This dataset follows the licensing terms of the original data sources.
It is intended for **research and academic use only**.

---

## 🤝 Acknowledgements

We thank the authors of the PREDICT model and the maintainers of biomedical databases used in constructing this dataset.

---

## 📬 Contact

* Name: [Your Name]
* Affiliation: [Your University]
* Email: [[your.email@example.com](mailto:your.email@example.com)]

---
