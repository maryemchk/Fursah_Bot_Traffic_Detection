Botnet Traffic Detection using Machine Learning
This project tackles the challenge of botnet traffic detection using the CTU-13 dataset and advanced machine learning techniques. The goal is to distinguish between normal and botnet traffic in a highly imbalanced environment.

📊 Dataset Overview
Dataset Size: 2,824,636 network flow records

Columns: 15 original features including StartTime, Dur, Proto, SrcAddr, Sport, Dir, DstAddr, Dport, State, TotPkts, TotBytes, etc.

Target: Label (botnet vs. normal flow)

🔍 Problem Characteristics
Type: Binary Classification (Normal vs. Botnet)

Challenge: Severe class imbalance (67.96:1)

Normal traffic: 2,783,675 samples

Botnet traffic: 40,961 samples

🧼 Data Preprocessing
✅ Missing Values
Sport, Dport, State, sTos, dTos had missing values.

Handled with conditional imputation and flags for missingness.

✅ Feature Engineering
Created 30+ new features, including:

Time-based features: Hour, Minute, Second

Statistical features: Packet rate, Byte rate, Avg packet size, Variance

Categorical transformations: Encoded Dir, State, port categories, etc.

Binary flags: Is_TCP, Is_UDP, Is_short_connection, etc.

✅ Feature Selection
Selected top 25 features based on importance using ensemble models.

⚖️ Class Imbalance Handling
Used SMOTE (Synthetic Minority Oversampling Technique) to balance the dataset:

Before: [Normal: 2,226,939 | Botnet: 32,769]

After: [Normal: 2,226,939 | Botnet: 2,226,939]

🤖 Model Development
Individual Models:
Model	ROC-AUC	PR-AUC	F1-Score	Precision	Recall
XGBoost	0.9992	0.9595	0.7074	0.5507	0.9888
LightGBM	0.9990	0.9507	0.6852	0.5246	0.9877
Random Forest	0.9980	0.8983	0.6213	0.4533	0.9872
Logistic Regression	0.9742	0.3499	0.2432	0.1397	0.9369

✅ Ensemble Model
Averaged predictions from XGBoost, LightGBM, and RandomForest:

ROC-AUC: 0.9990

PR-AUC: 0.9497

F1-Score: 0.6858

Optimal threshold tuning achieved F1-Score = 0.88, Recall = 0.87, and Precision = 0.89 on botnet class.

📈 Evaluation (Test Set)
Accuracy: 99.9%

Botnet Detection:

Precision: 0.89

Recall: 0.87

F1-Score: 0.88

📌 Key Takeaways
Applied SMOTE to address class imbalance, which drastically improved botnet detection.

Feature engineering played a crucial role in increasing model performance.

Ensemble learning outperformed individual classifiers in both ROC-AUC and PR-AUC.

Optimal threshold tuning helped balance between false positives and false negatives.

🧠 Author
Maryem Chakroun – AI & Software Engineering enthusiast with a strong focus on cyber security and impactful ML systems.

