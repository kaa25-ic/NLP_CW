# NLP Coursework — PCL Detection

This repository contains my solution for **Patronising and Condescending Language (PCL) detection** proposed in SemEval-2022 Task 4 for the purposes of Imperial College London NLP CW submission. It uses **RoBERTa-base** model with data preprocessing and hyperparameter tuning.

Key Files:
- BestModel artifacts in /BestModel
- BestModel training in /Code/NLP_CW_Modeling.ipynb (note that this file contains full training and a number of experiments, the best model training can be found at the end under section 6. BestModel)
- Final predictions for **official dev** and **official test** sets (`dev.txt`, `test.txt`)
- Work is divided into three notebooks in /Code: EDA, Modeling, and Evaluation

The project includes:
- Exploratory Data Analysis (EDA)
- Model training + hyperparameter tuning (BestModel)
- Local evaluation (ablation + error analysis)

## Repository structure

```text
NLP_CW/
├── Additional/
│   └── figures/                 # Saved plots (EDA + evaluation visuals)
│       └── exp5.txt             # baseline model predictions
├── BestModel/                   # Exported HuggingFace model artifacts
│   ├── config.json
│   ├── model.safetensors
│   ├── tokenizer_config.json
│   ├── tokenizer.json
│   └── training_args.bin
├── Code/
│   ├── NLP_CW_EDA.ipynb          # EDA notebook
│   ├── NLP_CW_Evaluation.ipynb   # Local evaluation: ablation + error analysis
│   └── NLP_CW_Modeling.ipynb     # Training + tuning + experiments
├── Data/
│   ├── dev_semeval_parids-labels.csv
│   ├── train_semeval_parids-labels.csv
│   ├── dont_patronize_me.py      # Official loader utility
│   ├── dontpatronizeme_pcl.tsv   # Official dataset
│   └── task4_test.tsv            # Official unlabeled test set
├── dev.txt                        # predictions on official dev set
├── test.txt                       # predictions on official test set
├── Report.pdf                     # Final submitted report
└── requirements.txt
---

## Environment setup
```bash
pip install -r requirements.txt
```

## How to run:
1. Clone the repo from GitHub.
2. For easiest setup move data files to the root of the directory or add the path to data loading cells.
3. Run the notebooks in any order, they are independent.
4. NLP_CW_Modeling.ipynb is also available on Colab for GPU utilization: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/kaa25-ic/NLP_CW/blob/main/Code/NLP_CW_Modeling.ipynb)
5. Run Code/NLP_CW_Modeling.ipynb → Section 6 (BestModel) to train and generate dev.txt/test.txt.
6. Run Code/NLP_CW_EDA.ipynb to reproduce EDA tables/figures.
7. Run Code/NLP_CW_Evaluation.ipynb to reproduce evaluation tables/figures.

> **Model weights (Git LFS):** This repo uses Git LFS for `BestModel/model.safetensors`.
> If you clone the repo, install Git LFS first:
```bash
git lfs install
git clone https://github.com/kaa25-ic/NLP_CW.git
cd NLP_CW
git lfs pull
```