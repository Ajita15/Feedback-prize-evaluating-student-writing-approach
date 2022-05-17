# Feedback-prize-evaluating-student-writing-approach
- This repository contains the approach followed by me during this Kaggle competiton.  
- https://www.kaggle.com/competitions/feedback-prize-2021.
- You can download the dataset from the competition and play with it.

##  Approaches Followed
- Converted this problem into a token-classification problem i.e entity extraction.

## Data Preparation
- TO-DO- add more dataset explanation
- **feedback_nb1** - contains the code for data preparation.
    - For every file - tokenized it, added labels to each tokens. 


## Model Training and Evaluation
- Converted the dataset into the format required by BERT.
- These files are long sequences - i.e longer than 512 words (max_length BERT).
- Followed preprocessing steps to prepare training and validation dataset for BERT model.
- **feebback_nb5** notebook contains the training code.

## Model Inference Pipeline
- After saving the model, load the model and get predictions for the test dataset.
- **feedback-inference2-final** notebook - Creates an inference pipeline for the same.