# Twitter-Sentiment-Analysis
This .py script contains the sentiment analysis of any topic by parsing the tweets fetched from Twitter using Python, ML - Naïve Bayes and SVM. 

# About 
Sentiment Analysis is the process of ‘computationally’ determining whether a piece of writing is positive, negative or neutral. It’s also known as opinion mining, deriving the opinion or attitude of a speaker.

# Installation:

Tweepy: tweepy is the python client for the official Twitter API.
Install it using following pip command: pip install tweepy

TextBlob: textblob is the python library for processing textual data.
Install it using following pip command: pip install textblob

Also, we need to install some NLTK corpora using following command: python -m textblob.download_corpora

# Authentication:
In order to fetch tweets through Twitter API, one needs to register an App through their twitter account. Follow these steps for the same:
1. Open the Twitter  and click the button: ‘Create New App’
2. Fill the application details. You can leave the callback url field empty.
3. Once the app is created, you will be redirected to the app page.
4. Open the ‘Keys and Access Tokens’ tab.
5. Copy ‘Consumer Key’, ‘Consumer Secret’, ‘Access token’ and ‘Access Token Secret’.


# Theory

We follow these 3 major steps in our program:

1. Authorize twitter API client.
2. Make a GET request to Twitter API to fetch tweets for a particular query.
3. Parse the tweets. Classify each tweet as positive, negative or neutral.

TextBlob is actually a high level library built over top of NLTK library. First we call clean_tweet method to remove links, special characters, etc. from the tweet using some simple regex.
Then, as we pass tweet to create a TextBlob object, following processing is done over text by textblob library:

Tokenize the tweet ,i.e split words from body of text.
Remove stopwords from the tokens.(stopwords are the commonly used words which are irrelevant in text analysis like I, am, you, are, etc.)
Do POS( part of speech) tagging of the tokens and select only significant features/tokens like adjectives, adverbs, etc.
Pass the tokens to a sentiment classifier which classifies the tweet sentiment as positive, negative or neutral by assigning it a polarity between -1.0 to 1.0 .
Here is how sentiment classifier is created:

TextBlob uses a Movies Reviews dataset in which reviews have already been labelled as positive or negative.
Positive and negative features are extracted from each positive and negative review respectively.
Training data now consists of labelled positive and negative features. This data is trained on a Naive Bayes Classifier.
Then, we use sentiment.polarity method of TextBlob class to get the polarity of tweet between -1 to 1.
