# nlp-hackathon
A one day NLP hackathon

## Executive Summary
Twitter is one of the fastest ways people can communicate and share information, making it a critical tool during an emergency or a disaster, such as a wildfire or an earthquake. However, it isn't always clear whether or not Tweets are referencing actual emergencies or are using similar language to describe a non-emergency metaphorically. Using Natural Language Processing, we created an ensemble model that classifies whether Tweets with certain keywords - such as bleeding, ablaze, apocalyse, etc - were referring to actual emergencies or were using these keywords metaphorically or as slang. 

Our model used Tweets from a Kaggle dataset to get samples of the differences in how a user was Tweeting about an emergency versus how a user was using similar keywords to Tweets about something more mundane. We analyzed the terminology and common phrases. With that information, we were able to apply our model to other a test set - Tweets the model had never seen before - and get predictions on whether the user was having or witnessing an emergency or not. 

This methodology has proven to be extremely effective at discerning the difference between Tweets that are using keywords as slang or coloquially and those Tweets that are using those keywords to describe an actual emergency. We recommend this model be used by emergency departments to detect emergencies in their community in order to hopefully increase response time in responding to those emergencies and disasters. Providing even incrementally faster aid could save lives and/or properties and homes depending on the type of disaster.

This project was completed in approximately 6 hours, as a single day hackathon. Because of this, there are certain improvements that can be done to the model. The one major one is that the model seems to misclassify more disasters as non-disasters than non-disasters as disasters. Misclassifying a disaster as a non-disaster has a worse outcome, potentially . If we decide to expand on this single day hackathon, tweaking the model to minimize false negatives instead of false positives would be the first thing we would look at.

---
## Problem Statement:
The goal of this project is to create a model that can analyze a Tweet and determine whether or not the individual needs aid.

---
## Target Audience:
Because Twitter is such a rapid source of news, this model can be used by emergency departments in order to discern who is in need of aid and to rapidly get help sent their way.

---
## Sources:
- (https://www.kaggle.com/competitions/nlp-getting-started/overview)


---
## Data Dictionary:
- keyword (string) - A word or phrase that flagged the Tweet as potentially referencing an emergency. Example keywords are ablaze, bleeding, accident, aftershock.
- location (string) - The location of the individual that is Tweeting.
- text (string) - the text of the Tweet.

---
## Notebooks:
### tweets.ipynb
The entire Hackathon was done in one notebook. If I decide to return to this project, I will likely split the code into separate notebooks.

---
## Analysis:
We trained several different models, including a Logistic Regression model and an ensemble model that was compiled of Logistic Regression, Random Forest, and Naive Bayes. The Logistic Regression model did the best at minimizing false negatives, with a recall score of 0.69. However the ensemble model just barely had the better F1 score, at 0.75 compared to the first model's F1 score of 0.74. Because we are more interested in minimzing false negatives, we are submitting the Logistic Regression model as our final model.

Both of our best models utilized CountVectorizer with basic English stop words. We also tried lemmatization, but it performed much worse when using the same models, scoring a 0.36 F1 score and a 0.32 Recall score. We theorize that this is because Tweets have a max length of 140 characters, so stripping away characters and only examining a word's base as lemmatization does was taking away too much data, which caused the model to perform poorly.

A detailed examination into the common words of each class (emergency and non-emergency) paints a clear picture of the differences in what people were Tweeting about. 'Youtube video', 'stock market crash', and 'movie' were some of the 15 most common words and phrases seen in non-emergency Tweets. It appears that a significant number of the non-emergency Tweets might be using similar terminology and keywords to discuss media. Another common phrase was 'body bag', which is referring to a type of purse that was commonly Tweeted about. The Tweets from actual emergencies had common words such as 'storm', 'killed', and 'homes razed'. 

---
## Conclusion:
From our analysis we find that natural language processing can be very successful at classifying emergencies and non-emergencies. Our model did, however, do better at identifying non-emergencies than it did identifying emergencies. In future work, we would like to tweak this so that the model is minimizing false negatives instead of false positives as it currently does. We would also like to add custom stop words, such as 'http' which was by far the most common word in the dataset as people were commonly Tweeting links. 

Finally, we would like to look into misclassifications and examine which Tweets are being misclassified the most. 
