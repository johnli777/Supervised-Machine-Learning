# Network Intrusion Detection with Machine Learning

This project implements and evaluates multiple machine learning algorithms for detecting malicious network activity using firewall log data. The models are trained on a dataset of over **65,000 network connection records**, with features describing traffic volume, timing, and protocol-level attributes.

---

## 📌 Project Overview
Network intrusion detection systems (NIDS) are essential for identifying cyber threats such as:
- Distributed Denial of Service (DDoS) attacks
- Brute-force login attempts
- Port scanning
- Data exfiltration

In this project, we:
1. Collected and analyzed firewall log data.
2. Engineered additional traffic behavior features.
3. Applied supervised machine learning algorithms.
4. Tuned hyperparameters using **5-fold stratified cross-validation**.
5. Compared models on accuracy, precision, recall, F1-score, and training time.
6. Visualized performance with boxplots, confusion matrices, and feature importance charts.

---

## 📊 Dataset
- **Total records**: 65,532  
- **Features**: 12 original → expanded to 32 after feature engineering.  
- **Classes**: Binary (Benign vs. Malicious).  
- **Source**: UCI / firewall log dataset.  

---

## 🛠 Features
- **Traffic Volume Features**: Bytes sent/received, packet counts.  
- **Temporal Features**: Connection duration, inter-packet timing.  
- **Engineered Features**: Bytes per second, packets per second.  
- **Categorical Encoding**: One-hot encoding for protocol types.  
- **Class Balancing**: SMOTE applied during training.  

---

## ⚙️ Models Used
- Logistic Regression  
- Random Forest  
- XGBoost  
- Support Vector Machine (RBF kernel)  

---

## 📈 Results

### **Held-out Test Performance (post-tuning + SMOTE)**

```latex
\begin{table}[H]
\centering
\caption{Held-out test performance (post-tuning + SMOTE). Best in \textbf{bold}.}
\label{tab:results}
\setlength{\tabcolsep}{3pt}
\footnotesize
\begin{tabular*}{\columnwidth}{@{\extracolsep{\fill}}lcccc}
\toprule
\textbf{Model} & \textbf{F1} & \textbf{Accuracy} & \textbf{Precision} & \textbf{Recall} \\
\midrule
Logistic Regression & 0.999103 & 0.999237 & 0.999641 & 0.998566 \\
\textbf{Random Forest} & \textbf{0.999552} & \textbf{0.999619} & 0.999283 & \textbf{0.999821} \\
XGBoost & 0.999193 & 0.999313 & \textbf{0.999104} & 0.999283 \\
SVM (RBF) & 0.995880 & 0.996490 & 0.995167 & 0.996594 \\
\bottomrule
\end{tabular*}
\end{table}
