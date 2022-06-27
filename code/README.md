# Project 3 - Web APIs & NLP

## Executive Summary
In our modern world of the internet and huge amounts of information it has become increasingly important to ensure that you are doing everything you can to beat the noise and get through to users. This means both identifying which users to target and how to best capture their interest and nothing in the world can tell you how to do that better than the users themselves. 

While this may seem to be a daunting task, utilizing the right tools can make it extremely manageable. In this report we present an opportunity to utilize a tool called natural language processing to compare posts of different users to identify what they're talking about and what they're passionate about. 

Our model uses posts from reddit.com to get sample of how users interested in different topics talk about that topic. With that information we can apply our model to other posts and predict what users are talking about. This report specifically focuses on taking a look at five major sports: baseball, basketball, football, hockey, and soccer. 

This methodology has proven to be extremely effective at identifying which of these major sports is being talked about by a given post. A marketing team can then apply this model to posts on other social media sites to find fans they may not already be reaching and make sure they engage with those users.

We can also further analyze discussion to find out which players or aspects of the sport are being talked about more positively or negatively to inform marketing decisions of what to promote to continue to increase fan excitement or capture new fans.


## Problem Statement:
The goal of this project is to examine how the usage of language differs between fans of different sports teams.

---
## Target Audience:
This report can be utilized by marketing deparments for sports leagues and teams to identify discussion about their sport.

---
## Sources:
reddit.com/r/soccer
reddit.com/r/nfl
reddit.com/r/nba
reddit.com/r/hockey
reddit.com/r/baseball


---
## Data Dictionary:
title(string) - Content of the post
subreddit(string) - Subreddit the post was taken from

---
## Notebooks:
### API.ipynb
Created function to pull data from subreddits

### data-clean.ipynb
Created functions to drop unnecessary features and clean data

### workflow.ipynb
Experimented with different models

### best-model.ipynb
Final model in separate notebook for readability

### CountVec.ipynb
Created function to look at common words

### sia-scoring.ipynb
Applied sentiment intensity analysis to posts

---
## Analysis:
In our analysis we ingested the titles of reddit posts from r/nfl and r/soccer in a logistic regression model to predict with natural language processing which sport's subreddit a post came from. This initial model was able to predict the sport being discussed very accurately, with a recall score of 0.94. We then expanded the scope to include r/baseball, r/nba, and r/hockey. We again found that our model was very successful, scoring a 0.88. 

We also utilized sentiment intensity analysis to take a look at the sentiment behind the language being used for each sport. This model, however gave much less definitive results finding the overwhelming majority of posts to be written with neutral language. This is likely due to utilizing primarily post titles for our dataset since text posts are rare in the sports subreddits and most of these titles read as news headlines rather than discussion with strong positive or negative sentiment. 

---
## Conclusion:
From our analysis we find that natural language processing can be very successful at identifying which topic is being discussed even as accurately as determining between specific sports. Our model did, however, do better at identifying some sports than others. Soccer was the most successfully identified. This likely has much to do with many of the fans being international and thus having more significant differences in language usage compared to American sports. When soccer was misclassified, it was most mistaken for hockey related discussion. This makes sense because they share more common vernacular (goals, assists, etc) than the other three sports. Our model struggled to identify baseball discussion the most this is likely due to a couple of factors. First, baseball is a very statistics heavy sport where many headlines and post titles are simply statlines/numbers which may be difficult for our model to identify. Second, one of the largest stories in baseball at the time this data was pulled was the suspension of a player for off-field misconduct thus titles discussing that news story would not be using language specific to the sport.

In future work we would like to expand our model to be used on comments as well as submissions. This would increase our sample size for much better sentiment analysis as well as improve our accuracy for identifying general discussion. Both of these would be valuable tools for our primary stakeholders in this study. Being able to scrape discussions and identify fan sentiment regarding certain players or teams are key to helping PR teams identify who fans are excited to see more of. Reddit is unique in that all of these users are posting on dedicated forums for their respective sports however other social media sites like facebook or twitter may have a number of users talking about these sports without interacting with accounts associated with those sports. Being able to recognize those conversations is a valuable tool in the current marketing environment.