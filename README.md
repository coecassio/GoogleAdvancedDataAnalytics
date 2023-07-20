## Salifort Motors Capstone Project
Analysing and Predicting Employee Turnover 


### Project Overview:

This was developed as the capstone project for the Google Advanced Data Analytics Course. The goal was to analyse a [Kaggle](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction?select=HR_comma_sep.csv) dataset and build predictive models to provide the HR of a fictional company, Salifort Motors, with insights regarding their high employee turnover problem. The final Random Forest model performed with 97.6% Accuracy and 92.8% F1 Score when predicting employee turnover, determining the 4 most important features being number of projects taken, average monthly hours worked, result of last employee evaluation and company time. EDA also indicated 2 other features, promotions and salary range, that weren't good predictors due to their extremely imbalaced distributions, but could be used as tools to reduce turnover.

### Business Understanding:

Employee turnover can be a huge problem for companies as it's both time consuming and costly to post job listings, interview candidates, hire new employees and offer them proper training. Work quality also decreases during this process, affecting team morale and client perception. Therefore, it is in the company's best interest to increase employee retention.

### Data Understanding:

The dataset used in this project was originally called "Hr Analytics Job Prediction", and can be found in [Kaggle](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction?select=HR_comma_sep.csv). Data consists of 15k observations, with around 20% being duplicates, and 10 columns, including our target. After removing duplicates, the target ended with a turnover rate of 16.6%, indicating a moderate imbalance. During EDA a few outilers (824 rows or 6.87% of total observations) were found in the company time feature and an ethical concern was raised in the work accident feature, causing it to be removed from the analysis.

### Modeling and Evaluation:

A random forest model was chosen since it is robust to outliers and those were determined to be important for the analysis. After running an instance of RandomForestClassifier with default hyperparameters, the satisfaction level was dropped as it was considered an unreliable feature in regards to availability and the initial model was relying to heavily on it. Three models were built, using default hyperparameters, RandomSearchCV and GridSearchCV, in order to compare results and tune the model. 

The final metrics of the tuned Random Forest model were:

- Precision: 0.942
- Recall: 0.914
- F1 Score: 0.928
- Accuracy: 0.976
- ROC AUC: 0.951

The most important features in the model were:

1. Number of Projects
2. Average Monthly Hours
3. Last Evaluation
4. Company Time
   
with the importance of other features being very low.

### Conclusion:

The tuned model could be used as a predictive tool to identify employees that are likely to quit soon for tentative emergency action, but it should be done only be as a temporary measure, until steps are taken to correct the problems causing the high turnover rate.

Even though salary and promotion were not considered important features by the model, their imbalaced distributions make them unreliable features for splitting data in decision nodes. EDA showed they do affect the turnover rates and should be considered when planning a response to this issue.

By combining the insights of the model's feature importance values and EDA, a few elements became clear:

- Employees are being overworked, as shown by the high importance of number of projects and average monthly hours. EDA identified a sharp drop in satistaction level for employees working more than 5 projects.
- Performance evaluation distribution is almost the same across salary ranges and promotion status, so higher performances don't seem to translate well to carrer improvement, making employees feel stagnated and undervalued, being more susceptible to ouside job offers.
- Finally, there seems to be a critical point at 4 years of employment that makes employees more prone to quitting. Considering the promotion rate for the last 5 years was only 1,7%, it could very well be that the lack of promotions over such a long period of time is making them seek employment elsewhere as an alternative for carrer improvement.

Now, here are a few recommendations based on those observations:

- Capping the number of projects each employee can work on, so it can't be higher than at least 5.
- Keeping a record of employees working overtime and setting limits of how many extra hours one should work until the cause is investigated and action is taken to support them.
- Reestructuring company policy for promotions to prioritize better performance evaluation and company time, with special atention to employees nearing 4 years in company time.

### Next Steps:

The satisfaction level survey showed good correlation to turnover, meaning they were applied in a way employees felt confortable in answering truthfully, but making use of that only for ratings seems a wasted opportunity. When applying future surveys, asking employees directly for their opinions, experiences and suggestions in order to make use of natural language processing to identify padrons in their responses might be a good idea. This could give interesting insights we wouldn't be able to reach using only company data.
