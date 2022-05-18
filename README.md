# Feedback-prize-evaluating-student-writing-approach
- This repository contains the approach followed by me during this Kaggle competiton.  
- https://www.kaggle.com/competitions/feedback-prize-2021.
- You can download the dataset from the competition and play with it.

##  Approaches Followed
- Converted this problem into a token-classification problem i.e entity extraction.

## Data Preparation
- Dataset Link - kaggle
- The dataset contains the sentences and their labels. Merged the sentences to the file they belonged to.
- Total number of training files - 15.6k
- Total number of labels - 15
- **feedback_nb1** - contains the code for data preparation.
    - For every file - tokenized it, added labels to each tokens.
    - Output - train_file_labels2.csv - this file will be used by subsequent notebooks for training. 


## Model Training and Evaluation
- Converted the dataset into the format required by BERT.
- These files are long sequences - i.e longer than 512 words (max_length BERT).
- Followed preprocessing steps to prepare training and validation dataset for BERT model.


### Model Training - Approach1
- The max_length this model can accept is 512.
- For each file, truncated it till 512 and then trained the model.
- feedback_nb3 notebook is used for training
    - input data is feedback_nb1/train_file_labels2.csv.
- **Model parameters**
    - MAX_LEN = 512
    - TRAIN_BATCH_SIZE = 2
    - VALID_BATCH_SIZE = 2
    - EPOCHS = 40
    - LEARNING_RATE = 1e-05
    - MAX_GRAD_NORM = 10
- **Model Inference**
    - For model inference also, truncated the test files till 512 tokens and then got the predictions.
    - Link to feedback_inference - this notebook is used for inference.

### Model Training - Approach2
- The max_length this model can accept is 512.
- So in this approach, divided each file into a batch of 512 tokens, in that way we don’t need to truncate the file content and as well there is no data loss.
- Trained the model using the BertForTokenClassification model. 
- feedback_nb5 notebook is used for training.
    - input data is feedback_nb1/train_file_labels2.csv.
- **Model parameters**
    - MAX_LEN = 512
    - TRAIN_BATCH_SIZE = 2
    - VALID_BATCH_SIZE = 2
    - EPOCHS = 25
    - LEARNING_RATE = 5e-05
    - MAX_GRAD_NORM = 10
- **Model Inference**
    - For model inference also, divided the test files into a batch of 512 tokens and then got the predictions.
    - feedback_inference2_final - This notebook is used for inference


### Comparison
- On the validation dataset, approach1 and approach2 f1-score were nearly the same for all classes.
- On the test-dataset i.e the final submission , approach2 performed better than approach1.
