# Cricket Match Outcome Predictor - Case Study

## Project Overview

This project aims to develop a machine learning model that predicts the outcomes of ICC Men's Cricket World Cup matches using structured match-level metadata. The prediction focuses on identifying the winning team based on inputs such as venue, toss winner, toss decision, and participating teams.

The motivation behind this project stems from the complexity and multifactorial nature of cricket match outcomes, especially in international tournaments. Due to the unavailability of player-level statistics and weather information in the dataset, the model uses encoded categorical features at the team and match level.

---

## Dataset Description

The dataset used in this case study was collected from [CricSheet.org](https://cricsheet.org/). It includes metadata for ICC Men’s World Cup matches played up to December 31, 2024. Each match is provided as an individual CSV file containing structured lines of information.

Only match-level information was parsed from these files. The fields extracted and used include:

- Date
- Venue
- Toss Winner
- Toss Decision
- Team1 and Team2
- Match Winner

A total of 257 matches were successfully parsed and used for model training and evaluation. Ball-by-ball details and player-level statistics were excluded from this analysis.

---

## Exploratory Data Analysis (EDA)

EDA helped uncover trends and imbalances in the dataset. Key observations include:

- Frequent appearances by teams like Australia, India, and England.
- Fewer entries for associate nations such as Namibia and Kenya.
- Slight correlation (~51%) between toss winners and match winners.
- Some venues host significantly more matches than others.

Plots were generated to visualize team dominance and venue frequency.

---

## Model Development

### Model Selection Criteria

The Random Forest algorithm was selected due to its interpretability, resistance to overfitting, and effectiveness with categorical variables. It is also suitable for imbalanced datasets when class weights are properly handled.

### Model Architecture

The model uses the following features, all label-encoded:

- team1
- team2
- toss_winner
- toss_decision
- venue

The target variable is the match winner, which was also label-encoded. A `RandomForestClassifier` with 100 estimators and a fixed random seed was used.

### Training Process

The full dataset was cleaned and preprocessed, and all categorical variables were label-encoded. A stratified 80-20 split was used to maintain the class distribution across training and testing sets. The Random Forest model was then trained on the training data and predictions were made on the test data for evaluation.

---

## Evaluation Metrics

The model achieved an accuracy of approximately 48%. Evaluation was done using the classification report from scikit-learn, which provided precision, recall, and F1-score per class.

Example results:
- Australia: Precision = 1.00, Recall = 0.89
- India: Precision = 0.71, Recall = 0.62
- England: Precision = 0.38, Recall = 0.75

Teams with higher match frequency generally had better evaluation metrics. Lower performance was observed for teams with fewer matches due to class imbalance.





