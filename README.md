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

| column name | data type | description |
|-------------|------------|-------------|
| id_str | TEXT | Unique identifier for each tweet |
| created_at | TEXT | Timestamp when the tweet was created |
| in_reply_to_status_id_str | TEXT | ID of the original tweet that this tweet is replying to |
| in_reply_to_user_id_str | TEXT | ID of the user to whom this tweet is a reply |
| lang | TEXT | Language of the tweet |
| quote_count | INTEGER | Number of times the tweet was quoted |
| quoted_status_id_str | TEXT | ID of the tweet that was quoted |
| quoted_user_id_str | TEXT | ID of the user whose tweet was quoted |
| reply_count | INTEGER | Number of replies to the tweet |
| retweet_count | INTEGER | Number of times the tweet was retweeted |
| text | TEXT | Content of the tweet |
| truncated | BOOLEAN | Indicates if the tweet is truncated |
| user_id_str | TEXT | ID of the user who posted the tweet |
| possibly_sensitive | BOOLEAN | Indicates if the tweet may contain sensitive content |
| sent_vader | REAL | Sentiment score of the tweet (VADER analysis) |
| sent_label | INTEGER | Sentiment label of the tweet |



**table '_users_'**

| column name | data type | description |
|-------------|------------|-------------|
| id_str | TEXT | Unique identifier for each user |
| name | TEXT | Full name of the user |
| screen_name | TEXT | Username of the user on the platform |
| verified | BOOLEAN | Indicates if the user account is verified |
| followers_count | INTEGER | Number of followers the user has |
| profile_background_color | TEXT | Hex code for the background color of the user's profile |
| profile_link_color | TEXT | Hex code for the color of links in the user's profile |
| profile_sidebar_border_color | TEXT | Hex code for the color of the sidebar border in the user's profile |
| profile_sidebar_fill_color | TEXT | Hex code for the color of the sidebar fill in the user's profile |
| profile_text_color | TEXT | Hex code for the color of the text in the user's profile |
| profile_use_background_image | BOOLEAN | Indicates if the user uses a background image in their profile |
| profile_background_image_url | TEXT | URL of the background image used in the user's profile |
| profile_background_image_url_https | TEXT | HTTPS URL of the background image used in the user's profile |
| profile_background_title | TEXT | Title or description of the profile background image |
| profile_image_url | TEXT | URL of the user's profile image |
| profile_image_url_https | TEXT | HTTPS URL of the user's profile image |
| profile_banner_url | TEXT | URL of the user's profile banner image |
| default_profile | BOOLEAN | Indicates if the user is using the default profile layout |
| default_profile_image | BOOLEAN | Indicates if the user is using the default profile image |


**table '_extended_tweets_'**

| column name | data type | description |
|-------------|------------|-------------|
| id_str | TEXT | Unique identifier for each tweet |
| full_text | TEXT | Full text content of the extended tweet |
| display_text_range | TEXT | Range of the text to be displayed in the extended tweet |


**table '_extended_tweet_urls_'**

| column name | data type | description |
|-------------|------------|-------------|
| id_str | TEXT | Unique identifier for extended tweet |
| url | TEXT | URL included in the tweet |

**table '_extended_tweet_hashtags_'**

| column name | data type | description |
|-------------|------------|-------------|
| id_str | TEXT | Unique identifier for each tweet |
| hashtag | TEXT | Hashtag included in the tweet |

**table '_extended_tweet_user_mentions_'**

| column name | data type | description |
|-------------|------------|-------------|
| id_str | TEXT | Unique identifier for each  tweet |
| user_mention | TEXT | Username mentioned in the  tweet |

**table '_entities_'**

| column name | data type | description |
|-------------|------------|-------------|
| id_str | TEXT | Unique identifier for each tweet|
| hashtags | TEXT | List of hashtags associated with the tweet |
| urls | TEXT | List of URLs associated with the tweet |
| user_mentions | TEXT | List of user mentions associated with the tweet |



**table '_emb_tweets_'**

| column name | data type | description |
|-------------|------------|-------------|
| id_str | TEXT | Unique identifier for each tweet |
| norm_tweets | TEXT | Normalized text content of the tweet |
| sent_vader | REAL | Sentiment score of the embedded tweet (VADER analysis) |
| sent_label | INTEGER | Sentiment label of the embedded tweet (1=positive, 0=neutral, -1 = negative)|



#### 2. 'Conversations.db'


**table '_conversations_'**

| column name | data type | description |
|-------------|------------|-------------|
| conversation_id | INTEGER | Unique identifier for each conversation |
| root_tweet_id | TEXT | ID of the root tweet in a conversation |
| conversation_json | TEXT | JSON data containing the entire conversation thread |

**table '_filtered_conversations_'**

| column name | data type | description |
|-------------|------------|-------------|
| conversation_id | INTEGER | Unique identifier for each filtered conversation |
| root_tweet_id | TEXT | ID of the root tweet in the filtered conversation |
| conversation_json | TEXT | JSON data containing the filtered conversation thread |
| topic | TEXT | Topic or category of the filtered conversation |

*Note: The filtered conversations contain only the conversations which fit a specific definition of a conversation. This is, when it starts with a user, an airline responsds, and the user answers again.




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
