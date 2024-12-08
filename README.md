# NBA MVP Predictor
This repository has 3 Jupyter Notebooks.

The first ML model is in Standard_Stats.ipynb. That is my first attempt at using machine learning to predict the regular season MVP of the NBA. It uses only standard statistics like points per game, assists, etc. along with team record data. The team record is included because the winner of the MVP award is almost always on one of the best-performing teams in their conference, especially before the 2000s. That is why some people used to call it "the best player on the best team award." In its current state, it can predict the correct MVP 27% of the time for the training data, 20% on the validation data, and 36% of the time on the test data. If you look at the notebook, you can see that these values correlate almost 1-to-1 with the percentage of the MVPs in each dataset who were the highest-scoring players in the league. It seems that the model has identified points per game as the most valuable statistic for determining MVP, which makes sense.

The second ML model is in Advanced_Stats.ipynb. I wasn't satisfied with the performance of my original model using standard statistics, so I decided to incorporate advanced statistics which could provide the model with more valuable information. Things like win-shares, PER, VORP, etc. are usually better metrics for evaluating the contribution of a player to their team than standard statistics. Unfortunately, most advanced statistics have only been tracked since the 1979-80 season, so I have less data to train the model on. Currently, it accurately predicts the regular season MVP 26% of the time on the training data, 29% of the time on the validation data, and 29% of the time on the test data. Unfortunately, my second model did not perform much better. Again, it tends to highly favor the player who scores the most points and disregards the other statistics. During my training process, I found that dimensionality reduction significantly improved the performance on the training data, but the model would underperform on the validation and test sets.

So, the 2 ML models did okay overall. They perform much better than a random selection (1 MVP / 75 Top Scorers = 1.3%), but not significantly better than the average NBA fan.

My third attempt is in Data_Sci_Comparison.ipynb. Instead of using ML for this model, I am using the correlation between the statistics and the winner of the MVP award. Technically, the notebook has 2 very similar models. One tracks the correlation between player statistics and the MVP winner as a 1-hot encoded vector. The other tracks the correlation between player statistics and the MVP voting share, so players who are close but don't win the award still influence the correlation. Both models use standard player statistics, team statistics, and advanced player statistics. Unsurprisingly, both models identified similar statistics to be the most important. For each model, I took the 15 statistics that correlated the most with the MVP metrics I just mentioned, and used them to calculate an "MVP score." The player with the highest score for each season is my prediction to win the MVP. The model that used MVP voting share correlation correctly predicted the MVP 52% of the time on the "training" data. The model based on correlation with the 1-hot encoded vector accurately predicted the MVP 55% of the time on the "training" data. Training is in quotes because I'm not training a model, but I am separating the data the same as I would for an ML model to ensure that the model isn't overfitted to the data used to create the model. Both models predicted the MVP 71% of the time on the test dataset.

I am much happier with the performance of the 3rd model that did not use ML. I am suprised that points per game was the 8th and 10th most correlated statistic for the correlation-based models because the ML models seemed to favor it more than any other metric.

Here are 2 sources that helped me in creating these models:

[UPenn Statistical Model](https://wsb.wharton.upenn.edu/wp-content/uploads/2023/05/Shen_2023_Basketball_MVP.pdf)

[Similar ML Model](https://www.samford.edu/sports-analytics/fans/2023/Using-Machine-Learning-to-Predict-the-NBA-MVP)

Here are the sources of data I used:
These are for the 2025 season, but I collected all the data since the 1955-56 season for standard and team stats. I only went back to the 1979-80 season for advanced stats and MVP voting shares because only a few advanced stats were tracked before that season.

[Per-game standard stats](https://www.basketball-reference.com/leagues/NBA_2025_per_game.html)

[Advanced stats](https://www.basketball-reference.com/leagues/NBA_2025_advanced.html)

[MVP voting results](https://www.basketball-reference.com/awards/awards_2024.html)

[MVP winners by year](https://www.basketball-reference.com/awards/mvp.html)

[Team records](https://www.basketball-reference.com/leagues/NBA_2024_standings.html](https://www.basketball-reference.com/leagues/NBA_2025_standings.html)
