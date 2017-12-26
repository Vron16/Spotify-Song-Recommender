# Spotify-Song-Recommender

The Spotify Song Recommender is based on a Databricks Notebook, which uses Scala and Spark to process a JSON file that contains all the songs in a user's selected playlist.

The JSON file from Spotify's Web API is first converted into a single-line JSON file that can be processed by Spark. A dataframe is constructed from this JSON file and accordingly altered so that a dataframe containing only the track IDs of every song in the playlist remains. 

The track IDs are then inputted into Spotify's Web Console, which returns another JSON file containing the audio features of each of those tracks. The audio features are displayed in a Databricks pie chart in order of the frequency they appear in songs on the playlist. This allows us to construct a general portrait of the dominant audio features of the playlist.

Using Spark's capability of measuring the correlation between various features, the correlation of each feature with every other feature is measured. From this, the recommender uses Spark's API to construct a logistic regression model that can determine whether or not a song will be liked or disliked. 

Ultimately, the model can be tested by inputting a playlist that is then studied by the code to determine its primary audio features. When a certain genre or another playlist of songs is introduced to the software, it performs logistic regression to identify which ones are most likely to be liked (recommended) and which ones are less likely (are not recommended). This can be stored in its own JSON file. 
