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
* I can also print it in a good looking way using (displacy) from spacy
* To do this i use function **(render on my doc and i choose style ent)**
* It gonna mark the most important informations, make them visible
* And nice describtion **(displacy.render(doc, style = "ent"))**

# I can load also (trained small model in Spanish language), as (es_core_news_sm)
* I change my text into spaninh version and start (for loop on it)
* It's not yet perfect but it catch some informations
* Because it's small model trained on lesser number of words

# Then to my blank pipeline i gonna add solo (ner) and put this same text as previous to process
* I gonna put with names of persons and names of cities
* The task of my model will be to extract exactly this informations from the text
* So I load (small model in english), put text into model and create empty list for (proper nouns)  
* Next I start for loop on my text, condition is simple
* If part of speech is equal to (PROPN) this words will fill my list
* I also print this words and number of them 

# I take another text with companies and create empty list for company names
* Then I start for loop on my text with condition **(that if word have label ORG)**
* It will fill out my list and also print out the names of the companies and their numbers

