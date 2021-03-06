---
layout: post
title: "Do you want to grab attentions on Twitter?"
author: "CaffeineOverflow"
header-style: text
tags:
  - Twitter
  - Data Analysis
---
![head](/images/head.jpeg)



<div align='center' ><font size='100'><strong>Do you want to grab attentions on Twitter?</strong></font></div>

<div align='center' ><font size='5'><font face="微软雅黑"> A study in Maximising an Original Post's Retweet Count</font></font></div>



# Why are we interested?

Twitter, as an online social media platform, is a place where we relax ourselves, interact with others and know what’s happening around the world. Also, over the past few years, it has been a distinct social medium where the president of the United States communicates with the public.  These days, Twitter has become more and more powerful as a social tool for all kinds of people. And naturally, we’d like to figure out what we can do to make a tweet seen by more people and to gain more interactions, and thus to make ourselves more influential. However, on Twitter, you are only one user among millions, and getting attention can be difficult. So what intrigues us the most is how can we establish a tweet, what kind of strategy can help us to **get more attention and gain more retweets**?

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="/images/rump.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">Why can Trump always get so many attentions? Well, surely because he is President of U.S...</div>
</center>


# What problems do we hope to solve?

Based on the data available, here we mainly focus on **analyzing the factors that covary with the number of original post's retweet**. In the original paper *Testing Propositions Derived from Twitter Studies: Generalization and Replication in Computational Social Science* by Hai Liang et al, they analyzed information diffusion at user and tweet level. However, the results only tell us whether multiple factors are positively or negatively correlated. We still have little idea of how exactly are they correlated: for example, does the retweet count linearly increase with the number of followers? Is there certain "threshold effect"? Also, have you ever wondered what is the best time to post? 

That’s what this article is all about. We’ll show you what types of user and tweet that people pay attention to. Let's explore together!

# Data Description

**EgoTimelines:** The dataset contains ego users’ dynamic activities, including <u>posting original tweets</u>, <u>retweeting</u>, <u>replying</u> and <u>@-mentioning</u>. It also contains information about the <u>number of retweets</u>, <u>presence of URLs</u> and <u>presence of hashtag</u>s for each tweet. The dataset is ideal to analyze the contributions of factors at the post level to the post’s influence.

**EgoAlterProfiles:** The dataset contains sampled users profiles, including the <u>number of followers</u>, <u>languages</u>, <u>account created time</u>, etc. Combined with the “retweet_count” term in EgoTimelines dataset we can analyze the effect of the number of followers and language (factors on the user level) on the post’s influence. For this dataset, we first filter out the profiles which are not egos, then count the follower numbers for each user.

**EgoNetwork:** This dataset contains <u>all pairs of ego-alter relationships</u>, where the number of followees for each ego users can be calculated and further analyzed.


# What do we find?

The problem is two-fold. We first explore it from a user perspective -- how does the user profile affect the influence and then from a tweet perspective -- how does the textual content of tweets affect the influence.

<font size=5> I. User Perspective </font>

First, we'd like to gain an intuitive understanding of how the number of retweet co-relates with the numbers of followers, followees and friends.

<center class="third">
	<img src="/images/followers-retweet.svg" width="600"/><img src="/images/followees-retweet.svg" width="600"/><img src="/images/friends-retweet.svg" width="600"/>
</center>

So what can we learn from above figures?

1. **Be more interactive and get more followers and friends--Duh!**

   Generally speaking, according to above figures, we noticed that the average numbers of retweet count are not very large: mostly are below 10, some are more than 20. And as the number of followers/followees/friends increases, the probability of receiving more retweets increases. To go a step further，we group the tweets by different numbers of followers/followees/friends, studied the corresponding distributions and found that **when number reaches a threshold, (in this case, three digits number) the effect starts to become significant.**

   <center> <img src="/images/threefactors.svg" width = "900" height = "600"/></center>

   The result is intuitively true, since Twitter is primarily about making connections and building dialogue. And the last time I checked, it takes at least two people to get a dialogue going : )

   <center> <img src="/images/colinearity.svg" width = "1200"/></center>

   Admittedly there might be strong multicollinearity among these factors - especially between the number of followers and the number of friends, as presented in the figures above. <u>But our conclusion remains the same: By following more people, being more interactive (getting more friends), you can hopefully get more followers and more retweets. </u>Maybe there's no obvious increase in terms of retweet at the beginning, when you only have a few followers, don't give up and continue to be interactive, as soon as the number of your followers reaches three digits, you can expect to see some significant changes.

2. **Always post with hashtags--Join trending hashtags on Twitter**

   Of course we know that with more followers, we can get more attentions. But it's eaiser said than done, for most of the users, how can they get more than 100 followers when they only get less than 10 for now? Here, we pick two users who are representative. 

   <center> <img src="/images/super.png" width = "900" height = "600"/></center>

   a. User 18670, who seems to be a famous person as she has lots of followers; 

   b. User 17159 - a user just like us! - with only one follower. But how come she manages to have so mant retweets, even more than those of user 18670?

   <center> <img src="/images/user18670andUser17159.svg" width = "900" height = "600"/></center>

   As shown in the figure, both user 17159 and user 18670 gain more retweets when using hastags. And although having less followers, user 17159 can get a fairly large amount of retweets when including hashtags in the tweets.

   From above analysis, we realize that, if you already have many followers, you might not need to do much to get retweets; but if you do not, just like user 17159, **it's a smart choice to post with hashtags**, which will make your posts seen by more people!

   <center>    <img src="/images/hashtag.png" width = "600" height = "300"/>    <br>    <div style="color:orange; border-bottom: 1px solid #d9d9d9;    display: inline-block;    color: #999;    padding: 2px;">Hashtags are laser pointers that shine on folks serious about a topic.</div> </center>

   

