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
# [Example 5: BERT text classification](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Text_Classification_BERT.ipynb)
# In this exercise i gonna be creating BERT model for text classification
* First i can see, that i have class imbalance in my dataset, ham category is much bigger
* I gonna make them equal to the lower class, so i take only finepart of ham emails and that concatenate both classes

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/imbalance.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/concatenation.png)

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/balance.png)

# And of course i convert ham and spam column into numerical form, for ham - 0, spam - 1

# Then i can create train and test sets, specifying that the number of sample must be equal for y (stratify = df balanced['spam']))
* And i download 2 BERT modules for preprocessing and encoding

# Next i create function in which i use these 2 modules, it will help me first to get preprocessed text and next to get embedding vector
* First i put preprocess module and sepecify a place for sentence, it will preprocess given sentence
* Then i apply encoder on preprocessed text and we can call the model and put sentences
* As an output we get these probability vectors from -1 to 1

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/BERT_uncased.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/sentence_embedding_function.png)

# Now i gonna put inside my function some phrases and check their cosine similarity
* It measure similarity between two non-zero vectors, so we have all we want, we just need to supply vectors indexes
* We can see that similarity between **(banana and grapes is higher - 0.99)** and **(between banana and jeff bezos is lower - 0.84)**, so everything works fine
* We can see that certain groups of words are arranged close to the other, banana and grapes re much likely to appear in same text than banana and Jeff Bezos
* But sometimes unrelated words appear in same text on which model is trained, thats why similarity is much higher than we expect

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/vectors_from_words.png)

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/cosine_similarity1.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/cosine_similarity2.png)

# Now i gonna create neural network using BERT combined with keras layers
* We start from passing input layer, shape will be figure out manually, data type is string, so we are gonna pass as an input some text
* Then we pass our BERT layer which preprocess these given text
* And net as previous the layer for vectorization

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/Model.png)

# Now after BERT layer i put some normal layers
* One is dropout layer, which just drop 0.1 of give neurons, its for purpose of not overfit the model
* And next is output layer, with normal sigmoid activation
* I save it as a model, which take text input for preprocessing, its first part
* And in the next part is the vector is given to remaining keras part of neural net
* I call summary on my model to get all informations about it, i can see that number of parameters is (109,483,010), but only 769 are trainable  

# Then i can pass all metrics, it will help me track my model progress during training
* I pass also parameters to compile my model and save metrics
* It will be adam and binary_crossentropy, these are the most popular parameters

# Next i train my model with 10 epochs, which contain batches of examples 
* I can see loss decay during training and rest of parameters are rising
* Then after evaluation i can see that metrics are very similar to training state

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/model_metrics.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/model_evaluation.png)

# Next i can see how visually looks predictions of my model 
* So i supply to the confusion_matrix true and predicted results
* And then use matplotlib to see on diagonal matrix all results
* We can see on plot that we have true class and true-false as well as in predicted class
* 170 right and 17 true-false, then 165 right predicted and 22 false-predicted

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/confusion_matrix.png)

# Now i gonna call classification_report on true and predicted class
* I can see that f1-score for both classes is similar, so i don't have any imbalance and more it is very high 
* So my model is very unlikely to make false predictions

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/classification_report.png)

# And then i gonna put some reviews and check if my model can predict to which class they belong
* As we can see, first 3 are spam text and next 2 are likely to be true messages
* And we see that we get on 3 first very high probability score and on other 2 very low probability

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/reviews_%20for_prediction.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_BERT_model/predicted_reviews.png)

# Next i can save my model for future development

