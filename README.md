# Generic Buy Now, Pay Later Project  
## - Low Risk, High Profit Project For Small BNPL Componies  
### Group 23: Yang Chen, Jialu Feng, Yu Deng, Yiting Liu, Liyang Chen
#### Audience:
Small BNPL companies who pursing low risk and continuous profit.
#### Action taken:
Only cooperate with no fraud record merchants or users.(Delete the probable fraud data)
#### Benefits:
No risk taken -> higher efficiency(every transaction will be complete safely).
#### Disadvantage:
Losing some costumers with relative low fraud probability.

## Project Overview:
![image](https://github.com/MAST30034-Applied-Data-Science/generic-buy-now-pay-later-project-group-23/blob/main/plots/blog-buy-now-pay-later.png)
BNPL, as the name suggests, is a transaction form that allows users to get the goods first and then pay. As long as the users' credit score is high enough, they can buy any goods they want. At the moment of the pandemic, BNPL is much more widely used, which is a project with great potential.

Our project has designed a merchant ranking system. As long as the merchant data is provided, the top merchants can be quickly obtained according to the algorithm. You can also enter keywords to query the top merchants under the corresponding label. If you request, we can also manually process the data to come up with some more interesting findings.

## How Does Our Algorithm Generated?
A demo dataset of merchant and customer information was used for this.
### Preliminary Analysis
#### Missing Value and Outlier Detection & Removing
In the demo dataset, dollar_value seriously dispersed, the maximum value is 77320, but the 75% quantile is only 150.42. Therefore outliers detected, after delete them the distribution become better.  
![image](https://github.com/MAST30034-Applied-Data-Science/generic-buy-now-pay-later-project-group-23/blob/main/plots/dollar_value.png)
![image](https://github.com/MAST30034-Applied-Data-Science/generic-buy-now-pay-later-project-group-23/blob/main/plots/dlt_dollar_value.png)  
  
By checking the revenue level distribution, it is clear to see the main customer’s revenue level are relative low(a,b,c).
![image](https://github.com/MAST30034-Applied-Data-Science/generic-buy-now-pay-later-project-group-23/blob/main/plots/revenue_level.png)  
Users with higher revenue level has higher fraud probability(60%-70%), even lower revenue level have over 30% fraud probability which is relative high. For each merchant, revenue level their probability of fraud is 14%.  
  
#### Why We Can Ensure Low Risk?
It can be seen above that users with higher revenue level has higher fraud probability(60%-70%), even lower revenue level have over 30% fraud probability which is relative high. For each merchant,revenue level their probability of fraud is 14%.  
![image](https://github.com/MAST30034-Applied-Data-Science/generic-buy-now-pay-later-project-group-23/blob/main/plots/consumer_fraud_prob.png)
![image](https://github.com/MAST30034-Applied-Data-Science/generic-buy-now-pay-later-project-group-23/blob/main/plots/merchant_fraud_prob.png)  
  
As BNPL is not a new idea, but with the boom in e-commerce during the Covid-19 pandemic, BNPL has exploded onto the payments scene as a major industry. Moreover, Covid-19 had a huge hit on people's economic situation, therefore a safe action need to be taken for this situation. In order to minimise risk, we decided to delete all transaction which may have fraud probability.  
  
The random forest and logistic regression were used to predict whether a transaction will be judged as "fraud". The recall values of both models were low, which means the models badly predicted "isfraud" transactions. Apart from that, because our project is aimed at small businesses that don't want to take the risk, all transactions for merchants and customers with potential for fraud have been removed.  
  
### How the Top Merchants be Generated?
Determine and sort a merchant's possible revenue by transaction amount times take rate, and use this to rank the merchants. The OLS regression model is used, which has fast modeling and simple algorithm, suitable for such data with many instances and columns. Has strong interpretability, can give the interpretation of each variable according to the coefficient.  

#### Variables Used
(for a single merchant)  
usercnt: user amount  
merchcnt: Number of product types sold  
openday: Number of dates that have transactions  
merchant_sold_cnt: total number of products  
ARPU: average revenue per user  
store_gmv: transaction amount  
store_level: maximum revenue level  
order_per_user
and mean amount of the personal income and population.  
  
For the demo dataset, four tags are chosen to be ranked. The main reason we choose cable as one of the tags is that we noticed that there are 12723 (among 215493) transactions(160 merchants) is about Cable tags and the surprising thing is they have same price 157 dollars, rest of transactions price are unique. Therefore we think this 157 dollars product is the most popular one. Thus it becomes one of the tag we discussed. For other tags, they are commonly used item in our daily life therefore and they have enough data.

#### Top Merchants
By the above algorithm, the top merchants can be easily generated. We generate the top 100 among all merchants, and top 10 merchants for each tags. It's not able to show all the top 100 merchants so only the top tens will be displayed below.  
![image](https://github.com/MAST30034-Applied-Data-Science/generic-buy-now-pay-later-project-group-23/blob/main/plots/top10gift.png)  
![image](https://github.com/MAST30034-Applied-Data-Science/generic-buy-now-pay-later-project-group-23/blob/main/plots/top10shoe.png)  
![image](https://github.com/MAST30034-Applied-Data-Science/generic-buy-now-pay-later-project-group-23/blob/main/plots/top10furniture.png)  
![image](https://github.com/MAST30034-Applied-Data-Science/generic-buy-now-pay-later-project-group-23/blob/main/plots/top10cable.png)  
And here's the store names and their predicted revenue:  
![image](https://github.com/MAST30034-Applied-Data-Science/generic-buy-now-pay-later-project-group-23/blob/main/plots/top10csv.jpg)  
  
As shown about, a interesting finding is that gift shops have the highest revenue. According to some research, gift shops can have very high profit if they have a good location and marketing techniques. Setting the gift shops around or inside canteens and cafes can attract many tourists who are tired from travel. With the improvement of the epidemic and the relaxation of policies, there will be increasing number of tourists, so the income of gift shops will not only be like this. Gifts come in all kinds, from ordinary souvenirs to jewelry and antiques, small gifts have small profits but quick turnover, and there are also many people willing to send high-end gifts. Apart from the souvenirs, gifts are also highly used in daily life. Now is the era of clicking to buy, and gift shops can easily expand their online shopping business, which will bring much more profit.  
  
### Future Planning
We will seek to cooperate with some merchant search platforms to create a website that allows users to find the top merchants they want. At the same time, we will also strive to develop algorithms for judging fraudulent transactions to detect fraud more accurately, rather than simply deleting them.
