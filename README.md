# I set out on this project to achieve the following goals:
* Obtain all of my streaming data from Spotify and featurize it using the spotipy API
* Build a classifier using pycaret to accuractely predict liked songs in my streaming history (potentially for a reccomendation system)
* Perform some EDA on my streaming history to discover historical top genres and artists
* Cluster the top genres and artists using NLP techniques (word2vec) and using simple PCA on the featurized dataset
<br>

## The results are as followed and can be seen in more detail in the notebooks
### 1) Obtaining data and linking
Succesfully downloaded all streaming data and extracted features, genres, etc. using the spotipy API to build a master dataset
<br>
### 2) Building Classifier

![image](https://user-images.githubusercontent.com/52717506/147284986-a712c687-efd2-4e2f-981b-9dee303ebf71.png)

The results show how difficult is to classify a liked songs vs not liked songs; most importantly it shows how difficult it is to classify or reccomend a liked song based on the features available in the spotify api.
Nonetheless this is consistent with my experience with spotify. There are many weeks when I do not like any of the songs pushed to me spotify's discover weekly playlists. Songs that I chose to like are exceedingly rare. There are many songs that I enjoy to have on, but don't actualy click the liked button, because my threshold for songs I want to save is very high.
The best classifier was one that was trained on the synthetic dataset (supplmental synthetic samples were added to balance the classes) with an accuracy of 0.74, but a precision of 0.17. Precision was the metric I was focused on because I want the classifier to be able to reliably find songs that I will like. This is a very difficult task, but nonetheless a preicion of 0.17 could be reliable enough. This could mean finding a song i like for every 5-6 songs reccomended, which is actually quite good. Aneetodcelty, this would be an improvement on Spotify's discover weekly reccomendations
My reccomendations for future work would be futher testing for model robustness, deploying the model in a production environment such as flask, focus on feature engineering, and finding additional features that may have better predictive power than the ones used here.

<br>
### 3) Basic EDA

![image](https://user-images.githubusercontent.com/52717506/147285061-ec906a96-0adc-497a-8532-54291083a8ba.png)

![image](https://user-images.githubusercontent.com/52717506/147285103-4fc9907c-1e35-4294-bf2b-a16889496186.png)

<br>

### 4) NLP Clustering using word2vec vs PCA on average features
I obtained some very interesting results for this part. I had a difficult time finding quality clusters using the averaged features for each dataframe; my hypothesis is that my streaming history is already so similar that it is difficult to seperate artists and genres. Nonetheless, using word2vec to cluster genres proved to quite effective as you can  see from the following plots. Plot 1 is clustering based on word2vec and plot2 is using the average features.
### word2vec clustering

![image](https://user-images.githubusercontent.com/52717506/147285398-cb93bcc4-5073-41a1-8546-b6d2d3e1131d.png)

### average features clustering

![image](https://user-images.githubusercontent.com/52717506/147285407-749fd08c-c082-4eda-b265-7eab74d781e3.png)

The results for clustering on artists were different that for genres. In this instance, the average df feaures were better at seperating clusters.
### word2vec clustering

![image](https://user-images.githubusercontent.com/52717506/147285479-4ebe24e8-5afc-4304-a7e2-7ea8a18c04f1.png)

### average features clustering

![image](https://user-images.githubusercontent.com/52717506/147285493-5410f28d-a00b-4491-bb65-f11ca62620d6.png)



