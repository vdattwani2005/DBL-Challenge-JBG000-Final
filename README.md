# DBL-Challenge-JBG000-Final

## Airline Tweet Analysis - easyJet

### Overview
This repository hosts scripts and Jupyter notebooks dedicated to the analysis of tweets concerning various airlines, with a special focus on easyJet. The project aims to extract meaningful insights from tweet data, such as customer sentiments and conversational dynamics, to assess the performance of easyJet's Twitter support team and decide whether they should be retained or replaced.

```diff
+ Code for DEMO is in Visualisations folder
```

### Repository Structure

- **EDA, Database Creation, Preprocessing**:
  - This is done in the folder `Database Creation + Conversation Mining` and `Exploratory Data Analysis (EDA)`.
  - Scripts for fetching, cleaning, and preparing data. These scripts handle the extraction of tweets, normalization of text, and structuring data into `tweets.db` and `conversations.db`.

- **Sentiment Analysis**:
  - Implementation of sentiment analysis using VADER to gauge public sentiment from tweets. Includes detailed sentiment tracking over time and across various service aspects.

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
