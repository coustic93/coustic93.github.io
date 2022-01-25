# Music Genre Classification

The purpose of this project was to classify songs into different genres. The data is from Spotify which includes 17996 observations with 14 predictor variables and one response variable.
The predictor variables include: Popularity, danceability, energy, key, loudness, mode, speechiness, acousticness, instrumentalness, liveness, valence, tempo, duration, time signature
The response variable is the Genre.

The different genres that are predicted are:
  1. Acoustic/Folk
  2. Alternative Music
  3. Blues
  4. Bollywood
  5. Country
  6. HipHop
  7. Indie Alternative
  8. Instrumental
  9. Metal
  10. Pop
  11. Rock

## Exploratory Data Analysis
3 columns included missing values : popularity (428), key (2014), and instrumentalness (4377)
Popularity was imputed with the median, key was imputed with "Missing", and instrumentalness was imputed with the mean. 
Separate binary columns were also created to indicate that it was missing.

## Modeling
Four different models were used : Logistic Regression, Random Forest, XGBoost, and neural network (one layer).
After the four models were trained on the training data, Random Forest performed the best.
For example, the Random Forest was able to correctly classify all 15 Red Hot Chili Peppers(my favorite band) as Rock while for the Logistic Regression model, it classified some of the songs as metal and blues.

A random variable was also intrudced into the Random Forest model to check variable importance. 
The three most important variables were duration, acousticness, and speechiness.

![Variable Importance](/variableimportance.png)

The accuracy of the random forest model on the test data was 51.3% compared to 9% if a genre was chosen by random. 

Furthermore, besides the top genre that the model selected, the second and third choices were also analyzed to check how much the accuracy increased. 
Including the second choice by probability increased the accuracy to 73.5% and including the third choice by probability increased the accuracy to 85.6%.

Additionally, the confusion matrix was analyzed to see which genres the model did a poor job in predicting. 
By checking precision and recall values, the genres the model was best able to predict were instrumental, acoustic/folk , and bollywood.
The genres the model were worst to predict were alternative music, indie alternative, and blues. 

![Confusion Matrix](/confusionmatrix.png)

For alternative music, the model was only able to predict correctly 2% of the time. Instead of predicting it as alternative, the model was predicting it as either indie alternative or rock. 
This makes sense as alternative is often considered as a category of rock and includes a lot of diversity. 

## Further Analysis
As a guitar player, I also wanted to analyze what differentiates between Rock and Metal. 
I subset the data to only include the genres rock and metal and ran another random forest model. 
The three most important variables were acousticness, energy, and valence. 
Below is a density plot that shows the difference of energy between rock (8) and metal (10).
![Density Plot](/energy.png)

While both genres have high energy, you can notice that the overall genre of rock have a more balaned distribution of energy.
The model was able to separate rock and metal with an accuracy of 80%. 

## Conclusion
It was a lot of fun running models for something I am passionate about. 
Music has always been a big part of my life and it was a great experience to use machine learning to classify genres. 
It was also interesting to see how poorly the model did in classifying indie vs alternative. 
However, this does make sense as the two genres are often confused among listeners and the difference really comes from the geographic origin of the songs.
An additional predictor of location might helped classify between the two genres. 

Click [here](https://github.com/coustic93/Music-Genre-Classification) to see my R code. 
