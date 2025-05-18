### 🔹 BoW = Bag of Words

This is a **very simple** method to transform text into numerical vectors:

- We create a **vocabulary** (list of all words seen in the corpus)
- Each document is represented by a **frequency vector** (or presence) of words

Yes, **with BoW**, each document is represented by a **vector of size equal to the total number of words in the vocabulary** (often thousands or even millions of dimensions).  
➡️ It's a **sparse vector** (mostly composed of 0s).

|Term|Content|Memory Representation|
|---|---|---|
|Dense vector|Majority of values ≠ 0|Stores all elements|
|Sparse vector|Majority of zeros|Stores only non-zero values|
|Dense matrix|Same logic as dense vector, in 2D||
|Sparse matrix|Represents a sparse 2D array (lots of zeros)||

| Term         | Content                        | Default Storage                  |
| ------------- | ------------------------------ | -------------------------------- |
| Sparse vector | Majority of zeros              | Can be stored dense **or** sparse |
| Dense vector  | Majority of non-zero values    | Stored dense (classic)           |
| Sparse matrix | Lots of zeros in 2D            | Compact representation (type `csr`) |

| Property            | Sparse Vector               | Dense Vector                     |
| -------------------- | --------------------------- | -------------------------------- |
| Size                | Large (ex: 10,000)          | Small (ex: 300)                  |
| Fill                | Mostly zeros                | Almost all non-zero numbers      |
| Memory used         | Low (optimized)             | Medium to high                   |
| Similarity calculation | Slower without optimization | Fast and adapted to models       |
➡️ **BoW, TF-IDF, one-hot** algorithms produce **sparse vectors**  
➡️ **Embeddings (Word2Vec, BERT, etc.)** produce **dense vectors**

#### Example:

Corpus:
- Doc 1: "black cat"
- Doc 2: "white dog"

Vocabulary = `["cat", "black", "dog", "white"]`

Then:
- Doc 1 → `[1, 1, 0, 0]`    
- Doc 2 → `[0, 0, 1, 1]`

📌 **Note**: Words are represented **by indices**, **without context**, **without semantic similarity**.

| Criterion                     | BoW                  | Embedding (Word2Vec, BERT, etc.) |
| --------------------------- | -------------------- | -------------------------------- |
| Type                        | Sparse vector        | Dense vector                     |
| Size                        | equal to vocabulary  | generally 100 to 1,000           |
| Encodes meaning?            | ❌ No                 | ✅ Yes                           |
| Uses context?              | ❌ No                 | ✅ Yes (for contextual models)    |
| Machine learning?          | ❌ No (manual)        | ✅ Yes (trained on corpus)        |

| Method        | Included Step              | Type                               | Examples              |
| -------------- | -------------------------- | ---------------------------------- | --------------------- |
| **BoW**        | After tokenization         | Manual vectorization (sparse)      | `[0, 1, 2, 0, 1]`     |
| **TF-IDF**     | After BoW                  | Finer weighting                    | same but weighted     |
| **Embeddings** | Trained with models        | Dense and semantic representation  | Word2Vec, GloVe, BERT |