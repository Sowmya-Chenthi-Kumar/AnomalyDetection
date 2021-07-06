# ANOMALY DETECTION IN LOG FILES 

### Concept of Log Files 

In computing, a log file is a file that records events that occur in an operating system or other software runs, messages between different users of a communication software. Essentially it is used to get information about the usage patterns, activities, and other operations. Hence these files can be used to understand system runtime problems. 

These problems can be identified using the concept of Anomaly Detection. . Anomaly detection/outlier detection is the identification of rare items, events or observations which raise suspicions by differing significantly as compared to the rest of the data. Traditionally, operators have to go through these log files manually to identify the problem. But however, in the recent years, the scale and the complexity of the systems have increased to mammoth amounts making it infeasible for manual inspection. Hence to reduce the manual effort, we use anomaly detection to automate log analysis.

#### PROCESS OF ANOMALY DETECTION:

This process involves four major steps which is shown below[4]: 
•	Log collection
•	Log parsing
•	Feature extraction
•	Anomaly detection

[image]

1. Log Collection:

Our data exists as a large log files from the Hadoop File Distributed System. We have used 2 datasets here. HDFS_1 that is used for training the model and the HDFS_2 for validating the model. HDFS_1 is a labelled dataset, where the logs are generated from a private cloud environment and manually labelled through a set of handcrafted rules to identify the anomalies.

2. Log Parsing:

A machine learning algorithm will require the data in terms of a structured format. Hence, we should extract features from the text log files which in turn can be converted to numerical which in turn can be useful for our machine learning algorithms. Though these text files look very long and highly disorganized, there is a specific underlying pattern which is present in them. 

The logs consist of two different parts – the constant parts and the variable parts which will vary for different log entries. For example, if we have two log entries like:
•	“Connection from 10.10.34.11 closed”
•	“Connection from 10.10.35.12 closed”

The constant parts are usually predefined by the developers and the random parts are dynamically generated. The dynamically generated random parts do not play significant role in the anomaly detection. Hence log parsing essentially differentiates the constant part (schema) from the variable / random part which are deemed to be not useful for our analysis.

3. Feature Extraction:

Once we are done converting the log files into a more useable format we should extract the key features in them. We have used a TF-IDF Vectorizers. This process is carried out with the help of the loglizer package. The output of this is a matrix which will further be split into a x_train, y_train, x_test and y_test dataset. This split is generated depending on the ratio of the split specified by us.

Once the test and train datasets are generated, we can carry out multiple analysis on them. 

4. Anomaly Detection Models:

Four models have been used to for our analysis:

    * Decision Tree Classifier
    * Naive Bayes Algorithm
    * Logistic Regression after Principle Component Analysis
    * Multi Layer Perceptron

    


