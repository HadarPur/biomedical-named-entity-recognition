# Biomedical Named Entity Recognition – Evaluation Report  
## PubMedBERT + Weighted Loss on BC5CDR

## 1. Overview
This experiment fine-tunes a PubMedBERT token classification model on the BC5CDR dataset for biomedical Named Entity Recognition (NER), targeting Chemical and Disease entity classes. Weighted cross-entropy loss was used to improve Disease precision.

---

## 2. Model
- Base model: `microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext`
- Task: Token classification (5 labels)
- Loss: Weighted Cross-Entropy  
  - O: 1.0  
  - B-Chemical: 1.0  
  - I-Chemical: 1.0  
  - B-Disease: 1.5  
  - I-Disease: 1.5  

---

## 3. Training Configuration
| Setting | Value |
|--------|--------|
| Epochs | 4 |
| Learning Rate | 1e-5 |
| Batch Size | 8 |
| Weight Decay | 0.05 |
| Warmup Ratio | 0.1 |

---

## 4. Validation Results
| Metric | Value |
|--------|--------|
| Loss | 0.106 |
| Precision | 0.879 |
| Recall | 0.916 |
| F1 | **0.897** |

---

## 5. Test Results
| Metric | Value |
|--------|--------|
| Loss | 0.1157 |
| Precision | 0.8632 |
| Recall | 0.9073 |
| F1 | **0.8847** |

### Per-Entity Performance
| Entity | Precision | Recall | F1 | Support |
|--------|-----------|--------|----|---------|
| Chemical | 0.91 | 0.94 | 0.92 | 5385 |
| Disease | 0.80 | 0.87 | 0.84 | 4424 |

**Macro Avg F1:** 0.88  
**Weighted Avg F1:** 0.89  

---

## 6. Summary
- Strong Chemical NER (F1 ≈ 0.92)  
- Improved Disease performance using weighted loss (F1 ≈ 0.84)  
- Overall F1 on BC5CDR reaches **0.88–0.89**  
