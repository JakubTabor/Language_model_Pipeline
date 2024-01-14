# [Example 1: Language model spacy](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Language_Processing_Pipeline_Spacy.ipynb)
# Language_Processing_Pipeline_Spacy

# In this example I gonna use some technics to preprocess text in English and Spanish
* First I "import spacy" and create **(nlp object with English as language)** and with blanc pipeline, so without any tools
* Then i load to my nlp object **(trained small model(with few thousand en. words))**
* I check the tools of my model and see that my pipeline is **(full of useful tools)**

# Then i gonna put a text into my nlp object and start (for loop for every token in my object)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/doc1.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/doc0.png)
* It will print first the token, then description and then base word
* Token is each word, then **(pos describe part of speech)** np. Verb, Num, Noun, Pron
* lemma take word and change into base word np. eats into eat.

# Next I gonna take another text with some useful words
* I also start for loop for each word in my doc, **(printing first word, then label and it explanation)**
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/doc2.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/doc_0.png)
* So I have printed word, next it label **(np. Date, Gpe, Location, Money)** and finally explanation of my label **(np. GPE | Countries, cities, states)**

# I can also print it in a good looking way using (displacy) from spacy
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/displacy_doc.png)
* To do this i use function **(render on my doc and i choose style ent)**
* It gonna mark the most important informations, make them visible
* And nice describtion **(displacy.render(doc, style = "ent"))**

# I can load also (trained small model in Spanish language), as (es_core_news_sm)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/doc_es.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/es_displacy.png)
* I change my text into spaninh version and start (for loop on it)
* It's not yet perfect but it catch some informations
* Because it's small model trained on lesser number of words

# Then to my blank pipeline i gonna add solo (ner) and put this same text as previous to process
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/text1.png)
* I gonna put with names of persons and names of cities
* The task of my model will be to extract exactly this informations from the text
* So I load (small model in english), put text into model and create empty list for (proper nouns)  
* Next I start for loop on my text, condition is simple
* If part of speech is equal to (PROPN) this words will fill my list
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/proper_nouns.png)
* I also print this words and number of them 

# I take another text with companies and create empty list for company names
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/text2.png)
* Then I start for loop on my text with condition **(that if word have label ORG)**
* It will fill out my list and also print out the names of the companies and their numbers
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/company_finder.png)
#
#
#
#
# [Example 2: word embeddings in spacy](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/spacy_word_embeddings_excercise.ipynb)
# First i gonna preprocess text which is in json format, then train different model with it and finally make measurement and visualize results
# This will be preprocessing phase
* I start from checking if there is a class imbalance, but we have perfect class balance

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_word_embed/class_balance.png)

* Next i encode my classes into numbers, i gonna need fully numerical data
* Then i load large model from spacy trained on english words
# And create function that will put the text into the doc, it is nlp object
* Next it iterate through the tokens, removing **stop words and punctuation**
* And it will fill the list with the rest base tokens
* I apply this function on my data and see that it simplified the text
# Next i will do vectorization of the text to make it full numerical
* I create this vectors in separate column and it will be create from (preprocessed_text column)
* After vectorization i can create (train and test sets) from the already numerical data
* So the (x will be vector column with access to values) and (y will be the label column)
* Next using numpy i gonna stack first X_train and next X_test, they are now 2D data, as we can see the shapes has changed
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_word_embed/shapes.png)
# Then i can train a couple of models and see the results
* I start with DecisionTreeClassifier, score is not so good

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_word_embed/decision_tree_report.png)

* We get average accuracy 70% and f1-score for (1 and 2 class are 0.68 and 0.72)
# Next i gonna try MultinomialNB, but first i need to scale my data into (0 - 1 range)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_word_embed/multinomialNB_report.png)
* And i train this model with scaled data and i can see that the score is pretty good
* I get average accuracy 0.83 and for f1-score (for 1 and 2 class are 0.81 and 0.81)
# Another model will be KNeighborsClassifier
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_word_embed/KNeighborsClassifier_report.png)
* After training the score i even higher than in previous model
* Average accuracy appears 0.86 and f1-score is (for 1 and 2 class are 0.86 and 0.87)
# And the next model will be RandomForestClassifier
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_word_embed/RandomForest_report.png)
* Score is very similar to the previous model 
* It is the average score 0.87 and for f1-score is (for 1 and 2 class 0.86 and 0.87)
# I also want to try GradientBoostingClassifier on this data
* And i train the classifier with this data
* I reach the best accuracy at this point, its average accuracy 0.89 and f1-score (for 1 and 2 class 0.89 and 0.90) 
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_word_embed/GradientBoosting_reprot.png)
# I also prepare confusion_matrix for the best classifier
* And plot it in seaborn, the diagonal is true prediction and rest is false prediction

