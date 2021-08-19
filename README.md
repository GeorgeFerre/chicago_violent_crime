## Business Problem
Chicago needs to face an epidemic of violence within the city. One way to face the problem is to use machine learning to determine how many victims of violent crime to expect on a given day. Using data from the city of Chicago, I will train regression models to predict upcoming crimes.

The underlying principal of this project is fairly intuitive: violent acts will lead to more violent acts. However, this project will examine the victims of violent crime in Chicago and see if differing victims (different ages, sexes, races, etc) effect predictions for future violent crime.

The model itself be created for the Chicago government to help predict the amount of first responders needed on a given day. For example, if a spike in crime occurs on a given day, the Chicago PD can proactively schedule more police officers and 911 operators.

## Guide
For a quick rundown of my project, view my [slideshow](https://github.com/GeorgeFerre/chicago_violent_crime/blob/main/chi_vi_slides.pdf).
My main technical notebook is [here](https://github.com/GeorgeFerre/chicago_violent_crime/blob/main/Regression_Models_v2.ipynb)
For my dahsboard (WIP!) see [here](https://github.com/GeorgeFerre/flask_dsc_072721)

## Data Sources and Methodology
Data was pulled from the [Chicago Data Portal](https://data.cityofchicago.org/Public-Safety/Violence-Reduction-Victims-of-Homicides-and-Non-Fa/gumc-mgzr) and includes 20k data points of victims of violent crimes between 2016 and 2021. Each row of data includes information about date, location, age, sex, race, police beat, and nearby access to street outreach organizations.

Using the victim data, I grouped the data by date, and got counts of victims in each demographic, and kept day of week and month as categorical variables per row.

## Early Data Analysis
After reviewing data, it appears that there are some trends. Younger (from teens to 30's) black men are the demographic that appear to be most victimized, and there tends to be more crime on weekends and in higher months. Crime also tends to be heavily concentrated on the west side (espcially in Austin), with pockets on the south side as well.

![dow graph](/images/cap_dow.png)

![Cap_Heatmap](/images/Cap_Heatmap.png)

## Results
Currently the best features for predicting the amount of victims are the day of the week and the month. The counts of victims by different demographics did not seem to impact the models used, although the overall count of recent victims (from the 7 days prior to the predicted day) did seem to slightly help the model.

I initially looked at Linear Regression, Decision Tree Regression, Stochastic Gradient Descent Regression, and Supoort Vector Regression models. After finding best features, the cross validation r-squared scores were as follows. 

* Linear: .34
* Decision Tree: -.39
* SGD: .34
* SVR: .33

From there, I used hyper parameter tuning on SGD and SVR models and checked Mean Squared Error. The MSEs are as follows:

* SGD: 22.68
* SVR: 22.88

![preds](/images/preds_results_v2.png)

## Conclusions and Next Steps
Unfortunately, it appears that our model is not currently successful at predicting the amount of victims to be expected on a given day in Chicago. We have a MSE of 19 for both SGD and SVR models, and most data points are below 25 victims.

It appears based on our analysis that the only solid predictors we have are day of week and month. While there does appear to be some truth that recent violence will lead to more acts of violence (adding in that data proved to make the model more reliable), it is not enough to make good predictions for our purposes.
