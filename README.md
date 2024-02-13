# In this first simple example i wanna show how GridSearchCV works 
* I gonna work on iris dataset, which contain flower target names and unique features for each example
* I make simple data preparation in python and split the data

# Next i fill all models parameters for hyperparameter tuning
* Next i supply my model GridSearchCV and specify parameters
* Feed the iris data inside and fill scores list for all models best score and best parameters
* And i put everything into DataFrame to get scores in that format

![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/Parameters.png)
#
#
#
# ! []()
# Now i gonna work of telescope hadron(background) and gamma(signal)
* First i load my data and map class column into numbers
* Then i check distribution columns using plt graphs

# Next i split my data into train, valid and test using numpy
* And next i check value counts in class columns and see that there is class imbalance

# So next i create function which will sample to class balance and scale my dataframe
* To do this i use RandomOverSampler and StandardScaler
* To reshape and stack my data i use numpy
* I solo oversample X_train set, and valid, test no, to not leak any data to my model

# Then i prepare and save parameters for my models
* Hyperparameter tuning is faze when you pass all parameters which not collide with each other
* And then i supply to GridSearchCV models and its parameters
* Train them and append scores in scores list 
![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/Parameters_adv.png)

# 
![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/Grid_Search_png.png)
