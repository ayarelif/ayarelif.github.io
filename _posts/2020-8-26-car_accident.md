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

The US population is approximately 330 million based on census gov’s publish. I could conclude that approximately 
0.016 % of car accidents happen every year. While only 0.007% of people who made a car accident are losing their 
lives every year, 0.45 % of people are injured or disabled. In other words, on average 1 or 2 people in the US 
make a car accident each year, and there is a 0.016 probability that she/he might die. Otherwise, the probability 
of getting injured or disabled is 0.45% for each person.



## **The Questions to Think About!**

What are the factors that directly are related to car accidents and their severity? How is the distribution of car
accidents among states and cities? How accurately could we predict the severity of car accidents depending on factors?

## **Dataset**

This research will be about the severity of car accidents on traffic and what factors are critical to cause accidents
in the US. The dataset is coming from the source, the [Kaggle](https://www.kaggle.com/sobhanmoosavi/us-accidents), and it contains 3.5 million observations and 49 features.
The dataset covers 49 states in the US, and the accident dataset is gained from February 2016 to June 2020 using two APIs.

## **Purpose**

I will try to predict the outcome of the cases which has a high serious car accident report or which has a low serious
car accident record with an 80% accuracy score.

## **Method**

I split the dataset into a Train/Val/Test set. Most of the columns have categorical variables and consist of a few classes. As this is a classification problem, any of the classification algorithms could be used. Thus, I used four types of models to get the best prediction; Logistic Regression with 71% accuracy score on validating the dataset, Decision Tree with 74% accuracy score on validate set, RandomForest with hyperparameters with 76% accuracy on the test set, and GXboost with 76% accuracy on a validating set. Based on my finding, I will apply the RandomForest Classifier model to predict best with a 76.38% accuracy score on the test set.

## **Baseline**

Before building the model, I checked the baseline prediction with the majority class and decided to use an 
accuracy score as an evaluation metric. Thus, the baseline score is 0.683742.

## **Features**

The original dataset covers 49 columns with 3.5 million observations, but I did not use the whole columns to predict the outcomes.
I used two methods to decide the best features, panda profiling report, and permutation importance.
I also applied a feature engineering to create a column to create a time series which tells us how long a car accident has an impact on the traffic.
As a result, I used only 38 features with a 3.5 million observation dataset.


## **Exploratory Data Analysis**

Before I dive into the prediction model, I like to discover the dataset with some important features and a target.

Let's look at the general cases over the US which states and regions are most likely to have car accidents since 2016

<iframe width="900" height="800" frameborder="0" scrolling="no" src="//plotly.com/~elif_a/104.embed"></iframe>

Based on the little purple clusters in the graph, Washington, NewYork, California, and Georgia have more cases. 
Most popular and big cities are all around these states, so the result is not surprising. 
As the populations with the big cities are high, the majority of car accidents appear around these cities and states.

Let's close look at the severity of the accident depending on the states which have a high number of car accident cases.

<iframe width="900" height="800" frameborder="0" scrolling="no" src="//plotly.com/~elif_a/111.embed"></iframe>

California is almost double on both parts. As we look at the graph closely, North California and South California has almost the same number of confirmed car accident cases.
The other two states Texas, and Florida are following behind California. 
Another interesting result is the low severity of car accidents in the states are following in the same order of the states at the high severity car accidents cases.
For example, California has the biggest number of low severity confirmed cases while it has still the greatest number of confirmed high severity cases.

## **Machine Learning**

After exploring the dataset a little bit, let's dive into the prediction model which I used. I used four different 
classifier models to get the best accuracy score on the validation set, 
and Random Forest with a hyperparameter optimization model provides with 76.3% the best accuracy score on the test set.


Permutation Importance Explained

![](https://cdn-images-1.medium.com/max/800/1*a6NZivC2BZN_j44ThCrV3w.png)

The dark green highlighted factors are the most significant features of the model. 
The number feature explains the street number in the address field while the traffic signal feature shows the presence of traffic_signal in a nearby location. 
I could consider that street number is a good indicator of a location where the car populations are a lot or not and where city traffic is crazy or not. 
Even though feature importance helps us to see important factors in determining the severity of car accidents,
we do not still have enough information to see how important the relationship between features and target. 
Because of the classifier model I used, we can not directly see coefficient numbers on the model. 
Instead, a partial dependence plot could be a good choice to look at closely features and their movement depending on the target.

## **Partial Dependence Plot**

![](https://cdn-images-1.medium.com/max/800/1*uKwMX3frE50wQyILkRrIUQ.png)

The majority of car accidents are low severe if there is a traffic signal.

![](https://cdn-images-1.medium.com/max/800/1*ec-faQW70Tfi-in4oSLikw.png)

The low severity of the car accident is increasing as the number of streets is increasing. 
After some point, it is not increasing anymore and stay stable. An increase in the number of streets is the indicator that they are main or downtown streets. 
Thus, most of the cases are low severe accidents around the street. However, while the street numbers are increasing, 
the high severity of the car accident range is slightly increasing and the street is making more impact on the accident as well.

![](https://cdn-images-1.medium.com/max/800/1*SXrS6FDBB-2o9kyVkMY-aw.png)

A heat map is another perspective to look at the two features at the same time. As time differences are increasing, the severity of accidents is getting high as well. 
That makes sense because the high severity of car accidents might take much more time to be reported and cleaned from the traffic.

## **Conclusion**

I do not hesitate to use classification models on my dataset because most of the columns have classes. However, regression models with different matrix evaluations could be applied for this dataset. Feel free to run my data and make your own predictive models. If you click the [my github](https://github.com/ayarelif/Car-Accident-in-USA) account, you can draw the raw files from my file. 


