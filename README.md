# DSCC 251 Final Project: Active Learning for Financial News Risk Detection

Overview: 
This project explores whether uncertainty-based active learning can reduce the amount of labeled data needed to build an effective classifier for financial news sentiment. The main question is whether active learning strategies, like entropy and margin sampling, can outperform random sampling while using fewer labeled training examples.

Dataset:
This project uses the Financial PhraseBank dataset, which contains financial news sentences labeled as positive, negative, or neutral based on their expected impact on stock prices from an investor's perspective. 

I used the Sentences_75Agree.txt version of the dataset because it provides a good balance between dataset size and label reliability.

Methodology:
The project was developed in 2 stages (UPDATED):
1. Revised RoBERTa experiment - I first tested a RoBERTa-based classifier in a somewhat low-label setting, using an initial labeled set of 180 samples. This was meant to simulate a realistic setting where labeled financial data is limited. After switching to GPU, RoBERTa ran much faster.
   
2. Updated active learning pipeline - I then implemented a faster TF-IDF + logistic regression pipeline, and I split the dataset into: a test set, a training pool, an initial labeled set of 60 samples, and an unlabeled pool. The 3 strategies I tested were random, entropy, and margin sampling. In each round, the model was retrained after adding more labeled samples from the pool.

Repository Structure:
- notebooks: Contains the code files for RoBERTa (new baseline + active learning experiments) and TF-IDF+LR, and additional analysis (LR weights, keyword interpretation, TF-IDF clustering)
- README
- dscc251results2.zip: Contains images of the outputs after running the code (updated results, after improving RoBERTa)
- Additional Analysis.zip: Contains images of the outputs after running the additional analysis codebook 

Here's the link to download the Financial PhraseBank dataset: https://www.researchgate.net/publication/251231364_FinancialPhraseBank-v10

Instructions for how to run the code files: I developed and tested this project using Google Colab, so these instructions show how to run it on there.
1. Download and open the .ipynb files from the notebooks/ folder (the RoBERTa files take the longest to run).
2. Extract the Sentences_75Agree.txt file from the zipped Financial PhraseBank dataset, and upload that .txt file into the Colab session ("Files" tab on the left, "upload to session storage" button). Change the file path in the notebook if needed (e.g. /content/Sentences_75Agree.txt).
3. For the RoBERTa code files: go to the "Runtime" tab at the top, and hit "Change runtime type." Select T4 GPU, and save.
4. Run all code cells in order, these are the same instructions for running all the files.
