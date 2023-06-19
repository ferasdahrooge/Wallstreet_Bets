# Wallstreet_Bets

This Project Known as Ticker Predictor is mainly an NLP Machine learning Project used to determine recommended actions for users who owns wallstreet tickers whether they should Buy/Hold/Sell their stocks based on the posts found on Wallstreet_bets subreddit based on data of the past 3 years 
This Project followed the following:

## Data Collection:

Starting off with collecting our data, we managed to Web Scrape our Data using PUSHSHIFT API based on post of the past 3 years (from Jan 1st 2019 - November 14th 2022)
the data was filtered based on 6 section: 'id', 'title', 'selftext', 'author', 'score', 'num_comments'
- id of the post
- Title of the post
- selftext which represents what did the author write about
- The author of the post
- The score of the post (upvotes / downvotes)
- num_comments which technically means the number of comments regarding that post

### Important Considerations were taken into account to avoid unnessecary posts such based on the mentioned sections:
- if Score > 100, then the post is uploaded by a human author to avoid bots
- Either the 'title' or 'selftext' must include a stock ticker based on the collection of tickers mentioned in the csv file.

- Initial Dataset: 1.5 million posts
- Filtering for Score: 55k posts
- Filtering for Ticker: 17k posts
    

### With some issues that were dealt with in this segment:
- PushShift API does not have updated ‘score’ ==> Use native Reddit API to update the ‘score’
- API was limiting our usage due to the large amount of data collection ==> Store data in pickle files (one for each day) so we could break the data collection into chunks/Make use of 4 different devices

## Data Labelling:

To ensure accurate specification for each sentence, manual labeling was employed to determine the main topic of the post and its sentiment.

- A total of 1,900 posts were selected randomly for manual labelling

### Issues and Solutions:

1) ambiguous underlying sentiment, making it difficult to correctly classify them
2) Stock tickers are the same as abbreviations that people often use online, as well as capitalized words that are not talking about stocks
3) Posts with multiple tickers + words that resemble tickers ==> Implementing clause separation. As well as NER (Named Entity Recognition) to determine the tickers and remove the common words 
4) Multiple obvious recommended action to classify the sentiment of the sentence
5) News articles with no other comments from posters ==> Nerutal Posts
6) Sarcastic Posts
7) Posts about daytrading analysis ==> Neutral Posts

### Data Preprocessing:

- The post title and body is combined to form the raw text
- Tokenization, followed by the removal of stop words and punctuation
- Special handling of emojis, certain special characters, and numbers
- Lemmatization to return the word into its original case


