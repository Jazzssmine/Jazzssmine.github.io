---
layout: post
title: "My Spacemacs Workflow"
subtitle: 'From Vim to Spacemacs'
author: "Hux"
header-style: text
tags:
  - Vim
  - Emacs
---
![head](/assets/images/head.jpeg)



<div align='center' ><font size='100'><strong>Do you want to grab attentions on Twitter?</strong></font></div>

<div align='center' ><font size='5'><font face="微软雅黑"> A study in Maximizing an Original Post's Retweet Count</font></font></div>



# Why are we interested?

Twitter is a place where we relax ourselves, interact with others and know what’s happening around the world. Also, over the past few years, it has been a distinct social medium where the president of the United States communicates with the public.  An influencer is someone with millions of followers and a global presence. These days, Twitter has become more and more powerful as a social tool for all kinds of people. However, on Twitter, you are only one user among millions, and getting attention can be difficult. So what intrigues us the most is how can we establish a tweet, what kind of strategy can help us to **get more attention and gain more retweets**?

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="/assets/images/rump.png">
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">Why can Trump always get so many attentions? Well, surely because he is President of U.S...</div>
</center>


# What problems do we hope to solve?

Based on the data available, here we mainly focus on **analyzing the factors that covary with the original post's retweet count**. In the original paper *Testing Propositions Derived from Twitter Studies: Generalization and Replication in Computational Social Science* by Hai Liang et al, they analyzed information diffusion at user and tweet level. However, the results only tell us whether multiple factors are positively or negatively correlated. We still have little idea of how exactly are they correlated: for example, is the retweet count linearly increase with the number of followers? Is there certain "threshold effect"? Also, have you ever wondered when is the best to post? 

That’s what this article is all about. We’ll show you what types of user and tweet that people pay attention to. Let's explore together!

# data description

<i class="fas fa-cat"></i> EgoTimelines: The dataset contains ego users’ dynamic activities, including posting original tweets, retweeting, replying and @-mentioning. It also contains information about the number of retweets, presence of URLs and presence of hashtags for each tweet. The dataset is ideal to analyze the contributions of factors at the post level to the post’s influence.
<center>
	<img src="/assets/images/timeline.png" width = "800" height = "200" />
</center>

<i class="fas fa-cat"></i> EgoAlterProfiles: The dataset contains sampled users profiles, including the number of followers, languages, account created time, etc. Combined with the “retweet_count” term in EgoTimelines dataset we can analyze the effect of the number of followers and language (factors on the user level) on the post’s influence. For this dataset, we first filter out the profiles which are not egos, then count the follower numbers for each user:![ego_profile](/assets/images/ego_profile.png) 

<i class="fas fa-cat"></i> EgoNetwork: This dataset contains all pairs of ego-alter relationships, where the number of followees for each ego users can be calculated and further analyzed.
<center>
	<img src="/assets/images/egonetwork.png" style="zoom:70%;" />
</center>

# What do we find?

### User Perspective

  * **Be more interactive and get more followers and friends--Duh!**

    <center> <img src="/assets/images/distribution_retweet.png" width = "900" height = "600"/></center>

    We noticed that as the number of followers/followees/friends increases (from the first row to the fifth row), the probability of receiving more retweets increases, that is, the plot gets "fatter". **Especially when number reaches a threshold, (in this case, three digits number) the effect starts to become significant.**

    The result is intuitively true since Twitter is primarily about making connections and building dialogue. And the last time I checked, it takes at least two people to get a dialogue going. 

    <center> <img src="/assets/images/collinearity_between_factors.png" width = "900" height = "600"/></center>

    Admittedly there might be strong multicollinearity among these factors - especially between the number of followers and the number of friends, as presented in the figures above. But our conclusion remains the same: By following more people, being more interactive (getting more friends), you can hopefully get more followers and more retweets. Maybe there's no obvious increase in terms of retweet at the beginning, when you only have only a few followers, don't give up and continue to be interactive, as soon as the number of your followers reaches three digits, you can expect to see some significant changes.

  * **Always post with hashtags**--**Join trending hashtags on Twitter**

    For most of the tweets, their average numbers of retweet count are quite small and thus it's hard to analyse the effect of Hashtag in a collective way. Here, we pick two users who are representative. 

    <center> <img src="/assets/images/super.png" width = "900" height = "600"/></center>

    1. user 18670, who seems to be a famous person as she has lots of followers; 
    2. user 17159 - a user just like us! - with only one follower. But how come she manages to have so mant retweets, even more than those of user 18670?


    <center class="half"> <img src="/assets/images/user_18669.png" width = "450" height = "300"/><img src="/assets/images/user_17159.png" width = "450" height = "300"/></center>


    From above analysis, we realize that, if you already have many followers, you might not need to do much to get retweets; but if you do not, just like user 17159, **it's a smart choice to post with hashtags**, which will make your posts seen by more!
    
    <center>    <img src="/assets/images/hashtag.png" width = "600" height = "300"/>    <br>    <div style="color:orange; border-bottom: 1px solid #d9d9d9;    display: inline-block;    color: #999;    padding: 2px;">Hashtags are laser pointers that shine on folks serious about a topic.</div> </center>

  * **What language do you speak?**

    Looking at the user language data, we can recognize some patterns in terms of the correlation between user language and user activeness in terms of retweeting. In particular, we can categorize the countries into 3 categories:
    
    The fanatics: Arabic speakers have the highest average number of followers count, and they also have the highest retweets frequency among all langauge user groups.

    The actives: Dutch speaker, and japanese speakers share a common point: they more like to retweet even though they don’t necessarily have a high number of followers count. Which may be explained as they really focus on their favorite followers and keep interacting with them rather than follow many people but remain inactive. Therefore, **if you are Dutch or Japanese speaker, we would suggest you to posting in these languages as your post might get a higher chance of being retweeted by your people!**
    
    The silent group: Russian speaker and German speakers are the exact opposite of the previous category. Russian speakers and German speakers they have a high average follower count, which means they are active on this social media. But in the same time they have a low retweet frequqncy, which could be explained as they are more cautious about retweeting what others say. Therefore, **if you are Russian or German speaker, you might like to post in English to change your audiances to those who are more willing to retweet.** :P

  

### Tweet Perspective



# what have we learn

What types of Tweet have your found are most effective for getting the attention of a crowd? What about for getting noticed by an individual?



