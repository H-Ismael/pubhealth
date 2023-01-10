# Fact check on claims from PUBHEALTH dataset
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
- Save clean data.

1.4. Check on Data balance and label distribution.  

1.5. Basic statistics on columns.  

1.6. PCA and TF-IDF for features insights.  

[PCA Notebook](https://github.com/H-Ismael/pubhealth/blob/main/PCA_insights.ipynb).  

- Conducting PCA on each column given considering tf-idf. 
- 'Subjects' column seems to expose quite the pattern.  
- Notes in the notebook.  


### 2. Models training and data iteration:  

2.1. Base model BERT.  
- Pretrained BERT was used on cleaned imbalanced dataset first.  

2.2. Iterate/modify model hyperparameters Data features (Enriching data based on **1.5.** results).  

2.3. BERT on [balanced/undersampled](https://github.com/H-Ismael/pubhealth/blob/main/data_balancing.ipynb) data. 

2.4. RoBERTa trial. 
    
### 3. Obstacles and challenges:
- Consumed my 2 google colab GPU trails. 
- Grid search could eventually not be considered due to the above reason.
- Hyperparameters tunning was done manually (guided by previous attempts of papers).Also sometimes in place iteration had to be done which may make models diversity diffcult to follow.  

### 4. Results and remarks:

- BERTA : accuracy < 0.61 , loss : 1.3 , F1 : 60 best ,Data : **Imbalanced**. From  combinations of the following [{lr : 1e-3 , batch_size : 128, Epochs : 10} , {lr : 1e-4 , batch_size : 64, Epochs : 12}].  

- BERTA : accuracy < 0.57 , loss : 1.1 , F1 : 62 best ,Data : **Balanced**. From  combinations of the following [{lr : 1e-3 , batch_size : 128, Epochs : 10} , {lr : 1e-4 , batch_size : 64, Epochs : 12}].  

### **Note**  :
Balancing decreased the precision and eventually due to more equal contribution of different labels/classes the F1_score increased.

- BERTA : accuracy < 0.67 , loss : 0.92 , F1 : 60 best ,Data : **Enriched (concatenated) with column 'Subjects'**. From  combinations of the following [{lr : 1e-3 , batch_size : 64, Epochs : 10} , {lr : 1e-4 , batch_size : 8 , Epochs : 12}].  

- RoBERTa : accuracy < 0.64 , loss : 0.83 , F1 : 64 best ,Data : **Enriched (concatenated) with column 'Subjects'**. From  combinations of the following [{lr : 1e-4 , batch_size : 64, Epochs : 10} , {lr : 1e-4 , batch_size : 8, Epochs : 12}].  

Next inline: DeBERTa.


### 4. Conclusion:

RoBERTa seems the best fitting model but still far from acceptable results though results from previous work using DeBERTa v3 did also great (testing in progress).

____________________________________________________________________________________________________________
