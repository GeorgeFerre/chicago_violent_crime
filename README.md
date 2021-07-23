# chicago_violent_crime
Build dashboard for first responders about victims of violent crime in Chicago

## Business Problem
Chicago needs to face an epidemic of violence within the city. One way to face the problem is to use machine learning to determine how many victims of violent crime to expect on a given day. Using data from the city of Chicago, I will train regression models to predict upcoming crimes so that emergency responders can prepare to prevent and mitigate the effects of violent crime.

## Data Sources and Methodology
Data was pulled from the [Chicago Data Portal](https://data.cityofchicago.org/Public-Safety/Violence-Reduction-Victims-of-Homicides-and-Non-Fa/gumc-mgzr) and includes 20k data points of victims of violent crimes between 2016 and 2021. Each row of data includes information about date, location, age, sex, race, police beat, and nearby access to street outreach organizations.

Using the victim data, I grouped the data by date, and got counts of victims in each demographic, and kept day of week and month as categorical variables per row.

## Results
Currently the total amount of recent victims and day of week appear to be the best indicators of how much crime will happen on a given day. Race, age, sex, and location of the victims currently do not appear to cause significant variation in the total future victims.

I am using Linear Regression, Decision Tree Regression, and Stochastic Gradient Descent models to make predictions. Currently my highest scores are as follows:

1. Linear: .70
2. Decision Tree: .54
3. SGD: In Progress

## Conclusions
As I keep tuning my Decision Tree and SGD models, I will see if demographic information is helpful in determing future number of victims. The project may be updated to time series if I find that temporal data is the overwhelming predictor in future violent crimes.
