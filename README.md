# Problem Statement

This project aims to deliver a model that can take in a submission from one of two subreddits, and decide which subreddit it came from. In particular, we focus on a few different subreddits where people post certain types of jokes. We attempt to answer the question:

Can we use natural language processing to distinguish between two joke-themed subreddits?


# Summary

In this project we explore Natural Language Processing techniques and classification models. Stemming, lemmatizing, and stopwords are all explored. We compare a variety of classification models including Logistic Regression, Multinomial Naive Bayes, Gaussian Naive Bayes, and Support Vector Machines.

Many joke-themed subreddits exist on Reddit, but 5 were chosen for comparison in this project: Jokes (just any kind of joke), DadJokes (e.g. "hi Hungry, I'm Dad"), MommaJokes (e.g. "yo momma so... she must have..."), CleanJokes (jokes with no racism/profanity/sexual themes), and DirtyJokes (jokes with racism/profanity/sexual themes). We make three main comparisons: Jokes vs Dad Jokes, Jokes vs Momma Jokes, and Clean Jokes vs Dirty Jokes.

Overall, logistic regression and support vector machines were the best predictors. We attain 76% accuracy in classifying Jokes vs DadJokes, over 92% accuracy with Jokes vs Momma Jokes, and over 81% accuracy with Clean Jokes vs Dirty Jokes.


The "code" folder of this project should be eplored in the following order: 

1) "1-webscraping": this is where the requests library and pandas are used to retrive data from Reddit.com using the pushshift api https://github.com/pushshift/api

2) "2-eda": This is where most of the data cleaning happened (dropping columns, cleaning null values, exploring size and datatypes).

3) "3-modeling": This is where all of the models were created and fit. There are three main sections, Jokes vs DadJokes, Jokes vs MommaJokes, and CleanJokes vs DirtyJokes. Within each of these sections, two or more models were created and scored.

4) "4-plots": This is where I created final bar charts for the presentation slides. 



# Data Dictionaries
Three datasets were created, cleaned, and used for modeling. They include jokes_v_dadjokes, jokes_v_mommajokes, and clean_v_dirty. 


|Feature|Type|Dataset|Description|
|---|---|---|---|
|**title**|*object*|all three|The title of the subreddit submission.| 
|**selftext**|*object*|all three|The body of the subreddit submission.|
|**is_dadjoke**|*integer*|jokes_v_dadjokes|0 if the submission is from /r/Jokes, 1 if the submission is from /r/DadJokes.|
|**is_mommajoke**|*integer*|jokes_v_mommajokes|0 if the submission is from /r/Jokes, 1 if the submission is from /r/MommaJokes.|
|**is_dirtyjoke**|*integer*|clean_v_dirty|0 if the submission is from /r/CleanJokes, 1 if the submission is from /r/DirtyJokes.|



# Conclusions

Jokes with standard phrasing are easier to classify, as in the Jokes vs MommaJokes case. The definition of a "dad joke" is not well defined, and thus distinguishing between a dad joke and just any joke (a submission from /r/Jokes) was more difficult. Also, interestingly enough, stemming and lemmatizing didn’t really help much with our model's performance, and sometimes even hurt it. 


In the future, it would be great to incorporate comments form reddit into the model, and to explore exactly which jokes were misclassified. Ultimately, the goal would be to create a multiclass model that would accept all joke subreddits, rather than analyzing just two at a time.




