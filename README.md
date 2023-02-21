# Prediction-of-Health-Insurance-Price
 Machine learning based prediction of Health Insurance Price for an individual or family.

### Table of contents
[1. Introduction](#introduction)
  * [Aim](#aim)
  * [Variables in the dataset](#variables-in-the-dataset)

[2. Basic Exploration](#basic-exploration)
  * [Examining distributions of the data ](#examining-distributions-of-the-data)
  
[3. EDA](#eda)
  * [Conclusion on EDA ](#conclusion-on-eda)
  
[4. Feature Engineering](#feature-engineering)
  * [Correlation](#correlation-analysis)
  * [Chi-squared test](#chi-squared-test)
  * [Kendall's test](#kendall-test)
  * [Anova test](#anova-test)
  
[5. Machine learning](#machine-learning)
  * [Performance comparision of the machine learning techniques](#performance-comparision-of-the-machine-learning-techniques)
  * [Conclusion ](#conclusion)

# Introduction
The majority of nations determine health insurance premiums based on a variety of variables, including age, the size of families, etc. Many companies struggle with determining what the true cost of health insurance for a single person or family should be.

### Aim: 
- Performing Exploratory Data Analysis to find hidden insights. 
- Performing necessay feature engineering to get better predictions.
- To find the best machine learning model for predicting the health insurance price.

### Variables in the dataset:

1) age: age of the primary beneficiary
2) sex: insurance contractor gender, female, male
3) BMI: Body Mass Index, providing an understanding of body weights that are relatively high or low relative to height, objective index of body weight (kg/m²) using the ratio of height to weight, ideally 18.5 to 24.9
4) children: number of children covered by health insurance, number of dependents
5) smoker: smoking or not
6) region: the beneficiary’s residential area in the US, northeast, southeast, southwest, northwest.
7) charges: individual medical costs billed by health insurance

# Basic Exploration

![image](https://user-images.githubusercontent.com/111430368/220310745-1e59838c-6793-4a7b-b7d1-4996f1470443.png)

To see few statistical measures of the data.

![image](https://user-images.githubusercontent.com/111430368/220311424-175cd280-baa1-4369-a4ec-bd7efe799df1.png)

### Examining distributions of the data

![image](https://user-images.githubusercontent.com/111430368/220311736-0f75bf1e-2e0b-468b-b9a3-881355d74b75.png)

# EDA

**Aim**: To find the relation between health insurance price and age.

![image](https://user-images.githubusercontent.com/111430368/220312776-72b0a7f8-1d35-4eb9-ad5f-b86026399791.png)

**Obs**:

1) With an increase in age , there's an increase in the insurace price.
2) People with smoking_staus = yes are having higher health insurance price
3) We can observe 3 categories in health_insurance_price with more number of people below 15k

Discretizing health insurance price column into 3 categories as price_category - less than 15k, 15k - 30k, more than 30k.

**Aim**: To know the relation between health insurance price and children.

![image](https://user-images.githubusercontent.com/111430368/220314149-b81b3ed7-6058-4f09-a250-4e5cfc2779e6.png)

**Obs**: Most of the people with no children fall under category health_insurance_price less than 15k

**Aim**: To know the relation between BMI and gender.

![image](https://user-images.githubusercontent.com/111430368/220314617-292ff367-dbd1-4eab-abbf-a662806c8f78.png)

**Obs**: Health_insurance_price greater than 30k consists of Obese people(BMI > 30).

**Aim**: To know the relation between location and health insurance price.

![image](https://user-images.githubusercontent.com/111430368/220315206-88270ffe-b239-4bfd-9bb4-eed9410826e6.png)

**Aim**: To know the relation between BMI, smoking status and health_insurance_price.

![image](https://user-images.githubusercontent.com/111430368/220316161-0bd1f423-a61d-44b2-920c-859ce6a1fd17.png)

### Conclusion on EDA 

1. People whose smoking_status = yes and Obese are having high health insurance price (greater than 30k).
2. Increase in age results in increase in health insurance price.
3. People without children likely to have less health insurance price(less than 15k) compared to others.
4. Southeast location has more obese people compared to other location.

# Feature Engineering 

**The column which indicates number of children was discretized and converted to 'Having_children' column.**

**No extreme outliers were found.**

**Missing values are less than 2%. Hence they are dropped.**

**Features were encoded & split in the ratio of 80% and 20% for training and testing.**

## Correlation analysis

![image](https://user-images.githubusercontent.com/111430368/220330362-46a5e9b8-8c9f-488f-963e-cc97a36f1c8e.png)

## Chi squared test

![image](https://user-images.githubusercontent.com/111430368/220330816-87f54b55-ece1-47a1-8a13-bf7da3533192.png)

## Kendall test

![image](https://user-images.githubusercontent.com/111430368/220331017-27f8a502-6ff9-419b-9c8a-8f9b4a510234.png)

## Anova test

![image](https://user-images.githubusercontent.com/111430368/220331248-4395c4bb-5295-4b29-a18c-a689735c8981.png)



# Machine learning

Feature selection was performed using **filter method** and features like 'age','BMI', "smoking_status_yes", "Having_Children_yes" were selected. These features were used to train the machine learning algorithms like decision tree, random forest, SVM, polynomial regression. **Hyperparameter tuning** & **cross validation** are performed during the training process.

## Performance comparision of the machine learning techniques 

| ML Algorithm  | RMSE on training set | RMSE on test set |
| ------------- | ------------- | ------------- |
| DecisionTreeRegressor  | 4297.538678977602 | 4838.145638893016 |
| RandomForestRegressor  | 4335.553798399824 | 4576.447753679875 |
| SVMRegressor  | 4705.987962348541 | 5112.518892575513 |
| SGDRegressor  | 4803.2764307103025 | 5182.987479847826 |  

Predictions of the above techniques on the test set are as follows :

![image](https://user-images.githubusercontent.com/111430368/220327665-8768c2d6-42ac-44af-8fc6-4dca5d928c97.png)

## Conclusion 
By comparing all the models, RandomForestRegressor seems to be performed well in the regression task.
