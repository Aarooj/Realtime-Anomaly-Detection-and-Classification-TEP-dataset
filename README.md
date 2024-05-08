# Tennessee Eastman Process Dataset Analysis and Anomaly Detection

This repository contains the implementation of machine learning models including Random Forest and Bi-directional LSTM (Long Short-Term Memory) followed by an ANN neural classifier. The objective of the repository is to achieve anomaly detection as early as possible and then classify them into the fault type for post analysis of faults in industries.

## Introduction

Usual alarm systems in industries are mechanized to work on pre-set threshold values for different kinds of control variables like pressure, flow rate, etc. These alarm systems miss out anamolies that are captured by combination of disturbances in more than one control variables. 

The Tennessee Eastman Process dataset is a widely used benchmark dataset in the field of process monitoring and fault detection. It simulates a chemical process with various operating conditions and potential faults. The goal of this project is to develop machine learning models to detect anomalies as early as possible and classify the fault type in the process.

## Dataset

The Tennessee Eastman Process dataset is available [here](https://www.kaggle.com/datasets/averkij/tennessee-eastman-process-simulation-dataset). It contains measurements from various sensors in the chemical process under different operating conditions and fault scenarios.

## Usage

A. "main" FOLDER

1. EDA has been performed separately in the notebook named "[EDA.ipynb](https://github.com/bns1808/MECE788Group1/blob/main/main/EDA.ipynb)", located in the main folder of the repo

2. Execute the Jupyter notebook named "RF and LSTM Combined.ipynb" to train and evaluate the models:

    For each session, the data is imported from google drive, stored into corresponding variables and then
    the files are temporarily deleted from the directory.

    Our intital dataset has some instances for each fault type, where the classes are mislabelled.
    So next part of the code deals with labels and adds a column named "faultOccurence", that sets 
    normal mode as '0', whereas all other fault types as '1'. This 

    With analysis from the EDA, it is followed by data pre-processing. This deals with capturing
    the temporal nature of the dataset by introducing the rolling window and taking lagged intervals
    as new features.

    A pipeline is defined, that has a standardsclaer transformer, succeeded by the Random Forest 
    binary classifier.

    Evaluation is carried out on the basis of precision, recall and f1-score metrics.

    The predicted values from this pipeline are sent as test set for the Bi-directional LSTM 
    followed by ANN classifier model. 

    For this problem the initial imported dataset is used, without any data-preprocessing and 
    feature engineering. The sliding window technique is used to make the sequences that goes
    into training the model.

    To make a multi classifier, the LSTM model is attached to a ANN neural classifier that has 21 
    neurons in the last layers, indicating 21 classes.

    Finally the evaluation is carried out on the basis of precision, recall and f1-score metrics.

3. "data_flow.pdf" file has the pictorial overview of the model.

4. "system_context.pdf", pictorially shows how the model fits into larger industrial system.

B. "secondary models" FOLDER

1. Folder named "EDA" consists the rest of the trials on the dataset to get the best insights

2. "Random Forest (Aarooj).ipynb" is an experimental model that tried random forest without adding lagged features.

3. "ANN + Autoencoder (Thomas).ipynb" and "Autoencoder + ANN (Aarooj).ipynb" tried the mentioned models to see the effect of dimensionality reduction using the latent space or the bottleneck layer of the Autoencoder and attaching it to a ANN classifier. Though both notebooks have the same architecture, the hyperparameters are different.

C. "Model Card.md" [here](https://github.com/bns1808/MECE788Group1/blob/main/Model%20card.md) file discusses the overall project.

D. "Readme.md" file gives the information about all the files location, usage and objective.

## Results

1. Random Forest binary predictor and classifier: 75%+ fault detection in first few minutes, with a precision of 93% for "normal mode - class 0" and 95% for "faulty mode - class 1"

2. BiLSTM achieved a mean precision of 86% for all 21 classes of faulty modes, and 98% precision on removal of fault 3,9 and 15.

## References
- "Introduction to the Tennessee Eastman Process Simulation Dataset", [Link to the dataset description and download](URL_to_dataset).
- [1] S. Zheng and J. Zhao, “A new unsupervised data mining method based on the stacked autoencoder for chemical process fault diagnosis,” Computers & Chemical Engineering, vol. 135, p. 106755, Apr. 2020, doi: 10.1016/j.compchemeng.2020.106755.
- [2] C. A. Rieth, B. D. Amsel, R. Tran, and M. B. Cook, “Issues and Advances in Anomaly Detection Evaluation for Joint Human-Automated Systems,” in Advances in Human Factors in Robots and Unmanned Systems, vol. 595, J. Chen, Ed., in Advances in Intelligent Systems and Computing, vol. 595. , Cham: Springer International Publishing, 2018, pp. 52–63. doi: 10.1007/978-3-319-60384-1_6.
- [3] A. Melo, M. M. Câmara, N. Clavijo, and J. C. Pinto, “Open benchmarks for assessment of process monitoring and fault diagnosis techniques: A review and critical analysis,” Computers & Chemical Engineering, vol. 165, p. 107964, Sep. 2022, doi: 10.1016/j.compchemeng.2022.107964.
