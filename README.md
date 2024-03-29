# [1. Grid search: Simple example](https://github.com/JakubTabor/Grid_Search/blob/main/Grid_Search_CV_excercise.ipynb)
# In this first simple example i wanna show how GridSearchCV works 
* I gonna work on iris dataset, which contain flower target names and unique features for each example
* I make simple data preparation in python and split the data

# Next i fill all models parameters for hyperparameter tuning
* Next i supply my model GridSearchCV and specify parameters
* Feed the iris data inside and fill scores list for all models best score and best parameters
* And i put everything into DataFrame to get scores in that format

#
#
#
# [2.Grid search: Telescope data Neural net](https://github.com/JakubTabor/Grid_Search/blob/main/GridSearchCV_magic_gamma_telescope.ipynb)
# Now i gonna work of telescope hadron(background) and gamma(signal)
* First i load my data and map class column into numbers
* Then i check distribution columns using plt graphs

# Next i split my data into train, valid and test using numpy
* And next i check value counts in class columns and see that there is class imbalance

![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/magic_gamma_telescope/class_imbalance.png)

# So next i create function which will sample to class balance and scale my dataframe
* To do this i use RandomOverSampler and StandardScaler
* To reshape and stack my data i use numpy
* I solo oversample X_train set, and valid, test no, to not leak any data to my model

![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/magic_gamma_telescope/scale_sampling_function.png)

# Then i prepare and save parameters for my models
* Hyperparameter tuning is faze when you pass all parameters which not collide with each other
* And then i supply to GridSearchCV models and its parameters
* Train them and append scores in scores list
* Next in DataFrame i specify that append only model and its best score and parameters

![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/magic_gamma_telescope/GridSearchCV.png)
![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/magic_gamma_telescope/model_scores.png)

# In this part i gonna create hyperparameter tuning for Neural Net
* I create plot function, which show on graph history of model tuning

![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/magic_gamma_telescope/plot_function.png)

# Then in function i create the model for the gamma, hadron dataset 
* In function i specify all hyperparameters, which are: number of nodes, dropout percentage, learning rate and so on
* I save history of my model training and return both: the model and its history

![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/magic_gamma_telescope/train_model_function.png)

# Now i specify all numbers in the hyperparameters for loop
* And plot history from my function on returned history from my model
* In the last part i specify that the validation will go to the last part and through all numbers
* And finally i call classification report, where i see class imbalance in first and second class
* The average score is pretty high in f1-score

![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/magic_gamma_telescope/hyper_parameters.png)
![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/magic_gamma_telescope/function_graph.png)
![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/magic_gamma_telescope/classification_report.png)

