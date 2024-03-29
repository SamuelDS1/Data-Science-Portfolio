Welcome to my portfolio. I am Samuel, and I invite you to explore my projects. Click on each header to delve into the details of each project. Within each project, you will find the comprehensive scripts I employed for analysis and development.

Thank you for your interest.

# [Project: Predicting Fraud in Insurance Claims](https://github.com/SamuelDS1/Data-Science-Portfolio/tree/main/Projects/Project%3A%20Fraud%20Insurance) 

In the insurance landscape, the battle against fraudulent claims has become a challenge for insurance companies worldwide. As losses incurred due to fraudulent activities continue to mount, it is important for insurance providers to adopt strategies that enable them to distinguish between genuine claims and fraud attempts. This project helps to address this issue by using predictive algorithm techniques to identify and preempt fraudulent insurance claims.


## Problem 
The problem is that fraud is really expensive for the insurance companies. The insurance industry consists of more than 7,000 companies that collect over $1 trillion in premiums each year. The massive size of the industry contributes significantly to the cost of insurance fraud by providing more opportunities and bigger incentives for committing illegal activities. The total cost of insurance fraud (non-health insurance) is estimated to be more than $40 billion per year. That means Insurance Fraud costs the average U.S. family between $400 and $700 per year in the form of increased premiums. [source](https://www.fbi.gov/stats-services/publications/insurance-fraud).
For example, the Federal Bureau of Investigation (FBI) reported COVID-19 related fraudulent insurance claims, where criminals used the confusion caused by the pandemic to file fraud claims.

The **objective** is to understand fraud trends and build a product that analyzes transactions and makes fraud predictions using a Machine Leaening Algorithm.

## The business process.
The next diagram explains the fraudulent claim submition process. There is two moments in which we can make a prediction.

![](images/fraud_insurance/bp.png)

1. Before the company accept to insures
2. During the decision process, when an agent decides whether to grant the claim or not.

## Predicion Frecuency
It can be done in:
1. Batches: If we decide to predict fraud during the decision process, as we have more time to double-check the policy holders information.
2. Real-Time: If we want to make predictions just when the potential customer wants to acquire a policy.

## Data Sources
The dataset contains **15,420 claims**. Each claim has 33 attributes describing the following components:

* Customer demographic details (age, sex, martial status)
* Purchased Policy (policy type, vehicle category, number of supplements, agent type, etc)
* Claim Circumstances (day/month/week claimed, policy report filed, witness present, past days between incident-policy report, incident-claim, etc)
* Other customer data (number of cars, previous claims, driver rating, etc)
* Fraud found (yes; 1 and no; 0)

## Solution
Take a look at the whole solution on the [jupyter notebook](https://github.com/SamuelDS1/Data-Science-Portfolio/blob/main/Projects/Project%3A%20Fraud%20Insurance/Fraud_Insurance_Claims.ipynb).

1. EDA
2. Data Preprocessing
3. Feature Engineering
4. Feature selection
5. Train model
6. Model evaluation
7. Product

## Analysis
We want to analyze the data and start creating a profile for the usual fraudster. If you want to see how I cleaned the data take a look at the notebook in the repository. 

The analysis shows that 88% of Frauds are commited by men, while 12% of the frauds left are commited by woman.

![](images/fraud_insurance/fraud_by_sex.png)

The 23.87% of Frauds are from Pontiac cars, 20.85% from Toyotas, 16.59% from Hondas, and the left 38.59% comes from cars brands like Mazda, Chevrolet, Ford, VW and others.

![](images/fraud_insurance/Frauds_by_Car_Brand.png)

The 85% of Frauds are from claims where the accident happened in an Urban area, but we can see a really strong class imbalance.

![](images/fraud_insurance/Frauds_by_Accident_Area.png)

Almost half of Frauds (47.19%) happend with cheap cars, between 20000 - 29000 . The 30000 - 39000 price range takes 19.61% from all frauds.  

![](images/fraud_insurance/Frauds_by_Vehicle_Price.png)

Vehicle of 7 or more years are the ones with more fraud listed in the data.

![](images/fraud_insurance/Frauds_by_Vehicle_Age.png)

Policy Holders between 31-40 years old is the Age group that commits more crime.

![](images/fraud_insurance/Fraud_by_Age_of_Policy_Holder.png)

Lets see if the different Types of insurance Base Policies are increasing frauds. In the dataset there are 3 categories: 

* **Collision**: It helps pay to repair or replace your car if it's damaged in an accident with another vehicle or object, such as a fence or a tree.
* **Liability**: It helps cover medical and legal fees if you're held legally responsible for someone else's injury, or damage to someone else's property.
* **All perils**: It is an insurance policy that would cover all the risks unless these are explicitly excluded in the policy text

![](images/fraud_insurance/Claims_by_Base_Policy.png)

Liability Base Policies have the least amount of frauds out of the 3 types. This could mean that most of Policy Holders that have a Liability Base Policy are better covered and therefore they feel less preassure to commit fraud.

But I think that is easier to commit fraud when you hit a Fence or a tree (Collision) rather than another person's car, even more, when someone else got hurt.

**So, I think that fraud is harder to commit Fraud for "Liability" Policy Holders because you are adding another variable; another person's injury or damage to their property.**

What type of cars suffer frauds the most?

Sedan cars (from the 3 categories) suffer fraud the most, followed by sports cars and utility vehicles. I would suppouse that theres not too much advantage from commiting fraud with sport cars.

![](images/fraud_insurance/Claims_by_Vehicle_Category.png)


## Feature Selection 
During the feature selection process we identified that the PolicyNumber feature had heavy importance.

![](images/fraud_insurance/ft_importance.png)

Further analysis showed that the model assigned high importance to this feature because of its correlation with the time feature "Year". 

As Year increases, PolicyNumber does too. The following graph shows that the PolicyNumber increases overtime (its assigned secuentially). 

![](images/fraud_insurance/PolicyNumber_by_Years.png)

But fraud does not increase overtime as we can see in the next figure.  

![](images/fraud_insurance/fraud_1994_1996.png)

So we can conclude that PolicyNumber helps the algorithm predict Fraud, because, a lower policy number means its an older policy, and there were less frauds at that time than today.

But I decide to drop **PolicyNumber** because its not a trend we want our model to learn, mainly due to future changes in fraud transactions.

Lets take a minute to understand what would really mean to train our model with this feature. It could mean that the newer the policy the more likely the model would predict a no-fraudulent transaction, which is something we dont want right? Because what if frauds increase after 1996?

## Training the model
The next models were performance tested with balanced and imbalanced datasets.

* Logistic Regression
* Random Forest
* SVM
* Neural Network

Results were not promising with the imbalanced dataset. There was 14208 no-fraudulent and 892 fraudulent claims; the data was balanced by reducing the amount of no-fraudulent as I didnt want to over represent fraudulent claims.

The balanced dataset resulted in 1784 (892; 0 and 892; 1). 

The best performing model was the RandomForestClasiffier. If you want to see how every model was tested check out the [jupyter notebook](https://github.com/SamuelDS1/Data-Science-Portfolio/blob/main/Projects/Project%3A%20Fraud%20Insurance/Fraud_Insurance_Claims.ipynb).

```
 # precision    recall  f1-score   support

   Not Fraud       0.86      0.65      0.74       190
       Fraud       0.72      0.90      0.80       194

    accuracy                           0.78       384
   macro avg       0.79      0.77      0.77       384
weighted avg       0.79      0.78      0.77       384

```

The table above means: Of all positive (fraud) cases the model identified **90%** of them, but, of all the cases the model labeled as positive only **72%** were actually positive.

Then we performed Hyperparatemer Tunning, with final results:

```
 # Tuned DecisionTreeClassifier Parameters: {'min_samples_split': 4, 'min_samples_leaf': 2, 'max_depth': 7}
   Tuned DecisionTreeClassifier Best Accuracy Score: 0.7589999999999999
```
And the final ROC AUC Score is **0.7991**, which is around **80%**.


---
# [Project: Predicting Employees Churn](https://github.com/SamuelDS1/Data-Science-Portfolio/tree/main/Projects/Project%3A%20Employees%20Churn) 
Employee churn, the phenomenon of employees leaving an organization, poses significant challenges for businesses in terms of productivity, morale, and financial implications. By leveraging the power of data, I have created a predictive model that effectively forecasts the likelihood of employees leaving a company.
Through data analysis, I have identified key factors that contribute to employee attrition, such as the number of companies employees worked for before, monthly compensation and . By using decision trees, and random forests, I have developed a model that can anticipate employees churn with **90% precision**.

## Problem
There´s a lot of employees leaving the company and the directors don't know why. The **objective** is to predict wheter employees churn or stay at the the company so we can reduce losses; we want to know what are the employee's characteristics that make it churn, so that the company can target those problems and act accordingly. This is a **Classification** problem.

## Data 
We'll use a Data set called employees. All the rows in the data (1470 observations) represent one employee and describe certain characteristics about it. The data comes from a DS course, you can find it in here [Course](https://ds4b.teachable.com/courses).

* **Preprocessing and cleaning** the data was by far the most time-consuming task of the project. 
* The only **data quality issue** encountered was the class inbalance in the churn variable.

## Analysis
The analysis revealed that there's a 16% churn rate.

![avg churn profile](images/churn_rate_employees_churn.png)

Further investigation shows that most employees who churned:
*  Had a low educational level.
*  Were single at the time.
*  Worked extra hours.
*  Worked in sales.

![avg churn profile](images/avg_churn_profile.png)

### Hypothesis Testing
I wanted to see if theres any job position that's better compensated than others, so I'll use an ANOVA test for this.
First let's take a look at how the salaries dirstribute.
Significance level set to **Alpha = 0.01**.

* **Null hypotheis**: There's no difference in salary between positions.
  *  H0: m1 = m2 = m3 = ... = mn
* **Alternative hypotheis**: At least one mean group is different.

![Salaries Across Positions](images/salaries_bt_positions.png)

There seems to be some a significal difference in the graphic, but to make sure I'll use ANOVA. 

![Salaries Across Positions](images/anova.png)

The p-value 0.00 is lower than Alpha = 0.01. Reject H0 in favor of HA. This is strong evidence that there's at least one mean group that's different. But which ones are different?

After a test we can see that the next job position pairs have different mean salary:

![Salaries Across Positions](images/anova_pairs_false.png)


## The ML Model
I used a **Random Forest Classifier** for this Classification problem; as a Desition Tree is more likely biased. To select the best parameters for the model we used **hyperparameter tuning**, returning: {'max_depth': 9, 'min_samples_split': 4, 'min_samples_leaf': 2}.

To solve the class imbalance issue mentioned at the beggining, I oversampled the smallest group (16% churn rate) to be 50-50 compared with the other group (employees who didn't churn).

![feature importance](images/resample_churns.png)


## Results 
To identify the model's performance and results we used a ROC AUC score, a confusion matrix and a feature importance graph. 
The models ROC AUC score is **0.90744**. 

The confusion matrix performs really well and doesn't return too many type I and II errors.
![](images/conf_matrix.png)

Now take a look at the feature importance graph.
![](images/ft_importance.png)

The Random Forest positions this features as important.
* Job Level: How high are they in the corporation, Directors for example have a high job level. 
* Home distance: How far employees live from the office.
* Extra hours: Whether or not employees work extra hours.
* Works in sales.
* Low Environmental Satisfaction.
* Low Peer Satisfaction.

This is a Data Visualization made in Tableau Public, that can help technical and non-technical steakholders understand the impact of employees leaving the company. Click in [here](https://public.tableau.com/views/employees_churn_data_visualization/Dashboard1?:language=es-ES&:display_count=n&:origin=viz_share_link) to explore the complete interactive visualization.

The product shows risk across positions and **16%** churn rate, **337** employees at risk, and over **$5 million** USD in potential losses. 

![](images/Dashboard_Employees_Churn.png)




