# Introduction
## The Data is from Kaggle. The project aims to help people understand the best time to book a hotel and the optimal length of stay in order to get best daily rate.Expect statements above, it is a open source that provides many information to explore.
* Original source link: https://www.sciencedirect.com/science/article/pii/S2352340918315191
* Kaggle source link: https://www.kaggle.com/jessemostipak/hotel-booking-demand
### Data is super clean as I focus on EDA, feature engineering and machine learning part

* This is how dataset looks like
![This is how dataset looks like](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/Loaddata2.jpg)
* Check out the detailed information for each columns
![column details](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/check%20columns.jpg)
# EDA
* Explore the cancellation ratio in the dataset
![cancellation ratio](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/cancellation%20ratio.jpg)
#### This barchart shows the number sof count of cancelled and not cancelled. Apparently, cancelled is about 60% of not cancelled. Because this columns is target label, we do not need to resample it in further machine learning building process.

* Describe the cancellation distribution from month to month
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/EDA-month.jpg)
#### In three years from 2015 to 2017, August has most number of cancellation followed by July and May. In January, there is least number of cancellation.

* create linechart to identify the relationship between length of lead time and cancellation rate.
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/leadtime1.jpg)
![](https://github.com/JesseyZ/Machine-Learning---Hotel-Booking-Cancellation/blob/main/imgdocs/leadtime2.jpg)
#### Binning the lead time into couple segments to reduce categories and easily to see the trend of cancellation ratio(# of cancellation / total # of reservation). And no doubt that with longer lead time, more possible consumers will cancel their reservations. The period from lead time 31-50 days and 301 to 500 days have two flat rate as cancel rates keep stable and even drops a bit.
