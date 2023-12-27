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
![](https://github.com/JakubTabor/Language_model_Pipeline/blob/main/Images_fastText_classification/model_neighbors.png)
