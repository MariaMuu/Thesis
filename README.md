
---

### Project Pipeline Overview

1. **Dataset Acquisition**
   I obtained a large dataset from Kaggle (https://www.kaggle.com/datasets/thedevastator/unlock-smarter-querying-with-lc-quad-2-0) containing natural language questions paired with SPARQL queries targeting the Wikidata and DBpedia knowledge bases.

2. **Data Cleaning and Filtering**
   I preprocessed the dataset by cleaning the data and retaining only:

   * The natural language questions
   * The corresponding Wikidata answers (SPARQL targets)

3. **Train/Test Split**
   The cleaned dataset was split into training and testing sets to evaluate model performance properly and avoid overfitting.

4. **Fine-Tuning the Language Model**
   I fine-tuned GPT-4.1 Mini on the training dataset to learn how to:

   * Translate natural language questions into correct SPARQL queries
   * Map entity identifiers accurately within Wikidata

   The training was performed over **5 epochs**. Prior to training, I used **tiktoken** to estimate token usage and calculate the expected cost of the fine-tuning process.

---

### Observations and Issues

Although the fine-tuning process showed generally good performance, several issues were observed:

* The model occasionally **hallucinated Wikidata IDs**, producing invalid or non-existent entity identifiers.
* In some cases, the **structure of the generated SPARQL queries was syntactically incorrect**, leading to execution failures.

---
