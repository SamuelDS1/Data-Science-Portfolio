Welcome to my portfolio. I am Samuel, and I invite you to explore my projects. Click on each header to delve into the details of each project. Within each project, you will find the comprehensive scripts I employed for analysis and development.

Thank you for your interest.

# [Project 1: Predicting Employees Churn](https://github.com/SamuelDS1/Data-Science-Portfolio/tree/main/Projects/Project%201:%20Employees%20Churn) 
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
![feature importance](images/conf_matrix.png)

Now take a look at the feature importance graph.
![feature importance](images/ft_importance.png)


This is a Data Visualization made in Tableau Public, that can help technical and non-technical steakholders understand the impact of employees leaving the company. Click in [here](https://public.tableau.com/views/employees_churn_data_visualization/Dashboard1?:language=es-ES&:display_count=n&:origin=viz_share_link) to explore the complete interactive visualization.

The product shows risk across positions and **16%** churn rate, **337** employees at risk, and over **$5 million** USD in potential losses. 

![feature importance](images/Dashboard_Employees_Churn.png)




