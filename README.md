# IndiavsAus_Hackathon
The Sledge Hack: Ind vs Aus Cricket Hackathon\

**Approach:**\
For whole dataframe\
•	Drop match_id, stumpings, catches, match_date columns\
•	Parse opposition column into opposition team and venue\
•	Insert column Indian_pitch by noting down all the Indian pitches from internet.\
•	Delete those entries for which specific opposition sample size is < 10.\
Create two copies if this dataframe for bowler and batsman.\
**For batsman dataframe:**\
•	Drop wickets column, venue, Indian_pitch ,runs_conceded column.
•	Ignore runs_scored rows where it was ‘DNB’ and “TDNB”
•	And for * in runs_scored, replace with “”.
•	Hot encode the opposition column
•	Store the list of all the players.
•	And for each player, based on its data train the model.
•	Store for each player its model to predict runs_scored.
**For Bowler dataframe:**
•	Drop runs_scored column.
•	Ignore rows where wickets= ‘-‘
•	Hot encode the opposition column
•	Create a bowling avg column where value = wickets/runs_conceded.
•	Normalize it.
•	Drop runs-conceded column.
•	For each player train its model and store it.
•	If for any player sample size is less than 10, don’t train the model just take the mean for prediction.
Store the list of Indian players and Australian players:
•	Predict for Australian players against India, and vice versa for Indian players.
**Different experiments done:**
1.	Just predict the wickets and runs_scored as the average of the data present for each player.
2.	Do not include opposition and Indian_pitch columns.
3.	Include opposition columns.
4.	Include Indian_pitch for both batsman and bowler, score diverged more.
5.	Not  include Indian_pitch for both.
6.	Include bowling average for bowler.
7.	Using Random Forest Regressor for both batsman and bowler.
8.	Use Decision Tree for bowler.
9.	Using XGBoost for both.
10.	Using Random Forest Classifier for bowling. It gave too much absolute results which might have not proved well when metric is rmse.
11.	Tried different hyperparameters for Random Forest Regressor.
12.	Using Random Forest Regressor for batting and XGBoost for bowling.
**Ideas that worked well.**
1.	Including opposition.
2.	Using bowling average as feature.
3.	Used hyperparameters which gave more flexibility to results for the actual day.
