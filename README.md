# CMPE255-KoyotoIDS
Anomaly-based intrusion detection system that aims to detect malicious traffic over a network. For this project, three learning models were assessed: random forest, xgboost, and neural networks.

## How to Run
1. Install Kyoto-IDSv13.ipynb with Data directory
2. Install the data from https://www.takakura.com/Kyoto_data/new_data201704/ (Note: 2015 data was used)
3. Extract the data into the Data directory, storing the extracted month folder in /Data
4. Execute the notebook in order

## Tools Used
Languages: Python
Tools: Jupyter Notebook

## Process

### Preprocessing
The first step for this project is to inspect the data to understand what type of preprocessing needs to be done. Based on [Kyoto Unversity's documentation](https://www.takakura.com/Kyoto_data/BenchmarkData-Description-New.pdf), this dataset includes 24 features. Once the data is loaded, these features were added as the columns on the dataset for future reference. <br>
![image](https://github.com/user-attachments/assets/cd29cc81-205f-4551-9f16-e1c4da7a8b48)
<br>
<br>

The next step is to verify that there is no missing values in the dataset. Once the data is thoroughly analyzed, the next step is to encode any string values for future processing. For encoding the data, one hot encoding was used. The three main features that were encoded would include service type, flag, and protocol. This decision was made since these attributes had less than 10 unique values, causing the attributes to only expand up to 42 attributes. The encoded data can be seen in the following image: <br>
![image](https://github.com/user-attachments/assets/d0efcec0-cafa-43aa-afba-828760ade8b4)
<br>
<br>

Further processing is required, in addition to dimensionality reduction. To drop the most irrelevant columns, mutual information was used. This can be seen in the following two images, where the remaining columns were ranked and only the top 90% were kept.
![image](https://github.com/user-attachments/assets/aa82625c-f09e-48e3-a1fc-2344815a0503)
![image](https://github.com/user-attachments/assets/f1f460b2-9b14-467e-b71d-80f17d3319f9)
<br>
<br>

Alongside mutual information, feature importance was used to capture the most important features within the set.
![image](https://github.com/user-attachments/assets/7a19123e-1270-4d15-9ebe-5400738e9487)
![image](https://github.com/user-attachments/assets/fc22e41e-1193-4407-841c-a7a1e05d660a)
<br>
<br>

Upon completion, the features were reduced from 42 down to 6. 
### Models, Post-Processing & Evaluation
Three models were used for classification: random forest, xgboost, and neural networks. Before modeling, the data was split in 30-70 ratio, for testing/training. The accuracy and ROC curve was computed to evaluate each model. The following output for each model can be seen below:
<br>
#### XGBoost
![image](https://github.com/user-attachments/assets/aa676f76-336e-4883-8834-aa4b8e60adc1)
![image](https://github.com/user-attachments/assets/1793eca0-1889-44ad-bcab-bd96a3941581)
![image](https://github.com/user-attachments/assets/e6f1e2f9-d85f-4a28-9259-87ba909a00b1)

#### Random Forest
![image](https://github.com/user-attachments/assets/b8c447bc-5251-4c41-83b2-305a751e2040)
![image](https://github.com/user-attachments/assets/940d1677-87c9-4253-96e0-752f5956aeca)
![image](https://github.com/user-attachments/assets/2afdca68-6860-4a66-9149-791ca27099ad)

#### Neural Networks
![image](https://github.com/user-attachments/assets/fb5e8ae8-354a-4188-b589-860c4c135804)
![image](https://github.com/user-attachments/assets/5f6743f2-c079-4367-b953-76e7ee3ecbd3)
![image](https://github.com/user-attachments/assets/fad52bcc-53c7-43b8-bde4-0e59dab9e6e8)

### Future Suggestions
For future reference, the data should be weighted correctly. After evaluating each model, the data was biased towards non attacks. This is due to the dataset having a low attack to benign network traffic. To take this into account, the data should be weighted to have an even amount of attack and benign data for training the models.
