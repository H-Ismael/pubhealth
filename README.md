# Fact check on claims from PUBHEALTH DATASET
The aim of this model is to predict the correct label associated with the claim based on claim and/or other columns.

## Table of content

### 1. Data exploration, preprocesing and feature analysis:
[Exploration and Preprocesing Notebook](https://github.com/H-Ismael/pubhealth/blob/main/exploration_preprocessing.ipynb).  


1.1. Data exploration.
- Loading data.  
- Prelimanary column/feature selection/elemination. 
    
1.2. Drop Missing Values.  

1.3. Check outliers.  
- Find and eliminate outliers in labels.

1.4. Check on Data balance and label distribution.  

1.5. Basic statistics on columns.  

1.5. PCA and TF-IDF for features insights.  

[PCA Notebook](https://github.com/H-Ismael/pubhealth/blob/main/PCA_insights.ipynb).  

- Conducting PCA on each column given considering tf-idf. 
- Notes in the notebook.  


### 2. Models training and data iteration:
2.1. Base model BERT.  
- Pretrained BERT was used on cleaned imbalanced dataset first.  
2.2. Iterate/modify model hyperparameters Data features (Enriching data based on **1.5.** results).  

2.3. BERT on balanced/undersampled data.  
2.4. RoBERTa trial. 
    
### 3. Obstacles and challenges:
- Consumed my 2 google colab GPU trails. 
- grid search could eventually not be considered due to the above reason.
- Hyperparameters tunning was done manually (guided by previous attempts of papers)
### 4. Results and remarks:
Base model : precision < 0.61 , loss : 1.3 with [{lr : 1e-3 , batch_size : 128, Epochs : 10}]
    
__________________________________________________________________________________
