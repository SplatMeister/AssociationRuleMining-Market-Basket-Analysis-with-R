# AssociationRuleMining-Market-Basket-Analysis-with-R
To perform association rule mining, the UCI machine learning repository includes a large variety of data sets. The main objective is to select a data set that is most appropriate to perform association rule mining and discover relationships among variables. 
Market Basket Analysis
Introduction
To perform association rule mining, the UCI machine learning repository includes a large variety of data sets. The main objective is to select a data set that is most appropriate to perform association rule mining and discover relationships among variables. To carry out association rule mining the “Online Retail Data Set” is used. The data set consists of 541,909 transactions on information on customer purchases across over 30 countries and states from around the world. Association rule mining can be used to find relationships between many variables. This is not restricted to only retail data but, across different types of data and find correlations among these variables and provide insights from the Online Retail Data Set.  
1.1 Objectives 
The association rule mining is widely used to analyze large data sets and derive correlations, frequent patterns, and associations from different types of data sets. Which includes transactional databases and relational databases. It is visible that many fields including, retail and healthcare are some of the prominent fields that use association rule mining to derive meaningful insights from the data. This results in understanding their consumers better and analyze their purchasing patterns. 
For instance, utilizing purchasing patterns in relation to retail stores and finding insights, “Target” one of the supermarket chains in America. Managed to predict a teenage girl pregnancy in 2012 prior to her father knowing about it. Target used its historic purchase data to analyze patterns in purchases. Thereafter, Target managed to send out coupons based on purchase history and likely what she may purchase next. To derive these insights Target may have used a combination of data mining and machine learning methods to derive these results. However, the Target case study is an example how association rule mining can help better understand customers better and analyze patterns from large data sets. 
Based on the above-mentioned example, there are several other benefits that organizations gain through association rule mining. 
1.	Understanding consumer insights.
By analyzing customer purchase behavior can result on understanding customers purchasing habits and gain insights into what products and purchased together or what customer personas will purchase certain types of products. As a result of understanding customer insights, companies can leverage on product placements and identify what products will be purchased together. 
2.	Customized marketing 
Companies allocate a substantial amount of budget for marketing activities, and this includes advertising. To derive the highest return on investment and conversions, companies look for methods to identify how best the marketing budget should be allocated. Through association rule mining, customers will have a better understanding what product groups should be focused and identify the right target audience and spend the marketing budgets efficiently and effectively. 
3.	Improve logistic operations.
Companies always look at efficient methods in utilizing its limited space. For an instance, retail store that is planning to operate in a new location with a limited space. Will have barriers in displaying or stocking all product types. Therefore, association rule mining will identify the most popular products that are purchased based on historic transactions. Based on the analysis the retail store will be able to stock more of the fast-moving products and will reduce the need for frequent restocking. In addition, the retail store will be able to use the limited spaced showroom to display fast moving items in a prominent location. This will ensure easy access to customers in the showroom. 
Based on the above mentioned three benefits, using association rule mining will improve decision making in an organization. Currently many organizations, lack the ability to make comprehensive decisions based on data. Through association rule mining and the findings that are generated can leverage companies on making more precise decisions backed by data and can monitor and make changes on the run. This will help organizations to reduce costs and increase revenue and most importantly understand consumer patterns and provide products or services to consumers and increase customer satisfaction. 
1.2 Data set description
The “Online Retail Data Set” is a retail data set that consist of transactions between 01/12/2010 to 09/12/2011 of an UK company. The company promotes all occasion gift items that are sold to customers who are wholesalers. 
Based on the data set, after performing exploratory data analysis using “quick_eda” from the python library. The attribute “Country” consists of 37 unique countries and the corresponding unit price and customer ID (Appendix 1.2.1). 
 
Figure 1 quick-eda Report
The above report represents a large portion of purchases taking place from United Kingdom and other markets. Therefore, it is visible that the UK based company is a e commerce platform that sells goods to the home market which is the United Kingdom and other international markets. 

Upon further analysis it is visible that there are purchases that take place from other international markets apart from the UK. There are 4,225 unique transactions that has taken place on the ecommerce platform. In terms of transactions there are small portion that has contributed from other markets (Appendix 1.2.2). 











