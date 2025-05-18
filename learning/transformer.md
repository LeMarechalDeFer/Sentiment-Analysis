When you pass text to the tokenizer (`transformers.AutoTokenizer`), it automatically performs:

| Step                                        | Integrated? | Detail                                                           |
| ------------------------------------------- | ----------- | ---------------------------------------------------------------- |
| **Lowercasing**                             | ✅ or ❌     | Depends on the model (`uncased` or `cased`)                       |
| **Punctuation removal or encoding**         | ⚠️ yes     | Punctuation is **encoded** if important (e.g. "?" or "!")        |
| **Tokenization (subwords)**                 | ✅          | Smart splitting into subunits (e.g. `playing → play + ing`)      |
| **Special tokens addition**                 | ✅          | `[CLS]`, `[SEP]`, `<s>`, `</s>`, etc. depending on the model     |
| **ID conversion**                           | ✅          | Each token becomes an ID from the model's vocabulary             |
| **Truncation / padding**                    | ✅          | To adapt to a fixed input size                                   |
| **Attention mask**                          | ✅          | Masks non-significant parts (e.g. padding)                       |

|Step|Classical NLP (BoW)|Modern NLP (BERT/GPT)|
|---|---|---|
|Manual preprocessing|✅ Yes|❌ No|
|Vectorization|✅ manual|✅ integrated in model|
|ML model|✅ yes|✅ yes or fine-tuning|
|Contextualization|❌ No|✅ Yes|

## Step by step details:

### 1. **Raw text**

- Original sentence, without manual preprocessing (no lowercase, no punctuation removal)
- Ex: `"This movie is absolutely incredible!"`
---

### 2. **Model tokenizer**

- Applies:
    - tokenization (often in _subwords_)
    - casing according to model (`cased`/`uncased`)    
    - padding, truncation, special tokens addition, etc.
        
- Produces:
    - `input_ids`
    - `attention_mask`
    - sometimes `token_type_ids` (in BERT)
        

---

### 3. **BERT / GPT model processing**

- Input: `input_ids`
- Output:
    - Vectors for each token
    - OR a global vector (`[CLS]`) representing the entire sequence
        

---

### 4. **Modeling on top**

Two options:

#### A. ✅ **Feature extraction + classical ML**

- You use embeddings as **fixed features**
- You train an ML model:
    
    - `LogisticRegression`
    - `SVM`
    - `RandomForest`
    - `MLP`, etc.
        

#### B. ⚡ **Fine-tuning** (more powerful but more costly)

- You add one or more classification layers **on top of the pre-trained model**
- And you **re-train** (all or part) the model with your own data.
---
### 5. **Post-processing**

- Converting output to class: e.g. `0 → "negative"`, `1 → "positive"`
- Saving, displaying, etc.



#### ➕ What is it?

> Adding "fake" tokens at the end of **short** sentences, so that all sentences have **the same length**.

#### ❓ Why?

Models like BERT expect **fixed-size tensors**. We therefore cannot pass them sentences of different lengths.

#### ✨ Example:

|Sentence|Token IDs|
|---|---|
|"I like this movie."|`[101, 149, 1312, 1345, 102]`|
|"Excellent."|`[101, 9987, 102, 0, 0]` _(padded)_|

The `0` is a **padding token**, ignored in calculations thanks to an **attention mask**.

---

### 2. ✂️ **Truncation** – cutting sequences that are too long

#### ➕ What is it?

> If a sentence is **too long** to be processed (often > 512 tokens), we **cut it**.

#### ❓ Why?

BERT and other models have a **maximum token length**.

#### ✨ Example:

python

CopyModify

`tokenizer("very long text...", truncation=True)`

---

### 3. 🔖 **Special tokens addition**

#### ➕ What is it?

> These are **mandatory tokens** added to guide the model in reading the text.

#### 🧠 Examples by model:

|Model|Special tokens added|Role|
|---|---|---|
|BERT|`[CLS]` at start, `[SEP]` at end|`[CLS]` = global summary, `[SEP]` = separation|
|GPT|`<s>` and `</s>` (or sometimes nothing)|Mark start/end|
|RoBERTa|`<s>` start, `</s>` end|Same|

#### ✨ Example:

python

CopyModify

`` "The movie is good."   → `[CLS]`, `The`, `movie`, `is`, `good`, `[SEP]` ``

---

## ✅ Clear summary

|Step|Used in BoW?|Used in BERT/GPT?|Role|
|---|---|---|---|
|Text cleaning|✅ Yes|❌ No (integrated in tokenizer)||
|Tokenization|✅ Yes|✅ Yes||
|Lemmatization|✅ Yes|❌ No (context learned)||
|Padding|❌ No|✅ Yes||
|Truncation|❌ No|✅ Yes||
|Special tokens|❌ No|✅ Yes|