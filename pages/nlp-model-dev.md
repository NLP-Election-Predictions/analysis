## Natural Language Processing Model

**Model description:**

We exploited the advantage that there is Reddit data categorized as conservative, liberal and moderate based on the group where each post was published. With this information, we built a data frame with each post title as a row, the words contained in the reddit titles as columns, and the group as the Y.

Following Gaurav, Kumar, Srivastava, Miller (2013) and Tumasjan, Sprenger, Sandner & Welpe (2010), we explored the predictive power of words of politicians with t-tests between liberal and conservative groups and we saw that frequent words like Obama and Trump had very little predictive power. Instead, we took the 10,000 most frequent words and ranked them based on their t-test between the liberal and conservative subsamples, using only training data. Having our predictors ranked by importance allowed us to use a fewer amount (1300 and 3000 depending on the case) so our computers would not run into a memory problem or take too long to run the models.

Reddit data does not have information about location, which makes the prediction exercise for midterm elections in the US extremely difficult. While we were counting on the Twitter data to provide location information, being blocked prevented us from doing that.
However, there was still value to get from Reddit. Since its titles are similar in length to Tweets and since the behavior on both platforms could have strong similarities, we decided to build a model that could predict whether each post was liberal or conservative so our model could be run on Twitter data in a real election scenario.