The online retail data set reflects sales and transaction patterns over a period of one year. Therefore, the data set can provide valuable insights about purchase patterns across other markets. The data set can be used to determine product suggestions for customers who enter the website. Generally, customers browse through the web site to find products they require. However, after performing association rule mining. The online retail website can suggest products that more likely the customers would buy. This will result in higher conversion rate. 


The data set consists of 8 attributes, which includes details of all purchases from the unit price to location it was purchased. The attributes and variables can provide insights on purchase patterns and derive frequent bought items.
Attribute	Information
InvoiceNo	Unique number to identify transaction
StockCode	Unique number to identify product
Description	Description of the product
Quantity	Number of products purchased
InvoiceDate	The date and time of transaction was made
UnitPrice	Price of one product
CustomerID	Unique number to identify customer
Country	Location the purchase took place

1.3 Data preprocessing
In order carry out association rule mining the data set requires to be preprocessed and changed to a suitable format to derive patterns through association rule mining. As the first step the data frame loaded to R and the data set consists of 541,909 records with 8 attributes. 
In the data cleaning process, identifying if there are any missing values. This is to ensure that the findings are accurate, and the data is complete. The data set consisted of 135,080 missing values. Which brought the transactions down to 406,829 from 541,909. Secondly, identifying negative values in the transactions. Since negative values indicates that the transactions were reversed. Therefore, it is important to remove the 8,905 transactions. Which resulted the transaction count to further reduce to 397,924. Thereafter under description remarks that are lower case are removed. This is due to the description that mentions the rejected transactions and the respective reasons. For instance, “mouldy, thrown away”, “mouldy, unsaleable” and “missing” are the remarks that are included in lower case. Therefore, all lower-case descriptions are removed which accumulated to 1,662. Thereafter, identified if there are any transactions where the “UnitPrice” is 0. These transactions are promotional items that has been provided at no unit price. Therefore, these transactions are removed. There are 34 transactions with the unit price is 0. In addition, removed “StockCode” that does not contain any number. This is due to the stock code which has an alphabetic letter did not consist of any customer ID number. Therefore, these transactions are not valid. In total 1,118 transactions are removed from the data set. Finally, under the stock code attribute values which consisted of “C2” removed. This is due to the corresponding attribute Description includes all values as “CARRAIGE”. Therefore 133 transactions are removed. In the end of the data cleaning process the transactions reduced from 541,909 transactions to 394,977 (Appendix 1.3.1). 








To ensure the cleaned data set does not have any outliers, visualized based on the quantity (Appendix 1.3.2). 
 
Figure 3 Boxplot of Quantity (before removing outliers)
Based on the above boxplot there are several outliers that needs to be removed and to remove the outliers where the range is defined by the first and third quartiles and the interquartile range. 
 
Figure 4 Boxplot of Quantity (after removing outliers)
After removing the outliers, the data transaction reduced to 369,462. As a result of this association rule mining will be able to generate an accurate analysis. 
Based on the above mentioned preprocessing the data set consisted of many observations and some needed to be removed based on the rational provided in the data processing steps to derive an accurate analysis prior to rule mining process.
For association rule mining based on the given data set, some of the variables that are used which includes ‘Country’, ‘Description’ and ‘InvoiceNo’ are categorical and can be used for association rule mining. However, to better understand the quantity and how it has been distributed equally and which bracket it falls under. The quantity is broken equally and added to the data frame (Appendix 1.3.3). 
Prior to performing rule mining, it is important an overview of the data set. Therefore, to identify if any attributes are required and to initial understanding of the data set is crucial. To understand what the quantity orders belong to which category. The quantity is divided by low, medium, and high (Appendix 1.3.4).  
 
Figure 5 Histogram by Quantity Ordered
Based on the above histogram most of the quantity falls under the low orders. Therefore, it is important to see if there is a seasonality in purchases and a particular month contributes to the overall orders (Appendix 1.3.5). 
 
