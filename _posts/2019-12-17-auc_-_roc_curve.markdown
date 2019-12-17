---
layout: post
title:      "AUC - ROC Curve"
date:       2019-12-17 05:23:59 +0000
permalink:  auc_-_roc_curve
---


In Machine Learning, there are plenty of metrics used to measure the performance of the model. For classification problems, AUC - ROC curves are an essential evaluation metric. Before we dive into the AUC - ROC curve, I will give a quick introduction to the **Confusion Matrix**.

A Confusion Matrix showcases the predicted and actual values in a binary classification task.

<img src="https://imgur.com/CqgrQCh.jpg" alt="Confusion" width="300" height="200"><br>
[Source (Image1)](https://stackabuse.com/understanding-roc-curves-with-python/)

Let's imagine we're working on a model that predicts if a basketball shot is made or not. In this binary classification model, the class labeled Positive (1) is a made shot, while the class labeled Negative (0) is a missed shot. The Actual Values are the real shot results and the Predicted Values are the model's predicted shot results.
Now we can give into the definition of each box.

* TP = True Positive - Model correctly predicts the positive class.<br>
Player made shot, model predicts shot was made.

* FP = False Positive - Model incorrectly predicts the positive class.<br>
Player missed shot, model predicts shot was made.

* TN = True Negative - Model correctly predicts the negative class.<br>
Player missed shot, model predicts shot was missed.

* FN = False Negative - Model incorrectly predicts the negative class.<br>
Player made shot, model predicts shot was missed.

Now that we are pros of the Confusion Matrix, let's get down to the ROC business. An **ROC curve** or Receiver Operating Charactisteric curve is a probability curve that measures the _True Positive Rate_ versus the _False Positive Rate_.

* TPR or Recall is the proportion of correctly predicted made shots over all player made shots.<br>
TPR = TP / (TP + FN)

* FPR is the proportion of incorrectly predicted made shots over all player missed shots.<br>
FPR = FP / (FP + TN)

<img src="https://imgur.com/t6GBppS.jpg" alt="ROC Curve" width="300" height="200"><br>
[Source (Image1)](https://scikit-learn.org/stable/auto_examples/model_selection/plot_roc.html)

Now how does this measure our model?<br>
This is where AUC comes into play. **AUC** is the Area Under the ROC Curve. AUC is the number we care about in our performance metric. It ranges in value from 0 to 1
* 0.0 is 100% wrong meaning the model predictions are the complete opposite of the actual values.
* 1.0  is 100% correct meaning the model predictions are spot-on with the actual values.
* 0.5 is pure chaos. Model is just randomly guessing. In image above, the blue dotted line represents a 0.5 AUC.

Here are some graphs that helps us visualize how the AUC works.

<img src="https://imgur.com/m10XM8X.jpg" alt="AUC 1" width="600" height="300"><br>
[Source (Image1)](https://www.datasciencecentral.com/profiles/blogs/roc-curve-explained-in-one-picture)

In the Excellent green model, we have an AUC of 100% or 1.0. This means the model was 100% accurate in determining if the shot was made or missed. The True Positives and True Negatives do not overlap at all.<br>
In the Good orange model, we have an AUC of 75% or 0.75. This means the model was 75% accurate. There is a slight overlap in the Positives and Negatives which represents the FN and FP.<br>
In the No Separability red model, we have an AUC of 50% or 0.5. Again, pure chaos. Complete overlap in Positives and Negatives.

Can we use AUC - ROC Curve for Multiclass Classification Models?
Yes you can! In a multiclass model, we would have to approach this using a 1 vs all method. Using the same example with basketball shots, imagine we have 3 classes; Made, Missed, and Turnover (lost the ball before a chance to shoot). We would need 3 AUC - ROC curves for each class.
* Made vs Missed and Turnover
* Missed vs Made and Turnover
* Turnover vs Made and Missed

I hope reading this gives you more insight on, in my opinion, one of the more confusing but best metrics for model performance. 
