# Real_Estate_Reddit_Web_Scraping

Forecasting Mortgage Rate and Scraping/Analyzing the "RealEstateInvesting" Subreddit</br></br>
A house shaped word cloud. I was having some fun.The past month I watched the 30-year Fixed Mortgage Rate almost hit 4%. Back in 2008, the mortgage rate hit above into 6% territory. I was curious about using some machine learning tools to predict what the mortgage rate will be based on historical data.</br></br>
Additionally, with all the real estate hype, I wanted to check out if there were any buzz words going on in the Real Estate Investing Subreddit. I ended up scraping the last 2 years' worth of comments with the keywords "buy" and "sell" to see what popped up.</br></br>
I first wanted to see the 30-year fixed mortgage rate forecasted. I threw the kitchen sink at the chart in terms of the ML tools I had available to me. I did the following predictions and the number of months calculated:</br></br>
ARIMA model prediction - 24 months</br></br>
LSTM (Long-Short term memory) neural net prediction - 30 months</br></br>
Facebook Prophet forecasting tool - 36 months</br></br>

Here are the results:</br></br>

LSTM Prediction - 30 months. Looks like it will hover around 3%–4%</br></br>
![LSTM_Prediction_30months](https://user-images.githubusercontent.com/62908910/156170155-c115a12e-f74c-4afa-83bb-f73726d97c53.PNG)
</br></br>

![FB_Prophet](https://user-images.githubusercontent.com/62908910/156170206-92e0cf5c-f39b-4dc8-8a75-e32c805cfe8d.PNG)
</br></br>
Facebook Prophet prediction shows something similar but much less variation for 36 months</br></br>

For ARIMA model, I had to detrend the data first to induce stationarity. Follow along below for the de-trending. Just note that the rate looks like it will spike in the short term.</br></br>
![Trend_Breakdown_Residuals](https://user-images.githubusercontent.com/62908910/156170255-7f3ef2a9-1bca-451d-932b-eb7f0c74c4b3.PNG)
</br></br>
First we have the trend breakdown and residuals. The huge spike was from the Nixon era.</br></br>

![Detrending_the_Data_1](https://user-images.githubusercontent.com/62908910/156170385-02cbc30b-ea4c-4f61-8fc0-b5176f99eb2f.PNG)
</br></br>
Detrending step #1 - Log transform the data</br></br>

![Detrending_the_Data_2](https://user-images.githubusercontent.com/62908910/156170407-366096d2-8fbd-448a-85ed-ec9129a11051.PNG)
</br></br>

Detrending step #2 - differencing the log transformed values - This induced stationarity and I was able to fit an ARIMA modelThe detrended prediction shows it will spike, but return to some middle line trending slightly upwards. I'll need to do more ARIMA modeling with different de-trending steps as future work.</br></br>


Now, we go scrape the subreddit "Real Estate Investing"</br></br></br></br>


The tool I used to scrape was PushShiftApi. A HUGE shoutout to Douglas Mill's sentiment analysis of the WallStreetsBets Subreddit for this portion of the project. Thanks Doug!</br></br>
I did the following:</br></br></br></br>
Scrape "Real Estate Investing" subreddit for key words "buy", "sell", and "mortgage"</br></br>
Create word clouds based on the data to see what popped up</br></br>
Run VADER sentiment analysis on the words and do word counts</br></br>

Here is what I found:</br></br>
"BUY" Keyword:</br></br>

![Buy_Body_wordcloud_high_number_of_words](https://user-images.githubusercontent.com/62908910/156170646-cd474b32-8f7b-4d89-85c8-58894c52004a.PNG)
</br></br>

Comment body Wordcloud for keyword "buy"</br></br>

![Buy_Author_wordcloud_high_number_of_words](https://user-images.githubusercontent.com/62908910/156170735-30437782-6268-4709-9727-9792086c3c49.PNG)
</br></br>

Author wordcloud for keyword "buy"</br></br>

"SELL" keyword</br></br>

![Sell_Body_wordcloud_high_number_of_words](https://user-images.githubusercontent.com/62908910/156170851-6fca641c-2d0c-434c-a467-e80a718c8783.PNG)
</br></br>

Comment body Wordcloud for keyword "sell"</br></br>

![Sell_Author_wordcloud_high_number_of_words](https://user-images.githubusercontent.com/62908910/156170866-a5d4cc4b-6f16-4881-9e0f-a846f1589095.PNG)
</br></br>

Author wordcloud for keyword "sell""MORTGAGE" Keyword:</br></br>
![Mortgage_Body_wordcloud_high_number_of_words](https://user-images.githubusercontent.com/62908910/156170888-8b7e4d06-21f9-45ee-bb8e-77cba9dcc47c.PNG)
</br></br>


Comment body Wordcloud for keyword "mortgage"</br></br>
![Mortgage_Author_wordcloud_high_number_of_words](https://user-images.githubusercontent.com/62908910/156170953-ce538415-b1ea-4c47-bd57-d85120347ea9.PNG)
</br></br>


Author wordcloud for keyword "mortgage"</br></br>


VADER Sentiment Analysis of Scraped Data:</br></br>

![BUY_BODY_SENTIMENT](https://user-images.githubusercontent.com/62908910/156170992-4ac84dd7-e1c3-4329-a659-cd3ca904d39f.PNG)
</br></br>

"BUY" Keyword in comment body shows mostly positive sentiment</br></br> 
![BUY_BODY_SENTIMENT_COUNTS](https://user-images.githubusercontent.com/62908910/156171015-7029b90a-fa20-4b88-913f-99f02f249baf.PNG)
</br></br>


Word counts of each category for "BUY" keyword</br></br>

![SELL_BODY_SENTIMENT](https://user-images.githubusercontent.com/62908910/156171050-ab13b218-8b6a-4c30-b19a-ee8f8ffeb05c.PNG)
</br></br>

"SELL" Keyword in comment body also shows mostly positive sentiment</br></br>

![SELL_BODY_SENTIMENT_COUNTS](https://user-images.githubusercontent.com/62908910/156171066-15d7c2b8-5d15-43fc-9b49-4e2c2be3b9c2.PNG)
</br></br>

Word counts of each category for "SELL"</br></br>



keyword"MORTGAGE" </br></br>

![MORTGAGE_BODY_SENTIMENT](https://user-images.githubusercontent.com/62908910/156171107-785acf73-d3c8-4d5a-829c-8318ba84c511.PNG)
</br></br>

Keyword also shows mostly positive sentiment. I'm guessing the word counts will reflect the same.</br></br>

![BUY_BODY_COMMENTS_COMMON_WORDS](https://user-images.githubusercontent.com/62908910/156171148-0db2f3d4-bad3-4788-a586-56d5ad7b0f67.PNG)
</br></br>

Common words wordcloud amongst the "BUY" keyword for positive and negative posts</br></br>


![SELL_BODY_COMMENTS_COMMON_WORDS](https://user-images.githubusercontent.com/62908910/156171170-aafc2d65-6703-4093-99f9-e2f1401a08d4.PNG)
</br></br>
Common words wordcloud amongst the "SELL" keyword for positive and negative posts</br></br>

WHEW! That was a fun project. Thanks again Doug, for showing me how you scraped the Wall Street Bets subreddit! There was so much future work I wanted to do here. I wanted to use LinkedIn Greykite for another ML forecast to add to the charts. I wanted to keep tinkering with different LSTM models from another library other than Keras. I also want to do more with the reddit comments. I feel like I only scratched the surface of NLP sentiment analysis. I'm really curious to try out IBM's Watson emotional tone analyzer on the reddit comment section.
Other than that, I am not satisfied with the ARIMA model. I want there to be more spikes and such. I'll have to revisit how I fitted the data and my detrending method and tinker around with the parameters.
Overall, my curiousity is satisfied…..for now.
