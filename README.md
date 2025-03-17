# Kaggle Completition: LLM Classification Finetunine

Large language models (LLMs) are rapidly entering our lives, but ensuring their responses resonate with users is critical for successful interaction. This competition presents a unique opportunity to tackle this challenge with real-world data and help us bridge the gap between LLM capability and human preference.

This completition utilized a large dataset collected from [Chatbot Arena](https://lmarena.ai), where users chat with two anonymous LLMs and choose the answer they prefer. My task in this competition is to predict which response a user will prefer in these head-to-head battles.

I plan to utilize and improve three different model architectures to complete this competition, and then analyze and compare their advantages and disadvantages.

## Dataset 
The dataset consists of user interactions from the ChatBot Arena. I have 2 data files: ‘train.csv’, ‘test.csv’ and 1 submission file: ‘sample_submission.csv’. And the training dataset detail follows below: 

- id: A unique identifier for the row.

- model_[a/b]: The identity of model_[a/b]. Included in train.csv but not test.csv.

- prompt: The prompt that was given as an input (to both models).

- respoonse_[a/b]: The response from model_[a/b] to the given prompt.

- winner_model_[a/b/tie]: The ground truth target column.


|id    |model_a           |model_b   |prompt                            |respoonse_a                                        |response_b|winner_model_a|winner_model_b|winner_model_tie|
|------|------------------|----------|----------------------------------|---------------------------------------------------|----------|--------------|--------------|--------------|
|30192|gpt-4-1106-preview|gpt-4-0613|Is it morally right to try to...|The question of whether it is morally right to...|As an AI, I don't have personal beliefs or ...|1|0|0|
|53567|koala-13b|gpt-4-0613|What is the difference between marriage...|A marriage license is a...|A marriage license and a marriage certificate...|0|1|0|

The Shape of Dataset: 

- Train Dataset(57477, 9): Total 19 Null response rows dropped. Totally I train 57458 samples.

- Test Dataset: (25000, 4) 


## Data Cleaning
I applied the `text_cleaning` function to preprocess the text data:

  - Converting all text to lowercase.

  - Replacing escaped forward slashes (\/) with regular slashes (/) and replacing tab characters (\t) with a space.
  
  - Removing any special characters from the text, allowing only letters, numbers, spaces, and a few punctuation marks (.,!?()).
  
  - Replacing multiple whitespace characters with a single space for consistency.
  
  - Stripping any leading or trailing whitespace.

Create Category Variable: It creates a new column named category by performing a dot product on three columns: winner_model_a, winner_model_b, and winner_tie, converting them into a single categorical variable.

## Model Construction
### XGBoost
I referenced the approach described in the [LLM Classification, Feature Engineering & XGBoost](https://www.kaggle.com/code/nikhilnb08/llm-classification-feature-engineering-xgboost) article. 

In the first part, I used Python’s `readability` library to extract fundamental features from the text data, which includes readability grades, sentence information, counts of nouns and verbs in the sentences, and sentence relationships. 

In the second part, I calculated correlations by assessing the similarities between the prompts and the responses from model A and model B. The correlation metrics used include cosine similarity, Euclidean distances, and Manhattan distances.

Based on the feature engineering described above, a total of **72 variables** were obtained.


## Reference
www.kaggle.com/competitions/llm-classification-finetuning/overview/$citation
