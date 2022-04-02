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
- [Feature Engineering](#feature-engineering)
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
  
**Missing values** were identified in two columns, **Product_category_2** (173.638 or 31%) and **Product_category_3** (383.247 or 69%). The missing values will be filled in the Data Preprocessing part. 

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

### Target variable distribution and outliers

In this section the scipy library was used for plotting the distribution of the target variable.

•	From distribution plot that represent the distribution of Purchase, we can conclude that our target variable follows Gaussian (Norma) distribution.
•	From the boxplot, can be seen that there are few values lying outside (outliers). But if the z-score is considered, can be concluded that there are no values above the usual threshold level (generally taken as 3).
• From the distribution plot that represents the distribution of each Product_Category_1, can be concluded that the target variable follows Gaussian(normal) distribution within each Product_Category_1


## Data Preparation

### Fill in missing values

As it was previously presented, there are 2 variables with missing values. In this regards, different strategies were tested:

o	Fill in with mean value.

o	Fill in with 0.

o	Custom fill in.

However, best results were received with the custom function for filling in the missing values, which includes: 

•	**For Product_category_3:** for all the combinations of values of Product_category_1 and Product_category_2, the most frequent Product_category_3 was found and it was used for filling in the missing values in Product_category_3 for the appropriate combination of the first two categories. For all the missing values in Product_category_3 for which also the Product_category_2 is empty, zero was used for filling in.

  _For example,_ when Product_Category_1 is 3 and Product_Category_2 is 4, the Product_Category_3 occurs as 5, 12, 9 and 8, but the most frequent is 5. This means, that every time when Product_Category_1 is 3, Product_Category_2 is 4 and the value of Product_Category_3 is missing, it will be filled in with 5. 

•	**For Product_category_2:** missing values were filled in with 0.

## Feature Engineering

- From the previous analysis, it was concluded that there is a very weak correlation between each feature and the target variable, except for the Product_Category_1 feature.

    As a result, it was decided, new features to be created, in order to increase the correlation, thus to increase the probability score of the prediction model     which will be developed. 

    The following **2 new features were created**:

     **Category_Count**-  it counts the number of categories (Product_Category_1, Product_Category_2 and Product_Category_3) to which each product belongs.

     **Product_popularity_score**- it counts the number of transaction per product, and then scales the values with MinMaxScaler. 

- In regards to ****label encoding of the categorical features****, different strategies were used, but no improvements of the model were reached. Thus, it was decided to use label encoding, because that way the model training was the fastest.

- After the performed feature engineering, the correlation between each feature and the target variable is presented on a **Correlation matrix**, with using the seaborn heatmap.

From the visualization it can be easily concluded what in fact through the previous analysis was proved, that there is a very low correlation between all the features and the target variable except Product_category_1, Product_category_2, Product_category_3 and the new features Category_count and Product_popularity_score. 

The 2 newly developed features appear with high correlation with the target variable, which justifies their existence in the model.

## Data Modeling

•	The obtained data set was divided into a train and test data set in a ratio of 70/30.

•	 For the data modeling, different algorithms with default parameters were used: Dummy regressor, Linear regressor, Lasso regressor, KNN regressor, Random forest regressor and XGB. 

•	Best results were reached with the XGB regressor, so this algorithm was selected for further development with HyperParameter Tuning.

•	Also, the kFold strategy and train dataset on 5 folds were used, in order to be sure that each segment of the data is trained equally, because the predicted target column will be used in the final analysis

•	The tuned XGB algorithm gives the best results, with accuracy of 0,73.

## Results Evaluation

•	The column 'Purchase_pred' was merged to the original data in order actual vs predicted values to be analyzed.

• As expected, according to the model precision that was reached (0,73%), the distribution of actual vs predicted Purchase are partially overlapped. But the good thing is that the predicted distribution matches picks of the actual distribution.

• Similarly, same match of the picks is visible on the plots with the separated Product_Category_1 prediction, except for the subcategories with less data.




