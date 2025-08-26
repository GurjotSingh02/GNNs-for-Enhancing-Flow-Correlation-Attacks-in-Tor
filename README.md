# Beyond All-Pairs Cosine: Leveraging GNN Smoothing for Enhancing CNN-Based Flow Correlation Attacks in Tor

## 📌 Overview
This project explores methods to improve the accuracy of **traffic correlation attacks** in the Tor anonymity network by integrating **Graph Neural Networks (GNNs)** with existing deep learning models.  

The baseline model, **DeepCoFFEA**, has demonstrated strong performance in correlating Tor entry and exit traffic flows using feature embeddings and amplification. However, it still suffers from a high rate of false positives.  
To address this, we propose a **GNN-based post-processing framework** that refines DeepCoFFEA’s predictions, leading to improved precision without significantly compromising recall.

---

## 🔬 Methodology

### 1. DeepCoFFEA Baseline
- Uses a **triplet network** to embed Tor entry and exit flows into a lower-dimensional space.  
- Employs **amplification via segmentation** (multiple embeddings per flow).  
- Achieves high correlation accuracy but generates thousands of false positives.

### 2. GNN-Based Post-Processing
- Constructs a **graph representation** where nodes are flow embeddings and edges are predicted correlations.  
- Applies **Graph Attention Networks (GATs)** to refine predictions by leveraging structural flow relationships.  
- Reduces false positives while maintaining high true positive rates.

### 3. Transformer-Based GNN
- Enhances the GAT-based model using **multi-head self-attention** on graph-structured data.  
- Employs a **CNN feature extractor + Transformer GNN** for refined embeddings.  
- Achieves **significantly higher Bayesian Detection Rates (BDR)**, with improved trade-offs between true positives and false positives.

---

## 📊 Results

- **DeepCoFFEA Baseline**  
  - TPR ≈ 0.89  
  - FPR ≈ 0.07% (≈ 3,015 false positives)  
  - BDR ≈ 0.384  

- **GAT Post-Processing**  
  - Slight BDR improvement to ≈ 0.396  
  - Reduced false positives to ≈ 2,852  

- **Transformer GNN Post-Processing**  
  - Achieved BDR up to **0.54** (and up to **0.89** in stricter threshold settings)  
  - Significant reduction in false positives while maintaining high recall  

These results confirm that **graph-based refinement techniques** are effective in boosting the reliability of flow correlation attacks.

---

## 🛠️ Tech Stack
- **Python 3.9+**
- **PyTorch / PyTorch Geometric**
- **NumPy, Pandas, Matplotlib**
- **Scikit-learn**
