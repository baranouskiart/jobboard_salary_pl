# Salary Estimator: Project Overview 
* Created a tool that estimates salaries **(MAE ~ ZL ???K)** to help polish specialists negotiate their income when they get a job.
* Scraped over **????** job descriptions from **RocketJobs??** using python and selenium
* Engineered features from the text of each job description to quantify the value companies put on python, excel, aws, and spark. 
* Optimized Linear, Lasso, and Random Forest Regressors using GridsearchCV to reach the best model. 
* Built a client facing API using flask 

## Code and Resources Used 
**Python Version:**  - ?????????? (3.7 prev)
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn, selenium, flask, json, pickle  
**For Web Framework Requirements:**  ```pip install -r requirements.txt```  
**Scraper Github:** https://github.com/arapfaik/scraping-glassdoor-selenium  
**Original project:** https://github.com/PlayingNumbers/ds_salary_proj/  

## Web Scraping
With each job, we got the following:
*	Job title
*	Salary Estimate
*	Job Description
*	Company 
*	Location
*	Industry
*	Sector

## Data Cleaning
After scraping the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

*	Parsed numeric data out of salary 
*	Made columns for employer provided salary and hourly wages 
*	Removed rows without salary 
*	Made a new column for company state 
*	Made columns for if different skills were listed in the job description:
    * Python  
    * Tableu
    * Excel  
    * PowerBI
    * LookerStudio
*	Column for simplified job title and Seniority 
*	Column for description length 

## EDA
I looked at the distributions of the data and the value counts for the various categorical variables. 

Below are a few highlights from the pivot tables. 

"Salary by Position"
"Job Opportunities by State"
"Correlations"

## Model Building 

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.   

I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.   

I tried three different models:
*	**Multiple Linear Regression** – Baseline for the model
*	**Lasso Regression** – Because of the sparse data from the many categorical variables, I thought a normalized regression like lasso would be effective.
*	**Random Forest** – Again, with the sparsity associated with the data, I thought that this would be a good fit. 

## Model performance
The Random Forest model far outperformed the other approaches on the test and validation sets. 
*	**Random Forest** : MAE = ??????????????????
*	**Linear Regression**: MAE = ??????????????????
*	**Ridge Regression**: MAE = ??????????????????

## Productionization 
In this step, I built a flask API endpoint that was hosted on a local webserver by following along with the TDS tutorial in the reference section above. The API endpoint takes in a request with a list of values from a job listing and returns an estimated salary. 



