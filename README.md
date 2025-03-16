# Kaggle Completition: LLM Classification Finetunine

Large language models (LLMs) are rapidly entering our lives, but ensuring their responses resonate with users is critical for successful interaction. This competition presents a unique opportunity to tackle this challenge with real-world data and help us bridge the gap between LLM capability and human preference.

This completition utilized a large dataset collected from [Chatbot Arena](https://lmarena.ai), where users chat with two anonymous LLMs and choose the answer they prefer. My task in this competition is to predict which response a user will prefer in these head-to-head battles.

I plan to utilize and improve three different model architectures to complete this competition, and then analyze and compare their advantages and disadvantages.

### Dataset 
The dataset consists of user interactions from the ChatBot Arena. In each user interaction a judge provides one or more prompts to two different large language models, and then indicates which of the models gave the more satisfactory response. And the dataset detail follows below: 

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
