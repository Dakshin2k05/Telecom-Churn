# 📡 Telecom Churn Prediction - Case Study  

## 📌 Project Overview  
In the telecom industry, customer churn is a major challenge, with an annual churn rate of **15-25%**. Given that acquiring a new customer is **5-10 times** more expensive than retaining an existing one, telecom companies must **identify and retain high-value customers** to minimize revenue loss.  

This project focuses on **predicting customer churn** using machine learning models. We analyze customer usage data, extract key insights, and develop predictive models to detect potential churners.  

---

## 🎯 Business Objective  
The goal of this project is to:  
✅ Predict high-value customers who are at **risk of churn**.  
✅ Identify key **indicators of churn** to help prevent customer loss.  
✅ Enable telecom companies to take **proactive retention measures**.  

---

## 🏷️ Defining Churn  
Since prepaid plans are more common in **India and Southeast Asia**, and customers can stop usage without notice, churn is defined using a **usage-based approach**:  

- A customer is considered **churned** if they have **zero usage** (no calls, SMS, or internet) in the **churn phase (Month 9)**.  
- High-value customers are defined as those whose **recharge amount** in the first two months is above the **70th percentile**.  

---

## 📊 Dataset Overview  
The dataset contains **customer-level data** for four months:  

| Month | Phase          | Purpose |
|-------|--------------|---------|
| 6 (June)  | Good Phase  | Normal usage behavior |
| 7 (July)  | Good Phase  | Normal usage behavior |
| 8 (August)  | Action Phase | Customer may show signs of churn |
| 9 (September) | Churn Phase | Churn is observed & tagged |

### **Key Features**  
- **Usage Data:** Total calls, SMS, internet data (2G/3G).  
- **Recharge Data:** Recharge amount, frequency.  
- **Customer Segmentation:** High-value customer classification.  

### **Target Variable**  
- `churn = 1`: Customer has **zero usage** in the churn phase.  
- `churn = 0`: Customer is **still active**.  

---

## 🛠️ Data Preparation & Processing  

### **1️⃣ Feature Engineering**  
- Derived new features to improve model performance.  

### **2️⃣ Filtering High-Value Customers**  
- Customers with recharge amounts **above the 70th percentile** in the first two months were selected.  
- This results in **~29.9k customers** for churn prediction.  

### **3️⃣ Labeling Churners & Removing Churn Data**  
- Customers with **zero usage** (`total_ic_mou_9`, `total_og_mou_9`, `vol_2g_mb_9`, `vol_3g_mb_9`) were tagged as churners.  
- All **Month 9 attributes** were removed to prevent data leakage.  

---

## 🤖 Model Development  

### **🔹 Handling Class Imbalance**  
Since churners make up **only 5-10%** of the data, we used:  
- **SMOTE (Synthetic Minority Over-sampling Technique)**  
- **Cost-sensitive learning**  

### **🔹 Dimensionality Reduction (PCA)**  
- Principal Component Analysis (PCA) was applied to reduce high-dimensional data.  

### **🔹 Model Training**  
We trained multiple machine learning models:  
✅ **Logistic Regression** (for interpretability)  
✅ **Random Forest**  
✅ **XGBoost** (for high accuracy)  
✅ **Support Vector Machines (SVM)**  

### **🔹 Model Evaluation**  
Evaluation metrics prioritized **identifying churners accurately**:  
- **Precision, Recall, F1-score**  
- **ROC-AUC Score**  

---

## 🔍 Key Insights  

### **📌 Important Churn Indicators**  
- **Decline in Recharge Amount** in the action phase.  
- **Decrease in Data Usage (2G/3G)** over time.  
- **Drop in Outgoing Calls & SMS** activity.  
- **Customers with Low Usage in the Good Phase** are more likely to churn.  

### **📌 Recommendations to Reduce Churn**  
✅ **Proactive Customer Engagement**: Identify at-risk customers early and offer personalized incentives.  
✅ **Special Retention Offers**: Provide discounts, better plans for high-value customers.  
✅ **Service Quality Improvements**: Address network complaints, improve customer experience.  
✅ **Loyalty Programs**: Reward frequent users with benefits to encourage retention.  

---

## 📁 Project Structure  

```bash
📂 Telecom-Churn-Prediction
│── 📜 README.md           # Project Overview
│── 📜 data_preprocessing.py  # Data Cleaning & Feature Engineering
│── 📜 churn_prediction.ipynb  # Model Training & Evaluation
│── 📜 churn_visualization.py  # Data Visualization
│── 📂 data/                # Raw & Processed Data
│── 📂 models/              # Saved Models
│── 📂 results/             # Model Performance Reports