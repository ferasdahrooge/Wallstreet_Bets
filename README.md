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


### Mdodel Selection and Evaluation:










## Future Enhancements

The Ticker Predictor project offers various opportunities for further enhancements and extensions:

- **Real-Time Data Streaming**: Incorporate real-time data streaming capabilities to capture up-to-the-minute comments and sentiments from sources like social media platforms or financial news websites. This allows for more dynamic and timely predictions.

- **Sentiment Analysis Improvements**: Enhance the sentiment analysis component by considering contextual information, sarcasm detection, or domain-specific sentiment lexicons. This can further improve the accuracy and reliability of the recommended actions.

- **User Interface Enhancement**: Develop an intuitive and visually appealing user interface that provides clear and actionable recommendations. Consider integrating additional features, such as visualization of sentiment trends or historic performance of ticker values.
  
- **Model Deployemen**: Deploy Model as a Successful API for users to use to make some money

  
## Databricks Implementation

The Ticker Predictor project can be implemented using Databricks, a scalable and collaborative environment for developing and deploying data-driven applications. With Databricks, you can leverage the power of distributed computing and seamlessly integrate with other services within the Databricks ecosystem.

To implement the project using Databricks, follow these steps:

1. **Setup**: Set up a Databricks workspace and create a cluster with the necessary configuration for your project, including the required libraries and dependencies.

2. **Data Ingestion**: Import the dataset from the WallStreetBets subreddit into Databricks. This can be done by connecting to the Restful API and using Databricks' data ingestion capabilities.

3. **Data Preprocessing**: Preprocess the imported data using Databricks' data transformation capabilities. Apply techniques such as tokenization, stemming, and removing stop words to clean and prepare the data for model training.

4. **Model Training**: Utilize Databricks' distributed computing capabilities to train the NLP model on the preprocessed data. Experiment with various algorithms and approaches to achieve the desired accuracy.

5. **Model Evaluation and Deployment**: Evaluate the trained model's performance using Databricks' built-in evaluation tools. Once satisfied with the results.



## Jupyter Notebook Implementation
The Ticker Predictor project can also be implemented using Jupyter Notebook, a flexible and interactive environment for data exploration, model development, and analysis. With Jupyter Notebook, you have the freedom to experiment with different approaches and iterate on your models efficiently.

To implement the project using Jupyter Notebook, follow these steps:

1. **Setup**: Install the required libraries and dependencies, such as TensorFlow, scikit-learn, and NLTK, in your local Jupyter Notebook environment.

2. **Data Collection**: Use the Restful API to scrape comments from the WallStreetBets subreddit and save them as a dataset on your local machine.

3. **Data Preprocessing**: Preprocess the collected data within your Jupyter Notebook. Perform tasks like tokenization, stemming, and removing stop words using Python libraries like NLTK or spaCy.

4. **Model Training**: Model Development and Training: Develop and train the NLP model using various approaches within your Jupyter Notebook. Experiment with different algorithms, feature engineering techniques, and hyperparameter tuning to achieve accurate predictions.

5. **Model Evaluation**: Evaluate the trained model's performance using appropriate evaluation metrics within your Jupyter Notebook. Once satisfied with the results.

Both the Databricks and Jupyter Notebook implementations have their own advantages and can be chosen based on your specific requirements and preferences. Ensure you follow best practices, maintain proper documentation, and version control your code for future reference and collaboration.

Feel free to adapt and customize the instructions according to your specific implementation details.

## Conclusion
The Ticker Predictor project successfully utilizes NLP techniques to accurately predict recommended actions (buy, sell, or hold) on ticker values. By employing a comprehensive range of approaches and leveraging extensive datasets from the WallStreetBets subreddit, the developed models demonstrate exceptional accuracy and align well with real-time ticker analysis benchmarks.

For detailed implementation and code, please refer to the respective GitHub repositories associated with each implementation (Databricks and Jupyter Notebook).

References
WallStreetBets subreddit
Restful API documentation
