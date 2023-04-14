# Reddit NLP (Natural Language Processing) Analysis

## Background

Reddit is a social media website that functions as a network of individual communities called subreddits. These subreddits cover topics ranging from any topic, and content is submitted through individual posts on the subreddit. The voting system is divided into upvotes and downvotes, each signalling if the community largely finds something agreeable or interesting. With enough interest, the post can be seen through the main website feed, which is sorted by highly popular or upvoted content. The foundation of each post is the title, body text (contains links and images as well), and comment chains, that people submit through online usernames.

In this project, we will be analyzing data from two subreddits:

1. [r/TalesFromRetail](https://www.reddit.com/r/TalesFromRetail/) (640k members): This subreddit talks about experiences from employees working in retail. The posts are mainly negative and largely refers to "Karens", people who are known for being entitled and demanding to others in a public environment.

2.  [r/raisedbynarcissists](https://www.reddit.com/r/raisedbynarcissists/) (714k members): This subreddit is a support group for people who had abusive and toxic parental figures. Posts range from personal history to questions and discussions regarding a user's personal life.

---

## Problem Statement
The aforementioned subreddits were chosen because both of them focus on negative experiences with specific people in their lives. The two subreddits also have a similar amount of activity. However, there is a large difference between the two as TalesFromRetail deals with one time interactions with strangers while raisedbynarcissists deals with longer and intimate history between family members. While “Karens” are known for being openly obnoxious and disliked by the public, narcissistic parents can be publicly beloved figures. This juxtaposition between public and private abuse led to a question if there was a connection between the two groups.

The main goal of this project is to see what type of vocabulary is seen in both subreddits in order to create a classification model that can predict the subreddit a piece of text comes from. Do Karens and narcissistic parents share any overlap in personality?


---

## Analysis Summary
CountVectorizer was used in order to identify the vocabulary seen in both subreddits. This allowed for a better list of stop words for the classification models. 

Notable top words in r/TalesFromRetail: store, customer, manager, work, people, lady

Notable top words in r/raisedbynarcissists: mom, feel, parents, dad, life, mother, family, years.

Both subreddits had a significantly higher use of female nouns.

TfidfVectorize was used for model prediction. The models used were LogisticRegression, KNeighborsClassifier, and RandomForestClassifier. A large problem found within the data is that model performance was heavily skewed by the "min_df" parameter that dealt with items that appeared too infrequently. The lower the min_df, the higher the cross val score, up to a 99% accuracy. Much of the project was spent so that specific words did not have too much impact. As the min_df was increased, the number of columns and relevant words plummeted.

Given equal pipelines, LogisticRegression gave the highest accuracy of 91%. RandomForestClassifer gave 90% and KNeighborsClassifier gave 72%.

---

## Conclusion
The project was inconclusive in finding a major connection between the two subreddits. A large attributor to this was due to both subreddits having unique vocabulary and slang. When these select words were taken out of the model, there were no significant outliers that would indicate similarities.

However, the data did show that both subreddits had more female gender nouns. r/TalesFromRetail had about 20% more references while r/raisedbynarcissists had up to 50% more. The latter also had significantly more slang related to mothers. Both subreddits also had a roughly equal amount of references to money.

---

## Recommendations
While the majority of the analyzed text gave limited information in their stories, a portion gave details on age and demographic. Additional work can be done in order to analyze posts specifically with this kind of detail in order to provide a better picture of the abusers. One possible route is to look at comments from the original poster for additional data.

However going forward there might not be enough data to indicate a connection, especially since the TalesFromRetail subreddit only provides personal estimations on the abusers. That being said, age and demographic extraction in the raisedbynarcissists subreddit alone may be worthwhile.
