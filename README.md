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
- There was only a minor class imbalance. 810 unpopular values, 302 popular values.
![class](Readme%20Images/popvsunpop.png)

## Feature Exploration
### Feature Importance
- Found that mode (whether a track is in a major or minor key) did not have importance in this model. However, I felt it would be important to incorporate later considering whether a key is major or minor has a large impact of the feeling of a song so I decided to use it later to engineer a new feature.
![class](Readme%20Images/mode.png)
- The feature of Speechiness (a way to detect whether a track is spoken word such as  a podcast episode, a part of a comedy album, or a rap) was also fount to have little importance and tracks tended towards 0 (little confidence that it is a spoken word track). This plus the fact there isn’t much spoken word in rock, I dropped this value.
![class](Readme%20Images/speech.png)

### Feature Engineering: Mood
- Using mode and key I created a feature called Mood
- Depending on whether a key has a traditionally brighter or darker feeling it is categorized as light or dark. 
- Example: Key = C and Mode = 0 (major) → Converted to 1 meaning it has a bright mood 
- I used my domain knowledge in music theory as well as several listening  observation to test this feature out and then referenced the songs in the dataset and their new mood values to see if my classifications were correct.
![class](Readme%20Images/feateng.png)

### Feature Correlation
- Dropped loudness from the dataframe since loudness and energy were highly correlated with a corrrelation coefficient of 0.773175	
![class](Readme%20Images/corr.png)

### Feature Distribution
- Generally normal distribution for Danceability, Track Energy, and duration in the set.
- Most Tracks have a low Acousticness, Instrumentalness and Liveness
![class](Readme%20Images/featuredist.png)

## Classification Algorithms
### Logistic Regression
- The Confusion Matrix only predicted True Negatives (unpopular songs) and did not predict Popular songs. Because of this not a good model.
![class](Readme%20Images/logregmatrix.png)
- Not able to calculate these in a helpful way because only accounts for and predicts unpopular songs.
![class](Readme%20Images/logregscore.png)
- Though the testing accuracy was 100% it wasn't a good model since it only predicted true negatives.

### Decision Trees
- There were many more False Negatives (says not popular, but actually popular) than True Negatives (not popular but actually popular)
- Better at predicting unpopular songs than popular songs.
![class](Readme%20Images/decitreeconfus.png)
- Testing Accuracy for Decision Tree Classifier: 71.94%
![class](Readme%20Images/dectreeacc.png)
- Performed Adaboost to increase accuracy but there was little to no difference when run

### Bagged Trees
- There were many more False Negatives (says not popular, but actually popular) than True Negatives (not popular but actually popular)
- Better at predicting unpopular songs than popular songs.
![class](Readme%20Images/baggedmatrix.png)
- Testing Accuracy for Bagged Tree Classifier: 73.02%
![class](Readme%20Images/baggedscore.png)
- Performed Adaboost to increase accuracy but there was little to no difference when run

### Random Forests
- There were many more False Negatives (says not popular, but actually popular) than True Negatives (not popular but actually popular)
- Better at predicting unpopular songs than popular songs.
![class](Readme%20Images/randformatrix.png)
- Testing Accuracy for Decision Tree Classifier: 71.94%
![class](Readme%20Images/randforscore.png.png)
- Performed Adaboost to increase accuracy but there was little to no difference when run

### Grid Search CV
- Only predicted True Negatives (unpopular songs) and False Negatives (says not popular, but actually popular) and did not predict True Popular songs. Because of this not a good model.
![class](Readme%20Images/gridmatrix.png)
![class](Readme%20Images/gridscore.png)
- Testing Accuracy for Grid Search: 72.30%

## Conclusions
- Decision Trees  produced the most relevant model.  Though it had the lowest accuracy at 72 %, it predicted the most true negatives (unpopular songs) as well as the most true positives.  
- All models were better at predicting unpopular songs than popular songs.
- In the future, I would like to either redefine the parameters of popularity or gather more data on popular songs for a more balanced collection more songs and create a larger dataset to possibly get a more accurate model and take care of the class imbalance.

