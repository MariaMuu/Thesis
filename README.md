
---

### Project Pipeline Overview

1. **Dataset Acquisition**

   I obtained a large dataset from Kaggle (https://www.kaggle.com/datasets/thedevastator/unlock-smarter-querying-with-lc-quad-2-0) containing natural language questions paired with SPARQL queries targeting the Wikidata and DBpedia knowledge bases.

2. **Data Cleaning and Filtering**

   I preprocessed the dataset by cleaning the data and retaining only:

   * The natural language questions
   * The corresponding Wikidata answers (SPARQL queries)

3. **Prompt Formatting (Chat Structure Design)**

   I formatted the dataset into a structured chat-style format suitable for fine-tuning. This included adding explicit role-based tokens such as:

   * `system`, `user`, and `assistant` roles
   * Proper **prefix and suffix formatting** for each training example

   This step ensured that each sample followed a consistent conversational structure, improving the model’s ability to generalize to instruction-following behavior.

4. **Train/Test Split**

   The formatted dataset was split into training and testing sets to properly evaluate performance and reduce overfitting risk.

5. **Fine-Tuning the Language Model**

   I fine-tuned GPT-4.1 Mini with OpenAI API supervised fine-tuning (SFT) on the training dataset to enable:

   * Translation of natural language questions into valid SPARQL queries
   * Accurate mapping of entity identifiers from Wikidata

   The training was run for **5 epochs**. Before starting the process, I used **tiktoken** to estimate token usage and calculate the expected cost of fine-tuning.

---

### Observations and Issues

Although the fine-tuning training process showed good convergence in both training loss and validation loss, some limitations were observed:

* The model occasionally **hallucinated Wikidata entity IDs**, generating invalid or non-existent identifiers.
* In some cases, the **SPARQL query structure was incorrect**, leading to execution errors.

---


