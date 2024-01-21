# [Example 1: Language processing in spacy](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Language_Processing_Pipeline_Spacy.ipynb)
# I use spacy to first tokenize and then describe each part of token
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/doc_0.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/doc2.png)
* I also put full phrases that contain different part of speech (LOC, MONEY, GPE, DATE...)
* Next i check if it woark in different languages (Epanish)
# And also i put text that contain (names and nouns)
* Then i write function that extract this information from the text and count number of them

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/text1.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images/proper_nouns.png)

#
#
#
# [Example 2: Word embeddings in spacy](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/spacy_word_embeddings_excercise.ipynb)
# I use pure python to first tokenize and then convert text and classes into numerical form
* Text is first preprocess, it mean that it change to simplified version
* Then i change this text into vector form and also scale it into range 0-1
* I **convert train and test sets into two-dimensional**

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_word_embed/shapes.png)
# Then i train couple model with this data and check their performance
* Scores are different for each model, its because these model work different with multi-dimensional data
* The best model is GradientBoostingClassifier
* I reach with it average accuracy 0.89 and f1-score 0.89 - 0.90

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_word_embed/GradientBoosting_reprot.png)

#
#
#
# [Example 3: FastText text classification](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/FastText_Text_Classification.ipynb)
# I use FastText model for text classification
* First i convert description of product into proper form for the FastText model
* I create function that remove signs, white spaces and make the lower cases

![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_fastText_classification/preprocess_function.png)

# Then i train FastText model and reach high accuracy
* Now i can use my model to check predictions and functionalities
* I put a text with description of a product to my model
* And it return me label of a product and certainty score
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_fastText_classification/model_prediction.png)
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_fastText_classification/model_prediction2.png)

# And then i use functionality (get_nearest_neighbors) on a product name
* It return me most similar words to give word with certainty score
* All words are taken by training process, so they seems to be unrelated
* Because its relation between words build by model and in this way it's correct
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
