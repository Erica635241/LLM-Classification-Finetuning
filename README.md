# Kaggle Completition: LLM Classification Finetunine

In this competition, the challenge was to predict which responses users will prefer in a head-to-head battle between chatbots powered by large language models (LLMs). Using a dataset of conversations from the [Chatbot Arena](https://lmarena.ai), where different LLMs generated answers to user prompts. 

### Dataset 

- id: A unique identifier for the row.

- model_[a/b]: The identity of model_[a/b]. Included in train.csv but not test.csv.

- prompt: The prompt that was given as an input (to both models).

- respoonse_[a/b]: The response from model_[a/b] to the given prompt.

- winner_model: The ground truth target column markered including a, b, tie.


|id   |model_a           |model_b   |prompt                            |respoonse_a                                        |response_b|winner_model|
|------|------------------|----------|----------------------------------|---------------------------------------------------|----------|--------------|
|30192|gpt-4-1106-preview|gpt-4-0613|Is it morally right to try to...|The question of whether it is morally right to...|As an AI, I don't have personal beliefs or ...|a|
|53567|koala-13b|gpt-4-0613|What is the difference between marriage...|A marriage license is a...|A marriage license and a marriage certificate...|b|

### Reference
www.kaggle.com/competitions/llm-classification-finetuning/overview/$citation