Figure 6 Histogram Quantity by Month
The histogram of quantity ordered by month shows that most of the orders were placed within the data period. November had the highest order quantity, while January and August had proportionately lower order quantities. Based on this insight, to increase the order quantity during the low months, steps can be taken to improve the orders by identifying rules to improve order quantities. Finally, the ‘CustomerID’ and ‘Date’ columns are removed as these attributes are not required for rule mining. 


1. 4 Rule Mining & Resulting Rules
1.	Top 10 Rules with support at 0.2% and the confidence at 80%.
After preprocessing the data set, for setting parameters for the processed data set. The minimum support is set at 0.2% and the confidence at 80%. This ratio is set to determine high quality association rules to determine if the preprocessed data set can provide the most optimal association rules. 
The algorithm that is used is Apriori algorithm. Since, the data set is the most suitable for market basket analysis to find frequently occurring sets of items and analyze purchase patterns.
Considering only the top 10 association rules (Appendix 1.4.1). 
 
Figure 7 Top 10 Rules Using the Grouped Method by 0.2% and the confidence at 80%
 
The items set “Wobbly Rabbit” is highly associated with “Metal” and “Decoration”. This represents that customers who purchase wobbly rabbit is likely to purchase metal and decorations. Furthermore, the item “Black Tea” is also associated with “Sugar jars” and “Coffee”. Finally, the item “Hook” is also associated with “Hanger” and “Magic Garden”. Based on the lift “Wobbly Rabbit” with “Metal” and “Funky Monkey” with “Art Lights” has high lift values. Therefore, this can be used to make good product recommendations to make placements on the website for purchasing.


 
Figure 8 Top 10 Association Graph

2.	Top 10 Rules with support at 0.3% and the confidence at 80%.
For the second iteration on the top ten rules by support and confidence the support is increased to 0.3% and confidence is at 80% to maintain a quality rules.







Based on the above top 10 rules and increasing the support by 0.3% has derived new rules. For instance, “White Tea” with “Sugar Jars” has a support of 0.003300749, that the rule has 0.33% of all transactions. The lift value of 207 indicates that customers who bought white tea are 207 times likely to buy sugar jars. 
If a customer buys white tea, the customers are 100% likely to buy sugar jars and if customers purchase metal items, they are 100% likely to buy decoration items. Also, if a customer purchase painted letters are likely to buy items “B” or “Nursery A”.
 
Figure 10 Figure 8 Top 10 Association Graph





3.	Top 10 Rules with support at 0.4% and the confidence at 80%.
To further investigate the rules, the support level is increased to 0.4% and confidence left at the same value of 80%. 
 
Figure 11 Top 10 Rules Using the Grouped Method by 0.4% and the confidence at 80%
The item set “Sugar Jars” and “Coffee” has a higher lift. The item set “Airline Lounge” and “Metal Sign” has the highest lift. This results in customers who purchase lounge sign are likely to buy other metal signs and important to cross sell. 

 
Figure 12 10 Figure 8 Top 10 Association Graph

1.5 Recommendations
Since, the UK based e commerce retail store carries its operations through the website and most of the transactions are carried out to the local UK market and overseas market. Based on the initial data exploration. It was evident that January to August were low order months. Therefore, using association rule mining on the given data set. Can improve the website placements of products and provide suggestions to whole seller customers. 
Users visit to buy goods based on their requirement and many spend time searching for products they require and check out. Therefore, based on the rules that were generated. The UK based online retails store can revamp the website and provide recommendations. 
Based on the rules that were discovered, for instance if a customer purchase “Wobbly Rabbit” the placement on the website can suggest “Decoration” and “Metal” items to increase the cart quantity and value. Furthermore, this can be used to determine items that frequently bought together. 
 
Figure 13 Website Outlook with Related Products

In addition, using “Google Analytics” and incorporating a “Google Analytics Tag” on the site to track transactions of users. The store can identify users who purchase specific products and target product related campaigns through digital media platforms. For instance, if a customer purchase “Black Tea” are likely to buy “Sugar Jars” and “Coffee”. The promotional campaign can identify users who bought black tea with Google Analytics and run ads with sugar jars and coffee. 
 
Figure 14 Digital Banner Ads for Targeted Ads
As a result of this, the online retails store can provide product recommendations to customers and provide targeted marketing campaigns to increase purchase quantity and increase revenue. 
