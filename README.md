# Sentiment Analysis: NLP

In this project, we are going to import the latest news articles from an open source, applying natural language processing(NLP) to understand the sentiment in the articles. There are three main parts where we can see the  sentiment scores of each article in the first stage. After that, we will find out what are the common words and phrases that frequently appear along with the topic by preprocessing the articles using fundamental NLP techniques. Finally, we are to build a Named Entity Recognition(NER) model to visualize what specific entities could be identified in all the articles.     


## Sentiment Analysis

We used the Newsapi to pull the latest news articles, in particular, for **Bitcoin** and **Ethereum** to create each Dataframe. We tried to pull the articles by calling all headlines, however, we ended up with using `get_everything` instead as there had not been a sufficient number of headlines pertaining to those keywords. We limited the number of articles up to a hundred each. 

We had to take out some redundant articles for 'bitcoin' after having recognized there had been a series of erroneous words taking place in the top frequency. We found out there were 14 articles duplicated in the result, dropping them out to have 87 articles remained in the dataframe.

>#### Statistics of Bitcoin Sentiment 

![](https://github.com/coolwonny/Sentiment_Analysis_NLP/blob/master/Images/bitcoin_score.png)


   
>#### Statistics of Ethereum Sentiment  

![](https://github.com/coolwonny/Sentiment_Analysis_NLP/blob/master/Images/ethereum_score.png)

>#### Which coin had the highest mean positive score?

  Ethereum did with a mean positive score of 0.064

>#### Which coin had the highest compound score?

 Ethereum had the highest compound score at 0.859

>#### Which coin had the highest positive score?

 Again, ethereum had the highest positive score at 0.28.   

## Frequency Analysis

In this section, we used **NLTK** and **WordCloud** to preprocess and visualize the texts to see what are the common words and phrases. For preprocessing, we went through tokenizing the text into words by using `word_tokenize()`, removing the punctuation and non-alphabetical characters by using regex compiler `re.comile('[^a-zA-z]')`, lemmatizing words into root words by using `WordNetLemmatizer()` and filtering out the stopwords by setting `set(stopwords.words('english'))`. We also did lowercase each word while doing the preprocessing.

Following the process, we generated N-grams counter to see in details what pairs of words appeared frequently. Here we used bigrams(N=2). The most common pair of words for bitcoin were 'twitter' and 'account' with 21 times frequency out of 87 articles, while 'char' and 'ethereum' pairs placed on top for ethereum with 10 times of frequency from 97 articles. Below are the top-10 results from each keywords and its wordcloud, respectively.

> #### Bitcoin   
[(('twitter', 'account'), 21),   
 (('high', 'profile'), 18),   
 (('elon', 'musk'), 16),   
 (('char', 'twitter'), 11),   
 (('bill', 'gates'), 10),   
 (('barack', 'obama'), 10),   
 (('profile', 'account'), 7),   
 (('joe', 'biden'), 7),   
 (('bitcoin', 'scam'), 6),   
 (('profile', 'twitter'), 6)]      
     
![](https://github.com/coolwonny/Sentiment_Analysis_NLP/blob/master/Images/wc_bitcoin.png)   

> #### Ethereum   
[(('char', 'ethereum'), 10),    
 (('ul', 'li'), 9),   
 (('bitcoin', 'ethereum'), 8),   
 (('char', 'bitcoin'), 6),    
 (('li', 'li'), 6),   
 (('char', 'day'), 5),   
 (('day', 'ahead'), 5),   
 (('ahead', 'ethereum'), 5),   
 (('ethereum', 'would'), 5),   
 (('would', 'need'), 5)]    
    
![](https://github.com/coolwonny/Sentiment_Analysis_NLP/blob/master/Images/wc_ethereum.png)   
   
## Named Entity Recognition(NER)
Fianlly, we built a NER model for both coins and visualize the tags using `spacy`.

Here are the snapshots of the results:
>### Bitcoin   

![](https://github.com/coolwonny/Sentiment_Analysis_NLP/blob/master/Images/ner_bitcoin.png)


>#### Ethereum   

![](https://github.com/coolwonny/Sentiment_Analysis_NLP/blob/master/Images/ner_ethereum.png)

## Conclusion

Both keywords showed a neutral-biased sentiment overall. However, we found that ***Ethereum had more positive sentiment over negative*** while Bitcoin is the opposite. Will this imply that Ethereum gets more favor over Bitcoin in the cryptocurrency market? We may not determine it only based on this analysis as there were overwhelmingly more articles regarding bitcoin than ethereum when querying the newsapi.    

We can interpret the result of the top-10 words that bitcoin comes with more issue relating to Twitter and entrepreneurs like **Elon Musk**(showed up 16 times) and **Bill Gates**(10 times), together with politicians like **Barrack Obama**(10 times) and **Joe Biden**(7 times). This trend looks outstanding when comparing with that of ethereum's where the most common words were **Ethereum**, **Bitcoin** and **Char**, we could hardly find any other words relating to any economic and political features. This is an interesting finding that we might say ***Bitcoin seems more reflective of current social issues or more complexed in trend than ethereum***. Ethereum resonances with more technical and intrinsic keywords rather than current trend, according to the analysis of recent 100 articles.    

    
(Jupyter Notebook: [crypto_sentiment.ipynb](https://github.com/coolwonny/Sentiment_Analysis_NLP/blob/master/crypto_sentiment.ipynb))


