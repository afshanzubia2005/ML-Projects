# NJIT-CS375-afshanakmal
(Machine Learning Project)

**Dataset Chosen**: Individual Age of Death and Related Factors

**Regression Problem**: Estimate the age of death with a 5-10 year period accuracy based on substance usage, major health issues, and family health risks. OR Predicting the number of lifetime surgeries based on these parameters.

**Input Features**: opioids y/n, addiction y/n, diabetes y/n, hds y/n (heart disease or stroke), asthma y/n, immune_defic y/n, family_heart_disease y/n

**Target Variables**: Estimated age of death (5-year period)

**Challenges**: One of the most obvious challenges is that the data consists of binary data (e.g. whether or not a person has diabetes or not). This provides a challenge because we need to determine what factors have a higher weight in influencing a person’s lifespan. Additionally, the age at which a person starts engaging in these habits also has a significant impact on their health.

**Application**: Insurance companies could use this information to estimate how much people will spend on healthcare and medical bills throughout their lifetime, which could impact how expensive health insurance is. 

*Dataset Details*:

**Size**: 6.58 MB

**Features**: age, weight, sex, height, Sys_bp, smoker, nic_other, Num_meds, occup_danger (0/1/2), Is_danger, canabis, opioids, other_drugs, Drinks_aweek, addiction, Major_surgery_num, diabetes y/n, hds y/n (heart disease or stroke), Cholesterol, asthma y/n, immune_defic y/n, family_cancer y/n, family_heart_disease y/n, family_cholesterol y/n

**Why I Chose This Dataset**: Determining how a person’s lifetime habits correlates with their risk for health problems later in life is interesting to learn about and can give us insights about whether family history has a large impact on our risk of developing health conditions in adulthood.

# Final Project Report

Algorithms Used: Decision Trees, XGBoost Regression, MLP (Neural Network)
**Algorithm 1: Decision Tree**

I chose to use a decision tree due to the nature of the decision boundaries and the data splits they would create, which can lead to easy interpretations of the data features. My dataset included a mix of numerical and categorical variables that could be used in a regression, and the decision tree also had a simple implementation that worked well for data with complex relationships.
The hyperparameters I focused on were the depth of the model and the minimum number of samples per leaf. I kept the depth
of the tree minimal after finding out that increasing the depth does not necessarily correlate to a better model of the data but rather leads to solid overfitting. I also increased the mininum number of samples per leaf from 2 to 5 to prevent a model that overfits.
When verified with cross validation, the decision tree was able to predict the correct age of death based on the features
with a margin of error of about 17 years, which is about 18% of the data range from 25 to 120 years. The r^2 was about 0.412.

**Algorithm 2: XGBoost Regression**

I chose to implement XGBoost because it builds off of the decision tree model I implemented previously. In contrast to training a single decision tree, XGBoost would implement multiple decision trees that learned from the errors of the previous trees. If I was able to create a better model with XGBoost, it would demonstrate that a decision tree was the right model for this type of dataset. 
In regards to hyperparameters, I changed the learning rate a couple of times to see if increasing or decreasing it slightly would lead to better model outcomes. Decreasing the learning rate from 0.1 to 0.05 or 0.01 had the same effect as increasing it to 0.2 or 0.5. No change to the learning positively impacted the model's final learning capacity, and some even lead to slightly worse predictions. Finally, I reset the learning rate to its original value of 0.1 because that seemed to be the most optimal rate to minimize the error range in predictions.
Cross validation showed that XGBoost was able get an average margin of error of 15 years, which is slightly better than the error margin of the previous decision tree. 

**Algorithm 3: MLP Regressor**

I chose to use an Artificial NN for my final model because it is best suited for data with complex, nonlinear relationships. 
The hyperparameter that I experimented with the most was the number of iterations. I drastically increased the number of iterations from 300 to about 1600 because the model was initially unable to converge and was delivering error messages. Increasing the number of iterations helped address the issue.
When testing the final model on the test validation set, the r^2 on the training data was 0.64, and the r^2 on the validation was 0.54. This difference in r^2 between the training and testing data can be considered normal for the dataset. The error margin, as depicted by the RMSE, was now 15, which is identical to the error margin depicted by the XGBoost model. However, the model still performed decently well on the unseen data because it was able to perform slightly better than random. With more hyperparameter tuning, the model could possibly improve on this performance rate.
