## Results

**And the Results Are**

Once we had our models developed, we believed that the random forest had the best combination of diverse predictions (not too concentrated on Conservatives) and accuracy. We used random forest model to predict ideologies on the data collected from our 4 groups (Politics, Economics, Wisconsin Politics, and Arizona Politics).

Politics was our biggest group by far, and our quick analysis of the top frequency words showed quite a bit of overlap with our training subreddit groups. The graph below shows our final results on this subreddit group. There is a stark favor towards Conservative predictions with our model. Overall, we predicted *98.7%* of the posts were conservative.

<img src="./../images/Prediction_results.jpeg?raw=true"/>



**Did it Work?**

Looking across the other models, we predicted 97-99% of the posts were Conservative. Although we are likely not getting the percent of posts correct, we think there could be a relative relationship between the liberal percentage of posts and election outcomes, even if we are not doing a great job of classifying.

Interestingly, Arizona was our most liberal group. In that state, 2 of the 9 Congress spots switched from Republican incumbents to Democrats (the remaining 7 seats were won by incumbents). In Wisconsin, no House of Representative seats switched.

<img src="./../images/test-groups.jpeg?raw=true"/>



**Future Research and Improving the Model**

Unfortunately, this is likely inaccurate and represents the biased samples that we used to train our models.
