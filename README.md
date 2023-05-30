# Language_Processing_Pipeline_Spacy
Here I gonna use some cool technics to preprocess text in English and Spanish
# First I "import spacy" and create nlp object with English as language and with blanc pipeline, so without any tools
# Then i load to my nlp object "trained small model(with few thousand en. words)" 
# Now I check the tools of my model and see that my pipeline is full of useful tools
# I gonna put a text into my nlp object and start for loop for every token in my object, it will print first the token, then description and then base word
# Token is each word, then "pos" describe part of speech np. Verb, Num, Noun, Pron. "lemma" take word and change into base word np. eats into eat.
# Now I gonna take another text with some useful words, I also start for loop for each word in my doc, printing first word, then label and it explanation
# So I chave printed word, next it label np. Date, Gpe, Location, Money and finally explanation of my label np. "GPE | Countries, cities, states"
# I can also print it in a good looking way using "displacy" from spacy, I use function render on my "doc" and I choose "style ent"
# It gonna mark the most important informations, make them visible and good describe "displacy.render(doc, style = "ent")"
# I can load also "trained small model in Spanish language" "es_core_news_sm", I change my text into spaninh version and start for loop on it
# It's not yet perfect but it catch some informations
# Now to my blank pipeline I gonna add solo "ner" and put this same text as previous to process
# I gonna put with names of persons and names of cities, the task of my model will be to extract exactly this informations from the text
# So I load "small model in english", put text into model and create empty list for "proper nouns"  
