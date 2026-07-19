# When and How to Ask: Dynamic Preference Elicitation Strategies for Conversational Recommender Systems

This repository provides resources developed within the following article:

>  F. Xia, S. Zhang and X. Wang When and How to Ask: Dynamic Preference Elicitation Strategies for Conversational Recommender Systems. In: Proceedings of SIGIR 2026, July 2026.

## Summary

Conversational Recommender Systems (CRSs) use multi-turn dialogue to capture evolving user preferences and deliver personalized recommendations. While prior work mainly focuses on static, attribute-based elicitation, the role of item-based strategies and their timing remains underexplored. This work studies preference elicitation from a stage-aware perspective, showing that optimal strategies are context-dependent: attribute-based methods work better early on, while item-based approaches become more effective as preferences refine. To support this, we introduce **InPE**, a dataset with fine-grained annotations for elicitation necessity and strategy selection.

## Dataset InPE

To enable a fine-grained analysis of preference elicitation strategies across different dialogue stages, we introduce **InPE**, an annotated and augmented version of the [INSPIRED dataset](https://github.com/sweetpeach/Inspired). 

### Description
For each dialogue turn identified by the LLM filter, annotators first verify whether preference elicitation is required based on the context; turns without this intent are excluded. For eligible turns, annotators classify the elicitation strategy as attribute-based, item-based, or hybrid (i.e., using both items and attributes). The system then provides multiple candidate responses under the selected strategy, and annotators choose the most appropriate one. Finally, annotators assess whether the selected response improves upon the original system utterance. If not, the annotation ends; otherwise, annotators record the reasons for improvement and submit the result.

- **conversation_id_{dialogue_id}_turn_{turn_id}**  
  A unique identifier for each data sample, composed of:
  - `dialogue_id`: the ID of the full conversation
  - `turn_id`: the index of the turn within that conversation

- **Dataset Split Mapping**  
  The dataset is divided into three subsets based on `dialogue_id`, as defined in the [inspired_cikm dataset](https://huggingface.co/datasets/ZhankuiHe/inspired_cikm), which is an extension of the [INSPIRED dataset](https://github.com/sweetpeach/Inspired):

  - **Train**: `dialogue_id = 198 ~ `
  - **Validation**: `dialogue_id = 0 ~ 98`
  - **Test**: `dialogue_id = 99 ~ 197`

### Annotation Questions

- **1. Based on the users latest message, should the assistant ask questions to explore users preferences?**  
  A. No  
  B. Yes or Not sure  

- **2. Which of the following strategies would be most appropriate for assistant to generate questions?**  
  A. Item-based  
  B. Attribute-based  
  C. Hybrid  
  D. d_none_of_the_above  

- **3. Below are four candidate responses generated using the strategy you selected. Which response fits best?**  
  A / B / C + 1 / 2 / 3 + Attribute-based / Item-based / Hybrid  

- **4. Do you think this response is better than the assistant’s latest response?**  
  A. Yes  
  B. No  

- **5. Why do you think this response is better than the original response?**  
  A. Information Sufficiency  
  B. Control  
  C. Efficiency  
  D. Preference Expression Sufficiency  
  E. e_others

### Annotation Format

Each data corresponds to a specific conversation turn, for example:

```json
{
  "conversation_id_0_turn_1.json": [
    {
      "1. Based on the users latest message, should the assistant ask questions to explore users preferences?": "B",
      "2. Which of the following strategies would be most appropriate for assistant to generate questions? If none apply, please choose \"None of the above\".": "A",
      "3. Below are four candidate responses generated using the strategy you selected. Which response fits best?": "C",
      "4. Do you think this response is better than the assistant’s latest response?": "A",
      "5. Why do you think this response is better than the original response?": "E"
    }
  ]
}
```

### Recommendation
For the recommendation part, you can find movie IDs and metadata in `entity2id.json`, `item_ids.json`, and `movie_database.tsv` with dialogue ID from the [inspired_cikm dataset](https://huggingface.co/datasets/ZhankuiHe/inspired_cikm).

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

## Citation
If you use the resources presented in this repository, please cite:
```
@inproceedings{xia2026and,
  title={When and How to Ask: Dynamic Preference Elicitation Strategies for Conversational Recommendation},
  author={Xia, Feng and Zhang, Shuo and Wang, Xi},
  booktitle={Proceedings of the 49th International ACM SIGIR Conference on Research and Development in Information Retrieval},
  pages={2039--2048},
  year={2026}
}
```

---
