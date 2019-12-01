# Project-Fraudulent-Activities

## OBJECTIVE OF THE PROJECT

This project aims at detecting which features can best describe a user that is about to commit fraud on the website. 
We have access to a dataset that contains several features that I’m going to explore in this project. 

## FEATURES EXPLORATION

There are no missing values in the dataset. 

### 1.	Add countries

The first step of the project is to associate the ip_address to a country thanks to another dataset that we have. 

### 2.	Country vs. Fraud 

The first step is to notice that the dataset contains now a lot of “unknown” countries. 
The next thing is that 40% of the frauds are committed in the US and 15% of it in an “Unknown” country. 

### 3.	Browser vs. Fraud

42% of the frauds are committed using a Chrome Browser but maybe its not significant since it is just a very popular browser.

### 4.	Device vs. Fraud

This relationship is one of the most interesting. Indeed, some device are used several times with different user ids. 
For example, the device EQYVNEGOFLAWK is used 20 times to commit Fraud with the same purchase value. And the time between signing up and purchasing is less than a second which indicates that probably it was robot and not human who commited fraud. 

### 5.	Sex vs. Fraud

The gender doesn’t seem to be really significant to predict a fraud. 

## FEATURE ENGINEERING 

Based on the first analysis, I’ve decided to create new features: 
-	*time_interval* : calculates the time in seconds between signing up and purchasing
-	*hour_cat* : creates categories for when the purchase was made during the day
-	*purchase_day* : indicates if the purchase was made during the week or in the weekend. 
-	*Age_ cat* : creates age categories
-	*device_nbr* : counts the number of times the same device was used
-	*device_count* : categories the device_nbr

## THE MODEL 

I’ve worked on two models: 
*	RandomForestClassifier
*	GradientBoostingClassifier

Both models work with Decisions Tree. 
Both were trained using GridSearch and Cross Validation to optimize hyperparameters. 

## THE RESULTS 
Both models seem to predict with the same precision and recall. The F1_score is 0.7089. 

## FURTHER EXPLORATION 
Since the dataset is very unbalanced: 9% of fraud vs. 91% of non-fraud. 
Maybe we should work on a smaller sample to balance the results: we can take the 15,000 fraud users and 15,000 random non fraud users. 
Or maybe we should add the country variable and not taking care of some countries that do not appear much.
