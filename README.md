# 🏥 NLP-Based Automatic Medical Report Summarization

### Fine-Tuning T5-Small on MIMIC-IV Clinical Data

---

## 📌 Overview

This project presents a complete **end-to-end NLP pipeline** for **abstractive summarization of medical reports** using a Transformer-based architecture.

We fine-tune **T5-Small (60M parameters)** on the **MIMIC-IV Brief Hospital Course (BHC)** dataset to automatically generate concise and clinically meaningful summaries from long hospital notes.

The goal is to demonstrate that **small, efficient models can achieve strong performance** on domain-specific tasks with proper fine-tuning.

---

## 🎯 Objectives

* Build a **reproducible Seq2Seq pipeline** for clinical text summarization
* Fine-tune **T5-Small** under **limited GPU resources**
* Generate **fluent and faithful abstractive summaries**
* Evaluate performance using **ROUGE metrics**
* Show that **domain adaptation > model size** in structured medical text

---

## 🧠 Methodology

The task is modeled as a **sequence-to-sequence learning problem**:

* **Input:** Full clinical note (admission + progress notes)
* **Output:** Short summary (Brief Hospital Course)

The model learns:

```
P(y | x) = ∏ P(y_t | y_<t, x)
```

Where:

* `x` = input medical report
* `y` = generated summary

---

## ⚙️ Pipeline

The project follows a structured **10-step pipeline**:

1. Task Definition
2. Dataset Preparation (MIMIC-IV)
3. Data Splitting (Train / Validation / Test)
4. Text Preprocessing
5. Tokenization (SentencePiece)
6. Model Selection (T5-Small)
7. Fine-Tuning
8. Training
9. Beam Search Decoding
10. Evaluation (ROUGE)

---

## 🏗️ Model Details

| Component         | Value                       |
| ----------------- | --------------------------- |
| Model             | T5-Small                    |
| Parameters        | 60M                         |
| Architecture      | Encoder-Decoder Transformer |
| Max Input Length  | 256 tokens                  |
| Max Output Length | 64 tokens                   |
| Training Epochs   | 6                           |
| Precision         | FP16 (Mixed Precision)      |

---

## 📊 Results

| Metric      | Score     |
| ----------- | --------- |
| ROUGE-1     | 0.394     |
| ROUGE-2     | 0.182     |
| **ROUGE-L** | **0.344** |

📌 **Key Insight:**
A small model (T5-Small) can achieve **competitive results** on clinical summarization when properly fine-tuned.

---

## ✨ Example

**Input:**

> Long clinical note including admission, treatment, and progress details

**Generated Summary:**

> Patient admitted with chest pain and shortness of breath. Echo showed reduced EF. Treated with diuretics and ACE inhibitors. Discharged stable with follow-up.

✔ Abstractive
✔ Concise
✔ Clinically structured

---

## 🚧 Challenges & Solutions

| Challenge          | Solution                                |
| ------------------ | --------------------------------------- |
| Limited GPU memory | Used T5-Small + gradient accumulation   |
| Small batch size   | Simulated larger batch via accumulation |
| Medical vocabulary | SentencePiece subword tokenization      |
| Exposure bias      | Beam search decoding                    |
| Overfitting        | Early stopping + weight decay           |
| Hallucination risk | ROUGE + future factuality checks        |

---

## 🔬 Key Learnings

* **Fine-tuning is more important than model size** in domain-specific NLP
* **Beam search improves multi-sentence coherence**
* **Mixed precision enables training on limited hardware**
* Clinical text is **structured and predictable**, making it ideal for Seq2Seq models

---

## 🚀 Future Work

* Use larger models (T5-Base, Flan-T5)
* Add **BERTScore / NLI** for factual correctness
* Pre-train on **medical corpora (PubMed, ClinicalBERT)**
* Deploy as a **clinical decision support tool**
* Evaluate **fairness across patient demographics**

---

## ⚠️ Ethical Considerations

* MIMIC-IV dataset is **fully de-identified**
* Generated summaries **must not replace medical professionals**
* Human validation is required due to **hallucination risk**

---

## 📁 Project Structure

```
├── data/                # Dataset (not included due to privacy)
├── notebooks/           # Training & experiments
├── models/              # Saved checkpoints
├── src/                 # Core pipeline code
├── report/              # LaTeX report
└── README.md
```

---

## 👨‍💻 Authors

* **Alaa Guedda**
* **Abdelaziz Tedjani**

Department of Computer Science
Faculty of Exact Sciences

---

## 📜 License

This project is for **academic and research purposes only**.

---

## ⭐ Final Note

This project shows that with the right pipeline and understanding,
you can build **high-impact NLP systems even with limited resources**.
