
|#|Main Topic|Sub-points identified in the document|
|---|---|---|
|1|**NLP Context & Evolution**|From feature-engineering to BERT, then to GPT and dialogue with a single model|
|2|**GPT Revolution: pre-training, fine-tuning & _in-context learning_**|GPT-1 → GPT-3, usage examples and performance|
|3|**Scaling Laws**|Size-data-compute-performance relationship; IsoFLOP concept|
|4|**Emergent Capabilities**|BIG-bench, "137 emergent abilities" and emergence definition|
|5|**Recent Open-Source Models**|LLaMA-2, Falcon-180B, BLOOM|
|6|**Prompting Paradigm**|Zero/one/few-shot, Chain-of-Thought, Self-Consistency, Generated-Knowledge, Least-to-Most, In-Context Impersonation|
|7|**Prompt Engineering & Fragility**|Format sensitivity, order sensitivity, AutoPrompt, prompt injection, false/neutral labels|
|8|**Analysis & Interpretability**|Attention heads (induction circuits), FFN neurons, n-gram / positional neurons|
|9|**Limitations & Famous Failures**|BPE "SolidGoldMagikarp", Iris dataset prompts, fixed bugs|

|Term|Short & Useful Definition|
|---|---|
|**LLM (Large Language Model)**|Language model with billions of parameters, trained to predict the next word on massive corpora.|
|**BERT**|Bidirectional encoder that generates contextual representations; pioneered the idea of a single reusable model for multiple tasks.|
|**GPT**|_Generative Pre-trained Transformer_; auto-regressive decoder architecture pre-trained then adapted (fine-tuning or simple prompting).|
|**Fine-tuning**|Supervised re-training of an LLM on task-specific data.|
|**In-context learning**|LLM's ability to learn from examples placed in the prompt, without weight updates.|
|**Zero/One/Few-shot**|Number of examples provided in the prompt (0, 1, 2+).|
|**Chain of Thought (CoT)**|Technique where the model is explicitly asked to "think step by step" before answering.|
|**Self-Consistency**|Aggregation of multiple chains of thought to improve robustness.|
|**Generated-Knowledge Prompting**|Model first generates useful facts, then reuses them as context.|
|**Least-to-Most Prompting**|Breaking down a complex problem into increasingly difficult subtasks.|
|**Prompt Injection**|Malicious bypass of initial prompt through user text.|
|**Scaling Law**|Empirical relationship: loss follows a power law of model size, data, and compute.|
|**Emergent Ability**|Capability that suddenly appears at a certain parameter/data scale, absent in smaller models.|
|**Attention Head / Induction Head**|Transformer subcomponent that learns, among other things, to copy [A]→[B] patterns seen in context.|
|**FFN Neuron**|Feed-forward layer neuron; some encode lexical or positional patterns.|
|**IsoFLOP**|Equal computation cost curve allowing comparison of different size × data combinations.|
|**BIG-bench**|Suite of 204 tasks evaluating LLM emergent capabilities.|
|**BPE (Byte-Pair Encoding)**|Tokenization algorithm; fusion errors can lead to inconsistent outputs.|

LSTM is Long Short Term Memory
RNN is Recurrent Neural Network 

positional encoding

BPE (byte pair encoding): - It's a **tokenization** method: breaking down a word into **frequent subunits** (subwords), for example:
    
    - `"unbelievable"` → `"un" + "believ" + "able"`
        
- Very useful for handling rare words, neologisms, or agglutinative languages.

scaling laws

inference

Input embedding is transforming each word (or token) into a vector of numbers that the model can understand

Self attention looks at all words in the sentence for context and this for each word
- query: word we're trying to understand
- key: what each word represents
- value: what we send if deemed relevant
=>