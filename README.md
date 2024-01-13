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
