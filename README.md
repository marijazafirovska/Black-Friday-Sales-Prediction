# Black-Friday-Sales-Prediction

<h3>Project description</h3>

A retail company wants to understand the customer purchase behavior (specifically, purchase amount) against various products of different categories.
They have shared a purchase summary of various customers for selected high volume products from last month. 

The data set also contains customer demographics (age, gender, marital status, city type, stay in_current_city), product details (product_id and product category) and Total purchase_amount from last month. 

<i>Now, they want to build a model to predict the purchase amount of customer against various products which will help them to create personalized offer for customers against different products <i>.
  
Your goal in this project is to create a robust regression model, that will use this data to predict the customers' total purchase amount for different products. 
  
  The project will be presented through the following stages:
  
- [Understanding the Business](#understanding-the-business)
- [Understanding the Data](#understanding-the-data)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Preparation](#data-preparation)
- [Data Modeling](#data-modeling)
- [Results Evaluation](#results-evaluation)
  
</small></p>

## Understanding the Business
<p>
The first Friday after Thanksgiving has been considered as the beginning of the Christmas shopping season in the USA since 1952. 
There are few theories how this day received its name. According to one of them, in the 1950s, many manages of companies started to call the first Friday after Thanksgiving as Black Friday due to reported sick leave from many of their workers on this day.
Years later, Black Friday was used by Philadelphia cops to describe the day after Thanksgiving because they had to work extended hours in terrible traffic. 

According to the most frequently present theory, on this day, occur 30- 40% of the total annual retail sales, and this is the period of the year when financial books move " from red into the black".  The previous comes from the old bookkeeping practice of recording profits in black ink and losses in red ink. 

However, in the last years the classic Black Friday has been replaced by the Cyber Black Friday, which is marketing word for its online version. The term was first used in 2009 in a press release entitled "Black Friday Goes Online for Cyber Black Friday".

Retailers develop their Black Friday sales plans and strategies entire year. They use different strategies, but mostly they offer low prices for overstock inventory and different discounts on seasonal products.
Additionally, high discounts for expensive brands of TVs, smart devices, and other electronics are offered. Also, special attention is paid on the Black Friday advertisements content, directed towards driving highest sales.
As a result of the previous, can be concluded how important is for retailers to have excellent knowledge of their costumer’s behavior, and accordingly, to implement the best marketing strategies for each customer segment.
</p>

## Understanding the Data
The data set consist of:
  - 550.068 records (rows)
  -   5.891 unique customers
  -   3.631 unique products. 
  -   7 numeric and 5 object features 
Missing values were identified in two columns, Product_category_2 (173.638 or 31%) and Product_category_3 (383.247 or 69%). The missing values will be filled in the Data Preprocessing part. 

## Exploratory Data Analysis
### Univariate Analysis
For this analysis, the seaborn library was used for creation of count plots for each categorical variable. These charts are expected to give picture of the number of transaction per category in every analyzed variable.
Insights:
1. In figure 1, The most transactions are performed by the customers in the range of 26–35 age 
2. In figure 2, Male customers executed more transactions than females.
3. In figure 3, Customers with occupations 0 and 4 performed the most transactions.
4. In figure 4, Custumers who stayed in the current city for 1 year, performed the highest number of transactions.
5. In figure 5, Customers from city category B, did the highest number of transactions.
6. In figure 6, Customers who are single, performed more transactions than married customers.

However, at this point, final conclusions in this respect cannot be made, but further analysis will be performed.

### Bivariate Analysis
Bivariate Analysis relates to analysis of two variables, for the purpose of determining the empirical relationship between them. In our case, the relationship between each categorical variable and the Purchase variable will be analyzed. 

Insights:
1. In figure 1, The most money was spent by customers aged 26 to 35 years.
2. In figure 2, Male customers spent more money than females.
3. In figure 3, Customers with occupations 0 and 4 spent the most.
4. In figure 4, costumer who stayed in the current city for 1 year spent the most.
5. In figure 5, Customers from city category B spent the most.
6. In figure 6, Customers who are single, spent more money than married customers.

If the insights from both analysis (univariate and bivariate) are compared, can be conclude that the same results were received. The reason behind this is the disbalance of the categories in each of the analyzed features. 

Consequently, the bivariate analysis will be supplemented with analysis of the relationship between the average of each categorical feature and the Purchase feature.

As it was assumed, this analysis shows that there is no significant correlation between each category within a feature and the Purchase. With other words, the presented correlation in the previous visualization was driven by the misbalanced set of data. 

## Data Preparation
## Data Modeling
## Results Evaluation



