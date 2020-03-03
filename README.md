# What makes an indie rock song popular?
## Can you predict if a song will be popular in the current musical landscape using audio analysis from Spotify?

## The Goal
to create as capable a classification model as possible  to identify a popular or unpopular indie rock song.

## My Original Dataset
### Data Sources: 
- Created a dataset of 1112 popular indie rock songs using Spotify’s top playlists classified as ‘indie’.
Ran the songs through the Spotify API for both Audio Analysis (track information) and Audio Features (track sound interpretation) and combined dataframes.

### Initial Dataset Features
Popularity, Duration, Acousticness, Danceability, Energy, Instrumenalness, Key, Liveness, Loudness, Mode, Speechiness, Tempo, Valance, Speechiness

## Target Variable 
### How do you define a popular song?
- To classify a track as popular or unpopular I used the popularity feature from Spotify’s database that contained integers 0 -100. My dataset had a range of 0 - 83. This popularity feature is calculated by an algorithm and is based on the total number of plays the track has had and how recent those plays are.
- Found that the top 25% of songs had a value of 56 or up.
- Created a new column called popularity_class to categorize this categorical data. 
- This became my target

##
