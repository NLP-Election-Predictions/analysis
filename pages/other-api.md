## Other Social Media APIs Considered

**Overall Context**

In order to expand our analysis, our team considered numerous social media APIs, including: Reddit, Facebook and Twitter.

Ultimately, Facebook's API proved too restrictive to be used and Twitter's API blacklisted our team due to too many packet pulls (twice actually...), so we ultimately focused our analysis on the Reddit Data.

However, to provide more context for our data aggregation techniques, we will provide more details about our attempts to pull data from the Twitter and Facebook APIs.

**The Twitter API**

The Twitter API was challenging. First, we pulled from the non-premium, basic API which only returned 15 tweets per API pull. Obviously, even with the construction of a complicated looping architecture, we thought (correctly) that it would be nearly impossible to cull the large dataset that we would need. Thus, we subscribed to Twitter's Premium API Sandbox.

Even subscribing to Twitter's Premium API is a nontrivial task. After submitting a formal application to Twitter, both Jake and Eric had to email back and forth three times each with their developers to receive authorization.

Once authorized as users, the team began pulling from the premium sandbox. Here again arose numerous challenges. To start, non-paying premium subscribers (yes, you can pay up to a $1000 / month for premium subscriptions!) are limited to only *50 pulls per month* and packets that contain at maximum *900 tweets*.

We discovered quickly that we had to be very strategic about our pulls.

Unfortunately, we discovered this too late. First, Jake was blacklisted (after spending an entire weekend creating the perfect loop to cull data going back 30 days before the 2018 election) and then Eric was blacklisted as well after attempting to execute the script.

This was a low point for the moral of the group.

**The Facebook API**

The Facebook API was equally challenging but much less tragic. We investigated the documentation and created developer accounts with Facebook (you need to register an App), but quickly discovered how challenging it was to correctly call this API. After numerous frustrating hours, we abandoned this API for the ill-fated Twitter API. It does not appear that there is a quality method to access Facebook through Python. Instead all get requests must go through their requests page and requests are again limited monthly on free API access versions. Both of these cause substantial issues in the research process.  
