Welcome to my portfolio. I am Samuel, and I invite you to explore my projects. Click on each header to delve into the details of each project. Within each project, you will find the comprehensive scripts I employed for analysis and development.

Thank you for your interest.

## [Project 1: Predicting Employees Churn](https://github.com/SamuelDS1/Data-Science-Portfolio/tree/main/Projects/Project%201:%20Employees%20Churn) 
Employee churn, the phenomenon of employees leaving an organization, poses significant challenges for businesses in terms of productivity, morale, and financial implications. By leveraging the power of data, I have created a predictive model that effectively forecasts the likelihood of employees leaving a company.
Through data analysis, I have identified key factors that contribute to employee attrition, such as the number of companies employees worked for before, monthly compensation and . By using decision trees, and random forests, I have developed a model that can anticipate employees churn with **90% precision**.

### Problem
There´s a lot of employees leaving the company and the directors don't know why. The **objective** is to predict employees churn so we can reduce it and save money to the company; we want to know what are the employee's characteristics that make it churn.


## Data 
We'll use a Data set called employees. All the rows in the data represent one employee and describe certain characteristics about it. The data comes from a DS course, you can find it in here [Course](https://ds4b.teachable.com/courses).
**Preprocessing and cleaning** the data was by far the most time-consuming task of the project. The only **data quility issue** encountered was the class inbalance in churn variable. 


### Analysis
The analysis revealed that there's a 16% churn rate.
![avg churn profile](images/churn_rate_employees_churn.png)

Further investigation shows that most employees who churned:
*  Had a low educational level.
*  Were single at the time.
*  Worked extra hours.
*  Worked in sales.

![avg churn profile](images/avg_churn_profile.png)

### Economic impact.

According to the Center of American Progress (CAP), the average turnover cost of employees based on their salary is:
* 16.1% for salaries below $30,000 a year.
* 19.7% for salaries below $50,000 a year.
* 20.4% for salaries below $75,000 a year.
* 21.4% for all cases (we will take this as more than 75k a year)

You can see more detailed information at [Center of American Progress](https://www.americanprogress.org/article/there-are-significant-business-costs-to-replacing-employees/)

Based on this information the potential losses can be up to **$5,470,760 USD**. 





