# 🧠 Sentiment Analysis with Bag of Words (Jupyter Notebook)

This project implements a sentiment analysis model on Amazon reviews using classical NLP techniques in a **Jupyter Notebook**. The pipeline relies on **lemmatization**, **Bag of Words (BoW)** vectorization, and several classification algorithms.


---

## 📊 Overview

- Dataset: Amazon Reviews
- Task: Sentiment Analysis
- Models: Logistic Regression, Multinomial Naive Bayes, SGD Classifier
- Evaluation: Accuracy, Precision, Recall, F1-score
- Tools: Python, NLTK, Scikit-learn, Pandas, NumPy
- Environment: Jupyter Notebook / Conda

---

Quick start with the notebook:

1. Clone the repository
2. Create the environment:

```bash
conda env create -f environment.yml
conda activate sentiment-bow
```

3. Run the notebook:

```bash
jupyter notebook sentiment_analysis.ipynb
```

---

## 📂 Dataset

- **Source**: [`bittlingmayer/amazonreviews`](https://www.kaggle.com/datasets/bittlingmayer/amazonreviews)
- Accessed via [`kagglehub`](https://pypi.org/project/kagglehub/)
- Format: `.bz2` text file with FastText labels (`__label__1`, `__label__2`)

---

## ⚙️ Pipeline Steps

1. **Dataset Loading**
   - Load 10,000 lines from `train.ft.txt.bz2`
   - Parse FastText-style labels and text content

2. **Text Preprocessing**
   - Remove punctuation
   - Lowercase
   - Lemmatize words (NLTK WordNetLemmatizer, no POS tagging)
   - Remove English stopwords (via CountVectorizer)
   - Extract 1-grams and 2-grams
   - Limit dictionary to top 3000 tokens (`max_features=3000`)

3. **Vectorization**
   - `CountVectorizer` used to convert text into sparse matrix (BoW)
   - Output matrix shape: `(10000, 3000)`

4. **Train/Test Split**
   - 80% training / 20% testing using `train_test_split`

5. **Model Training & Evaluation**
   - Models tested:
     - Logistic Regression
     - Multinomial Naive Bayes
     - SGD Classifier
   - Metrics:
     - Accuracy
     - Precision / Recall / F1-score (`classification_report`)

6. **Custom Prediction**
   - Run `predict_sentiment(comment, model, model_name)`
   - Test your own comment (e.g., `"This product was terrible"`)

---

## 🧪 Example Test Comments

```python
predict_sentiment("Absolutely love it, highly recommend this product.", model=clf, model_name="Logistic Regression")
predict_sentiment("This product was terrible and broke in two days.", model=clf, model_name="Logistic Regression")
predict_sentiment("The quality is decent, but the price is too high.", model=clf, model_name="Logistic Regression")
```

---

## 📝 Requirements

See [environment.yml](./environment.yml)

---

The full explanation, methodology, model comparison, and discussion of performance and limitations are available in [report.pdf](./report.pdf).

--- 

## 📜 License

[GNU GENERAL PUBLIC LICENSE](./LICENSE)

--- 