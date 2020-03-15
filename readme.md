# Description
## Objective
-To predict the total number of active users (guest-users + registered-users) to help with demand forcasting. 

## Usage
install the required dependencies by running run.sh
> bash run.sh

## Design
1. Approach the problem through understanding the objective
-With objective, the context and irrelevant data could be removed and aggregated
2. Data Importation: Data grab from given url.
3. Data Cleaning
-Target: total_users where guest_users + registered_users
-Features: All given parameters. 
-Begin by checking for null data and listing down the unique values for those variables that are ought to be categorial in nature
-For example: There were -ve values in guest_users/registered_users which should be the case in reality. Those -ve values are set 0.
-Features: Given context, dates are converted to more usable categorial variables of weekday, numbering Mon-Sun (0-6)
-Features: Categorial variables for hours would be too many and redundant. To streamline a make-sense binning of the data to 4 hours which covers morning/lunch/dinner times are used.
-Dataframe is then arranged according to date and time as well for better viewing.

## Data Exploration & Modelling
For Data Exploration, basic distribution of the target-guests were created. It is found to be not really normally distributed but a quick way to visualize the distribution. 

Heatmap based on correlation matrix was created to pick out and identify any variables that are high correlated to each other (e.g. temperature and feels-like-temperature). Remove such variables to simplify the model and minimize collinearity. Also to pick out key factors that have stronger correlation to our total_guests for use in the model.

Due to basic knowledge on regression models the following approach was made:
1. Model using Linear Regression
2. Model using Polynomial Regression
3. Model using Random Forest

Using metric of R2 values to identify the best model to fit. It was then found ot by Polynomial model. Within polynomial model a graph was generated to identify the lowest possible polynomial to speed up processing speeds.

## Evaluation
-In terms of modelling R2 scores: 2.>3.>1.
-All R2 scores are really low, ~0.4-0.5 indicating that the models might not explain most of the relationship between chosen features and the target variable.
-Considering that I have modelled the data to my best capabilities and with reasonable features that are context logical, I believe there might be other features which the dataset have not captured that may allow the model to achieve higher R2 values. For example, price of the scooter rental etc. which might be key factors impacting the number of users.
-It would be interesting to create a pricing problem.