#
#
#
# [Example 3: FastText text classification](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/FastText_Text_Classification.ipynb)
# In this example i gonna use Ecommerce dataset to classify products
* I start from preprocessing, so i droping duplicated rows, simplified the labels and make it more visible 
* Then i create function that use regular expressions to clean text from signs

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_fastText_classification/preprocess_function.png)

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_fastText_classification/preprocessed_example.png)

* Make the lower cases and make the text clear and readable
* Then i take the merge column with (label and description of the product) and use on it preprocess function
# Now when my text is preprocess and clear i can create train and test sets
* And i convert it into a format that is proper for the fasttext model
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_fastText_classification/train_test_to_csv.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_fastText_classification/label_description.png)
* Then i train and test the model, score that i achieve is high
# Next i put some phrases into the model for predictions
* From the descriptions of predict it return the label of product and certainty score
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_fastText_classification/model_prediction.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_fastText_classification/model_prediction2.png)
* All predictions are correct and certainty score is high, so the model is well behaved and very certain
* I also call my model to return me the most similar words to given word
* It return words from the patterns that it learned with certainty score

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_fastText_classification/model_neighbors.png)

#
#
#
# [Example 4: Stop words](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Stop_Words.ipynb)
# 
# In this exercise i gonna be working with stop words 
* First i load **small model in english, which i assign to nlp** and put a **text into nlp object, i assign it doc**
* Then i **call functionality is_stop, it means that if token is stop word**, then do something   
* And we print this stop words tokens, **they don't add any new context to the meaning of given text**

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_Stop_Words/token_stop.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_Stop_Words/tokens.png)

# Next i create preprocess function, which take given text and remove all stop words
* In list comprehension i define that **if token from given text is not stop word and punctuation**, it says that we don't want this type of tokens
* And then we align them and convert into string instead of list
* And we see that all stop words are moved, we get pure informations

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_Stop_Words/preprocess_function.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_Stop_Words/function_text.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_Stop_Words/function_text2.png)

# I load dataset, which contain informations and i take only this with topic, rest i ignore
* And i **apply my preprocess function on 4 row, column contents**
* Number of words are changed from **5504 to 4217**

# Next i gonna create function which count number of stop words in the given text and return their percentage
* I start from setting **2 variables for counts (total and percentage) to zero**
* Then i **start for loop for every token in text and if it is stop word token it will fill the list of stopwords tokens**
* And all words will fill also total words list
* Next i print the stop words count as well as percentage of all stop words in given text

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_Stop_Words/stop_words_function.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_Stop_Words/num_of_stop_words.png)

# Then i **create function that will take a text and remove stopwords, i check if it can recognise negative and positive context**
* So i define that it **return me token that are not stopwords and join all remaining text**
* But i must specify that in this context **word 'not' is not a stopword**
* And we se that after specification it is able to recognise this 2 contexts 

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_Stop_Words/stop_words_function.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_Stop_Words/num_of_stop_words.png)

# Next i create function that will recognise word that appear the most
* First i create list for tokens, which are not stop or punctuation 
* And make for loop where i specify that if token is stopword or punctuation it will be ignored
* And any other tokens will just fill the list
* Next i create dictionary for the token with the most occurence
* I start a for loop for the previous list of tokens and **also exclude from text ('\n' - new line, and ' ' - space)**
* And i specify, that if token with most occurence is not already in the dict. it will appear, frequency_tokens[token] = 1
* Otherwise it will just add, frequency_tokens[token] += 1
* And then after the loop i assign that the token with most occurrence by taking max from our dictionary

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_Stop_Words/max_frequency_token.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_Stop_Words/max_frequency_word.png)

#
#
#
#[Example 5: BERT text classification](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Text_Classification_BERT.ipynb)
# In this exercise i gonna be creating BERT model for text classification
* First i can see, that i have class imbalance in my dataset, ham category is much bigger
* I gonna make them equal to the lower class, so i take only finepart of ham emails and that concatenate both classes

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/imbalance.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/concatenation.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/balance.png)
