# Vehicle-Insurance-Cross-Sell
This project aims to order a potential client list by propensity score.
## 1.0 Business Problem

Insurance All is a company that provides vehicle insurance to its customers, and the product team is analyzing the possibility of offering policyholders a new product: **health insurance**.

As with vehicle insurance, customers of this new health insurance plan need to pay an amount annually to Insurance All to obtain an amount insured by the company, intended for the costs of an eventual accident or damage to the vehicle.

Insurance All conducted a survey of about **380,000 customers** about their interest in joining a new health insurance product last year. All customers expressed interest or not in purchasing health insurance, and these responses were saved in a database along with other customer attributes.

The product team selected **127,000 new customers** who did not respond to the survey to participate in a campaign, in which they will receive the offer of the new health insurance product. The offer will be made by the sales team through telephone calls.

However, the **sales team has the capacity to make 20,000 calls** within the campaign period.
## 2.0 Top Insights
* **Early Aulthood and adolescent are about 26.1% of the cutomer who want the vehicle insurance. The midlife customers are more likely to get insurance, they are about 48.3%**
![image](https://github.com/user-attachments/assets/c13e29b2-d9c7-47b1-8e74-0af086ffb404)
* **There is a significant relationship between having health insrance and the likelihood of purchasing vehicle insrance , but not as we think: customers with health insurance are more likely to buy vehicle insurance. It seems that when customers have previously purchased health insurance, they are less inclined to buy vehicle insurance. The probability that a person who previously purchased health insurance will buy vehicle insurance is only 0.09%**

P(Vehicle=Yes | Health=Yes): 0.0009047804475799987
  
P(Vehicle=Yes | Health=No): 0.22545415800969582

Chi-squared: 44357.96472219977

p-value: 0.0

Degrees of Freedom: 1

Conclusion: Have a relationship between having health insurance and the likelihood of purchasing vehicle insurance.
* **97.9% of customers who are interested in purchasing vehicle insurance had previously experienced vehicle damage.**
  ![image](https://github.com/user-attachments/assets/1c1b624a-0806-4224-8c0e-97c2cdaf31d0)
* **Although young customers account for the majority, but they aren't the group customer with the highest likelihood of wanting vehicle insurance. People who want insrance are in between 40 and 50 years old.**
![image](https://github.com/user-attachments/assets/f0fe0299-bda7-445a-8024-88547cf151b8)
## 3.0 Machine Learning Applied
### Model Performance Comparison
Here's all cross validation results of the machine learning models with their default parameters. These metrics corresponds to a k = 50%, up to 50% of data. The cross validation method is important to show the capacity of the model to learn.

| Model               | Precision@K        | Recall@K           | F1@K               |
|---------------------|--------------------|---------------------|--------------------|
| Dummy               | 0.1231 ± 0.0008     | 0.5021 ± 0.0034      | 0.1977 ± 0.0013     |
| LightGBM            | 0.2419 ± 0.0003     | 0.9868 ± 0.0013      | 0.3885 ± 0.0005     |
| Logistic Regression | 0.2421 ± 0.0003     | 0.9877 ± 0.0011      | 0.3889 ± 0.0004     |

### 4.0 Machine Learning Performance
The chosen model was Logistic Regression and it was tuned to improve their parameters and scores. Below there's a table with the capacity of the model to learn.

| Model                 | Precision@K        | Recall@K           | F1@K               |
|-----------------------|--------------------|---------------------|--------------------|
| Logistic Regression GS| 0.2411 ± 0.0003     | 0.9834 ± 0.0013      | 0.3872 ± 0.0005     |

It's possible to determinize the capacity of the model to generalize using unseen data. In other words, capcity of the model to classify new data as shown.
| Model                  | Precision@K | Recall@K | F1@K   |
|------------------------|-------------|----------|--------|
| Logistic Regression GS | 0.2804      | 0.9151   | 0.4293 |
These graphs below show the accumulative gain and lift curve.
![image](https://github.com/user-attachments/assets/022ab2b3-fc76-4fe6-bb50-4ed12a71aecc)
![image](https://github.com/user-attachments/assets/3be5d450-54eb-4701-90ca-110bb7d6b44e)

## 4.0 Business Results

### • What percentage of customers are interested in purchasing auto insurance? Will the sales team be able to reach them by making 20,000 calls?

1. The database is based on **46,876 (12.3%)** of customers interested in health insurance and **334,232 (87.7%)** of customers not interested.

2. The model results have shown that the model has the **precision of 24.11%**  
   (24.14% for excellent performance or 24.06% for poor performance).  
   So, using the model it's possible to contact **4,822** customers interested in health insurance from **20,000 calls**  
   (4,828 for excellent performance or 4,812 for poor performance).  
   However, the **recall is about 98.34% (+/- 0.0013)**.

---

### • If the sales team's capacity increases to 40,000 calls, what percentage of customers interested in purchasing auto insurance will the sales team be able to contact?

Increasing to **40,000 calls**, the model may help the sales team contact **9,644** customers interested in health insurance  
(9,660 for excellent performance or 9,620 for poor performance).

---

### • How many calls does the sales team need to make to contact 80% of customers interested in purchasing auto insurance?

The model sorted **98.31% (46,084 customers)** of the customers interested in 50% of the database with **381,109 customers**.  
Using the model, it's possible to contact **80%** of customers interested in health insurance with **155,064 calls**  
(155,064 for both excellent and poor performance).