3. **What language do you speak?**

   

   Looking at the user-language data, we can recognize some patterns in terms of the correlations between user language and user activeness in terms of retweeting. 

{% include language.html %}

In particular, we can categorize the countries into 3 categories:

- group1 (high retweets / follwers / followees count): <u>Arabic speakers</u> 

- group2 (high retweets / statuses; low followers / followees count): <u>Dutch speaker, and Japanese speakers</u>

- group3 (low retweets / statuses; high followers / followees count): <u>Turkish, Russian and German speakers</u>

  But let's not jump into the conclusion but take a closer look! - Distribution should be more precise than a summary statistic.

  <center>    <img src="/images/specificLanguages.svg" width = "1200" />    </center>

  According to the distribution presented above, the countries can indeed be categorized into 3 categories in terms of users' activity patterns(Here we assume a high retweet count suggests that tweets in a certain language is more likely to be retweeted, and that a certain language speaker will be more likely to retweet what others have posted.):

  - **The fanatics:** Arabic speakers have the highest average number of followers count, and they also have the highest retweets frequency among all langauge user groups.
  - **The actives:** Dutch speakers and japanese speakers share a common point: they are more likely to retweet even though they don’t necessarily have a high number of followers count, which probably means that they really focus on their own followers and keep interacting with them rather than following many people but remain inactive. Therefore, <u>if you are Dutch or Japanese speaker, we would suggest you to post in these languages as your post might get a higher chance of being retweeted by your people!</u>
  - **The silent group:** Russian speaker and German speakers are the exact opposite of the previous category. Russian speakers and German speakers they have a high average follower count, which means they are active on this social media. But at the same time they have a low retweet frequqncy, which could be explained as they are more cautious about spreading others' words. Therefore, <u>if you are Russian or German speaker, you might like to post in English to change your audiances to those who are more willing to retweet.</u> :P

<font size=5> II. Tweet Perspective </font>

Now let's move from user perspective to tweet perspective. 

- **What type of tweets get the most attentions?**

  Here we categorise tweets into 4 types: 

  - Original tweets
  - Replies of tweets
  - Retweets of non-egos' tweets
  - Retweets of egos' tweets
  
  We can see that most retweets are tweeted from other users rather than egos, which makes sense since egos are only small parts of the whole population. Besides, an obvious observation is that compared to original tweets, retweets of tweets gain more attentions. But keep in mind that only a small fraction of tweets are retweeted, so don't pressure yourself. Even if you only got one retweet,  it's still better than most of the tweets!
{% include sboxplot.html %}

- **How does time affect the number of retweets?**

  - Years & Months

    First we want to check out how the number of retweets grow with the year.

    <center>    <img src="/images/overall_trend.svg" width = "500" />    </center>

    Ah-hah! It turns out that there are more retweets in 2014 than other years, which is probably due to an increase in the number of users. 

  - Days & Hours

    Now Let's check out how tweeting time(hour and day of the week) effects the number of retweets. 

{% include most_tweeted.html %}

{% include non_retweets_hour.html %}

From the above figure, we can tell that the number of most retweeted origianl tweets and replies don’t follow the general trend to increase from 5-11h and 12-21h. instead, most of these tweets are posted at 9 and 10 a.m.

Also, based on our study in regression analysis, we notice that at 9 a.m. and 10 a.m., there's small but siginficant postive correlation with retweet count, suggesting that you can try tweeting at 9 or 10 a.m.

Due to a lack of data to train a decent classifier, instead of propensity score matching，we found some users to examine if the time of posting influences the retweet count. Here, we pick user 18670. Based on the violin plot below, we find that though user 18670 tweeted very often during the peak hours, the time of the tweet doesn't show effect on the number of retweets he/she gets. So when you already have a lot followers, tweet whenever you want?

{% include u18670.html %}

- **Do holidays matter?**

  During holidays, people usually have more free time to relax themselves and a guess is that we can gain more retweets during this time. As Christmas is the most widely celebrated holiday in the world, we start exploring how much effect that Xmas has on the number of retweets. Here we only keep counties where Christmas is a national public holiday. 

  And our guess is validated, the average number of retweets clearly peaked on Christmas eve! So if you want to get more attentions, it's a good time to tweet on Christmas Eve! 🎄

{% include xmas.html %}





# What to do now? 
Based on the analysis above, we reach several simple and straightforward conclusions:

- Get more followers 👯
- Use hashtags 🏷️
- When tweeting in different languages, use different strategies 🇬🇧🇨🇭🇺🇸
- Retweet your own tweets 📱

- Time matters! 🕙

- Don't forget to tweet during holidays! 🎄




