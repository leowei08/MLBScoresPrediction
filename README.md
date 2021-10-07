# MLBScoresPrediction
Predicts Over/Under and Score Difference on Daily MLB Matchups

## Motivation
On average, the total runs of a baseball game is 8 to 9 points and the over/under is set around that average, adjusted a little by the starting pitchers past performance and the home venue. The lower range can be 5.5 and the higher range can be 12.5 for over/under, and very often the total runs turn out to be far above or below the threshold for that game. The run difference between the winning and losing team seems to be very random because there are many ways to score a run and human error occurs on both offensive and defensive ends. Therefore, it is an interesting problem to me to find out if I can better generalize or predict the over/under and score difference for a given game. 


## Approach
The initial approach was to model the third game of a 3-game series given the outcomes of the first two because many times we see that the team that lost the first two games end up taking the last game and I wonder if that is by chance or that the winning team took the series win, got ready for the next series, and made it an easier game for the other team. However, following this approach didn't turn out so good because the predictions were pretty much around the average total runs per game and didn't give much insight. Therefore, I figured more data could potentially produce better results and tried to predict a single game result given team and pitcher data. With the loss of the predictors, I added the team batting splits to compensate for that and planned to add more variables to capture recent performance of both teams. The predictions turned out to be more scattered while the residuals are normally distributed. 

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
