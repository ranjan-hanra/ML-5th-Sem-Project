🌐 Network Protocol Classification Using Machine Learning

A Machine Learning project that predicts the network protocol (TCP, UDP, DNS, ARP, ICMP, etc.) of a network packet using its packet information.

📌 Table of Contents
About the Project
Project Description
Objectives
Dataset
Workflow
Technologies and Libraries
Machine Learning Models Used
Results and Outcomes
How to Run the Project
Project Structure
Limitations and Future Work
Conclusion
Author
📖 About the Project

Every time we browse a website, play an online game, or send a message, our device sends and receives small chunks of data called packets. Each packet follows a protocol, which is a set of rules for how the data is sent. Common protocols are:

Protocol	What it is used for
TCP	Reliable data transfer (web pages, file downloads)
UDP	Fast data transfer (online games, video calls)
DNS	Converting website names into IP addresses
ARP	Finding the device address inside a local network
ICMP	Network error messages and ping

This project uses Machine Learning to look at a packet's characteristics and predict which protocol it belongs to. This is a multi-class classification problem.

📝 Project Description

The project uses a network traffic capture dataset called KT GameBox (KT_GameBox_1.csv). The data looks like what the Wireshark tool records, with columns such as No., Time, Source, Destination, Protocol, Length and Info.

The work is done in these stages:

Load the dataset and understand its structure.
Clean the data by removing missing values and duplicate rows.
Explore the data using graphs, such as the protocol distribution.
Create features by extracting Hour, Minute and Second from the Time column.
Select features: Length, Hour, Minute and Second are the inputs, and Protocol is the target to predict.
Encode the protocol names into numbers using LabelEncoder.
Split the data into 80% training and 20% testing.
Scale the features for the models that need it (Logistic Regression and KNN).
Train four ML models and compare their accuracy.
Evaluate the best model using a classification report, confusion matrix and feature importance.
Predict the protocol of a brand-new packet.

Why not use Source and Destination (IP addresses)? IP addresses have a huge number of unique values, which makes the problem too complicated for a first model. This project focuses on simple packet characteristics instead.

🎯 Objectives
Understand the full Machine Learning workflow from raw data to prediction.
Learn data cleaning, visualization and feature engineering.
Train and compare multiple classification algorithms.
Learn to evaluate a model using accuracy, a classification report and a confusion matrix.
Find out which packet feature matters most for identifying a protocol.
Build a small demo that predicts the protocol of a new packet.
📂 Dataset
Property	Details
Name	KT GameBox (KT_GameBox_1.csv)
Type	Network packet capture (Wireshark-style)
Target column	Protocol
Features used	Length, Hour, Minute, Second

Columns in the original file: No., Time, Source, Destination, Protocol, Length, Info

🔄 Workflow
Load Dataset
     ↓
Understand & Clean Data
     ↓
Exploratory Data Analysis (graphs)
     ↓
Feature Engineering (Hour, Minute, Second)
     ↓
Select Features & Encode Target
     ↓
Train / Test Split (80% / 20%)
     ↓
Train 4 ML Models
     ↓
Compare Accuracy → Find Best Model
     ↓
Confusion Matrix & Feature Importance
     ↓
Predict a New Packet
🛠 Technologies and Libraries
Language: Python 3
Platform: Google Colab
Libraries:
pandas, numpy for data handling
matplotlib, seaborn for visualization
scikit-learn for machine learning models and evaluation
🤖 Machine Learning Models Used
#	Model	Notes
1	Logistic Regression	Simple baseline model (uses scaled data)
2	K-Nearest Neighbors (KNN)	Classifies using the 5 nearest data points (uses scaled data)
3	Decision Tree	Learns simple if-else rules (max_depth=10)
4	Random Forest	Many decision trees combined (n_estimators=100)
📊 Results and Outcomes
Model Comparison
Model	Accuracy	Accuracy (%)
Logistic Regression	0.901188	90.1188%
KNN	0.997256	99.7256%
Decision Tree	0.999461	99.9461%
Random Forest	0.999385	99.9385%
🏆 Best Model
Model           Decision Tree
Accuracy             0.999461
Accuracy (%)        99.946124

The Decision Tree achieved the highest accuracy, about 99.95%, on the test data.

Outcomes of the Project
A working model that predicts a packet's protocol from its features.
A comparison of four classification algorithms on the same data.
Visual outputs: protocol distribution, packet length histogram and box plot, model comparison bar chart, confusion matrix, and feature importance chart.
A function-style demo that predicts the protocol of a new packet, for example Length = 64.
Practical understanding of data leakage prevention (the scaler is fitted only on training data).
▶️ How to Run the Project
Option 1: Google Colab (easiest)
Open Google Colab and click New Notebook.
Clone this repository:
python
   !git clone https://github.com/ranjan-hanra/ML-5th-Sem-Project.git
   %cd ML-5th-Sem-Project
Install the libraries:
python
   !pip install pandas numpy matplotlib seaborn scikit-learn
Make sure KT_GameBox_1.csv is in the working folder. If it is not, upload it:
python
   from google.colab import files
   uploaded = files.upload()
Run the project notebook or script: [your_notebook_or_script_name]
Option 2: Run locally
bash
git clone https://github.com/ranjan-hanra/ML-5th-Sem-Project.git
cd ML-5th-Sem-Project
pip install pandas numpy matplotlib seaborn scikit-learn
jupyter notebook

Open the project notebook and run all cells in order.

📁 Project Structure
ML-5th-Sem-Project/
│
├── KT_GameBox_1.csv        # Dataset 
├── [project_notebook].ipynb # Main code
└── README.md               # Project documentation
⚠️ Limitations and Future Work

Limitations

Very high accuracy needs a closer look. An accuracy near 99.95% can happen when the dataset is imbalanced (one protocol makes up most of the packets), so a model can score high by mostly predicting the common protocol. The classification report and confusion matrix should be checked, not just accuracy.
Time features: Hour, Minute and Second are only meaningful if the Time column contains real clock timestamps. In Wireshark exports, Time is often "seconds since capture start", in which case these features may carry little information.
Only one train/test split was used. Cross-validation would give a more reliable result.
Only four features were used, and IP addresses were left out on purpose.

Future Work

Use more rows and the full dataset.
Add features from Source, Destination and Info.
Try handling class imbalance (class weights, resampling).
Report precision, recall and F1-score for every protocol.
Tune model parameters with GridSearchCV.
Try other models such as SVM or Gradient Boosting.
✅ Conclusion

This project shows how Machine Learning can be used to classify network traffic by protocol. After cleaning the data, creating features and comparing four models, the Decision Tree performed best with an accuracy of 99.95%. The project gave hands-on practice with the complete ML pipeline: data cleaning, visualization, model training, evaluation and prediction.

👤 Author

Ranjan Hanra, Brainware University, GitHub: @ranjan-hanra