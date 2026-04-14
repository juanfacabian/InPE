# When and How to Ask: Dynamic Preference Elicitation Strategies for Conversational Recommender Systems

This repository provides resources developed within the following article:

>  F. Xia, S. Zhang and X. Wang When and How to Ask: Dynamic Preference Elicitation Strategies for Conversational Recommender Systems. In: Proceedings of SIGIR 2026, July 2026.

## Summary

Conversational Recommender Systems (CRSs) are interactive systems that use multi-turn natural language dialogue to understand evolving user preferences and provide personalized recommendations. To achieve this goal, CRSs rely on preference elicitation strategies to actively gather informative preference cues from users; however, the timing and selection of these strategies during a conversation remain largely unexplored. While many existing studies emphasize eliciting explicit item attributes and tend to adopt relatively static elicitation strategies, the use of item-based preference elicitation and its variation across different dialogue stages remains less explored. In this work, we conduct a systematic investigation of preference elicitation strategies from a stage-aware perspective. We provide empirical evidence that optimal preference elicitation strategies are stage-dependent and context-sensitive: attribute-based inquiries are effective in early stages, while item-based strategies become superior as preferences refine. To support this paradigm, we introduce **InPE**, a dataset enriched with fine-grained annotations for elicitation necessity and strategy selection. With this dataset, we propose **COPE** (**CO**nversational **P**reference **E**licitation via Mixture of Experts), a novel architecture for strategy modeling. Extensive offline evaluation and pairwise human evaluation on our dataset indicate that context-aware preference elicitation strategies are beneficial for conversational recommendation. In addition, analysis of the predicted strategies uncovers consistent stage-wise tendencies in dialogue progression, providing empirical evidence of common interaction patterns in conversational recommendation systems.

## Dataset InPE

To enable a fine-grained analysis of preference elicitation strategies across different dialogue stages, we introduce **InPE**, an annotated and augmented version of the [INSPIRED dataset](https://github.com/sweetpeach/Inspired). 

### Description
  For each dialogue turn identified by the LLM filter, annotators first review the context to validate whether preference elicitation is genuinely required. Turns lacking this intent are excluded from further annotation. For eligible turns, annotators classify the elicitation strategy used by the system as attribute-based, item-based, or hybrid. Note that hybrid strategies indicate that the system considers both items and attributes for joint preferences elicitation. Next, for each eligible turn, the system provides multiple candidate responses generated under the selected strategy, and annotators choose the most appropriate response. Annotators then assess whether the selected response constitutes an improvement over the original system utterance. If no improvement is identified, annotation for that turn ends; otherwise, annotators record the corresponding reasons for the improvement and submit the annotation.

- **conversation_id_{dialogue_id}_turn_{turn_id}**  
  A unique identifier for each data sample, composed of:
  - `dialogue_id`: the ID of the full conversation
  - `turn_id`: the index of the turn within that conversation

- **Dataset Split Mapping**  
  The dataset is divided into three subsets based on `dialogue_id`, as defined in the [inspired_cikm dataset](https://huggingface.co/datasets/ZhankuiHe/inspired_cikm), which is an extension of the [INSPIRED dataset](https://github.com/sweetpeach/Inspired):

  - **Train**: `dialogue_id = 198 ~ `
  - **Validation**: `dialogue_id = 0 ~ 98`
  - **Test**: `dialogue_id = 99 ~ 197`
  
- **Question 1 Based on the users latest message, should the assistant ask questions to explore users preferences?**  
  A. No  
  B. Yes or Not sure  

- **Question 2 Which of the following strategies would be most appropriate for assistant to generate questions?**  
  A. Item-based  
  B. Attribute-based  
  C. Hybrid  
  D. d_none_of_the_above  

- **Question 3 Below are four candidate responses generated using the strategy you selected. Which response fits best?**  
  A / B / C + 1 / 2 / 3 + Attribute-based / Item-based / Hybrid  

- **Question 4 Do you think this response is better than the assistant’s latest response?**  
  A. Yes  
  B. No  

- **Question 5 Why do you think this response is better than the original response?**  
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
      "1. Based on the users latest message, should the assistant ask questions to explore users preferences?": "Yes or Not sure",
      "2. Which of the following strategies would be most appropriate for assistant to generate questions? If none apply, please choose \"None of the above\".": "Item-based",
      "3. Below are four candidate responses generated using the strategy you selected. Which response fits best?": "A3. Item-based",
      "4. Do you think this response is better than the assistant’s latest response?": "Yes",
      "5. Why do you think this response is better than the original response?": "e_others"
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
```

---
