# Analysis of Public Opinion on Autonomous Vehicles

### Overview
The notion of self-driving cars dates back to 1939, when General Motors unveiled the first AV model at the World's Fair. A radio-controlled electromagnetic field-guided electric car prototype that ran on magnetised metal spikes buried in the road. This approach was ultimately adopted in 1958.
Since then, R&D in the field of autonomous cars has steadily improved; the revolution in this sector began in 2003, when Tesla was formed. This industry, however, confronts several problems. The most important is ensuring that the vehicles perform safely and effectively in an uncertain environment.

This is a constantly growing field, with hundreds of innovations being introduced on a regular basis; some of them succeed, while others fail, resulting in mishaps; as a result, it has become a contentious topic, with numerous public perceptions linked with it.
The general public may now convey their views and thoughts on any issue more easily than ever before, thanks to the growing popularity of microblogging sites such as Twitter, Instagram, and Reddit. This analysis aims to detect various points of view by collecting and analysing data about autonomous vehicles from Twitter.


### Data Collection
Initially, I thought of using Twitter's API for collecting the tweets, but soon got to know that it has a limitation of fetching only the last 3200 Tweets unless the user is registered as a researcher. So, I ended up using [Twint](https://github.com/twintproject/twint).

Twint is an advanced Twitter scraping tool written in Python that allows for scraping Tweets from Twitter profiles without using Twitter's API.
Twint utilizes Twitter's search operators to let you scrape Tweets from specific users, scrape Tweets relating to certain topics, hashtags & trends, or sort out sensitive information from Tweets like e-mail and phone numbers.
Twint also makes special queries to Twitter allowing you to also scrape a Twitter user's followers, Tweets a user has liked, and who they follow without any authentication, API, Selenium, or browser emulation.

I gathered public Tweets over the last four months that included any or all of the following keywords and hashtags: "#selfDrivingCar", "#autonomousCar", "#Auton- omousVehicles", "Autonomous Vehicles", and "self driving car". I was able to retrieve 35,476 Tweets in total, the oldest of which was dated December 2nd, 2021.


### VADER

The nature of content on microblogging platforms, such as Twitter and Facebook, presents substantial challenges to practical implementations of sentiment analysis.
These difficulties originate from the massive number of user-generated social media information, as well as the contextual sparsity caused by the length of text and the usage of slang and emoticons.
[VADER](https://github.com/cjhutto/vaderSentiment), or Valence Aware Dictionary and sEntiment Reasoner, is a sentiment analysis tool that is rule and lexicon-based, and it is tuned in to social media sentiments.
It has proved beneficial for analysing social media attitudes since it works well with lingo and emoticons.

VADER derives four sentiment measures from word grading. The first three, positive, neutral, and negative, address the scope of the material falling into those categories.
The compound score, the final metric, is the total of the lexical grades, which have been harmonised to range from – 1 to 1.
I used VADER's SentimentIntensityAnalyzer function to return the compound value of all tweets and generated a new column named "sentiment" with the strings "Positive," "Negative," or "Neutral" based on the compound value.


### Files

#### dataset.csv

This contains the scraped data that I collected for the analysis. 
It contains 35475 rows and 36 columns.

#### twint_dataset.ipynb

This is the python notebook with code for using twint to collect the data from Twitter.

#### analysis.ipynb

This is the python notebbok with code for the complete analysis.
It includes data reading, cleaning, tokenization and lemmatization, using VADER's sentiment analyzer and finally generating graphs and wordclouds.
