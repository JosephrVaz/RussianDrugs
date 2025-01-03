# Russian Illegal Drug Review Sentiment Classification

# Dataset
This dataset contains russian illegal drugs reviews and its overall sentiment, either positive or negative. It was sourced from the darknet marketplace Hydra. This dataset only has 1200 rows and 2 columns, one for the review and the sentiment denoted as -1 (negative) or 1 (positive). 

# Goal
The goal is to create a robust text classification model that correctly classifies the reviews. This model will be helpful for law enforcement agencies to analyze for intelligence purposes 

# Use Cases
Drug Quality Monitoring: Law enforcement can analyze reviews to assess the quality of drugs being sold, helping to identify potentially dangerous substances and take action to protect public health.

Seller Surveillance: The model can help track and monitor sellers on illegal marketplaces, identifying those with consistently negative reviews and potentially harmful products.

Trend Analysis: By analyzing the sentiment of drug reviews over time, law enforcement can identify emerging trends in drug use and distribution, allowing them to allocate resources more effectively.

Intelligence Gathering: The model can provide valuable insights into the operations of illegal drug markets, helping law enforcement agencies to understand the dynamics of these markets and develop targeted strategies to combat them.

Early Warning System: By monitoring reviews for sudden spikes in negative sentiment, law enforcement can quickly identify and respond to new, dangerous drugs entering the market.


# Models
Random Forest Classifier with a spacy pipeline
Text Categorizer

# Preprocessing
- Removed stop word
- Removed punctuation
- Removed numbers 
- Lemmatization 
- Tokenization (for ml model only)

# Training
We load the Russian spacy model. For the ml model , we process and tokenize the text. Then in a spacy pipeline we choose TF IDF as the vectorizer and random forest classifier as the classifier. We split the data with a test size of 0.2.  Hyperparameter tuning for ml model, we test the effect of different depths and estimators.
For the spacy model, we set up the textcat with a single label cnn with a custom configuration. The embed_size being set is 4500. Add the labels positive and negative. Convert the dataframe into the format spacy can use. Put it through the training loop with no dropout. Hyperpaarmeter tuning for spacy model, with test the effect of different batch sizes and dropouts.

# Results
The ML model has a test accuracy of 84 and a train accuracy of 92 percent, indicating overfitting. After hyperparameter tuning the test accuracy increased to 85 percent if there were 200 estimators and a depth of 20. The spacy model had a test accuracy of 83 and a train accuracy of 100, indicating overfitting. After hyperparameter tuning test accuracy increased to 84 if dropout was 0.3 with a batch size of 32. Both model f1,recall and precision were well within range of each other and balanced. Hyperparameter tuning seemed to help the model increase its accuracy but still the root cause was not fixed. The root problem of overfitting was caused by the limited amount of data in the dataset. If we used SMOTE or acquired more data, results would have been higher with no overfitting.  Performance wise, ML model was faster in execution and training compared to the spacy model. This is most likely due to configurations that were initialized in the configurations in the text categorizer. Overall, if the problem of overfitting is solved by oversampling, both models will be suitable for the given task of classifying drug reviews.

## License
This project is licensed under the Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International (CC BY-NC-ND 4.0) License. See the [LICENSE](./LICENSE) file for details.

