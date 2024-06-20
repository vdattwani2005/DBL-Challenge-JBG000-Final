# DBL-Challenge-JBG000-Final

## Airline Tweet Analysis - easyJet

### Overview
This repository hosts scripts and Jupyter notebooks dedicated to the analysis of tweets concerning various airlines, with a special focus on easyJet. The project aims to extract meaningful insights from tweet data, such as customer sentiments and conversational dynamics, to assess the performance of easyJet's Twitter support team and decide whether they should be retained or replaced.
The code creates SQLite databases (tweets.db and conversations.db) to store and manage the processed tweet data.

```diff
+ Code for DEMO is in Visualisations folder
- It contains timestamp given during the DEMO.
```

### Repository Structure
- **EDA, Database Creation, Preprocessing**:
  - This is done in the folder `Database Creation + Conversation Mining` and `Exploratory Data Analysis (EDA)`.
  - Scripts for fetching, cleaning, and preparing data. These scripts handle the extraction of tweets, normalization of text, and structuring data into `tweets.db` and `conversations.db`, SQLite databases created for storing tweet data and conversation details.

- **Sentiment Analysis**:
  - Implementation of sentiment analysis using VADER to gauge public sentiment from tweets. Includes detailed sentiment tracking over time and across various service aspects and some visualizations.

- **Data Visualization**: Folder `Visualisations `
  - Jupyter notebooks that generate visualizations to depict trends in sentiment and response times, providing a visual assessment of service quality and public perception. These maninly include the visualisations for the DEMO.

- **Topic Modeling**: In folder `Text Normalization + Topic Mining`
  - Notebooks dedicated to uncovering prevalent themes and topics within the tweet data, using advanced NLP techniques such as BERTopic for deeper content analysis. DISCLAIMER the model needs 6+ hours to run on a intel 12th gen i7 core and Nvidia gpu with 8.6 compute capabilities. 

- **Normalization**: In folder `Text Normalization + Topic Mining`
  - Normalization for the entire text in tweets.db, this was primarily used for topic modeling. DISCLAIMER the model needs 3+ hours to run on a intel 12th gen i7 core and Nvidia gpu with 8.6 compute capabilities.
- **Topic/Sentiment Insertion**: In folder `Text Normalization + Topic Mining`
  - inserts the topic model and sentiment analysis outcomes into the conversation database. It also computes the sentiment evolution score.


- **Model Statistics**: In `Performance`
  - Helper modules that facilitate database interactions and then check for accuracy and other stats related to the models bring used.

### Database structure
The code creates the databases 'tweets.db' and 'conversations.db' with the following structures.
#### 1. 'Tweets.db':
**table '_tweets_'**
|column name | data type |
|--- | --- |
|id_str|TEXT|
|created_at | TEXT |
| in_reply_to_status_id_str |TEXT|
|in_reply_to_user_id_str | TEXT|
|lang|TEXT|
|quote_count|INTEGER|
|quoted_status_id_str|TEXT|
|quoted_user_id_str|TEXT|
|reply_count|INTEGER|
|retweet_count|INTEGER|
|text|TEXT|
|truncated|BOOLEAN|
|user_id_str|TEXT|
|possibly_sensitive|BOOLEAN|
|sent_vader|REAL|
|sent_label|INTEGER|


**table '_users_'**
|column name | data type |
| --- | --- |
|id_str|TEXT|
|name|TEXT|
|screen_name|TEXT|
|verified|BOOLEAN|
|followers_count|INTEGER|
|profile_background_color|TEXT|
|profile_link_color|TEXT|
|profile_sidebar_border_color|TEXT|
|profile_sidebar_fill_color|TEXT|
|profile_text_color|TEXT|
|profile_use_background_image|BOOLEAN|
|profile_background_image_url|TEXT|
|profile_background_image_url_https|TEXT|
|profile_background_title|TEXT|
|profile_image_url|TEXT|
|profile_image_url_https|TEXT|
|profile_banner_url|TEXT|
|default_profile|BOOLEAN|
|default_profile_image|BOOLEAN|

**table '_extended_tweets_'**
|column name | data type |
| --- | --- |
|id_str|TEXT|
|full_text|TEXT|
|display_text_range|TEXT|

**table '_extended_tweet_urls_'**
|column name | data type |
| --- | --- |
|id_str|TEXT|
|url|TEXT|

**table '_extended_tweet_hashtags_'**
|column name | data type |
| --- | --- |
|id_str|TEXT|
|hashtag|TEXT|


**table '_extended_tweet_user_mentions_'**
|column name | data type |
| --- | --- |
|id_str|TEXT|
|user_mention|TEXT|

**table '_entities_'**
|column name | data type |
| --- | --- |
|id_str|TEXT|
|hashtags|TEXT|
|urls|TEXT|
|user_mentions|TEXT|

**table '_emb_tweets_'**
|column name | data type |
| --- | --- |
|id_str|TEXT|
|norm_tweets|TEXT|
|sent_vader|REAL|
|sent_label|INTEGER|


#### 2. 'Conversations.db'

**table '_conversations_'**
|column name | data type |
| --- | --- |
|conversation_id|INTEGER|
|root_tweet_id|TEXT|
|conversation_json|TEXT|
|in_reply_to_status_id_str|TEXT|

**table '_filtered_conversations_'**
|column name | data type |
| --- | --- |
|conversation_id|INTEGER|
|root_tweet_id|TEXT|
|conversation_json|TEXT|
|topic|TEXT|





### Getting Started

#### Prerequisites
- Python 3.8 or higher
- CUDA-compatible GPU for deep learning models (optional but recommended for BERT-based models and text normalization)
- Required Python packages (install using `pip install -r requirements.txt`):
  - pandas
  - numpy
  - matplotlib
  - seaborn
  - vaderSentiment
  - transformers
  - scipy
  - nltk
  - scikit-learn
  - sqlite3
  - torch with cuda driver
  - bertopic
  - sentence tranformer
  - spacy
  - tqdm

#### Installation
Clone the repository and install the necessary packages.

#### Correct order of files for complete run:
- 1- Database Creation + Conversation Mining, 2- EDA, 3- Text Normalization, 4- Sentiment Analysis - Topic Mining, 5- Topic/Sentiment Insertion, 6- Performance and Visualizations
