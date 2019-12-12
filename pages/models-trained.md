## Models Trained

**Train Models Now; Predict Later**

In order to select the best algorithm for predicting conservative or liberal tweeters, we trained our in-sample model on 2012, 2014, 2016 and 2018 for subreddit groups that *self-identified* as *liberals*, *conservatives*, or *moderates*. This way, when splitting the in-sample into training and testing groups, we could compute the accuracy of our models.

**The 5 Models We Trained**

To do this, we trained our in-sample data on 5 models, including Multiple Logistic Regression, LASSO Logistic, Principal Components Regression (PCR), Random Forest and Neural Networks. We chose these models because they demonstrated increasing complexity (with Neural Networks being the most complex) and they drew from different and distinct methodological approaches in order to achieve classification. For instance, LASSO is a regularization methodology while Random Forest is a tree-based approach.

**The Winner Is ...**

After testing all of the above-mentioned models on the testing data (whether a Redditer was a self-reported Liberal, Conservative or Moderate), we compared the accuracy rates (as shown below in *table 1*) and found that **Random Forest** was our best algorithm with a score of 86.17% accuracy.

<img src="./../images/Models.jpeg?raw=true"/>


**Do It, Do It Now!!!**

With time running out, we then applied our Random Forest model to our *lockbox* sample: 2018 Reddit data from the *Politics* page where users were not self-identified by their political beliefs. Read about our conclusions on our *"Final Results"* webpage.
