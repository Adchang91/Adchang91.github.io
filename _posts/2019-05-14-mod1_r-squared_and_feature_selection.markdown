---
layout: post
title:      "Mod1 R-Squared and Feature Selection"
date:       2019-05-14 12:22:13 -0400
permalink:  mod1_r-squared_and_feature_selection
---


In a scatterplot of independent and dependent variables, datapoints are usually not plotted in an easy straight line. The most you can hope for is a pattern. A Linear regression model attempts to define the relationship between the variables by best fitting a linear equation. In order to measure the accuracy of the linear equation, we use a statistical measure called R-Squared.

R-Squared or coefficient of determination is used to assess the goodness of fit of a linear Regression model. R-Squared is always interpreted on a 0% to 100% scale. 0% represents a model that cannot explain any of the variation of the dependent variables. 100% represents a model that is able to explain every variation of the dependent variable. 

The formula for R-Squared is 1 –  RSS/TSS. RSS is the residual sum of squared errors or the distance between the actual value and the linear equation’s predicted value. TSS is the total sum of squared error or the distance between the actual value and the mean value of all dependent variables. Based on the formula, if the RSS value is smaller, the R-Squared is higher.  

With the Kings County House dataset, we are tasked to build a linear regression model that predicts future sales. However, because the data includes multiple independent variables, exactly 19, we need to build a multiple linear regression model.  What makes this complicated is that each independent variable, or feature, weighs differently toward the dependent variable, or target. 

This is where R-Squared comes into the play. Using a powerful Python package called Statsmodels, we can determine the R-squared for each feature’s relation to the target. To clarify, this is whilst all features are determining the multiple linear equation’s predicted value. Below is an example of a table of features and associated linear regression values.
(<a href="https://imgur.com/AHqifky"><img src="https://i.imgur.com/AHqifky.png" title="source: imgur.com" /></a>)
From the table, we can see that the feature ‘grade’ has the highest R-squared value, which means it will weigh the heaviest towards the predicted target. The weights are known as the coefficients of determination. The coefficient of a feature can be positive where it will increase the target value or negative where it will decrease the target value. The coefficients of determination or feature importance is based on the absolute value of a coefficient. A highly negative coefficient has more feature importance than a lower positive coefficient. ‘Grade’ will have the largest impact on the model while ‘sqft_lot15’ will have the smallest impact.

Now that we know which features have the most impact on the model, let’s move on to Feature Selection.  Feature Selection is a process where you select features that contribute the most towards the predicted target. It’s not always good practice to grab every feature because it can reduce accuracy from irrelevant features and increase training time. For us to determine which features to select, we need to rank all the features. Scitkit-Learn has a great feature selection tool, RFE or Recursive Feature Elimination, that will rank all of the features. Below is a bar graph of the coefficients for the top features in order on the X-axis. 
![](<a href="https://imgur.com/BVuVXhh"><img src="https://i.imgur.com/BVuVXhh.png" title="source: imgur.com" /></a>)
As you can see from the bar graph, the rank of the feature is not necessarily the highest absolute value of the coefficients but it’s the highest importance to the model. Although, the absolute value of the coefficient is a big factor for determining the ranking of features. 

After we’ve ranked all the features, we can loop through numbers of features and find the R-squared value of each loop. For example, we can find the R-squared value for just the best feature, then the R-squared value of the 2 best features, then the R-squared value of 3 best features, and so on… Eventually we will come to a point where adding more features will barely affect the model. This is the point where the model plateaus but when exactly it happens is arbitrary. A way we can visualize the plateau of a model is using elbow plots.
![](<a href="https://imgur.com/CbB2GJk"><img src="https://i.imgur.com/CbB2GJk.png" title="source: imgur.com" /></a>)
The above graph shows us the increase of R-Squared after a certain number of features. In the example above, 5 features has an R-squared of about 0.57, 10 feature is about 0.80, and 20 features is about 0.82. From the elbow plot, you can say that the model plateaus at around 10 features.

Adding more features beyond 10 is up to the user. However, adding more beyond the necessary features can increase the model’s likelihood of being susceptible to inaccuracy. Furthermore, running additional models, like Train-Test Split model, with more insignificant features will increase the train time for the model.  The model’s R-Squared is the percentage of the target’s variable variation that a multiple linear regression model can explain. If 80% of the model can be explained by the top 10 features, do we really need all 56 features to explain 84% of the model? This is feature selection. 

