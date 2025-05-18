| Model                  | Typical cloud inference cost                                               | Notes                 |
| ----------------------- | ----------------------------------------------------------------------------- | ------------------------- |
| **FastText**            | 🪙 Around **$0.001 – 0.01 per 1000 requests**                               | Very light, CPU sufficient |
| **GPT-4 / GPT-3.5**     | 💸 **$0.01 – 0.10 per request**, or **~$10-20/h** if massively used | Memory + GPU intensive    |
| **DistilBERT / MiniLM** | 🟡 In between, ~**$0.5-1/h** if self-hosted                              | Excellent compromise       |

Use:

- `distilbert-base-uncased`
- `MiniLM`
- `albert-base-v2`

You can **fine-tune** and **self-host** them for <$1/h with a T4/A10 GPU on affordable cloud platforms (e.g., RunPod, Vast.ai, Lambda Labs).