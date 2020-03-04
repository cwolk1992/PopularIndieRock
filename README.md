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
- This became my target variable

## Feature Exploration
### Feature Importance
- Found that mode (whether a track is in a major or minor key) did not have importance in this model. However, I felt it would be important to incorporate later considering whether a key is major or minor has a large impact of the feeling of a song so I decided to use it later to engineer a new feature.
- The feature of Speechiness (a way to detect whether a track is spoken word such as  a podcast episode, a part of a comedy album, or a rap) was also fount to have little importance and tracks tended towards 0 (little confidence that it is a spoken word track). This plus the fact there isn’t much spoken word in rock, I dropped this value.

### Feature Engineering: Mood
- Using mode and key I created a feature called Mood
- Depending on whether a key has a traditionally brighter or darker feeling it is categorized as light or dark. 
- Example: Key = C and Mode = 0 (major) → Converted to 1 meaning it has a bright mood 
- I used my domain knowledge in music theory as well as several listening  observation to test this feature out and then referenced the songs in the dataset and their new mood values to see if my classifications were correct.

### Feature Correlation
- Dropped loudness from the dataframe since loudness and energy were highly correlated with a corrrelation coefficient of 0.773175	

### Feature Distribution
- Generally normal distribution for Danceability, Track Energy, and duration in the set.
- Most Tracks have a low Acousticness, Instrumentalness and Liveness



