# Data Science Portfolio
Hi! My name is Samuel. Take a look at my porfolio!
Click in each header to see more about each project. If you want to see the scripts I used you'll find them inside of each project.  


## [Project 1: Predicting Employees Churn](https://github.com/SamuelDS1/Data-Science-Portfolio/tree/main/Projects/Project%201:%20Employees%20Churn) 
Employee churn, the phenomenon of employees leaving an organization, poses significant challenges for businesses in terms of productivity, morale, and financial implications. By leveraging the power of data, I have created a predictive model that effectively forecasts the likelihood of employees leaving a company.
Through data analysis, I have identified key factors that contribute to employee attrition, such as job satisfaction and compensation. By using decision trees, and random forests, I have developed a model that can anticipate employees churn with **90% precision**.

### Problem to solve
The objective is to predict employees churn so we can reduce it and save money to the company; we want to know what are the characteristics of employees that are most likely to quit.


### Analysis
After cleaning the data the analysis revealed that there's a 16% churn rate.
![avg churn profile](images/churn_rate_employees_churn.png)

I also found out that most employees who churned:
*  Had a low educational level.
*  Where single at the time.
*  Worked extra hours.
*  Worked in sales.

![avg churn profile](images/avg_churn_profile.png)

#### Economic impact.

According to the Center of American Progress (CAP), the average turnover cost of employees based on their salary is:
* 16.1% for salaries below $30,000 a year.
* 19.7% for salaries below $50,000 a year.
* 20.4% for salaries below $75,000 a year.
* 21.4% for all cases (we will take this as more than 75k a year)

You can see more detailed information at [Center of American Progress](https://www.americanprogress.org/article/there-are-significant-business-costs-to-replacing-employees/)

Based on this information the potential losses can be up to **$5,470,760 USD**. 

<div class='tableauPlaceholder' id='viz1687914385537' style='position: relative'><noscript><a href='#'><img alt='Dashboard Employees Churn ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;em&#47;employees_churn_data_visualization&#47;Dashboard1&#47;1_rss.png' style='border: none' /></a></noscript><object class='tableauViz'  style='display:none;'><param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> <param name='embed_code_version' value='3' /> <param name='site_root' value='' /><param name='name' value='employees_churn_data_visualization&#47;Dashboard1' /><param name='tabs' value='no' /><param name='toolbar' value='yes' /><param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;em&#47;employees_churn_data_visualization&#47;Dashboard1&#47;1.png' /> <param name='animate_transition' value='yes' /><param name='display_static_image' value='yes' /><param name='display_spinner' value='yes' /><param name='display_overlay' value='yes' /><param name='display_count' value='yes' /><param name='language' value='es-ES' /></object></div>                <script type='text/javascript'>                    var divElement = document.getElementById('viz1687914385537');                    var vizElement = divElement.getElementsByTagName('object')[0];                    if ( divElement.offsetWidth > 800 ) { vizElement.style.width='1366px';vizElement.style.height='795px';} else if ( divElement.offsetWidth > 500 ) { vizElement.style.width='1366px';vizElement.style.height='795px';} else { vizElement.style.width='100%';vizElement.style.height='1177px';}                     var scriptElement = document.createElement('script');                    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';                    vizElement.parentNode.insertBefore(scriptElement, vizElement);                </script>







