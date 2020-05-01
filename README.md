Machine Learning Homework - Exoplanet Exploration

Model 1: Support Vector Machine (SVM)

The first model I developed was an SVM model.  For this model I included all of the x-values intially to determine the accuracy of the model with no features eliminated.  I scaled the numerical data (ie. the x values) using the MinMaxScaler.  The initial run of the model produced a fairly accurate result with a testing score of 0.841.  The hyperparameters were tuned further using GridSearchCV and the model was run again resulting in a "best model" with an improved score of 0.869 (C=10 and gamma=0.0001).  Thus the model is fairly accurate with all features included.  Unfortunately SVM models do not indicate which features are most important so it is very difficult to tell which features should be eliminated to increase the accuracy of the model.  This led to my choice for my second model.

Model 2: Random Forest Classifier Model

My original SVM model was fairly accurate at classifying exo-planets, but it included all of the possible parameters from the dataset.  It may be possible to make an even more accurate model by removing certain parameters that are not contributing to the accuracy.  In order to determine which parameters to remove, I decided to run a Random Forest Classifier model.  The data was pre-processed in much the same way as the SVM model.  The x-values were again scaled using the MinMaxScaler.  The Random Forest model was run and returned a fairly accurate score of 0.900.  So the Random Forest model is more accurate at classifying exo-planets than the SVM model.

I then inspected the feature importances of the different parameters and found that surprisingly the features were all fairly equal in their importance to the accuracy of the model.  All features scored from 0.1-0.002 in importance, with 3 of the 4 error flag parameters being the most important and two of the star characteristics (temperature and radius) being the least important along with planet number (which makes sense as it's just a number and not actual data).

The model was run again after removing all parameters that fell below 0.01 in importance.  This did not increase the accuracy of the model (testing score of 0.898).  This is likely due to the fact that all of the parameters scored fairly equally in importance and are all likely contributing to the accuracy of the model.  The only parameter I would suggest removing was the plant number parameter as it was simply an id number and did not contain any data (and it scored the lowest in importance with a 0.02).

Best Model: Random Forest Classifier

In the end, while both models performed well, the Random Forest Classifier (0.900) was more accurate than the Support Vector Machine (0.869).  This is likely due to the fact that Random Forest is a more flexible model than SVM as it is comprised of a large number of invdividual trees that operate as an ensemble.  SVM on the other hand is attempting to draw an optimal hyperplane to seperate classes, which is more rigid and may result in loss of variability and nuances between the classes and thus decrease accuracy.  The Random Forest Classifier is considered to be at the top of the classifier hierarchy as "a large number of relatively uncorrelated models (trees) operating as a committee will outperform any of the individual constituent models" (https://towardsdatascience.com/understanding-random-forest-58381e0602d2).  Thus it is not surprising that the Random Forest Classifier was the most accurate model.

