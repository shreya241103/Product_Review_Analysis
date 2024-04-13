

## Overview
The goal of this project is to analyze reviews for a product by using an api and then generating a list of features as required by the customer.

## Approach

Our approach consists of three main parts:

## 1. User Feature Set Extraction:

### Load Survey Data:
- Read CSV file (survey_responses.csv).
- Convert string representations to dictionaries.

### Extract 'Love' and 'Hate' Values:
- Define function (extract_values) to extract 'love' and 'hate' values.
- Create separate DataFrames for 'love' and 'hate' values.

### Preprocess Data:
- Drop null rows.
- Filter positive and negative reviews.
- Convert text to lowercase.
- Tokenize and filter stopwords, non-alphabetic characters, and short words.
- Lemmatize words focusing on nouns.
- Filter out single-word entries.

### Create Dictionary and Matrix:
- Create dictionaries to map words.
- Generate document-term matrices for 'love' and 'hate' data.

### Train LDA Models:
- Train LDA models for 'love' and 'hate' data.
- Generate topic dictionaries for each user.
- Print and visualize topics.

## 2. Product Feature Set Extraction:

### Feature Extraction:
- Extract 'love' and 'hate' features from survey responses, stored in dictionaries.

### Data Preprocessing:
- Drop null rows from 'love' and 'hate' DataFrames.
- Normalize textual data to lowercase.
- Tokenize text into individual words for processing.
- Remove stopwords, short words, and non-alphabetic characters.
- Lemmatize words to their base form, focusing on nouns.
- Retain only nouns for substantive meaning.

### Document-Term Matrix Creation:
- Construct a document-term matrix representing term frequencies within each document.

### LDA Topic Modeling:
- Construct LDA models for 'love' and 'hate' DataFrames to uncover topics.
- Print identified topics from LDA models.

### Visualization:
- Use PyLDAvis to visually represent identified topics for interpretation.

## 3. Recommendation System Using Customer & Product Features

### Custom Preprocessor Function:
- Define custom_preprocessor function to remove punctuation and convert text to lowercase for vectorization.

### Load Customer Data:
- Implement load_customer_data function to read customer data from a CSV file and store it in a dictionary. Each key represents a customer identifier, and the corresponding value contains 'Love Value' and 'Hate Value' attributes.

### Calculate Cosine Similarity:
- Develop calculate_cosine_similarity function to compute cosine similarity between customer and topic vectors using TF-IDF vectorization.

### Find Most Relevant Topic:
- Create find_most_relevant_topic function to iterate through each customer's data, calculate cosine similarity between their preferences and each topic's love and hate features, and select the topic with the highest similarity as the most relevant topic for the customer.

### Generate Description:
- Implement generate_description function to generate a description for each customer based on the love features of the most suitable topic.

### Calculate Score:
- Develop calculate_score function to calculate a score indicating how well the customer fits with the chosen topic based on the cosine similarity between their preferences and the love features of the topic.

### Write Results to CSV:
- Implement write_to_csv function to write the results (customer identifier, most relevant topic, description, and score) to a CSV file.



##LDA MODEL: 

LDA is a generative probabilistic model used for topic modelling, a technique for discovering abstract topics that appear in a collection of documents.
We have utilised the LDA model to identify the product features set and user features set. 

For the product feature set, we have identified 10 topics for both love and hate sentiments.
For the user features set, we have found 1 topic for each user to represent their preferences.

Topics founds for product from love reviews:


<img width="1411" alt="Screenshot 2024-04-13 at 12 55 47 AM" src="https://github.com/Moumitha120104/G2/assets/115857097/37589bd2-88d6-4033-a803-a1d03a802832">




Topics founds for product from hate reviews:


<img width="1397" alt="Screenshot 2024-04-13 at 12 56 07 AM" src="https://github.com/Moumitha120104/G2/assets/115857097/c978e6cc-4e0f-4fe4-a04f-0b1dda967fd6">




PyLDAvis plot for visualisation:


<img width="1312" alt="Screenshot 2024-04-13 at 12 56 43 AM" src="https://github.com/Moumitha120104/G2/assets/115857097/4c341d85-d410-4b0d-8a04-ce98f7548721">





Each bubble in the above figure represents a topic. The larger the bubble, the higher percentage of the number of reviews in the corpus is about that topic.
Blue bars represent the overall frequency of each word in the corpus
As we can see from the image below, there are about 400 occurrences  of the word ‘go’, and this term is used about 150 times within topic 1.
The word with the longest red bar is the word that is used the most by the tweets belonging to that topic.


The output entails mapping the user feature set with the product feature set to assess the likeness between customers and the product. This is achieved by identifying similarities between product topics and customer topics.


<img width="828" alt="Screenshot 2024-04-13 at 1 01 43 AM" src="https://github.com/Moumitha120104/G2/assets/115857097/489b3934-5a1e-43b9-835c-40295f1d125d">





Conclusion : 
This project efficiently utilizes natural language processing to extract customer preferences from product reviews, facilitating targeted recommendations. With clear setup instructions and transparent file descriptions, it offers a user-friendly framework. Collaborative contributions and acknowledgments underscore its reliance on established libraries. Overall, it's a concise yet effective tool for deriving actionable insights from customer feedback.


Contributors
PRARTHANA P BHAT
SHREYA KASHYAP
R S MOUMITHA
## Acknowledgements
This project uses techniques from natural language processing and topic modeling. Special thanks to the NLTK, Gensim, and scikit-learn libraries for providing tools for text processing and topic modeling.
