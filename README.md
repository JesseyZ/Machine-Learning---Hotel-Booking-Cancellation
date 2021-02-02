# Introduction
## The Data is from Kaggle. The project aims to help people understand the best time to book a hotel and the optimal length of stay in order to get best daily rate.Expect statements above, it is a open source that provides many information to explore.
* Original source link: https://www.sciencedirect.com/science/article/pii/S2352340918315191
* Kaggle source link: https://www.kaggle.com/jessemostipak/hotel-booking-demand
### Data is super clean as I focus on EDA, feature engineering and machine learning part

#### This is how dataset looks like
![This is how dataset looks like](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/Loaddata2.jpg)
* Check out the detailed information for each columns
![column details](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/check%20columns.jpg)
# EDA (list some factors that could mainly affect cancellation ratios)
#### Explore the cancellation ratio in the dataset
![cancellation ratio](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/cancellation%20ratio.jpg)
- This barchart shows the number sof count of cancelled and not cancelled. Apparently, cancelled is about 60% of not cancelled. Because this columns is target label, we do not need to resample it in further machine learning building process.

#### Describe the cancellation distribution from month to month
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/EDA-month.jpg)
- In three years from 2015 to 2017, August has most number of cancellation followed by July and May. In January, there is least number of cancellation.

#### Create linechart to identify the relationship between length of lead time and cancellation rate.
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/leadtime1.jpg)
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/leadtime2.jpg)
- Binning the lead time into couple segments to reduce categories and easily to see the trend of cancellation ratio(# of cancellation / total # of reservation). And no doubt that with longer lead time, more possible consumers will cancel their reservations. The period from lead time 31-50 days and 301 to 500 days have two flat rate as cancel rates keep stable and even drops a bit.

#### Cancellation can be related to whether adults have babies and  children or not.
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/eda-baby.jpg)
- Create a new feature showing if adults travel with babies or children or both. As we can see the ratio of cancelled or not seems not have a really strong realtionship with this new feature.

# Missing value handling
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/missing%20values.jpg)
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/missing%20values2.jpg)
- As we can see, there are many missing values but all distributed in three columns.
- Delete agent and company directly because these are IDs for both columns.
- For country, delete it for now because we cannot judge customers whether they will cancel the reservation by where they are from.
- Children column has 4 missing values, it takes a very small percentage of all values, will fill it with zero.

# Check correlation of numerical variables with ''Is_canceled'' column
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/correlation.jpg)
- As shown, 'arrival_date_week_number', 'children', 'stays_in_weekend_nights' and 'arrival_date_day_of_month' are less correlated with cancellation. Considered some of thses columns can be converted and be used for creating new features. I will feature engineer some of them later on.

# Feature Engineering
### Convert categorical variables to numerical variables by One-hot encoding. (Not considering using label encoder because there is not variables have no ordinal relationship). Creating new features based on existing features.
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/feature%20engineering.jpg)

# Machine Learning
### Baseline model - XGBoost(XGBoost is good algorithm to apply as a baseline model as it cannot be affected by missing values and it has built-in L1 and L2 regularization which can prevent overfitting. Additionally, it uses multiple CPU to accelarate the whole process.)
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/baseline-xgboost.jpg)
* XGBoost performs well without validation, and compared to two reports, which indicates the model dose not overfit.

### Below is one of algorithm(Logistic regression) with validation, based on the EDA part, this is not a imbalanced dataset, so we do not need sampling.
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/lr1.jpg)
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/lr2.jpg)
- Logistc Regression performs nicely with low bias and it is not overfitting. Other algorithms are in the notebook. Tree-based models are overfitting.

# Interpretation - Permutation Importance
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/permutation1.jpg)
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/permutation2.jpg)

# Conclusion
 - Even Logistic Refression model does not have the highest score in both training and testing sets but it is the most balanced model that has low bias and variance. the other two have overfitting issues. Because of time limits, three models can be improved by doing more jobs on EDA and feature engineering to reduce variance in two tree based models. 
 - From permutation importance chart, we can notice that arrival date week numbers affects most to the LR model followed by number of special request, which means arrival date of week are most predictive feature affecting the model. Second comes number of special requests which are shown on coef_ chart as well indicating it put most negative impact on baseline model(LR).
