

# Early Process Fault Diagnosis

**Model ID**: Tennessee-Eastman-Fault-Detection

**Summary**: This model leverages a combination of RandomForestClassifier and LSTM networks to monitor and classify faults in real time using the Tennessee Eastman Process Simulation Dataset. Initially, it detects the occurrence of a fault, then identifies the specific class of the fault for targeted interventions.

# Table of Contents

- [Model Details](#model-details)
- [Intended Use](#intended-use)
- [Training and Evaluation](#training)
- [Ethical Considerations](#ethical-considerations)
- [Limitations and Recommendations](#limitations-and-recommendations)
- [Additional Information](#maintenance)


## Model Details

- **Model Name**: Tennessee Eastman Fault Detection Model
- **Model Version**: 1.0
- **Model Type**: Hybrid (RandomForest for fault detection, LSTM for fault classification)
- **Developers**: MECE788Group1
- **Release Date**: April 19, 2024

## Intended Use

- **Primary Use**: This model is primarily developed for real-time monitoring and fault detection in the Tennessee Eastman chemical process. It aims to identify when a fault occurs and classifies the type of fault to enable timely corrective actions.
- **Intended Users**: The model is intended for chemical process engineers, operational staff, and safety personnel who manage and maintain the Tennessee Eastman process. It aids in enhancing operational safety and efficiency by providing early fault detection.
- **Out-of-Scope Use Cases**: This model is not designed for use in non-industrial contexts, such as healthcare monitoring, financial forecasting, or consumer behavior prediction. Additionally, it should not be employed in chemical processes significantly different from the Tennessee Eastman setup, as the model's accuracy and reliability are specific to the data and scenarios it was trained on.


## Training and Evaluation

### Training Procedure
The model was trained using the Tennessee Eastman Process Simulation Dataset. The RandomForest classifier was first trained to detect the occurrence of faults in real-time. Training parameters included a maximum depth of 40, with 200 estimators, and a random state for reproducibility. The LSTM network was subsequently trained to classify the type of fault based on sequences of process data, using a learning rate of 0.001 and 200 epochs.

### Evaluation Metrics
The model's performance was evaluated using precision and F1 score for the RandomForest classifier, and loss for the LSTM. The RandomForest achieved an accuracy of 95% and an F1 score of 93%, while BiLSTM achieved a mean precision of 86% for all 21 classes of faulty modes, and 98% precision on removal of fault 3,9 and 15.

### Baseline Comparison
Compared to a baseline XGBoost classifier that achieved an 80% accuracy and an F1 score of 0.82, the RandomForest classifier shows significant improvement in both accuracy and precision. The LSTM's ability to classify fault types surpasses that of a traditional RNN.

## Ethical Considerations

## Ethical Considerations

### Fairness and Bias
The model utilizes the Tennessee Eastman Process Simulation Dataset, which is synthetic and designed to simulate typical process faults. While the synthetic nature of the data precludes traditional biases associated with human factors, it is still important to continuously scrutinize the model's decision-making processes to ensure no algorithmic biases are introduced during development. We employ techniques such as feature importance analysis to monitor and mitigate any potential biases. These steps help in identifying any unintended model behaviors or biases that might affect the model's generalization across various synthetic scenarios.

### Privacy
Since the dataset is synthetic and does not contain any real personal or sensitive data, privacy concerns related to personal data are inherently mitigated. Our model does not require or process any real-world personal information, ensuring compliance with privacy best practices. This approach not only minimizes privacy risks but also represents how synthetic data can be used in developing models without compromising ethical standards.

### Security
Given the application context of industrial process monitoring, ensuring the security of data and model predictions is crucial, particularly to prevent data leakage and potential exploitation of the model's output. It is recommended that industrial setups using this model have stringent access controls and monitoring systems in place to detect and respond to any unauthorized access or anomalies in real-time data processing.

### Transparency
We are committed to maintaining transparency in how our models operate. Detailed documentation of the model's design, training process, and performance evaluations are made available to all users. This transparency would fosters trust and enable users to understand and verify the model's functionality and limitations.


## Limitations and Recommendations

### Known Limitations
- **Data Specificity**: While the model is trained on the Tennessee Eastman Process Simulation Dataset, its ability to generalize to real-world industrial environments with different operational parameters may be limited. Users should validate the model’s performance with pilot tests before full-scale deployment.
- **Performance Variability**: The model's performance may degrade under conditions not represented in the training data, such as novel fault types or unexpected operational scenarios.
- **Scalability Issues**: The current implementation may require adjustments to scale up to larger, more complex industrial systems or to integrate with different types of process control equipment.

### Recommendations for Use
- **Validation Before Deployment**: It is recommended that users conduct thorough validation of the model using their own specific datasets to ensure it performs as expected in their operational context.
- **Continuous Monitoring and Updating**: Users should continuously monitor the model’s performance over time and consider retraining with new data to adapt to changes in the operational environment.
- **Ethical Use**: Ensure that the model’s use complies with local regulations and ethical standards, particularly in making decisions that could affect the safety and reliability of industrial processes.


## Additional Information

### References
- The Tennessee Eastman Process dataset is available [here](https://www.kaggle.com/datasets/averkij/tennessee-eastman-process-simulation-dataset).
- [1] S. Zheng and J. Zhao, “A new unsupervised data mining method based on the stacked autoencoder for chemical process fault diagnosis,” Computers & Chemical Engineering, vol. 135, p. 106755, Apr. 2020, doi: 10.1016/j.compchemeng.2020.106755.
- [2] C. A. Rieth, B. D. Amsel, R. Tran, and M. B. Cook, “Issues and Advances in Anomaly Detection Evaluation for Joint Human-Automated Systems,” in Advances in Human Factors in Robots and Unmanned Systems, vol. 595, J. Chen, Ed., in Advances in Intelligent Systems and Computing, vol. 595. , Cham: Springer International Publishing, 2018, pp. 52–63. doi: 10.1007/978-3-319-60384-1_6.
- [3] A. Melo, M. M. Câmara, N. Clavijo, and J. C. Pinto, “Open benchmarks for assessment of process monitoring and fault diagnosis techniques: A review and critical analysis,” Computers & Chemical Engineering, vol. 165, p. 107964, Sep. 2022, doi: 10.1016/j.compchemeng.2022.107964.


### Contact Information
- **Lead Developers**: Mansimran, Yarooj, Thomas, Madhura 
- **Email**: [mansimra@ualberta.ca](mailto:mansimra@ualberta.ca), [mali19@ualberta.ca](mailto:mali19@ualberta.ca), [tkaminsk@ualberta.ca](tkaminsk@ualberta.ca), [mdeval@ualberta.ca](mailto:mdeval@ualberta.ca)

