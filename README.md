# FellowshiAI - Building AgNewsTextClassifier

### Introduction
Our task is to classify the News (a free text field) into their specific classes. The dataset is provided by Fast.AI. It contains 4 difference classes of the news. Also, there are other two columns, i.e., Title and Description. Hence, this problem can  be best solved as Multilabel Text Classification.

### My approach
1) I have combined the train and test data and checked for the duplicates.
2) I checked the distribution of the classes and we found there is no skewness.
3) No duplicates value found in the entire dataset
4) I combined both text field and description field into one column, 'full_text'.
5) Then, I performed the preprocess of the full_text column by creating a function which will clean the data such as remove extra spaces, remove puncutation or special characters, etc. I also did the stemming opertaions to get only the root word and then remove all the stop words in english language.
6) After the processing, I stored the data in a pickle format, as it takes lot of times to run the process till point 5.
7) For model building part, I used Contextual Augmentation logic - Word2Vec, and embedded the layer in Kears model layers. 
8) The best accuracy with good model performance on confusion matrix is found with word2vec parameter as: vector_size=50, workers=32, min_count=1, window=2
![image](https://user-images.githubusercontent.com/38045473/144970369-4160563a-a2b7-4d94-a2e0-31543f0ee6b1.png)

### Conclusion
- I found that with different embedding parameters, we were able to get the better accuracy of the model with the validation accuracy=92%.
Also, the validation loss is better i.e. 0.24
- Overall, as it is a mutilabel classification problem, accuracy is not the standard as it may give us false positive or false negative results. So, we looked at the confusion matrix to determine our model performance. We found out that our model has performed pretty good in identifying TRUE positive and TRUE negative classes as it can be seen diagonally on the above confusion matrix with following correct values:
    - ClassI: 5156; ClassII: 5615; ClassIII: 5961; ClassIV: 5344;
    - ClassI TrueNegative: 5615+38+106+35+5961+29+213+159+5344=17500
- There are few false positive and false negative results as well for ex:
    - ClassI: FalseNegative: 628+53+120=801; FalsePositive: 236+24+283=543

### Future work
- We can run with just title or with just description column and check if our model performance improved or not.
- We can use other transfer learning approach such as ULMFiT to further improve the model performance and reduce the false false negative or false positive error rate.
- I did tried ULMFiT model, but due to the insufficient resources available on my Google Colab, not able to finished running it. I will try to update it later over here once I am able to find a turnaround of resource contraint.




 
