🎬 Movie Rating Prediction using Machine Learning
BY-
sudhansu sahoo
Roshan choudary
surya narayan panda
soumya ranjan pradhan

This project builds a machine learning model that predicts the IMDB rating of Indian movies using features like Year, Genre, Votes, Duration, Director, and Actors.

📌 Project Overview

We work with the dataset IMDB_Movies_India.csv containing:

Movie details (Name, Year, Genre)

Cast (Director, Actor 1, Actor 2, Actor 3)

Rating & Votes

The goal is to predict a movie’s Rating based on the above features.

🔧 Steps Performed
1️⃣ Data Cleaning

Handled missing values using mean, mode, or defaults.

Converted text columns (Year, Duration) into numeric.

Cleaned Votes column by removing commas or letters.

Removed duplicates.

2️⃣ Feature Engineering

Created new numerical features:

Feature	Meaning
Genre_mean_rating	Average rating of all movies in that genre
Director_encoded	Average rating of movies directed by that director
Actor1_encoded / Actor2_encoded / Actor3_encoded	Average rating of movies done by each actor

These values help the model understand the historical performance of people involved in the movie.

3️⃣ Model Building

Three models were trained:

Model	R2 Score	Notes
Linear Regression	0.71	Good baseline
Decision Tree	0.54	Overfits
Random Forest Regressor	⭐ 0.77 (Best)	Best accuracy

Random Forest was selected as the final model.

📊 Evaluation Metrics

Used:

Mean Squared Error (MSE)

Mean Absolute Error (MAE)

R2 Score

Random Forest achieved the best performance.

🚀 Predicting a New Movie Rating

Example code:

new_data = pd.DataFrame({
    'Year': [2019], 
    'Votes': [36], 
    'Duration': [111],
    'Genre_mean_rating': [5.8], 
    'Director_encoded': [4.5],
    'Actor1_encoded': [5.3], 
    'Actor2_encoded': [4.5], 
    'Actor3_encoded': [4.5]
})

predicted_rating = regressor.predict(new_data)
print("Predicted Rating:", predicted_rating[0])

❓ How to Get These Input Values?
Field	How to get it
Year	Release year of the new movie
Votes	Estimated number of IMDB votes
Duration	Movie runtime in minutes
Genre_mean_rating	Average rating of that movie’s genre in your dataset (already calculated during training)
Director_encoded	Average rating of movies by that director from your dataset
Actor Encoded Features	Average rating of movies by each actor from your dataset

👉 If a new Director/Actor does not exist in your dataset → use the overall mean rating.

📁 Files Included

Movie_Rating_Prediction.ipynb – Full Jupyter Notebook

IMDB_Movies_India.csv – Dataset

README.md – Project Report (this file)

🏁 Conclusion

This project demonstrates:

Data cleaning

Feature engineering

Exploratory data analysis

Building multiple ML models

Selecting the best model (Random Forest)

Making predictions for new movies
