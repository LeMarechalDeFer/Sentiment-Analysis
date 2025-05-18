**TF-IDF**, or **Term Frequency - Inverse Document Frequency**.

It's an **intelligent** way to assign a **weight to each word** in a document, based on **its frequency in the document** and **its rarity in the corpus**.

---

## 🔹 TF-IDF Breakdown

TF-IDF = **TF × IDF**

### 📌 1. **TF (Term Frequency)** : word frequency in the document

> **TF(t,d)** = (number of times term t appears in document d) / (total number of words in d)

Example: in `"cat cat sleeps"`,

- `TF("cat") = 2 / 3 = 0.66`
    

---

### 📌 2. **IDF (Inverse Document Frequency)** : word rarity across all documents

> **IDF(t)** = log(N / df(t))

- N = total number of documents
    
- df(t) = number of documents containing word t
    

➡️ The **rarer** a word is, the **higher** its IDF  
➡️ A word that appears **in all documents** → IDF = 0 → it's **non-informative**

---

## 🔹 Intuitive Example

Corpus:

text

CopyModify

`Doc 1 : "black cat sleeps" Doc 2 : "black dog barks" Doc 3 : "black white"`

|Word|TF in Doc 1|DF (nb of docs with word)|IDF|TF-IDF|
|---|---|---|---|---|
|**cat**|1/3|1|log(3/1) ≈ 1.10|≈ 0.37|
|**black**|1/3|3|log(3/3) = 0|0|

➡️ `"black"` is **too frequent** → not discriminative → weight = 0  
➡️ `"cat"` is **rare** → more important → weight > 0

---

## ✅ Why is it useful?

|Problem|TF-IDF solves this|
|---|---|
|Frequent but useless words ("the", "and", "of")|Very low weight|
|Rare and discriminative words|High weight|
|Need for **weighted** text representation|Perfect for this|
|Too much noise with BoW|TF-IDF filters better|

---

## 🧠 Clear Summary:

|Concept|Used to...|High value if...|
|---|---|---|
|**TF**|measure importance **in the document**|word repeated often in a doc|
|**IDF**|measure rarity **in the corpus**|word present in few documents|
|**TF-IDF**|fine weighting frequency × rarity|word frequent in this doc, but rare globally|