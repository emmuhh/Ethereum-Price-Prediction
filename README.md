# Natural Language Processing With Cryptocurrency
## Emma Steuer


### The purpose of this project is to predict cryptocurrency prices using natural language processing and machine learning. 

Over the summer, I spent some time learning about cryptocurrency and made a few investments, so when my Computational Linguistics professor announced that we could work on any sort of project we wanted to, I jumped at the chance to combine my curiosity of cryptocurrency/blockchain and natural language processing. I knew Twitter, Reddit, and news articles greatly skewed cryptocurrency prices, and I wondered if I could use natural language processing and the machine learning algorithms we had learned in class to predict swings in cryptocurrency prices. 

I started researching the topic to see if others had attempted this and it turned out many had. There are many research teams working on this and many hobbyists documenting their work online. There are myriad sources of opinion-based text data surrounding cryptocurrency—such as Twitter, Reddit, news articles and headlines—and historical cryptocurrency prices are public. I wanted to start building my project right away and knew I needed to test different methods and data points. 

I decided to start with Twitter. The platform is something I am quite familiar with, and I had read in research and heard from friends that cryptocurrency prices seem to correlate closely with tweets. Additionally, many researchers use Tweepy, Twitter’s official API. I assumed this would work best for my objectives; however, when I began to test it I soon realized it has many limitations. Tweepy has a free version open to anyone who applies for a developer license. After applying and trying out the search tweets function, I quickly realized it was unable to pull tweets from specific dates. After inputting the query to search for an n number of requested tweets, the free version of Tweepy only returns the n most recent query results. This was not effective to reach my objective. I needed something to pull n tweets between two dates. The paid versions of Tweepy allow this, but I decided to stick to free APIs and scrapers because I wanted to use the lean ideology: create a minimum viable product to gauge the feasibility of my hypothesis. (I included a file using Tweepy to pull and analyze data in order to show my understanding of how this API works.)

After more research, I discovered a homemade Twitter text scraper called SnScrape. It does not have much documentation, but after much internet searching and trial and error, I was able to create a function to pull tweets from each day between two specified dates. 

After pulling n number of tweets from each day in a specified date range, I created a function to clean and preprocess the tweets. This is necessary for any kind of text data analyzation, as the text needs to be uniform and free from unusual errors that might impact the data. After this, I created a function to add each tweet and certain data from each tweet to a data frame. I used TextBlob, a common text processing Python library, to determine the subjectivity and polarity of each tweet. The polarity of a piece of text is a float from -1 to 1, where 1 is completely positive and -1 is completely negative. The subjectivity of a piece of text data is a float from 0 to 1, in which 0 refers to personal opinion and 1 refers to an objective fact. Finally, I created a simple function to return a ‘positive’, ‘negative’, or ‘neutral’ string about each tweet using polarity. The subjectivity of a tweet and the function to determine whether a tweet is positive, negative, or neutral in natural language and its data is not used in this particular program, but will be more useful later when I analyze the data in different ways. After adding all this data to a data frame, I plotted the average subjectivity of each day’s tweets. 

Next, I needed to gather cryptocurrency prices. After much research and trying out different APIs, I landed on Crypto Compare. It is easy to use for historical cryptocurrency prices and simplifies the data for you, simply inputting any data you chose into a data frame. For this particular demonstration, I chose Ethereum, the last 30 days, and the closing price. I plotted these prices using a line graph. 

Finally, I created a new data frame containing only dates, polarity, and closing price of Ethereum. I then needed to decide upon the first machine learning algorithm I would use to test my hypothesis. I wanted to begin with a supervised learning algorithm because I wanted to input my labeled data, rather than unlabeled data where the algorithm would look for hidden patterns. Further, I wanted to find a regression algorithm, as these are often helpful in analyzing numerical data. After research, I landed upon random forest regression as the first algorithm to manipulate the data. I decided upon this algorithm for multiple reasons: it has a high accuracy, it still works well when some data is missing, and it works well when there is a lot of data. 

With that said, this model predicts the price of the currency against the polarity score of the tweets. I trained the model with an 80% train and 20% test split with 200 estimators. (Below this number the error rate was higher, and raising it above 200 did not seem to alter the results significantly.) After plotting and analyzing the results, the root mean squared error (RMSE) of the model ~60. With the average price of Ethereum being 4400 USD in the last 30 days, this gives ~1.5% error rates. 

There are multiple limitations to my project:

- The computer I work on outside of school does not have significant processing power. It often runs slowly when tasked with large dataset manipulation. This is why I chose to only pull ten tweets a day over only a 30 day span. Additionally, this project is only considered a minimum viable product. I do not want to spend time processing an enormous dataset only to get preliminary results. 

- I am only able to pull the most recent tweets from each day that I analyze, beginning at midnight each day. This is true for both Tweepy and the text scraper I am using. Preferably, data from each day should be random and not pulled at a certain time each day. 

If I had unlimited resources, I would:

- Search for at least 10,000 random tweets each day beginning in December 2020. (The prices started to soar in December 2020 and before then there was not much movement in the price of Ethereum, so prices that would remain stagnant prior to that date would skew the data.) I would filter out any tweets that were not in English. I want to have as many accurate and random data points as possible. 

- I would input all the closing prices from Ethereum starting in December 2020 until the current date. 

I have myriad next steps. I would like to analyze many different cryptocurrencies, add more features to my learning model such as number of retweets and likes for each tweet to see if these effect coin price, experiment with many different kinds of both supervised and unsupervised machine learning models, and be able to input many more data points. I would also like to attempt to predict future prices of cryptocurrencies based on the data I have gathered. Additionally, I would like to use more data in different ways. I plan to use the subjectivity of tweets to see if this data affects price points. Finally, I would like to see what kind of preprocessing techniques lead to the most accurate results. 

I left my API keys on the files so you can easily see my results and play around with my code if you wish. Please let me know if you would like to see more code or more writing examples. 


