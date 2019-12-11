## Reddit EDA

**Overall Context:** Reddit is a social network that has a specific set of users that are likely unique to the platform. At the start of this project, we were not overly familiar with the posting patterns of the Reddit community, especially within the different political groups. Given this, we had to do some basic EDA to understand what were the guidelines and trends around Reddit posts, what were the differentiating words between the political ideologies, etc.

**Project description:** Our main objectives in this area were to: (1) understand overall posting patterns in Reddit, (2) understand high-level differences in posting patterns between subgroups, and (3) identify the key differentiating words and phrases between Conservatives, Liberals, and Moderates.

**Training and Testing Data Samples:** We used different subreddits to divide our training and testing datasets. Our training is based on self-identified groups (Conservative, Liberal, and Moderates). The test datasets are based on groups that do not self-identify (Politics, Economics, Wisconsin Politics, and Arizona Politics)


## Reddit Overview
**Reddit Score:** For each post, there is a score based on "upvotes". This is graphed below for the Conservative, Liberal, and Moderate groups.


<img src="./../images/reddit_score.png?raw=true"/>

**Extreme Outlier Note:**
There is an extreme outlier in the conservative thread titled: "Why we won", which happened after the 2016 election. This must have happened late in the evening so that it still technically happened on the election day. Link [here](https://www.reddit.com/r/Conservative/comments/5c3xah/why_we_won/)


**Post Overview:** On Reddit posts can be up to 300 characters long. This is fairly similar to Twitter, which allows for the option to apply our models to other social network sites. The conservative posts seem to be well represented by all shorter and longer posts, but this might be more due to volume of posts. Liberal appears to have longer posts, especially in 2012 and 2014. Moderate politics has the shortest posts. However, all of these appear to be roughly similar, and there doesn't appear to be any reason to think this will negatively impact our model.

<img src="./../images/reddit-post-length.png?raw=true"/>


## Key Findings

**Word Cloud:** A quick and easy way to visualize word differences is through word clouds. This is shown on the graph below for each of our 3 groups. It is interesting that conservatives tend to use democrat more, and liberals tend to use republican more often. This likely shows that each are posting about the other groups.
<img src="./../images/reddit_wordcloud.png?raw=true"/>


**Frequency Graph:** We also looked at the frequency of words seen across Reddit posts in the Conservative, Liberal, and Moderate groups. This is similar to a word cloud but gives a better sense of the actual word frequencies across the different groups.

<img src="./../images/reddit_word_freq.png?raw=true"/>

**Words by T Test:** Most applicable for our model, we looked at the words that showed the biggest difference in frequency among the groups using a proportions t test.


## Test Dataset
**Reddit Score:** Similar to the training data, we can look at the score, or number of upvotes, for each post in a subreddit group by year. This visual is biased because the politics page has many more posts compared with the other groups, due to the widespread appeal of the group. Economics receives a significant amount of upvotes. Wisconsin and Arizona pages do not show many votes -- this is likely due to the niche scope of the groups.


<img src="./../images/reddit_score_test.png?raw=true"/>


**Frequency Graphs:** Due to the different nature of the groups, the top 20 words were fairly different, so we needed to look at the frequency graphs for each group individually. For 2018, these are shown below.

<img src="./../images/politics-freq-2018.png?raw=true"/>
<img src="./../images/economics_freq_2018.png?raw=true"/>
<img src="./../images/wisconsin-freq-2018.png?raw=true"/>
<img src="./../images/arizona-freq-2018.png?raw=true"/>
