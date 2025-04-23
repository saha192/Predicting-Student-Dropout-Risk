# Predicting-Student-Dropout-Risk
Problem Statement: An e-learning platform is offering digital courses to students. Some students actively participate and complete their learning journeys, while others drop out midway. You are tasked with building a machine learning model to predict student dropout risk, so we can proactively engage at-risk learners.
## 📊 Dataset Description

The dataset `learning_data.csv` contains information about students enrolled in various online courses. It is structured as follows:

| Column Name            | Description                                                       |
|------------------------|-------------------------------------------------------------------|
| `student_id`           | Unique identifier for each student                                |
| `age`                  | Age of the student                                                |
| `gender`               | Gender of the student (`Male` / `Female` / `Other`)               |
| `course_type`          | Type of course enrolled in (`Digital Marketing` / `Python` / `UI/UX`) |
| `session_count`        | Total number of sessions attended                                 |
| `avg_session_duration`| Average time (in minutes) spent per session                        |
| `quiz_attempts`        | Number of quiz attempts made                                      |
| `assignments_submitted`| Number of assignments submitted                                  |
| `satisfaction_rating`  | Satisfaction rating on a scale from 1 to 5                        |
| `dropout`              | Target variable – `1` = Dropped Out, `0` = Completed              |

## 📄 Summary Report

### 1. 📊 Data Insights

**Dataset Overview:**  
The dataset contains information on **200 students** including demographics, engagement metrics, course details, and dropout status (`1` = Dropped Out, `0` = Completed).

#### 🔍 Key Findings:

- **Correlations:**
  - `session_count` and `satisfaction_rating` show moderate correlation with `dropout`.
<p align="center">
  <img src="https://github.com/saha192/Predicting-Student-Dropout-Risk/blob/ef4935427b38a15fd59da8380dd4b7628e354904/EDA1.png?raw=true" alt="EDA Visualization" width="600"/>
  <br>
  <em>Figure: Feature Correlation with Dropout</em>
</p>

- **Dropout Rates by Category:**
  - **Course Type:** Python courses had higher dropout rates compared to UI/UX and Digital Marketing.
  - **Gender:** Female students showed higher dropout rates.
<p align="center">
  <img src="https://github.com/saha192/Predicting-Student-Dropout-Risk/blob/db98b52cadd15b207b04f099c9756e6e9494ee31/EDA2.png?raw=true" alt="EDA 2" width="45%" style="margin-right: 10px;"/>
  <img src="https://github.com/saha192/Predicting-Student-Dropout-Risk/blob/db98b52cadd15b207b04f099c9756e6e9494ee31/EDA3.png?raw=true" alt="EDA 3" width="45%"/>
  <br>
  <em>Figure: Dropout Across Categories</em>
</p>



- **Engagement Trends:**
  - Students who dropped out had:
    - Fewer sessions attended (`session_count`)
    - Shorter average session durations (`avg_session_duration`)
<p align="center">
  <img src="https://github.com/saha192/Predicting-Student-Dropout-Risk/blob/1637de4ac48f2d5f4cacdf63998c953bd0d5869e/EDA4.png?raw=true" alt="EDA 4" width="45%" style="margin-right: 10px;"/>
  <img src="https://github.com/saha192/Predicting-Student-Dropout-Risk/blob/1637de4ac48f2d5f4cacdf63998c953bd0d5869e/EDA5.png?raw=true" alt="EDA 5" width="45%"/>
  <br>
  <em>Figure: Boxplots highlighting low session counts + low satisfaction = high dropout trend</em>
</p>

---

### 2. 🧠 Modeling Approach

- **Pre-processing:**
  - Removed `student_id`
  - Encoded categorical variables (`gender`, `course_type`)
  - Scaled numerical features

- **Algorithms Tested:**
  - Logistic Regression
  - Decision Tree
  - Random Forest
  - XGBoost
  - SVM

- **Validation Strategy:**
  - 80-20 train-test split
  - 5-fold cross-validation

---

### 3. 📈 Evaluation Results

**🏆 Best Model: Random Forest**

- **F1-Score:** `0.8564` (± `0.0438`)
- **Accuracy:** `82.5%`
- **ROC-AUC:** `0.8402`

**🔍 Performance Comparison:**

| Model               | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|---------------------|----------|-----------|--------|----------|---------|
| Logistic Regression | 0.7750   | 0.7000    | 0.8235 | 0.7568   | 0.7813  |
| Decision Tree       | 0.8250   | 0.7778    | 0.8235 | 0.8000   | 0.8248  |
| **Random Forest**   | **0.8250** | **0.7273**  | **0.9412** | **0.8205** | **0.8402** |
| XGBoost             | 0.8250   | 0.7778    | 0.8235 | 0.8000   | 0.8248  |
| SVM                 | 0.7500   | 0.6522    | 0.8824 | 0.7500   | 0.7673  |

**📌 Feature Importance (Random Forest):**

- `session_count`: **38%**
- `satisfaction_rating`: **21.8%**
- `avg_session_duration`: **12.3%**

---

### 4. 💼 Business Recommendations

- **Proactive Interventions:**
  - 🔔 **Boost Engagement:** Target students with low `session_count` via reminders, incentives, or personalized schedules.
  - 🎯 **Improve Satisfaction:** Act on feedback from students with low `satisfaction_rating` (e.g., course content, instructor support).
  - 📚 **Course-Specific Support:** Provide extra help in high-risk courses (e.g., Python).
  - ⚠️ **Early Warning System:** Deploy Random Forest model to flag at-risk students in real-time.
  - ⏱️ **Monitor Session Duration:** Investigate if longer durations cause fatigue or are due to difficult content.

> **📌 Takeaway:** Focus on increasing session participation and addressing course-specific pain points to reduce dropout rates by **15–20%**.
