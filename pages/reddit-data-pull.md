## Reddit API Pull

**Overall Context** While many social media sites have some kind of API to pull user-created content, Reddit had advantages in a few specific areas. First, the API was completely free and well-documented. Second, the goal of our project is to identify the ideological belief of people posting content. On most user platforms, this would be difficult, subjective, and potentially invasive. However, on Reddit, people are anonymous and join groups to create posts on the social network. This can be useful for our experiment because these groups can be aligned with political identity.

**Pulling For Model Development:** To create the model, we needed to identify groups in Reddit where people with certain political affiliations would be active. For this, we looked at [this site](https://www.reddit.com/r/redditlists/comments/josdr/list_of_political_subreddits/) showing the list of all political subreddits groups. We wanted to get a sense of political ideology on Reddit, so we chose 3 groups: (1) [Conservative](https://www.reddit.com/r/Conservative/), (2) [Liberal](https://www.reddit.com/r/Liberal/), and (3) [Moderates](https://www.reddit.com/r/moderatepolitics/). Due to the liberal-lean of Reddit's general network, the Conservative subgroup is the largest due to a general exodus from the mainstream channels as U.S. politics became more divisive and polarized. There are still posts within the moderate and liberal channels, so we can also use these as a way to understand the language features. For this, we were able to pull 27,830 posts from Reddit in these 3 groups across 2012, 2014, 2016, and 2018 election periods (filtering for 30 days before the election date).

Posts Pulled by Ideological Group:
Conservative: 24,175,
Liberal: 2,916,
Moderates: 739



**Pulling the Test:** For our project, we are trying to observe political voting behavior, so we needed to revisit our [list of political subreddits](https://www.reddit.com/r/redditlists/comments/josdr/list_of_political_subreddits/). Based on this list, the optimal groups we want are some mix of the very mainstream groups with a wide breadth of users and more specific groups that might allow insight into voting patterns in specific areas. For this, we pulled from 4 groups: (1) politics, (2) economics, (3) Wisconsin politics, (4) Arizona politics. Politics is the most mainstream political page on Reddit and has been known to be fairly biased towards liberal ideologies, but Economics serves as an area that is fairly popular but shows little or no ideological bias. Wisconsin and Arizona have political pages that are small but may provide insight into the different posting ideologies happening in contentious states. Again, we looked across 4 years and pulled a total of 188,499. The politics page on Reddit is very large, so this accounted for a much larger sample than the other groups.

Posts Pulled by Ideological Groups:
politics: 180,608
Economics: 7,611
Arizona Politics: 170
Wisconsin Politics: 110
