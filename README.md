# InPE  

**When and How to Ask: Dynamic Preference Elicitation Strategies for Conversational Recommender Systems**

---

## Data Sources

This project is based on the following public resources:

### 1. Inspired Dataset
**Source:** [Inspired GitHub Repository](https://github.com/sweetpeach/Inspired)

**Note:**  
- train.tsv  
- dev.tsv  
- test.tsv  
- movie_database.tsv  

### 2. Supplementary Resource
**Source:** [inspired_cikm dataset (Hugging Face)](https://huggingface.co/datasets/ZhankuiHe/inspired_cikm)

**Note:**  
- entity2id.json  
- item_ids.json  

---

## Contents of This Repository

This repository contains **human annotation data** built on top of the Inspired dataset for studying preference elicitation strategies in conversational recommender systems.

### Annotation Format

Each file corresponds to a specific conversation turn, for example:

```json
{
  "conversation_id_0_turn_1.json": [
    {
      "1. Based on the users latest message, should the assistant ask questions to explore users preferences?": "Yes or Not sure",
      "2. Which of the following strategies would be most appropriate for assistant to generate questions? If none apply, please choose \"None of the above\".": "Item-based",
      "3. Below are four candidate responses generated using the strategy you selected. Which response fits best?": "A3. Item-based",
      "4. Do you think this response is better than the assistant’s latest response?": "Yes",
      "5. Why do you think this response is better than the original response?": "e_others"
    }
  ]
}
```

## Data Usage Notice

- The original datasets and supplementary resources are from their respective owners.
- No explicit license information was found for the original sources listed above.
- Therefore, this repository does **not** claim any rights over the original data.

Only the annotation results created and released in this repository are included here.  

## License

The annotation data in this repository is licensed under CC BY 4.0.

This license applies only to the annotations created by the authors.  
The original datasets are not included and may be subject to separate terms.
Users should obtain the original datasets from the official sources and ensure their own compliance with any applicable terms before use.

---
