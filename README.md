# Overview






![MEX Bank](https://github.com/user-attachments/assets/9c89ceeb-17ab-47d4-a65d-a2a3f9026118)




# Problem Statement:
Mex bank has experienced a steady reduction in customer retention, with a rise in customers closing their accounts. The bank manager needs to know the major drivers of customers churn in the bank, the group of customers that are likely to churn, and develop data-driven strategies to maintain long-term relationships with their customers. 

# Objectives:
•	To identify high-risk customer groups that are likely to churn. 
•	To investigate the relationship between customers’ demographics (location, age, account balance, credit score, etc.) and churn.
•	To recommend data-centric solutions to reduce customer’s churn rate at MEX Bank. 

# Data Description: 
The dataset covers customers’ demographics and account information across two tables. 

## Table 1: 
* CustomerId: A unique identifier for each customer
* Surname: The customer’s last name
* CreditScore: A numerical value representing the customer’s credit score
* Geography: The country where the customer resides (France, Spain, or Germany)
* Gender: The customer’s gender (Male or Female)
* Age: The customer’s age
* Tenure: How long the customer has been with the bank
* EstimatedSalary: The estimated salary of the customer

## Table 2: 
* CustomerId: A unique identifier for each customer
* Balance: The account balance of the customer
* Numofproducts: The number of bank products that the customer uses (runs from 1 to 4)
* HasCrCard: Indicates whether the customer has credit card or not. (Yes/No)
* Tenure: How long the customer has been with the bank. 
* IsActiveMember: Whether the customer is an active member (Yes/No)
* Exited: Whether the customer has churned or not. (1=Yes, 2=No). 
* Data Preparation Procedure

# Data Cleaning: 
## Cleaning Steps:
1.	Standardized rows
2.	Removed duplicates
3.	Replaced Exited 1 or 0 with “Yes” or “No”
4.	Replaced French and FRA in geography with “France” using the formula ` =IFS(D2="FRA", "France", D2="French", "France", TRUE, D2)`
6.	Replaced the “?” the name H? with H using the substitute formula.. `=SUBSTITUTE(B2, "H?", "H")`
8.	Negative EstimatedSalary values were assumed invalid and deleted from the dataset.
9.	Combined the tables using… `=XLOOKUP($A3, Customer_Info!$A:$A, Customer_Info!D:D)`

# Groupings Created: 
1. Age Grouping: Age grouping was done using… `=IFS(F2<25, "18-24", F2<35, "25-34", F2<45, "35-55", F2<65, "55-64", F2>=65, "65+")`
2. Credit Score Grouping: 
Poor (300-579), Fair (580-669), Good (670-739), Very Good (740-799), Excellent (800-850)
Calculation `=IFS(C2<580, "Poor", C2<670, "Fair", C2<740, "Good", C2<800, "Very good", C2>=800, "Excellent")`.
3. Products Engagement Grouping (NumOfProducts): 
Low Engagement (1 product), Medium Engagement (2-3), High Engagement (4)
Calculation `=IFS(J2=1, "Low Engagement", J2<=3, "Medium Engagement", J2=4, "High Engagement")`
4. Income Category: low income (0-29,999), Lower-Middle Income (30,000-59,999), Upper-Middle Income (60,000-89,999), High Income (90,000 -120,000), Very High Income (>120,000). 
Calculation… `=IFS(H2<30000, "Low Income", H2<60000, "Lower-Middle Income", H2<=120000, "High Income", H2>120000, "Very High Income")`
5. Customers’ Balance: Zero balance (0), Low balance (1k – 49,999), Regular User (50k-99999), High Balance (100k-149999), Very High (>150,000).
Calculation… `=IFS(I2=0, "Zero Balance", I2<50000, "Low Balance", I2<100000, "Regular User", I2<150000, "High Balance", I2>=150000, "Very High")`
6. Tenure Grouping: New Customers (0-1years), Developing Customers (2-3years), Old Customers (4-6 years), Loyal Customers (7-10 years). 
Calculation… `=IFS([@Tenure2]<=1, "0-1", [@Tenure2]<=3, "2-3", [@Tenure2]<=6, "4-6", [@Tenure2]<=10, "7-10")`

# Key Insights
## Key Performance Indicators (KPIs):
* Average Age of Customers –indicates the average age of all customers in the bank
* Total Customers: Indicates that the total number of customers at the time of the analysis is 9997
* Average Tenure: Shows that the average duration a customer has banked with MEX is 5 years
* % churn: is the percentage of customers that left compared to the total. A 20.4% churn shows that a high number of customers are leaving, indicating a need to worry about the customers’ exit and develop retention strategies. 

# Customers Churn Insights
## Customer Demographics
<img width="631" height="290" alt="Mex customers demographics" src="https://github.com/user-attachments/assets/933c01b2-9149-49ed-84c8-5d02719cb406" />

* Female customers churned more.
* Customers in Germany churned more (814), followed by those in France (810).
* Customers within the pre-retirement age bracket (55-64) churned more followed by the mid-adults (35-44).
* Very high income earning customers churned more

## Customer Behaviour

  <img width="632" height="287" alt="Mex customers behaviour" src="https://github.com/user-attachments/assets/e4de6668-436d-47ba-88ac-720c630b90c1" />

* Customers with inactive accounts and without credit cards have higher churn
* Customers who interact with the least products churned more
* Customers with high account balance, and have spent more than 6 years with the bank churned more which could be a result of poor service attitude or inappropriate staff conduct.
* The fair (580-669) and poor (300-579) credit scores bands churned more. 

# Recommendation
1.	Conduct in-depth research into staff interactions, response to customer complaints and service quality to identify the major cause of dissatisfaction among high balance and long-term customers. 
2.	Launch region-specific survey to identify the major causes of high churn in Germany and France and potential competition. 
3.	Design a loyalty program that rewards engagement and tenure offering VIP benefits to long-term and high engagement customers. 
4.	Create female-targeted marketing campaigns and services to promote inclusivity among the female customers. 
5.	Introduce financial literacy programs for customers with poor and fair credit scores to help build trust, help them improve financial stability and reduce churn. 
6.	Provide age-specific financial planning programs. Introduce attractive retirement webinars, banking and investment opportunities to attract customers within the pre-retirement and mid-adult age. 

# Conclusion 
A 20.4% churn rate for MEX bank is high and a major call for concern. This analysis shows that not only are the new customers or low value customers churning, but high value customers are also leaving. Customers with a high account balance, in the high-income bracket, within the pre-retirement age and mid-adults, and those that have spent up to 10 years banking with MEX constitute the major churned customers indicating a need for retention strategies that runs across service satisfaction, engagement, and personalization services. 
Also, customers with no credit cards, who are less active and have low engagement with MEX bank products are likely to churn. 
By leveraging insights from this analysis and acting on the recommendations, MEX bank can actively reduce churn, improve customer satisfaction and drive long-term growth. 



 


