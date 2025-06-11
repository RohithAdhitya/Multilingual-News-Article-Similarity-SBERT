# 🌍 Multilingual News Article Similarity using SBERT

**This project uses the SBERT model to analyze semantic similarity between multilingual news article pairs. It evaluates whether two articles refer to the same event by generating sentence embeddings and applying a deep regression model.**

---

## 📄 Overview

With the rise of global news content, evaluating the semantic similarity of articles across different languages is key to verifying integrity and detecting redundancy. This project tackles this challenge using SBERT embeddings and a sequential regression model.

---

## 🧾 Dataset

- **Source**: [SemEval 2022 Task 8](https://semeval.github.io/SemEval2022/tasks/)
- **Size**: 10,000 article pairs
- **Languages**: 18 (including English, German, Spanish, Arabic, Polish, etc.)
- **Format**: HTML/JSON, converted to CSV
- **Similarity Dimensions**: Geography, Time, Entities, Style, Tone, Narrative, Overall

---

## 🧹 Preprocessing

- Converted nested JSON/HTML to flat CSV using `glob` and custom parsers
- Removed:
  - Punctuation
  - URLs
  - Numbers
  - Null values in `pair_id`, `title`, and `text`
- Final structured data was used for SBERT embedding

---

## 🤖 Methodology

### Sentence Embeddings
- Model: `paraphrase-multilingual-mpnet-base-v2`
- Outputs: 768-dimensional vector per sentence

### Regression Model
- Framework: TensorFlow / Keras
- Architecture:
  - 7 Dense Layers
  - ReLU activations
  - Batch Normalization
  - Dropout layers
- Loss: Huber Loss
- Optimizer: Adam
- Train/Test Split: 70:30
- Epochs: 500 (early stopping after 5 stable epochs)

---

## 📊 Evaluation

- **Metric**: Mean Absolute Error (MAE)
- **Train MAE**: 0.976  
- **Validation MAE**: 0.96  
- Shows stable learning curve without overfitting

---

## 🧠 Key Insights

- Multilingual SBERT embeddings are highly effective for cross-language similarity
- Removing noisy tokens and optimizing dropout significantly improved generalization
- Regression outperforms simple threshold-based similarity detection

---

## ⚠️ Limitations

- High sensitivity to hyperparameters
- Training required large compute due to model depth
- Some overfitting observed with low learning rates
- Generalization to new data may vary

---

## 🚀 Future Work

- Integrate additional metadata: images, links
- Explore contrastive loss and Siamese networks
- Expand to real-time news feed comparison
- Add model explainability (e.g., SHAP for embeddings)

---

## 👨‍💻 Authors

- **Rohith Adhitya Chinnannan Rajkumar**
- **Rutvik Shah**

---

## 📜 License

For academic and research purposes only. Dataset sourced from SemEval 2022 under fair use.
