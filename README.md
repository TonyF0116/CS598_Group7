# CS598_Group7

# Current state: Naive Retrieval-Augmented Generation (RAG) Evaluation

Our project now implements a naive RAG model for answering questions using the HotpotQA (http://curtis.ml.cmu.edu/datasets/hotpot/hotpot_train_v1.1.json) dataset. Three data retrieval approaches are evaluated on their efficacy in retrieving correct supporting facts for question answering tasks.

## Dataset

The code will automatically download the HotpotQA training dataset from 'http://curtis.ml.cmu.edu/datasets/hotpot/hotpot_train_v1.1.json' if it does not already exist. The dataset is saved in dataset/hotpot_dataset.json.

### Dataset Structure

The HotpotQA dataset contains important fields like:

- question: The question to be answered.
- context: A list of passages related to the question.
- supporting_facts: Specific supporting passages for answering the question.
- answer: The ground truth answer.

## Code Execution

The notebook includes several main steps:

1. **Dataset download and loading**: Downloads the HotpotQA dataset if not present and loads it into memory.
2. **Data preprocessing**: Adds a dictionary (context_d) to each data instance, where passage titles map to lists of sentences for faster reference.
3. **Model setup and evaluation**: Defines helper functions for answer and supporting fact accuracy evaluation.

To run the evaluation process, simply execute each cell of the notebook in sequence.

### RAG Approaches

Three methods are defined in naive_rag function to retrieve supporting facts:

1. **Single-Entry Approach**: All entries under each title are treated as one entry.
2. **Title-Entry Combination Approach**: Each entry is combined with its title and treated as one individual entry.
3. **Two-Stage Matching Approach**: Conduct similarity search of the query on both the title and the entries, then add up the scores.

## Results

The evaluation is based on the percentage of correct supporting fact retrievals for each approach.

- Approach 1: Accuracy ~0.526
- Approach 2: Accuracy ~0.196
- Approach 3: Accuracy ~0.26
