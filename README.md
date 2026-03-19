# Assignment 2 Notebook Setup

This repository contains the notebook [`code/GenAISWE_Assignment_2_Sam_Bennett.ipynb`](/Users/sambennett/Desktop/CSCI555/assignment_2_clean/code/GenAISWE_Assignment_2_Sam_Bennett.ipynb), which should be run from the repository root.

## Prerequisites

- Python 3.12.9 and Jupyter Notebook installed

## Setup

Run the following steps from the repository root:

1. Create and activate a Python 3.12 virtual environment:

```bash
python3.12 -m venv .venv
source .venv/bin/activate
```

2. Install the notebook dependencies:

```bash
pip install -r working_requirements.txt
```

3. Download the SIDE checkpoint:

```bash
mkdir -p data/side_checkpoint && \
gdown --folder "https://drive.google.com/drive/folders/1OTqpr5tFWAeh_zdEZiIi6uSZ_JIxAa5n" -O data/side_checkpoint
```

4. Add an IPython kernel for the virtual environment:

```bash
python -m ipykernel install --user --name=csci555-venv --display-name "Python (assignment2-venv)"
```

5. Add your GitHub authentication token to reduce API rate limiting used by the notebook:

```bash
export GITHUB_TOKEN=your_github_token_here
```

## Run The Notebook

Start Jupyter Notebook from the repository root:

```bash
jupyter notebook code/GenAISWE_Assignment_2_Sam_Bennett.ipynb
```

When the notebook opens:

1. Use the kernel selector in the top-right corner.
2. Choose `Python (assignment2-venv)`.

## Notes

- The notebook reads `GITHUB_TOKEN` from the environment when making GitHub API requests.
- If the token is not set, the notebook will still run, but GitHub API calls may be rate-limited.

## Intermediate Outputs
All data produced or consumed by the notebook lives under `data/`.

- `data/java_summary_repos`: local clone directory for the Java GitHub repositories mined during dataset construction.
- `data/dataset_construction_audits`: audit artifacts from dataset mining and filtering, including snapshots of raw mined method-summary pairs, dropped-example audits, comment-miss audits, English-filter audits, and repository yield reports.
- `data/code_summarization_dataset`: the cleaned dataset used for training and validation. The notebook writes `train_code.txt`, `train_summary.txt`, `val_code.txt`, and `val_summary.txt` here.
- `data/code_summarization_dataset/embeddings`: CodeT5-based serialized embedding/tokenization artifacts generated from the train and validation text files, including `train_code.pt`, `train_summary.pt`, `val_code.pt`, and `val_summary.pt`.
- `data/lstm_checkpoints`: saved LSTM model checkpoints from training, including the best validation checkpoint used later for evaluation.
- `data/test_data`: test-set inputs and evaluation artifacts used in the notebook's final evaluation stage, including the tokenized test CSV.
- `data/test_data/results`: generated test predictions and computed evaluation metrics, such as the saved JSON outputs for predicted summaries and metric reports.
- `data/side_checkpoint`: downloaded local SIDE model checkpoint files used to compute SIDE scores during evaluation.
