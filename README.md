# Black-Friday-Sales-Prediction

![resize](https://user-images.githubusercontent.com/79594181/161444729-63ba574f-c16f-437b-b45b-f83e7fe7a456.jpg)

<h3>Project description</h3>

A retail company wants to understand the customer purchase behavior (specifically, purchase amount) against various products of different categories.
They have shared a purchase summary of various customers for selected high volume products from last month. 

The data set also contains customer demographics (age, gender, marital status, city type, stay in_current_city), product details (product_id and product category) and Total purchase_amount from last month. 

<i>Now, they want to build a model to predict the purchase amount of customer against various products which will help them to create personalized offer for customers against different products </i>.
  
Your goal in this project is to create a robust regression model, that will use this data to predict the customers' total purchase amount for different products. 
  
  The project will be presented through the following stages:
  
- [Understanding the Business](#understanding-the-business)
- [Understanding the Data](#understanding-the-data)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Preparation](#data-preparation)
- [Feature Engineering](#feature-engineering)
- [Data Modeling](#data-modeling)
- [Results Evaluation](#results-evaluation)
- [Limitation of the model](#limitation-of-the-model)
  
  
 
</small></p>

## Understanding the Business

The first Friday after Thanksgiving has been considered as the beginning of the Christmas shopping season in the USA since 1952. 
There are few theories how this day received its name. According to one of them, in the 1950s, many manages of companies started to call the first Friday after Thanksgiving as Black Friday due to reported sick leave from many of their workers on this day.
Years later, Black Friday was used by Philadelphia cops to describe the day after Thanksgiving because they had to work extended hours in terrible traffic. 

According to the most frequently present theory, on this day, occur 30- 40% of the total annual retail sales, and this is the period of the year when financial books move " from red into the black".  The previous comes from the old bookkeeping practice of recording profits in black ink and losses in red ink. 

However, in the last years the classic Black Friday has been replaced by the Cyber Black Friday, which is marketing word for its online version. The term was first used in 2009 in a press release entitled "Black Friday Goes Online for Cyber Black Friday".

Retailers develop their Black Friday sales plans and strategies entire year. They use different strategies, but mostly they offer low prices for overstock inventory and different discounts on seasonal products.
Additionally, high discounts for expensive brands of TVs, smart devices, and other electronics are offered. Also, special attention is paid on the Black Friday advertisements content, directed towards driving highest sales.
As a result of the previous, can be concluded how important is for retailers to have excellent knowledge of their costumer’s behavior, and accordingly, to implement the best marketing strategies for each customer segment.


## Understanding the Data
The data set consist of:
  - 550.068 records (rows)
  -   5.891 unique customers
  -   3.631 unique products. 
  -   7 numeric and 5 categorical features 
  
**Missing values** were identified in two columns, **Product_category_2** (173.638 or 31%) and **Product_category_3** (383.247 or 69%). The missing values will be filled in the Data Preprocessing part. 

## Exploratory Data Analysis
### Univariate Analysis
For this analysis, the seaborn library was used for creation of count plots for each categorical variable. These charts are expected to give picture of the number of transaction per category in every analyzed variable.

![Univariate Analisys 1](https://user-images.githubusercontent.com/79594181/161399502-97c7d487-50e5-4d2c-8bb8-a7201c08e07f.png)

Insights:
1. In figure 1, The most transactions are performed by the customers in the range of 26–35 age 
2. In figure 2, Male customers executed more transactions than females.
3. In figure 3, Customers with occupations 0 and 4 performed the most transactions.
4. In figure 4, Custumers who stayed in the current city for 1 year, performed the highest number of transactions.
5. In figure 5, Customers from city category B, did the highest number of transactions.
6. In figure 6, Customers who are single, performed more transactions than married customers.

However, at this point, final conclusions in this respect cannot be made, but further analysis will be performed.

### Bivariate Analysis
Bivariate Analysis relates to analysis of two variables, for the purpose of determining the empirical relationship between them. In our case, the relationship between each categorical variable and the target variable (Purchase) will be analyzed. 

![Bivariate Analisys](https://user-images.githubusercontent.com/79594181/161443739-138079d8-da9f-4b63-bc95-d163e5754b61.png)

Insights:
1. In figure 1, The most money was spent by customers aged 26 to 35 years.
2. In figure 2, Male customers spent more money than females.
3. In figure 3, Customers with occupations 0 and 4 spent the most.
4. In figure 4, costumer who stayed in the current city for 1 year spent the most.
5. In figure 5, Customers from city category B spent the most.
6. In figure 6, Customers who are single, spent more money than married customers.

If the insights from both analysis (univariate and bivariate) are compared, can be concluded that the same results were received. The reason behind this is the disbalance of the categories in each of the analyzed features. 

Consequently, the bivariate analysis will be supplemented with analysis of the relationship between the average of each categorical feature and the target variable.

![Bivariate mean analysis](https://user-images.githubusercontent.com/79594181/161397994-70e9410a-97f6-4387-b210-2ebb93f84c2c.png)


As it was assumed, this analysis shows that there is no significant correlation between each category within a feature and the Purchase. With other words, the presented correlation in the previous visualization was driven by the misbalanced set of data. 

### Multivariate Analysis

![Multivariate analysis_2](https://user-images.githubusercontent.com/79594181/161398008-9cab2357-6494-4abd-9de3-259ca5245991.png)

•	From this analysis it is evident lower purchase amount for age group 0-17 females in the City_Category A, age group 46-50 male in City_Category A and age group +55 males in City Category A, so the company can make some special promotions for this categories in order to increase the sales if this is in line with their sales stragegy.

### Target variable distribution and outliers

In this section the scipy library was used for plotting the distribution of the target variable.

![Target variable distribution](https://user-images.githubusercontent.com/79594181/161398029-0e7a30a6-6a6b-42b3-a2a6-d8dddfd4b6c4.png)

![Target variable  and outliers](https://user-images.githubusercontent.com/79594181/161398038-864aaece-6ac0-4cf8-934b-d06c0291849e.png)


•	From the distribution plot, which represent the distribution of the target varibale (Pruchase), can be concluded that the target variable follows the Gaussian (Norma) distribution.

•	From the boxplot, can be seen that there are few values lying outside (outliers). But if the z-score is considered, can be concluded that there are no values above the usual threshold level (generally taken as 3).

• From the distribution plot that represents the distribution of each Product_Category_1, can be concluded that the target variable follows Gaussian(normal) distribution within each Product_Category_1


## Data Preparation

### Fill in missing values

As it was previously presented, there are 2 variables with missing values. In this regards, different strategies were tested:

o	Fill in with mean value.

o	Fill in with 0.

o	Custom fill in.

However, best results were received with the custom function for filling in the missing values, which includes: 

•	**For Product_category_3:** for all the combinations of values of Product_category_1 and Product_category_2, the most frequent Product_category_3 was found and it was used for filling in the missing values in Product_category_3, for the appropriate combination of the first two categories. For all the missing values in Product_category_3, for which also the Product_category_2 is empty, zero was used for filling in.

  _For example,_ when Product_Category_1 is 3 and Product_Category_2 is 4, the Product_Category_3 occurs as 5, 12, 9 and 8, but the most frequent is 5. This means that every time when Product_Category_1 is 3, Product_Category_2 is 4, and the value of Product_Category_3 is missing, it will be filled in with 5. 

•	**For Product_category_2:** missing values were filled in with 0.

## Feature Engineering

- From the previous analysis, it was concluded that there is a very weak correlation between each feature and the target variable, except for the Product_Category_1 feature.

    As a result, it was decided, new features to be created, in order to increase the correlation, thus to increase the probability score of the prediction model     which will be developed. 

    The following **2 new features were created**:

     **Category_Count**-  it counts the number of categories (Product_Category_1, Product_Category_2 and Product_Category_3) to which each product belongs.

     **Product_popularity_score**- it counts the number of transaction per product, and then scales the values with MinMaxScaler. 

- In regards to ****label encoding of the categorical features****, different strategies were used, but no improvements of the model were reached. Thus, it was decided the label encoding to be used, because that way, the model training was the fastest.

- After the performed feature engineering, the correlation between each feature and the target variable is presented on a **Correlation matrix**, with using the seaborn heatmap.

![Corr_matrix](https://user-images.githubusercontent.com/79594181/161398092-8239e628-331c-48be-a1d5-03ffdcbe322f.png)

From the visualization, it can easily be concluded, what in fact through the previous analysis was proved, that there is a very low correlation between all the features and the target variable, except for Product_category_1, Product_category_2, Product_category_3 and the new features, Category_count and Product_popularity_score. 

The 2 newly developed features appear with high correlation with the target variable, which justifies their existence in the model.

## Data Modeling

•	The obtained data set was divided into train and test data set, in a ratio of 70/30.

•	 For the data modeling, different algorithms with default parameters were used: Dummy regressor, Linear regressor, Lasso regressor, KNN regressor, Random forest regressor and XGB. 

•	Best results were reached with the XGB regressor, so this algorithm was selected for further development with HyperParameter Tuning.

•	Also, the kFold strategy and train dataset on 5 folds were used, in order to be sure that each segment of the data is trained equally, because the predicted target column will be used in the final analysis

•	The tuned XGB algorithm gives the best results, with R2 score of 0,73, MAE 2.000 and RMSE 2.664.

## Results Evaluation

•	The column 'Purchase_pred' was merged to the original data in order the actual vs predicted values to be analyzed.

![download](https://user-images.githubusercontent.com/79594181/161519456-79e87011-7957-4f28-9887-7decf6705f76.png)

• As expected, according to the model precision that was reached (R2 score 0,73), the distribution of actual vs predicted Purchase are partially overlapped. But the good thing is that the predicted distribution matches the picks of the actual distribution.

• Similarly, same match of the picks is visible on the plots with the separated Product_Category_1 prediction, except for the subcategories with less data.

• Additionally, an online research was conducted in order to collect different ideas and to compare the results from the previously presented model. The research outcomes showed that none of the online found models treating the same issue, reached better results. 

https://github.com/nanthasnk/Black-Friday-Sales-Prediction/blob/master/Black%20Friday%20Sales%20Prediction.ipynb
**R2 score 0.66**

https://www.kaggle.com/code/ishanvardhan/black-friday-sales-analysis-and-prediction/notebook
**MAE score 2188**

https://github.com/nanthasnk/Black-Friday-Sales-Prediction
**RMSE score 2879.**

https://medium.com/analytics-vidhya/sales-prediction-on-black-friday-using-ml-regression-technique-380af62c181e
**RMSE score  2739**.

https://github.com/EagleDangar/BlackFriday-prediction/blob/master/blackfriday-insights-and-prediction.ipynb
**R2 score 0.68**


## Limitation of the model

For development of the model, only data from the month before Black Friday was provided. However, it is considered that it would be more relevant if the model was trained with historical data from the previous years’ Black Fridays. Оne of the reasons for the previous is the fact that usually, buyers in the period before Black Friday refrain from buying products for which they expect promotions during Black Friday.

Additionally, the analysis showed that the correlation between the demographic features of the clients and the target variable is very low. On the other hand, their product category preferences had high correlation with the target variable. Consequently, the used data set (only from one month) had limited learning possibilities. 



