# Adv-Morphology---Affixal-Rivalry-ed-y
This is an end of semester project for the class Advanced Morphology at the University Paris Cite'.

The aim of this project is to investigate the affixal rivalry between the ending -ed and -y in English. According to the paper by Nagano (2022), there exists a purely semantic affixal rivalry between these two endings in the denominalized adjectives, created from English concrete nouns. This project aims to investigate the findings from Nagano (2022) by using the distributional methodology. 

There are three experiments in this project. The first one is to calculate and compare the difference vectors between the two affixes to see if they are semantically comparable or not, using the examples given by Nagano in the paper. The two affixal process are seen as semantically comparable if the distributional vectors of the processes are cosine similar. Because cosine similarity is in the range of [-1, 1] with -1 as totally different and 1 as totally similar, we believe that a similarity of around 0.5 would suffice to prove that the two affixal processes are semantically similar. The 76 examples given by Nagano are first converted to vectors by using the Google News 300 pre-trained Word2Vec model. Then the difference vectors are calculated using the roots and their derivations. Finally, the difference vectors of the two affixal processes are averaged, then compared to each other using cosine similarity. If the two processes are rivals, then the two difference vectors should be similar. 

The second experiment is to train a classifier on these difference vectors, then test the classifier on unseen data, in this case the data from UniMorph. The training data from Nagano is converted into a set of roots and labels. The roots are labeled "0" if having a "-ed" derivation, and "1" if "-y". The roots are then vectorized, then the training data is fed into a feedforward Neural Network model with one hidden layer. The model is trained for 100 epochs, with the training data is shuffled and splitted into 10 folds during each epoch to make the best use of the limited training data. After training, the model is used to predict the derivation of a test set created from UniMorph English data. The test set has 4192 examples, but only 3875 are kept because the other words are not present in the Word2Vec model. The hypothesis is that there exists affixal rivalry between "-ed" and "-y" if the prediction accuracy is around 50%, or in other words, the classifier cannot make an accurate prediction.  

The third experiment is applying the retrofitting algorithm from Faruqui (2015) on the word vectors, then calculate the difference vectors again. The hypothesis is that if the two affixal processes are differentiated purely on semantics, there should be some changes in the difference vectors after retrofitting.

The result of the three experiments were generally in line with the hypotheses. The first experiment produced a similarity score of 0.4162, which is 3.18 times higher than the similarity between two random word vectors. The second experiment produced an accuracy score of 49.146% with 100 training epochs and 10 fold, and 56.662% with early stopping mechanism implemented. The third experiment slightly improved the similarity score of the two difference vectors to 0.495, and this is the result of a few substantially improved examples and many slight reductions. These results suggested that the two affixal processes of _-ed_ and _-y_ are rivals, and they might be semantically differentiated, which are in line with the findings from Nagano (2022).