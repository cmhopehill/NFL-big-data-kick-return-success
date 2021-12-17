## NFL Kickoff Return Success
**By Curtis M Hope Hill** 
A data science project investigating the factors that impact the success of a kickoff return.

[Link to Kaggle Data](https://www.kaggle.com/c/nfl-big-data-bowl-2022/data)

[Executive Summary](https://docs.google.com/document/d/138o9vUubIE3FDfHrl4aANi8Xrs7Z9qcfZGFojj77OFk/edit?usp=sharing)

### Problem Statement
NFL Football Team ® has contracted with Hope Hill Data Science to examine special teams plays from the recent NFL seasons to understand factors impacting kickoff return success. A satisfactory project will involve producing a model that is able to predict a successful return at a higher rate than average from the 2018 - 2020 seasons. To accomplish this I will be using the data provided by the NFL for their Big Data Bowl 2022 that is focused on evaluating special teams performance. (The current project has focused on data from the 2018 season, but I will be working to update it to include all data from 2018-2020 in the coming days and weeks.)

**There's three parts to football: Offense, Defense, and Special Teams. You'd no more ignore Special Teams than you would Offense or Defense. **
    **-Marv Levy (Coach of Buffalo Bills 1986 - 1997)**

### Background
American Football involves three phases of the game: Offense, Defense, and Special Teams. Special Teams, or the Kicking Game involves four types of plays: Kickoffs, Punts, Field Goals, and Point After Attempts following a Touchdown. While teams typically spend the majority of their time in games either on Offense and Defense, the success of their Special Teams unit can help or hurt both of the other phases. A great kickoff or punt return can give their Offense a shorter field and a greater likelihood to score, and a great kickoff or punt can ensure that the opposing team's Offense has to go the full length of the field. Successful Field Goals, and Point After Attempts also ensure that when the Offense has a successful drive they come away with points. On average Special Teams account for ~35% of the points scored in a given NFL season. If a team is able to find ways to improve their success on special teams 

### Data Provided
The NFL Big Data Bowl on Kaggle provided the following datasets for the 2018-2020 Seasons:
1. Plays Data
    * Each Individual Special Teams play from 2018 Season
    * Score, Play Type, Yardage Gained, Penalties, Kicker and Returner ID, etc.
2. Games Data
    * Game Information (Date, Time, Week, Home vs. Away Team, etc.)
3. Player Data
    * Individual Player Profiles (Height, Weight, Birth Date, Name, etc.)
4. Pro Football Focus (PFF) Scouting Data
    * Kick Type, Hang Time, Direction of Kick & Return, Formations, etc.
5. Player Tracking Data
    * Frame to frame tracking of each player for each special teams play
    * The tracking data was broken down by season due to the size of each file (1.6 -1.75 gbs for each season).

### Data Process
I initially started by cleaning and merging the PFF and Plays datasets and subsetting down to kickoff plays that involved a kickoff return. By doing this I excluded kickoffs that went for a touchback, onside kicks, and kick returns that led to a fumble or other turnover. However, after some initial modeling on this data, I came to the conclusion that my models were underfit and that I ought to work to include the other datasets in to add further complexity to the model. 

After adding in the Games, Player, and Tracking datasets I had to go through a second round of cleaning and preprocessing. I made the decision to move to only modeling with the 2018 season to ease the time it would take me to clean and preprocess the data and to make modeling in a reasonable timeframe possible. In this second round of cleaning and preprocessing I ended up dropping a couple of kickoff returns that involved two returners for time's sake. 

### Modeling
1. Ran an initial, but unsuccessful, Logistic Regression on just the PFF and Plays data
2. Ran the following models on the full 2018 season data:
    * Logisitc Regression 
    * Decision Tree
    * Bagged Decision tree
3. Decision Tree ended up being the best of the bunch

### Conclusions & Recommendations
* The Decision Tree Model provided the best model for accurately predicting a successful return, even if it does appear to slightly over predict success.
* For teams receiving a kickoff the DT coefs indicate that returning the kick down the center or intending to return it left are the best bets to try and increase the odds of a successful return.

### Limitations
* Computing power and time were the largest constraints. 
* Size of the tracking files made them difficult to work with, and I don’t feel that I fully tapped the potential information there.

### Future Directions
* Further investigating the tracking data.
* Looking at ways to use data from 2018-2020
* Investigating Punt Returns
* Deploying a working model with Streamlit
* Submitting final findings to NFL’s Big Data Bowl on Kaggle
