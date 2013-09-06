2013-Sep-HR-ML-sprint
=====================
> Introductory curriculum for the Machine Learning sprint at Hack Reactor. Adapted from a 6-day machine learning sprint created by a group of students from the Hack Reactor June 2013 cohort. We used Kaggle tutorials, the Coursera Machine Learning Course, and a number of other resources to form this curriculum.


### Contents
* Introduction
* Setting up your environment
* Prototyping Models with Excel, R, and Rattle
* Python FTW
* Extra Credit
* Nightmare Mode

### Introduction
How does your spam filter predict what emails to mark as spam? How does Google guess the traffic to the Giant’s game next week? How does Netflix make you movie recommendations? Machine learning is the art and science of using data to make predictions.

In this sprint, you start by examining records of survivors from the Titanic disaster to create an algorithmic model capable of predicting whether a passenger lived or died, and what kind of things about a person would make them more or less likely to have survived. For example, as women and children were given priority seating among the ship’s scarce lifeboats, they were much more likely to survive than other demographics.

You will start by using simple pivot tables and regression in Excel. Then you will use Python to apply regression models and implement a random forest algorithm.

To begin, watch the [videos from week 1](https://class.coursera.org/ml-003/lecture/index) of the Coursera Machine Learning class (approx. 20 - 40 minutes, depending on whether you watch them at 2x speed or not). Then make sure you have a working machine learning environment, as described below.

### Setting up your environment
* [The wiki](https://github.com/palimpsests/2013-Sep-HR-ML-sprint/wiki/Setting-up-your-dev-environment) has instructions

### Prototyping Models with Excel, R, and Rattle

##### Problem Analysis
* The data you'll be working with is in ```train.csv```, with the following variables:
  * Survival (0 = No; 1 = Yes)
  * pclass: Passenger Class (1 = 1st; 2 = 2nd; 3 = 3rd)
  * Name
  * Sex
  * Age
  * sibsp: Number of Siblings/Spouses Aboard
  * parch: Number of Parents/Children Aboard
  * ticket: Ticket Number
  * fare: Passenger Fare
  * Cabin: cabin number
  * embarked: Port of Embarkation (C = Cherbourg; Q = Queenstown; S = Southampton)

_Notes on the variables:_

* _Pclass is a proxy for socio-economic status (SES): 1st ~ Upper; 2nd ~ Middle; 3rd ~ Lower_
* _Age is in Years; Fractional if Age less than One (1).  If the Age is Estimated, it is in the form xx.5_
* _With respect to the family relation variables (i.e. sibsp and parch) some relations were ignored.  The following are the definitions used for sibsp and parch._
    * _Sibling: Brother, Sister, Stepbrother, or Stepsister of Passenger Aboard Titanic_
    * _Spouse: Husband or Wife of Passenger Aboard Titanic (Mistresses and Fiances Ignored)_
    * _Parent: Mother or Father of Passenger Aboard Titanic_
    * _Child: Son, Daughter, Stepson, or Stepdaughter of Passenger Aboard Titanic_
    * _Other family relatives excluded from this study include cousins, nephews/nieces, aunts/uncles, and in-laws. Some children travelled only with a nanny, therefore parch=0 for them.  As well, some travelled with very close friends or neighbors in a village, however, the definitions do not support such relations._

##### Exploration with Pivot tables
* Explore the data by using Excel, Google spreadsheets, or similar software.
* Pivot tables are helpful here - if you're not sure how to use these, refer to the [Kaggle instructions](http://www.kaggle.com/c/titanic-gettingStarted/details/getting-started-with-excel). Determine:
  * Percent of people who survived by sex
  * Percent of people who survived by class
  * Percent of people who survived by age
  * Any other information you think may be relevant or that will help you understand the data
* Feel free to make submissions to Kaggle to compare your results!

##### Using the Rattle library for R
* [This is a nice short overview on Rattle](http://onepager.togaware.com/StartO.pdf)
  * Import train.csv into Rattle
  * Choose which variable you want to predict, which variables you think will contribute to this prediction (the inputs), and which variables to ignore
* Visualize the data using Rattle’s tools on the explore tab
  * Explore the options for each section
  * At a minimum,  use the Explore → Interactive → Latticist feature
  * Try to find a view to support the conclusions you came up with previously
* Explore the models available in Rattle
  * Why are there different types of models?
  * When would you use each type?
  * Run multiple models and look at the data
    * Understand what [AUC](http://en.wikipedia.org/wiki/Receiver_operating_characteristic#Area_under_the_curve) means
    * Compare the AUCs from different models to see what works better with the data
  * Choose a model to evaluate your data
* Once you have chosen a model, evaluate how well the model works on your validation data
  * Become familiar with the Evaluate Tab
  * In the Data section, choose validation.  This will run your model on the validation data

* Evaluate the testing data using the model you chose above
  * Choose type: Score, Data type: csv: test.csv
  * This will output a file in CSV format.

##### Higher Level Concepts:

* Watch [The Problem of Overfitting](https://class.coursera.org/ml-003/lecture/39) Coursera video (10 min)
  * You can ignore the mathematical equations in the video, but you should understand the high level concept of overfitting and how to address it
* Watch [Model Selection and Train/Validation/Test Sets](https://class.coursera.org/ml-003/lecture/61) Coursera video (12 min)
  * Understand why you need train / validation / and test data sets and how they help solve the overfitting problem
  * Using this information, go back to Rattle and experiment with partitioning the data into these 3 sets

### Python FTW

* Complete a similar analysis, this time using Python as instructed in [this Kaggle tutorial](http://www.kaggle.com/c/titanic-gettingStarted/details/getting-started-with-python).
* Create a new feature by regrouping and separating the ticket fares into bins.
  * Combine your new feature with existing features to create a more accurate “survival table”.
  * Write the results to a CSV using the process described in the tutorial.
* Watch [this video](http://www.youtube.com/watch?v=kwt6XEh7U3g#t=45m35s), which introduces Random Forests, or 'Ensembles of Decision Trees' -- a very powerful and widely-used type of algorithm (note: video starts at about 45 minutes in, the important stuff starts there and continues for about 15 minutes).
* Following the [Random Forest Tutorial](http://www.kaggle.com/c/titanic-gettingStarted/details/getting-started-with-random-forests), use Python's Scikit-Learn library to make predictions with a RF algorithm.
  * You'll need to munge the data appropriately with .
  * Experiment with tuning the parameters of the RF algorithm
  * Write the results of your algorithm to a CSV.

### Extra Credit

* Split data into training / cross validation / testing sets
* [Normalize](http://en.wikipedia.org/wiki/Normalization_%28statistics%29) and scale the data so all values are between zero and one
* Research the physical layout of the Titanic and use it to engineer at least two completely unique features
* Go through the [Scikit-learn tutorial](http://scikit-learn.org/stable/tutorial/index.html)
* Watch [this video on Sciki-learn](http://www.youtube.com/watch?v=cHZONQ2-x7I) and follow along in an iPython notebook
* Watch the “Regularization” ML Coursera Lecture
* Watch the “Applying Machine Learning” ML Coursera Lecture
* Watch the “Linear Regression” ML Coursera Lecture

### Nightmare Mode

* Find a Kaggle competition where data includes blocks of text and use the NLTK library to extract and engineer 10 unique features. What are the time complexities of your algorithms?
* Get the [data](http://qsf.cf.quoracdn.net/QuoraAnswerClassifier_testcases.zip) for the Quora Answer Classifier challenge and make a prediction using a logistic regression model (beware the implications of dealing with sparse data)
* Rewrite your code to implement an algorithm that creates unique feature combinations to be used by your model.
* Rewrite your code to implement “one hot encoding” before predictions are made.
* Rewrite your LR model to implement  “greedy feature selection” -- an algorithm that keeps track of the most useful features as it runs and disregards the poor ones.
* Rewrite your LR model to use a cross-validation loop to score itself and output results to a CSV.
* Win money on Kaggle!

### Recommended Reading
* _Data Mining with Rattle and R_, Graham Williams
* _Python for Data Science_, Wes McKinney

Good luck!

~ T. Chakraborty, K. Geppert, G. Hilkert, G. Morita, A. Spade, F. Tripier, and Z. Zibrat