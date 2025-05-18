
| Approach Type         | Examples                                         | Limitations                                                                                                                                                                                           |
| --------------------- | ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Rule-based            | ELIZA, Regex, grammars, rule-based NER           | **deterministic** systems based on **linguistic rules** and **formal grammars**.                                                                                                                       |
| Lexical / Symbolic    | WordNet, thesauri, grammars, parse trees, NER    | These approaches treat language as a system of **structured symbols**, analyzed according to **grammatical and syntactic logic**. !!! review to use as complement to transformer models                  |
| Simple Statistical    | n-gram, TF-IDF, BoW                              |                                                                                                                                                                                                        |
| Structured Processing | Syntax trees, rule-based POS tagging             |                                                                                                                                                                                                        |
| Expert Systems        | Scripted dialogue, symbolic AI                   |                                                                                                                                                                                                        |
- **N-gram Models** (probability of a word given the previous one)
- **TF-IDF** (term weighting in documents)
- **Bag of Words (BoW)**
=> pre-ML approach

Before ML, many NLP tools already existed:

- **Spell/Grammar Checkers** (based on dictionaries and rules)
- **Scripted Chatbots** (like ELIZA or PARRY)
- **Rule-based Machine Translation Systems** (e.g., SYSTRAN)

| Step                           | **Classical ML** Pipeline                    | **Traditional NLP** Pipeline                                      | **Transformers (BERT/GPT)** Pipeline                                                             |
| ------------------------------- | -------------------------------------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| **1. Raw Data**                 | Table with numeric/categorical columns       | Raw text (sentences, documents)                                   | Raw text (without manual cleaning)                                                               |
| **2. Preprocessing**            | - Normalization - One-hot encoding           | - Lowercasing - Cleaning - Tokenization - Stopwords - Lemmatization| Integrated Tokenizer: - Tokenization (subwords) - Padding - Truncation - Special tokens addition |
| **3. Vectorization / Features** | Already vectorized or after encoding         | BoW, TF-IDF, Word2Vec, etc.                                       | Model-produced embeddings (contextualized)                                                        |
| **4A. ML Model** _(classical)_  | Regression, SVM, etc.                        | Same: classical ML on BoW/TF-IDF vectors                          | Classical ML on `[CLS]` or averaged embeddings                                                    |
| **4B. Fine-tuning (DL)**        | —                                            | —                                                                  | Model is retrained with a classification head                                                     |
| **5. Post-processing**          | Result = 0/1, class, raw prediction          | Mapped to label (positive, negative, etc.)                        | Same: prediction extraction, labeling, visualization                                             |
- **Tokenizer**: splits text → list of tokens
- **Vectorizer**: transforms tokens into **numeric vectors** usable by a model

Reminder:
An **embedding** is a **vector representation of a word, subword, or token** in a numeric space (often 50 to 1,000 dimensions).

### NLP Preprocessing

possible but not all options are always desirable
- lowercasing => reduces same words distinction
    - steps almost universally applied except for the following exceptions:
        - Named Entity Recognition ("paris"(verb) != "Paris"(city))
        - stylistic analysis
        - languages where case has more morphological importance (e.g., German with nouns)
        - for BERT/GPT models the preprocessing phase is already included in the model's "tokenizer" so no modifications needed!!!
- suppressing punctuation, numbers and special characters
    - for simple vectorization models
- tokenization: cutting phrases into units (tokens) (often a word but not always)
    - for BoW/TF-IDF, Word2Vec/GloVe in words, and for Transformer models it's in wordpieces [[tokenization]]
- stopwords => removing connecting and transition words
- lemmatization / stemming => cutting words to their root
- spelling errors (advanced)

### Bag of Words ()

=> binary bow
=> frequency bow: more informative but not always useful and sometimes crude
- risk of overfitting, model sensitive to repetitions and unnecessary overload for short texts
**TF-IDF** (weights frequency **and** word rarity)

in practice

|Objective|Recommended|
|---|---|
|Long text analysis|Frequency BoW + TF-IDF|
|Short text or simple presence|Binary BoW|
|Scale-sensitive model|Binary BoW or normalization|
|Unbalanced data|TF-IDF preferred|

### Transformer models pipeline:

[1] Raw text
   ↓
[2] Model tokenizer (integrated preprocessing)
   ↓
[3] Pre-trained model (BERT, GPT...) → extraction of representation vectors (embeddings)
   ↓
[4] Machine learning model or fine-tuning (logistic regression, SVM, MLP…)
   ↓
[5] Post-processing (labeling, visualization, decision, etc.)

You **don't need regex** to use a Transformer model, **but** you can use it to **improve input/output quality**, especially in production contexts or for specific tasks.