<img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/579461d7-efb9-469c-a1ce-c25fe618199b" />

# AbuelaBot

## Overview
This repository contains AbuelaBot, a Spanish-language fine-tuned model designed to emulate the warm, culturally rich advice of a Puerto Rican grandmother. The model was tuned on a custom dataset of Puerto Rican sayings, advice, and cultural expressions to produce affectionate, culturally authentic responses. The goal is to explore how fine-tuning can adapt a base large language model (LLM) to a highly specific persona while preserving fluency and coherence.

## Summary of Work Done
AbuelaBot takes in user questions, either in Spanish or English, and replies in the style of a Puerto Rican abuela.
The project compares model responses before and after fine-tuning to evaluate improvements in cultural tone, relevance, and warmth.

Two evaluation phases were performed:
   - Base Model: Qwen2.5 7B 
   - Fine-Tuned Model: Same base model fine-tuned using LoRA on a custom dataset (abuela_dataset.jsonl)

A fixed set of 7 culturally relevant questions was asked to both models, and responses were saved for comparison. I only used 7 questions for the evaluation becasue the data that the model was tuned on was small. 

## Data 
**Type:** Instruction dataset (.jsonl and csv versions avaliable)
**Name:** abuela_dataset.jsonl
**Format:** Alpaca-style instruction–response pairs
**Total Entries:** 127
**Source:** Manually compiled from:
  - https://tayaboa.blogspot.com/2018/03/refranes-mas-comunes-en-puerto-rico.html
  - https://www.openslr.org/74/
  - https://www.youtube.com/watch?v=zx_B-C4nEH8
  - https://www.pinterest.com/pin/59039445100529806/
  

## Training 
**Software:** Google Colab, Pandas, PyTorch, Transformers, Unsloth, PEFT, Gradio
**Hardware:** NVIDIA T4 GPU (Colab)
**Base Model:** unsloth/Qwen2.5-7B
**Fine-Tuning Method:** LoRA (Low-Rank Adaptation)
**Parameters:**
  - Epochs: 3
  - Learning Rate: 2e-4
  - Batch Size: 1
  - Max Sequence Length: 2048
  - Precision: 4-bit quantization


## Evaluation 
A fixed evaluation question set was created. For each question I recorded the base response and fine-tuned response

### Base Model Eval 
<img width="694" height="471" alt="Screenshot 2025-08-11 003350" src="https://github.com/user-attachments/assets/427f93ce-a26c-4402-b850-e0c7feaf9f48" />

### Fine-tuned Model Eval 
<img width="710" height="168" alt="Screenshot 2025-08-11 002122" src="https://github.com/user-attachments/assets/0cf96c6c-4a6c-42aa-a258-bd919425ac61" />


## Roadblocks



## Conclusion 
This project demonstrated how fine-tuning a large language model on a small but culturally specific dataset can dramatically change its tone, vocabulary, and personality.
The fine-tuned AbuelaBot provided warmer, more culturally grounded answers than the base model.

## Future Work 
To improve AbuelaBot, the first priority would be expanding the dataset. The current dataset is relatively small, and I believe that having more diverse and representative examples would significantly enhance the model’s performance. I would also like to experiment with different base models. I initially chose Qwen2.5 7B for its multilingual capabilities and manageable size, but testing other architectures could lead to better results. Another improvement would be integrating voice input and output, allowing the model to capture subtle nuances in conversational tone and delivery. Finally, adding a user-friendly interface similar to ChatGPT would make it easier for people to interact with AbuelaBot in a natural, conversational way. I attempted to use gradio to include a UI for interacting with AbuelaBot, but was not able to deploy in the timeframe given.


## How to reproduce results 
1.) Download the dataset (abuela_dataset.jsonl)
2.) Install dependencies: pip install -U transformers datasets peft bitsandbytes gradio unsloth
3.) Load the base model (unsloth/Qwen2.5-7B)
4.) Fine-tune with LoRA using the notebook provided (finetuned_Owen2_5_7B_Alpaca(2).ipynb)
5.) Deploy locally using notebook (abuela_chatbot.ipynb)


##  Overivew of Files 
File	Description
  - abu_data - Sheet1 (1).csv: dataset in CSV format
  - abuela_dataset.jsonl: dataset in json format
  - abuelabot_chatbot.ipynb:	this file runs the fine-tuned model and asks the evaluation questions
  - base_responses.ipynb:	this file runs the base model (not fine-tuned) and asks the evaluation questions
  - finetuned_Qwen2_5_7B_Alpaca (2).ipynb:	Fine-tuning notebook for Qwen2.5 7B using LoRA
  - Qwen2_5_(7B)_Alpaca (2).ipynb:	this file contains the notebook provided by unsloth for fine-tuning 



## Software Setup 
| Package        | Version (or Minimum) |
|----------------|----------------------|
| `transformers` | >= 4.37               |
| `datasets`     | >= 2.16               |
| `peft`         | >= 0.7                |
| `bitsandbytes` | >= 0.41               |
| `gradio`       | >= 4.0                |
| `unsloth`      | latest                |
| `torch`        | >= 2.0                |
| `pandas`       | >= 1.5                |













