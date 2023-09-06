**GRID SEARCH SIMPLE EXAMPLE**
# Grid_Search
* I gonna show how to search for best parameters in your model, with different examples

# I gonna use different model with hyperparameters and my training data will be iris data
* So first i import datasets and load iris data from datasets
* Then I put iris data into pandas Dataframe and set columns as features of iris and set flower column as my target column
* Then I apply on target column names of flowers, my data is read, I have names of flowers and their features and all is labeled

# Now I import train_test_split and get train and test set, I use iris.data as X and iris.target as y
* Then I import GridSearchCV which is the model to search for best parameters
* And I gonna import also models for training, (svm, RandomForestClassifier, LogisticRegression)
* Now I gonna save models params, so I put some parameters and GridSearchCV will check every combination and return the best
* First i set model name, then put model itself and finally parameters, I do it for my three models

# When I have all "model_params" prepared, I can implement "GridSearchCV" 
* So I start with create list for scores, than I start for loop for model names and model parameters in my saved params, with access to items
* Then I create object of GridSearchCV puting inside models and parameters, then cv parameter, where i epecify number of folds
* I set "return_train_score to False", so it will not include training scores

# Then I train GridSearchCV with (iris.data and iris.target), And not I choose which parameters will append in my list 
* So I choose first model name, then best score which I get using "best_score_ from my model" and also best parameters using "best_params_ from my model"
* I put my data into pd.DataFrame and pass previous filled scores list and columns for better description

# And I get each model with best score and best parameters, scores are pretty high, but my data was not so complicated
* This is a common technique when you search for best parameters for your model, I put only few parameters buy there are lot of parameters which you can check
* Searching for best model and best parameters is an trail and error tehnic, You need to give different parameters to your model
* And some parameters are not compatible with others, This is powerfull tehnic which can be used in every project to find best performance of your model

**GRID SEARCH ADVANCE**
# I gonna show some examples how to use GridSearchCV, on more complicated dataset and also check performance of some model and Neural Network

* First I load my dataset and pass columns for better description, class (g and h) are gamma and hadron
* Then I map my columns class into numeric variables, one for gamma and zero for hadron
* Next I gonna plot columns to see how my data is distributed, I can see very different distribution only in column "fAlpha"

# In other cases distribution is pretty much the same, with exception on "fLength", "fAsym" and "fM3Long"
* Now I gonna split my data into train, test and valid sets, I use for it numpy split, first shuffling samples
* First split will be on 60% of my data and next of 80% of my data, than I check size of my classes, I see that there is imbalance

# I gonna use over sampling method, so I import "RandomOverSampler", next I create function that will oversample my data and scale them
* So I create function "scale_dataset" and as arguments put (dataframe and oversample set to False), I gonna choose which sets I want to oversample
* I define X and y variables, which will be columns from my dataframe, y as the last and X as rest of them

# Now I create objects of my scaler, and use "fit_transform" of X variable to scale all columns
* Then I create object of class "RandomOverSampler" and use method "fit_resample" on X and y variables, I save it as X and y
* Next I need to stack my both variables and create new data of them 
* To do this I gonna use "numpy hstack", on X variable and y variable, but reshape into 2D object and save this operation as "data"  
* I gonna return from my function new "data", but also X and y

# Then I prepare train, valid and test sets, with use of my function "scale_dataset", for my train sets I set oversample 
* But for valid and test sets I set (oversample to False), because I want to measure performance of my model with this sets

# Now when I have my sets I can import some model to measure their performance on my dataset, it will be(svm, LogisticRegression, KNeighborsClassifier and GaussianNB)
* Then I import "GridSearchCV" which help me find the best parameters for my models
* So first I put name of my model, then models itself, with some parameters that I want to mesure 
* Next I put parameters, there are parameters that have the most significant impact on model performance

# I you want to get better accuracy you need to put more parameters and your model will check all of them
* Now when I pass all params and model I save it all as "model_params" and put my data to "pd.DataFrame"
* Then I gonna prepare "GridSearchCV", so I create list for all scores and make (for loop for model name and model params) in my variable that contain "model_params"

# Next I create object of "GridSearchCV", then pass (model and parameters), and set five folds (cv = 5), and specify that will not include training scores
* Then I train my "GridSearchCV" and specify what will append in scores, so I want here ( model name, best score and best params)
* Finally my "GridSearchCV" will return me all of this in "DataFrame", I pass here prepared variable "scores" and named columns of my data

# In output I get all my model with the best combination of parameters
* With help of "DataFrame" my results are clearly shown, now if I want I can choose the best model which deal with this task
