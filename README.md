# MLBScoresPrediction
Predicts Over/Under and Score Difference on Daily MLB Matchups

## Motivation
On average, the total runs of a baseball game is 8 to 9 points and the over/under is set around that average, adjusted a little by the starting pitchers past performance and the home venue. The lower range can be 5.5 and the higher range can be 12.5 for over/under, and very often the total runs turn out to be far above or below the threshold for that game. The run difference between the winning and losing team seems to be very random because there are many ways to score a run and human error occurs on both offensive and defensive ends. Therefore, it is an interesting problem to me to find out if I can better generalize or predict the over/under and score difference for a given game. 

## Files
[GetData](GetData.ipynb): Webscrape from baseball-reference at https://www.baseball-reference.com/ and collect data from statsapi.

[GetTeamBattingSplits](GetTeamBattingSplits.ipynb): Webscrape team batting splits (home/away) from baseball-reference at https://www.baseball-reference.com/.

[SeriesPrediction](SeriesPrediction.ipynb): Use the first and second games of a 3-game series as training data to model the total runs and runs difference for the third game.

[GamePrediction](GamePrediction.ipynb): Revise the approach and model for each game. Add in more variables like team batting splits.

[GamePredictionWeather](GamePredictionWeather.ipynb): Incorportate weather data via the OpenWeatherMap API. A script to be run daily to recieve predictions and save the weather data from the API calls to a local database for future use.

### Key Takeaways and Notes
* Picked up Selenium when BeautifulSoup doesn't work
* 3-game series has too little samples and poor predictions
* Plot residuals to assess the assumption of linear models
* Within 3.5 mean absolute error for total runs and run difference
* Continue with weather data
* Add in more variables to capture recent performance for teams and starting pitchers
