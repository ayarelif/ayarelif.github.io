---
layout: post
cover-img: 
title: Vehicle Accidents in the US & Machine Learning
tags: [Vehichle Accident, Machine Learning]
---


## **Introduction:**

[1–800-The-law-2](https://www.1800thelaw2.com/blog/how-many-car-accidents-us) mentions that;
> "According to the National Highway Traffic Administration, car accidents happen every 60 seconds.
That equates to about 5.25 million accidents across the nation on a yearly basis. Statistics by the Association 
for Safe International Road Travel show that 37,000 people die annually due to vehicular accidents with an additional 
2.35 million either injured or disabled."

Currently, the U.S. population is 331 million, based on Census gov’s data. Then, one could infer that approximately 16 car accidents per thousand people every year. There are 7 deaths per one thousand car accidents while 45% of people who are involved in a car accident are injured or disabled.



## **Questions to Think About!**

What are the factors that are correlated with car accidents and their severity? Can we identify the factors, associated with the severity of car accidents? How does the distribution of car accidents change across the U.S.? I am curiosity about these questions, and I will try to find answers in my post.

## **Dataset**
The dataset is from [the Kaggle](https://www.kaggle.com/sobhanmoosavi/us-accidents), and it contains 3.5 million observations/car accidents and 49 features. It covers 49 States in the U.S., and the time period of the dataset is from February 2016 to June 2020.

## **Purpose**

This research will be about the severity of car accidents and what factors are critical in explaining the accidents and their severity in the U.S. I will try to predict the outcome of the cases which has a high serious car accident report or which has a low serious car accident record with a 77% accuracy score.

## **Method**

I split the dataset into Train/Val/Test datasets. Most of the columns have categorical variables and consist of a few classes. As this is at its core a classification problem, any of the classification algorithms could be used. Thus, I have used four types of models to get the best prediction; Logistic Regression with 71% accuracy score on validating the dataset, Decision Tree with 74% accuracy score on validate set, RandomForest with 77.22% accuracy on the test set, and GXboost with 76% accuracy on a validating set. Based on these findings, I have decided to apply the RandomForest Classifier model to predict with a 77.16% accuracy score on the test set.

## **Baseline**

Before building the model, I checked the baseline prediction with the majority class and decided to use the accuracy score as an evaluation metric and the baseline score was 0.683742.

## **Features**

The original dataset covers 49 columns with 3.5 million observations, but I did not use the all columns to predict the outcomes. I have used two methods to decide the best features: panda profiling report, and permutation importance technique. I also applied a feature engineering to create a new time series column which tells us how long a car accident has an impact on the traffic. As a result, I ended up using 38 features with 3.5 million observations.


## **Exploratory Data Analysis**

Before I dive into the model, I like to discover and describe the dataset with some important features and a target.

Let’s look at the general distribution of car accidents across the US. The following map shows States and regions that are most likely to have car accidents since 2016.

<iframe width="900" height="800" frameborder="0" scrolling="no" src="//plotly.com/~elif_a/104.embed"></iframe>

Based on the little purple clusters in the graph, Washington, NewYork, California, and Georgia have more cases. These are big cities with large populations;hence, the map is not surprising, but still informative.
Let’s closely look at the severity of the accidents in the States which have the highest number of car accident cases.

Let's close look at the severity of the accident depending on the states which have a high number of car accident cases.

<iframe width="900" height="800" frameborder="0" scrolling="no" src="//plotly.com/~elif_a/111.embed"></iframe>

California has almost twice number of accidents on both parts: low and high severity accidents. As we look at the graph closely, North California and South California have almost the same number of confirmed car accident cases. The other two states, Texas and Florida, are following California. Another interesting result is that the order of low severity car accidents is exactly the same as the order of high severity car accidents among these five States. For example, California has the biggest number of low severity confirmed cases while it also has the greatest number of confirmed high severity cases.

## **Machine Learning**

After exploring the dataset a little bit, let’s dive into the prediction model. I used four different classifier models to get the best accuracy score on the validation set, and Random Forest with a hyperparameter optimization model provides with 77.1% and that is the best accuracy score on the test set.


Permutation Importance Explained

![](https://cdn-images-1.medium.com/max/800/1*a6NZivC2BZN_j44ThCrV3w.png)

The dark green highlighted factors are the most significant features of the model. The “Number” feature explains the number of streets in the address field while the “Traffic_ Signal” feature shows the presence of traffic signal in a nearby location. I would argue that street number is a good indicator of a location with high density of cars and traffic. Even though feature importance helps us to see the important factors for the severity of car accidents, we do not still have enough information to see how important the relationship between features and the target. Because of the classifier model I used, we can not directly see the coefficient numbers on the model. Instead, a partial dependence plot could be a good way to look at features and their movement depending on the target.

## **Partial Dependence Plot**

![](https://cdn-images-1.medium.com/max/800/1*uKwMX3frE50wQyILkRrIUQ.png)

The majority of car accidents have low severity. The number of the confirmed car accidents is high at traffic_signal_0.

![](https://cdn-images-1.medium.com/max/800/1*ec-faQW70Tfi-in4oSLikw.png)

The low severity of the car accident is increasing as the number of streets is increasing. After some point, the severity is not increasing anymore and it stabilizes. An increase in the number of streets is the indicator that these are main or downtown streets. Thus, most of the cases are low severity accidents around the street. However, while the number of streets is increasing, the high severity of the car accident range is slightly increasing and the number of streets is making more impact on the accident as well.

![](https://cdn-images-1.medium.com/max/800/1*SXrS6FDBB-2o9kyVkMY-aw.png)

A heat map provides another perspective to look at the two features at the same time. As time difference is increasing, the severity of accidents is going up as well. That makes sense because the high severity car accidents could take more time to be reported and cleaned from the traffic.

## **Conclusion**

I have not hesitated to use the classification models on my dataset, because most of the columns have classes. However, regression models with various matrix evaluations could be also used for this dataset. Feel free to use my data and make your own predictive models. If you click [my github](https://github.com/ayarelif/Car-Accident-in-USA), you can draw the raw files from my account. See you in my next post!



