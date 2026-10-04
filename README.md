# 🚀 Winning the Space Race with Data Science

**IBM Data Science Professional Certificate – Capstone Project**
Author: **Anshul Kumar Singh** | Date: 24 September 2026

An end-to-end data science project that predicts whether the **SpaceX Falcon 9 first stage will land successfully**, and therefore estimates the cost of a launch.

📄 Full report: [`Winning_Space_Race_with_Data_Science.pdf`](Winning_Space_Race_with_Data_Science.pdf)

---

## 📌 Problem Statement

SpaceX advertises Falcon 9 launches at about **$62 million**, versus **$165 million+** from other providers. Most of the saving comes from reusing the first stage. If we can predict whether the first stage will land, we can estimate the cost of a launch. That is useful to any company that wants to bid against SpaceX.

**Goal:** build a machine learning pipeline that predicts first-stage landing success.

**Questions answered**
- What factors determine whether the rocket lands successfully?
- How do features interact to affect the landing success rate?
- What operating conditions are needed for a successful landing programme?

---

## 🧭 Methodology

| Step | Description | Tools |
|------|-------------|-------|
| 1. Data collection (API) | GET requests to the SpaceX API, JSON decoded and normalised into a DataFrame, missing values handled | `requests`, `pandas` |
| 2. Data collection (scraping) | Falcon 9 launch records scraped from Wikipedia HTML tables | `BeautifulSoup` |
| 3. Data wrangling | Launch counts per site and orbit, landing outcome converted to a binary `Class` label (0 = failure, 1 = success), one-hot encoding of categorical features | `pandas`, `numpy` |
| 4. EDA with SQL | Queries on the dataset loaded into SQLite | `SQLite`, `ipython-sql` |
| 5. EDA with visualisation | Flight number, payload, orbit and year vs. success | `matplotlib`, `seaborn` |
| 6. Interactive map | Launch sites, outcome markers and proximity analysis | `Folium` |
| 7. Dashboard | Interactive success dashboard | `Plotly Dash` |
| 8. Predictive analysis | Classification models tuned with GridSearchCV | `scikit-learn` |

---

## 📊 Key Findings

**Exploratory analysis**
- More flights at a launch site means a higher success rate there.
- Success rate has risen steadily since **2013** through **2020**.
- Orbits **ES-L1, GEO, HEO, SSO** had a 100% success rate, and **VLEO** was also high.
- **KSC LC-39A** had the most successful launches (41.7% of all successful launches) and the highest site success ratio (**76.9%**).
- First successful ground-pad landing: **22 December 2015**.
- Launch sites sit on the US coasts (Florida and California). They are close to the coastline and away from cities, railways and highways.

**SQL highlights**
- Total payload carried for NASA (CRS): **48,213 kg**
- Average payload for booster version F9 v1.1: **2,928.4 kg**

**Predictive analysis**

| Model | Tuning |
|-------|--------|
| Logistic Regression, SVM, Decision Tree, KNN | GridSearchCV |

- **Best model: Decision Tree Classifier**, with a cross-validation accuracy of **~87.3%**.
- Best parameters: `criterion='gini'`, `max_depth=6`, `max_features='sqrt'`, `min_samples_leaf=2`, `min_samples_split=5`, `splitter='random'`.
- Test confusion matrix: 12 true positives, 3 true negatives, 3 false positives, 0 false negatives (15 of 18 correct, about 83%).
- The main weakness is **false positives**: failed landings predicted as successful.

---

## 📁 Repository Structure

```
├── Dataset/                                      # Collected and processed data
├── Important_SQL_Labs_PDF/                       # SQL lab reference PDFs
├── LAB7_SpaceX_Dashboard/                        # Plotly Dash app (spacex-dash-app.py)
├── Plot/                                         # Saved plots and screenshots
├── LAB1_Data_Collection_API_SpaceX.ipynb
├── LAB2_Data_Collection_with_Web_Scraping_SpaceX.ipynb
├── LAB3_Data_Wrangling_SpaceX.ipynb
├── LAB4_EDA_with_SQL.ipynb
├── LAB5_EDA_with_Data_Visualization.ipynb
├── LAB6-Interactive-Visual-Analytics-with-Folium.ipynb
├── LAB8_Machine_Learning_Prediction_Lab_SpaceX.ipynb
└── Winning_Space_Race_with_Data_Science.pdf      # Final presentation
```

---

## 📓 Notebooks

1. [Data Collection – SpaceX API](LAB1_Data_Collection_API_SpaceX.ipynb)
2. [Data Collection – Web Scraping](LAB2_Data_Collection_with_Web_Scraping_SpaceX.ipynb)
3. [Data Wrangling](LAB3_Data_Wrangling_SpaceX.ipynb)
4. [EDA with SQL](LAB4_EDA_with_SQL.ipynb)
5. [EDA with Data Visualization](LAB5_EDA_with_Data_Visualization.ipynb)
6. [Interactive Visual Analytics with Folium](LAB6-Interactive-Visual-Analytics-with-Folium.ipynb)
7. [Plotly Dash Dashboard](LAB7_SpaceX_Dashboard/spacex-dash-app.py)
8. [Machine Learning Prediction](LAB8_Machine_Learning_Prediction_Lab_SpaceX.ipynb)

---

## ▶️ How to Run

```bash
# 1. Clone the repo
git clone https://github.com/Anshulworld/IBM-Data-Science-Capstone-SpaceX-Project.git
cd IBM-Data-Science-Capstone-SpaceX-Project

# 2. Install dependencies
pip install pandas numpy requests beautifulsoup4 matplotlib seaborn \
            folium scikit-learn dash plotly ipython-sql jupyter

# 3. Run the notebooks in order (LAB1 → LAB8)
jupyter notebook

# 4. Launch the dashboard
cd LAB7_SpaceX_Dashboard
python spacex-dash-app.py
```

---

## 🛠️ Tech Stack

Python · Pandas · NumPy · Requests · BeautifulSoup · SQLite · Matplotlib · Seaborn · Folium · Plotly Dash · Scikit-learn · Jupyter

---

## 🔭 Possible Improvements

- Larger dataset: the test set has only 18 records, so the accuracy estimate is noisy.
- Report precision, recall and F1 alongside accuracy to address the false-positive issue.
- Try ensemble methods (Random Forest, Gradient Boosting) and feature importance analysis.

---

## 📬 Contact

**Anshul Kumar Singh**
LinkedIn: [linkedin.com/in/anshulworld](https://www.linkedin.com/in/anshulworld/)
Portfolio: [anshulworld.github.io](https://anshulworld.github.io)
GitHub: [@Anshulworld](https://github.com/Anshulworld)
