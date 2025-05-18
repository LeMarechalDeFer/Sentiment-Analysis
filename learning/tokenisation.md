| Criterion            | Word Tokens                  | Subwords / WordPieces              |
| -------------------- | ---------------------------- | ---------------------------------- |
| Unit                 | Whole word                   | Word piece (prefix, suffix)        |
| Vocabulary size      | Very large                   | Reduced (typically 10k-50k)        |
| Unknown words        | Impossible to handle         | Handled via subword composition    |
| Used by              | TF-IDF, BoW, older models    | BERT, GPT, T5, etc.                |

### 🔹 **Classic Token (word token)**

A **word token** is a complete word as it appears in a sentence, separated by spaces or punctuation.  
Example:

> Sentence: `"ChatGPT is impressive"`  
> Word tokens: `["ChatGPT", "is", "impressive"]`

✅ **Advantages:**

- Easy to understand and use
- Well represents surface "human" language

❌ **Disadvantages:**

- Huge vocabulary (millions of words)
- Unable to properly handle unknown or rare words (e.g., `"ChatGenius"` would be considered unknown)
---

### 🔹 **Subwords / WordPieces**

**Subwords** (or **wordpieces**, which is a specific subword method used by BERT) are text units **smaller than words** but **larger than characters**.  
They are automatically learned from a corpus to maximize coverage with a limited vocabulary.

Example (with WordPiece, used in BERT):

> `"impressive"` → `["imp", "##ression", "##nant"]`

The `##` symbol indicates a word continuation (suffix).

✅ **Advantages:**

- **Much smaller vocabulary** (e.g., 30,000 tokens in BERT)
- **Handles unknown or rare words**: an unseen word can be reconstructed using known pieces
- Good balance between performance and vocabulary size

❌ **Disadvantages:**

- Less intuitive
- Can sometimes "break" semantic structure (depending on granularity)