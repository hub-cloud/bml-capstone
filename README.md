
### Project Title: Sleep/Wake Classifier

**Author**: Srikanth Tummala

#### Executive summary

Sleep is a cornerstone of our health and well-being. However, a significant proportion of the population grapple with sleep disturbances, which, if left unaddressed, can lead to severe long-term health repercussions.

In our Capstone project, we explore the capabilities of contemporary wearable devices as a more accessible alternative to traditional, and often cumbersome, overnight stays at sleep clinics. With the proliferation of these devices in our daily lives, there's an unprecedented opportunity to harness their data to better comprehend sleep patterns. By doing so, we aim to identify potential sleep anomalies and pave the path for innovative, personalized sleep management solutions.

For our project, we employ the MESA sleep dataset, which offers sleep scores generated in a clinical environment using various signals. From this rich dataset, we carefully extract only the heart rate, activity count, and the sleep stage (where 0 indicates wakefulness and 1 signifies sleep). The sleep stage is scored using multiple parameters, but for this project we will use only the heart rate and activity count to predict the sleep stage.

 We specifically choose heart rate and activity count because they can be effortlessly captured by most wearable devices, allowing for a broader application of our findings. Our objective is to discern whether we can reliably predict sleep/wake stages using just these two indicators.

We used sleep data encompassing 1,972 participants, culminating in approximately 2.2 million consolidated records. Our findings strongly suggest that wearable devices can effectively serve as viable alternatives for traditional sleep measurements. For a more in-depth exploration of our results, please refer to the details in the "Results" section.
  

#### Rationale

The advent of wearables has seamlessly integrated them into our daily routines. While Polysomnography (PSG) is revered as the gold standard for sleep assessments, emerging research is highlighting the potential of using actigraphy (a feature embedded in many wearables) and heart rate as a plausible alternative. Tapping into the data from wearable devices to analyze sleep trends can help with new strategies for sleep management, making diagnostics and interventions more personalized and accessible.


#### Research Question

Can the data sourced from everyday wearable devices serve as a viable alternative to sleep assessments conducted in clinical environments?

#### Data Sources

Multi-Ethnic Study of Atherosclerosis (MESA) is an NHLBI-sponsored 6-center collaborative longitudinal investigation of factors associated with the development of subclinical cardiovascular disease and the progression of subclinical to clinical cardiovascular disease. Between 2010-2012, 2,237 participants also were enrolled in a Sleep Exam (MESA Sleep) which included full overnight unattended polysomnography, 7-day wrist-worn actigraphy, and a sleep questionnaire. (https://sleepdata.org/datasets/mesa)


#### Methodology

We followed the CRISP-DM methodology for this project, ensuring a structured and robust approach to our data analysis.
Our steps encompassed:

1. Preprocessing of raw data to extract relevant metrics.
2. Merging of preprocessed datasets based on timestamps.
3. Machine learning analysis using various classifiers to understand patterns and correlations.

#### Results


| Classifier            | Accuracy            | Sensitivity | Specificity | Precision (Class 1) | F1-score (Class 1) |
|-----------------------|---------------------|-------------|-------------|---------------------|--------------------|
| Logistic Regression   | 0.7388855310239905  | 0.92        | 0.41        | 0.74                | 0.82               |
| Random Forest         | 0.7419719578701587  | 0.91        | 0.44        | 0.75                | 0.82               |
| Gradient Boosting     | 0.7423396632278555  | 0.91        | 0.44        | 0.75                | 0.82               |
| Decision Tree         | 0.7415123261730375  | 0.91        | 0.43        | 0.75                | 0.82               |
| K-Nearest Neighbors   | 0.7033697897874434  | 0.84        | 0.45        | 0.74                | 0.79               |
| Stacked Ensemble      | 0.7421810902923487  | 0.90        | 0.44        | 0.75                | 0.82               |


In our analysis, we employed several machine learning methods to predict whether a subject is asleep (Class 1) or awake (Class 0). Here's a breakdown of the various results:

Accuracy: This tells us how often the machine's prediction was correct. Most of our methods predicted correctly around 74% of the time, with the K-Nearest Neighbors method being slightly less accurate at 70%.

Sensitivity: This measures how well the machine identified sleep when it occurred. Most methods detected sleep around 91% of the time, with K-Nearest Neighbors being a bit lower at 84%.

Specificity: This gauges how well the machine recognized when someone was awake. Here, our methods varied more, identifying wakefulness correctly between 41% and 45% of the time.

Precision (Class 1): This indicates how often the machine was right when it predicted sleep. The values hovered around 74%-75%, implying that when the machine said someone was asleep, it was right three-quarters of the time.

F1-score (Class 1): This is a balance between precision and sensitivity for detecting sleep. The higher the score, the better the balance. Our methods mostly scored around 82%, with K-Nearest Neighbors at 79%.

In summary, the machine learning methods were fairly consistent in predicting sleep, with minor variations between them. The methods were particularly good at detecting sleep but had more difficulty distinguishing when someone was awake.


We can further determine the best classifier to use, based on the criteria

Accuracy: The Gradient Boosting method slightly outperforms the other techniques with an accuracy of approximately 74.23%.
Sensitivity: All the methods (except K-Nearest Neighbors) have a high sensitivity of around 91%, meaning they are good at detecting when someone is asleep.

Specificity: K-Nearest Neighbors has the highest specificity at 45%. However, this method has a lower accuracy and sensitivity compared to others. Random Forest and Gradient Boosting both achieve a specificity of 44%, which is competitive.

Precision (Class 1): The values for precision are closely clustered around 74-75% for all methods, indicating consistent performance in correctly predicting sleep when the prediction is made.

F1-score (Class 1): All the methods, except K-Nearest Neighbors, have an F1-score of around 82%, indicating a good balance between precision and sensitivity for detecting sleep.


#### Outline of project
- [Link to Preprocess the MESA Dataset](preprocess_data.ipynb)
- [Link to Merge PreProcessed MESA Data](merge_preprocessed_data.ipynb)
- [Link to Data Modeling and Analysis](final_analysis.ipynb)


### Next Steps:

1. **Exploring Other Models**: While we utilized a range of machine learning models in our analysis, there are several advanced models and neural networks that could potentially offer improved predictions.

2. **Detailed Sleep Cycle Classification**: Our current analysis mainly focused on distinguishing between wakefulness and sleep. However, sleep can be further divided into several stages, each with its unique characteristics and importance for health. 
 
3. **Feature Engineering**: To further enhance the performance of our models, we can delve deeper into creating new features from the available data.

4. **External Data Sources**: Incorporating external factors like environmental data (temperature, noise levels), individual's health metrics, or lifestyle data might provide additional context and improve our model's predictive capabilities.

#### Acknowledgements
The Multi-Ethnic Study of Atherosclerosis (MESA) Sleep Ancillary study was funded by NIH-NHLBI Association of Sleep Disorders with Cardiovascular Health Across Ethnic Groups (RO1 HL098433). MESA is supported by contracts from the National Heart, Lung, and Blood Institute, and by cooperative agreements funded by NCATS. The National Sleep Research Resource was supported by the National Heart, Lung, and Blood Institute.

#### Citations
- [Zhang GQ, Cui L, Mueller R, et al.](https://pubmed.ncbi.nlm.nih.gov/29860441/)
- [Chen X, Wang R, Zee P, et al.](https://pubmed.ncbi.nlm.nih.gov/25409106/)
- [Sleep stage prediction with raw acceleration and photoplethysmography heart rate data derived from a consumer wearable device](https://pubmed.ncbi.nlm.nih.gov/31579900/)

