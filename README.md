# DBL-Challenge-JBG000-Final

## Airline Tweet Analysis - easyJet

### Overview
This repository hosts scripts and Jupyter notebooks dedicated to the analysis of tweets concerning various airlines, with a special focus on easyJet. The project aims to extract meaningful insights from tweet data, such as customer sentiments and conversational dynamics, to assess the performance of easyJet's Twitter support team and decide whether they should be retained or replaced.

### Repository Structure

- **File 1**:
  - Contains exploratory data analysis (EDA) on airline tweet datasets focusing on frequency, sentiment distribution, and interaction patterns.

- **File 2**:
  - Scripts for sentiment analysis using VADER and additional context with NLP libraries. It also includes visualization scripts to illustrate sentiment over time and by topic.

- **File 3**:
  - Notebooks for deep analysis involving topic modeling and trend analysis over specific periods.

- **data_ingestion**:
  - Scripts for data ingestion and preprocessing, including SQL queries for extracting and organizing data from tweets.db and conversations.db.
  - 
### Repository Structure

- **Data Ingestion and Preprocessing**:
  - Scripts for fetching, cleaning, and preparing data. These scripts handle the extraction of tweets, normalization of text, and structuring data into `tweets.db` and `conversations.db`.

- **Sentiment Analysis**:
  - Implementation of sentiment analysis using VADER and BERT-based models to gauge public sentiment from tweets. Includes detailed sentiment tracking over time and across various service aspects.

- **Data Visualization**:
  - Jupyter notebooks that generate visualizations to depict trends in sentiment and response times, providing a visual assessment of service quality and public perception.

- **Topic Modeling**:
  - Notebooks dedicated to uncovering prevalent themes and topics within the tweet data, using advanced NLP techniques like LDA and BERTopic for deeper content analysis.

- **Utilities**:
  - Helper modules that facilitate database interactions, text processing, and common data manipulation tasks required across multiple scripts.



### Getting Started

#### Prerequisites
- Python 3.8 or higher
- CUDA-compatible GPU for deep learning models (optional but recommended for BERT-based models)
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

#### Installation
Clone the repository and install the necessary packages:
```bash
git clone <repository-url>
cd DBL-Challenge-JBG000-Final
pip install -r requirements.txt
