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

![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/Parameters.png)

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

![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/Parameters_adv.png)

**GRID SEARCH NEURAL NET**
# Now I gonna build a Neural Network to deal with this task
* I gonna search for the best parameters and write plot function to plot on graph all results

# So I define my function, which will plot on graph history of my model, I will plot it with "subplots"
* First I definne "loss" of my model from history, then "validation loss" during the training
* Then named (x axis and y axis) as (Epoch and Binary crossentropy)
* Secound plot will be with (accuracy and validation accuracy) and also I named (x axis and y axis) as (Epoch and Accuracy)

# Now when I have defined plot function I import tensorflow to build my model
* I create function "train_model" and pass inside (X_train, y_train for training)
* I pass also "num_nodes", so (neurons to define them later), I do exactly this same with (dropout_prob, to pass numbers later) 
* And also I pass "learning rate" to specify later values, as well as "batch size" and "epochs"

# Then I specify my model, it will be normal Neural network, so I call tensorflow keras Sequential model
* But instead of passing exact values I gonna pass previous defined variables to specify them later in parameters training
* I pass first "Dense layer" and put inside my variable responsible for neurons, then activation and shape, it will be ten classes in my dataset
* Next I pass "Dropout layer" and put inside "variavle dropout_prob", which correspond for dropping neurons 
* Then I pass another "Dense layer", same as previous and after also "Dropout layer"
* And I pass last Output layer" with one neuron and activation "sigmoid"

# Now I compile my model with optimizer as "adam" "tf.keras.optimizers.Adam" and add variable "lr" to specify later numbers for learning rate
* And loss will be "binary_crossentropy" for my binary output, metrics as "accuracy"
* I save training process of my model as history to plot it later on graph

# I use "X_train and y_train" as training data, than pass "epochs variable", I also pass "batch_size  variable"
* Then I set "validation_split" at (0.2), now its time to set "hyperparameters"
* I set epochs to (50), then I make for loop for "hyperparameters", first I set some numbers for "num_nodes"
* Next I set some numbers for "dropout_prob", then for learning rate and for batch size, there are the most popular options

# I set print option for every parameter, so it gonna show all parameters under the graph
* Then I make model training and call plot function on history variable of my model
* I also make evaluation of my model on (X_valid and y_valid), I save it as "val_loss"
* And in the end i put condition for my hyperparameter loop (if val_loss variable is less than least val_loss) it will become it
* This variable "least_loss_model" is equal to "model"

# And then all stars, so i get graphs with training and evaluation, below all parameters
* I can see that all parameters are changing after every epoch and accuracy is around 86%
* Now I can pick the best parameters, which is close to 88%

![](https://github.com/JakubTabor/Grid_Search/blob/main/Images/Grid_Search_png.png)

# I also make predictions on X_test and reshaped them to accurate range for "classification_report"
* Then I print "classification_report" and see that my (true and predicted class) are just a bit different, but model perform good

# In that case training results of hyperparameters are no so much different, but in the end I get model with the best parameters
* Even if I get just a bit better model, searching for hyperparameters is always good option
