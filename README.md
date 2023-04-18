# SC1015-MINIPROJECT League of Prediction
School of Computer Science and Engineering<br>
Nanyang Technological University<br>
Lab: A135<br>
Team:7<br><br>
Member:<br>
 &nbsp; &nbsp;  1. Zhou ShiYong (@ZhouShiYong17)<br>
  &nbsp;&nbsp;  2. Ong Xin Ning Trini(@triniong2013@gmail.com><br>
  &nbsp; &nbsp; 3. Yao YuZhi(@smyaokai@gmail.com)<br>

## Description: <br>
This repository contains all the Jupyter Notebooks, datasets, images, video presentations, and the source materials/references we have used and created as part of the Mini Project for SC1015: Introduction to Data Science and AI.

This README provides an overview of the project's accomplishments. If you require a more comprehensive explanation, please consult the Jupyter Notebooks in this repository. They contain more in-depth explanations and minute details not mentioned in this README. The notebooks have been divided into five sections that correspond to the five main sections of this project.



## 1.Introduction
In January 2014, more than 67 million people played League of Legends per month, 27 million per day, and more than 7.5 million simultaneously during peak hours.  As the ranking system is a way for players to demonstrate their skill, there are numerous ranked matches occurring simultaneously every day.<br>

Existing tools were developed by companies and players alike for the sole purpose of determining the optimal strategy for victory.  Such applications include op.gg, u.gg, champions.gg, counterstats, rankedboost, and others. While they all provide players with valuable statistics, they all focus on improving the player's solo potential while ignoring team composition. Existing tools cannot answer the question, "when will my team perform at its best in the game?" As a result, we decided to develop this tool to make up for the dearth of readily accessible statistics for team compositions.<br>

 Our questions: 
 1. "What type of champion is Aatrox?“ 
 2. "If my team is formed up by Jayce,	Zac,Taliyah,Xayah	and Thresh. when will my team perform at its best in the game?"
 
 
Our dataset:<br>
1. [Competitive Matches](https://www.kaggle.com/chuckephron/leagueoflegends)<br>
aims to analyse the types of champions we see on League of Legends and why they fit into their respective lanes.We hope that this will help players, who specialise in only one champion, to figure out strategies use their champion to fit into other roles. For example, base Karma is primarily played as a Support, however, some players have managed to use items to supplement her stats to make her viable in other lanes such as Top and Mid. <br>

2. [Champion-9.2.1.json](http://ddragon.leagueoflegends.com/cdn/9.2.1/data/en_US/champion.json)<br>
What does it do: This feature requires the user to input the five champions he believes can form a team. The team has the roles of Top, Jungle, Mid, ADC, and Support. All five roles with distinct champions will classify the team competition into three distinct categories: Early game (before 20 minutes), Mid game (between 20 and 30 minutes), and Late game (after 30 minutes). What do these three categories mean? Well, based on the words alone, we can roughly determine the length of the game. Every champion in League of Legends will have their own "power spike," meaning that at a certain point, they will be extremely powerful and difficult to deal with. For instance, if a champion is considered an early game champion, it implies that the champion will be very strong and powerful before 20 minutes, but will lose effectiveness after 20 minutes. The same logic applies to the team as a whole, so if the team is categorised as Late game team comp, it indicates that the team will perform less well in the early game but will be extremely dominant in the late game. Therefore, it is essential for the user to know, if he chose five champions, what team composition they will form so that he can play around the team if he is a player. However, the dataset that we used pertains to competitive matches, where all the players are professional players and a group of coaches decided the team and strategy for them; as a result, sometimes even the team is classified as an early game team comp, despite the fact that, due to their professions, they can easily extend the game past 30 minutes. Which can cause us and the model some difficulty when making predictions. <br>


## 2.Data Preprocessing
[Matchinfo.csv](https://www.kaggle.com/chuckephron/leagueoflegends)<br>

 &nbsp; &nbsp; Data cleanning->
 1. Though there are a lot of missing data in the column, we found out that majority of them are belongs to the League"LJL".  Since only the names of the players are missing rather than the champions they played. Hence, our analysis would not be affected and we decided not to drop any rows.<br>
 <br>
 
 &nbsp; &nbsp; Data prepartion->  
 1. We discard the team color information and further condense the original columns into fewer columns as our topic only focuses on the categories of the team composition<br>
 2. We rename the roles (top, jungle ...etc) to (p1,p2 ...etc) to simplify the problem and We will also rearrange the champions so that different permutations are regarded as the same.
 3. We devise our own Good pick score in order to determine whether the team combination is good or bad.<br>
 <br>
 
 &nbsp; &nbsp; Data Analysis-> 
 1. We dummify the Champion-9.2.1.json and combine 2 datasets together (set champion's name as the header of new dataframe)<br>
 2. Look out for the correlation between Best and worst performers in all competitive matches
 3. Analysis the frequence -which champion is commonly played with other champions
 4. Analyse why certain champions are not in the running for selection.<br>
 **`For further findings and explanations, please refer to the Jupyter Notebook on Data Analysis for Competitive matches`**
<br><br>

[Champion-9.2.1.json](http://ddragon.leagueoflegends.com/cdn/9.2.1/data/en_US/champion.json)<br>
 &nbsp; &nbsp; Data prepartion->  
 1. We did the feature engineering to classfiy Primary and Secondary attributes 
 2. Finding the correlation between each champion type and their defining characteristics.(E.g Defensive stats contribute to attack while magical stats are inversely proportional to the attack stats..etc)
 3.Using different mechine learnign models to differentiate champion type<br>
 **`For further findings and explanations, please refer to the Jupyter Notebook on Data Analysis on Champions`**

## 3.Methodology
For the question:" "What type of champion is Aatrox?"<br>
'Input:champs[info_types + stat_types + additional_types] ------> output:champs[['tag1','tag2']]' <br>
We used KMeans and GMM to assess the number of champion types via unsupervised learning and found that unsupervised learning can only detect 5 types. Before that, we used PCA, StandardScaler, LabelEncoder and OneHotEncoder to make the data suitable for the algorithms. After that, we trained 4 models: LogisticRegression for champion type and GradientBoostingRegressor x3 for attack, defense, and magic. Each of them were trained with 85% of the total 143 champions and the remaining 15% were used as test cases. We rejected models that performed badly on the test data set because that showed that the model was overfitting (after all, the unsupervised techniques didn’t achieve good results so there already was a high risk of overfitting). We also performed feature importances on our logistic regression model.<br>
**`For further findings and explanations, please refer to the Jupyter Notebook on Data Analysis on Champions and Machine Learning for Champions`**

For question:"If my team is formed up by Jayce,	Zac,Taliyah,Xayah	and Thresh. when will my team perform at its best in the game?"<br>
‘Input: an arrary consisits of 5 five champions ------>output either 0, 1, 2 where 0 corrsponding to early game, 1 corresponding to middle game and 2 corresponding to lategame '
We first removed the lose team records from the dataset and then splited it into three datasets for early, mid, and late game periods. This allowed us to find the frequency of champions appearing in each of datasets. We then split the data into X and y, where X consisted of the names of 5 champions, and y was the game duration. After comparison, we found that RandomForest had a relatively excellent predictive result. With 'Accuracy(test)' 44.90, Accuracy(train)'99.48', 'Cross validation score'0.5021 and 'Standard Deviation' 0.08
**`For further findings and explanations, please refer to the Jupyter Notebook on Data Analysis for Competitive matches and Find_Early_Mid_Late_game_team_comp`**


## 4.Experiment
For the question:" "What type of champion is Aatrox?"<br>
we use various techniques to make our data more palpable for machine learning.Firstly we definitely have to standardise the data. An obvious reason as `attack` going up to a maximum of 10 while `maxhp` goes up to 2578.
We also have to label encode our `y` into numerical values.`partype` also has to be hotencoded since it's not our output variable.We also performed PCA on the data and got a model that reduced our data to just 19 dimensions while preserving 95% of the variance. However, there is no real need to perform PCA as our data set is pretty small, standing at 143 champions and about 40 features.<br>

We input our training sets into 10 different models( LogisticRegression,KneighborsClassifier ...), among which we found logistic regression to be the best model with corss-val of 0.6742.LogisticRegression is able to detect the champion types with amazing accuracy compared to GaussianMixture, this shows that supervised learning is vastly superior to unsupervised techniques.
**`For further findings and explanations, please refer to the Jupyter Notebook on Data Analysis on Champions and Machine Learning for Champions`**

<br><br>


For question:"If my team is formed up by Jayce,	Zac,Taliyah,Xayah	and Thresh. when will my team perform at its best in the game?"<br>

we performs hyperparameter tuning for a random forest classifier using GridSearchCV from scikit-learn. It specifies a grid of possible values for the following hyperparameters: 'criterion', 'min_samples_leaf', 'min_samples_split', and 'n_estimators'. The GridSearchCV function fits the random forest classifier with all possible combinations of hyperparameters specified in the grid, and selects the best combination based on the highest cross-validation score. The best combination of hyperparameters is stored in 'clf.best_params_'. The X_train and X1_test variables are assumed to be the training and testing data, respectively.<br>
The result as shwon:‘{'criterion': 'gini',
 'min_samples_leaf': 1,
 'min_samples_split': 4,
 'n_estimators': 700}’

By doing so, the accuracy of the model has improved from 44.9 to 51.02%
**`For further findings and explanations, please refer to the Jupyter Notebook on Data Analysis for Competitive matches and Find_Early_Mid_Late_game_team_comp`**
## 5 Conclusion
