![](https://user-images.githubusercontent.com/64694891/142995964-ad7912b9-e46e-4bc7-8076-8e5c93c95c95.png)

# A breif introduction about the Jobathon:
This Jobathon hosted by Analytics Vidhya is one of the India's Largest Data Science Hiring Event, where in the last Jobathon 1600+ of candidates have interviewed for over 65+ companies. In this Jobathon, **7677** people participated for a course of 3 days including me. This jobathon had one of the most challenging and unique problem statement.

# Ranking:
**12 out of 7677**

# Problem Statement:
## Predicting Employee Attrition    
In recent years, attention has increasingly been paid to human resources (HR), since worker quality and skills represent a growth factor and a real competitive advantage for companies. After proving its mettle in sales and marketing, artificial intelligence is also becoming central to employee-related decisions within HR management. Organizational growth largely depends on staff retention. Losing employees frequently impacts the morale of the organization and hiring new employees is more expensive than retaining existing ones. 

You are working as a data scientist with HR Department of a large insurance company focused on sales team attrition. Insurance sales teams help insurance companies generate new business by contacting potential customers and selling one or more types of insurance. The department generally sees high attrition and thus staffing becomes a crucial aspect. 

To aid staffing, you are provided with the monthly information for a segment of employees for 2016 and 2017 and tasked to predict whether a current employee will be leaving the organization in the upcoming two quarters (01 Jan 2018 - 01 July 2018) or not, given:

1. Demographics of the employee (city, age, gender etc.)
2. Tenure information (joining date, Last Date)
3. Historical data regarding the performance of the employee (Quarterly rating, Monthly business acquired, designation, salary)

## Data Dictionary
Given below is the data description and a screenshot of the data. 

**Train Data**

* `Variable | Definition`
* `MMMM-YY | Reporting Date (Monthly)`
* `Emp_ID | Unique id for employees`
* `Age | Age of the employee`
* `Gender | Gender of the employee`
* `City | City Code of the employee`
* `Education_Level | Education level : Bachelor, Master or College`
* `Salary | Salary of the employee`
* `Dateofjoining | Joining date for the employee`
* `LastWorkingDate | Last date of working for the employee`
* `Joining Designation | Designation of the employee at the time of joining`
* `Designation | Designation of the employee at the time of reporting`
* `Total_Business_Value | The total business value acquired by the employee in a month (negative business indicates 
cancellation/refund of sold insurance policies)`
* `Quarterly Rating | Quarterly rating of the employee: 1,2,3,4 (higher is better)`

![](https://user-images.githubusercontent.com/64694891/142997967-01bbdc2c-120d-48ee-ab2e-e19e7aaec4d1.png)

**Test Data**

* `Variable | Definition`
* `Emp_ID | Unique Id for the employee`

### Evaluation Metric:
The evaluation metric for this competition was macro f1_score

# My Approach:
The problem statement combined machine learning along with the time series in which the most difficult part was changing the problem into a machine learning problem and then transform the data accordingly.

As the main objective of this problem statement was predicting the attrition of employees or the employees who are going to leave the company in the next two quaters, the target variable will be 0 incase of no attrition or 1 in case of attrition. I created the target variable from the training data with the help of feature `LastWorkingDate`. If the last working date of the employee was given in the dataset, then he/she have left the company otherwise if the last working date was null, the employee is still working in the company. The next step was to remove the employees with the `Emp_ID` present in the test dataset, as they are the ones we are to trying to predict for.

I also created some features like `experience` which explained that how much experience the employee has after each reporting at the start of the month. These features along with the other features like `Quarterly Rating`, `Joining Designation`, `Designation`, `Salary`, `Age` were very important in giving the insights that an employee is going to leave the company or not. Finally, I merged the test data with the training data on the basis of `Emp_ID` and then removed it from the original data for the model building.

# Model Building:
To build a model with good learning and interpretition, I first of all scaled the data and then balanced the data in order to avoid the bias or variance. I used the Logistic regression model as my model of choice as it will identify the perfect relationship between the variables and target after the scaling as we saw that the relationship is linear. I used the class weight as balanced and the other parameters were default.

## Final Performance:
Logostic Regression model learned the data very well and thus resulting into a very good performance on the leaderboard. The metrics that I used as mentioned was f1_score. The final score that I got is **0.7289** on the private leaderboard with rank **12** and a score of **0.7175** on the public leaderboard with rank **32**.

Please find the notebook with the complete code [here](https://github.com/AmandeepSinghDhalla/Hackathons/blob/Job-A-Thon-Nov-Dec-2021/Jobathon%20Nov-%202021.ipynb)
