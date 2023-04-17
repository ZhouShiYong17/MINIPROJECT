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

What does it do: This feature requires the user to input the five champions he believes can form a team. The team has the roles of Top, Jungle, Mid, ADC, and Support. All five roles with distinct champions will classify the team competition into three distinct categories: Early game (before 20 minutes), Mid game (between 20 and 30 minutes), and Late game (after 30 minutes). What do these three categories mean? Well, based on the words alone, we can roughly determine the length of the game. Every champion in League of Legends will have their own "power spike," meaning that at a certain point, they will be extremely powerful and difficult to deal with. For instance, if a champion is considered an early game champion, it implies that the champion will be very strong and powerful before 20 minutes, but will lose effectiveness after 20 minutes. The same logic applies to the team as a whole, so if the team is categorised as Late game team comp, it indicates that the team will perform less well in the early game but will be extremely dominant in the late game. Therefore, it is essential for the user to know, if he chose five champions, what team composition they will form so that he can play around the team if he is a player. However, the dataset that we used pertains to competitive matches, where all the players are professional players and a group of coaches decided the team and strategy for them; as a result, sometimes even the team is classified as an early game team comp, despite the fact that, due to their professions, they can easily extend the game past 30 minutes. Which can cause us and the model some difficulty when making predictions. 
 
 Our questions: 
 1. "What type of champion is Aatrox?“
 2. "If my team is formed up by Jayce,	Zac,Taliyah,Xayah	and Thresh. when will my team perform at its best in the game?"
 
 
Our dataset:<br>
1. [Competitive Matches](https://www.kaggle.com/chuckephron/leagueoflegends)<br>
2. [list of champions in the game](http://ddragon.leagueoflegends.com/cdn/9.2.1/data/en_US/champion.json)<br>


## 2.Data Preprocessing
Matchinfo.csv (Competitive matches)<br>

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
 4. Analyse why certain champions are not in the running for selection.
 For further findings and explanations, please refer to the Jupyter Notebook on Data Analysis for Competitive matches
<br><br>

Champion-9.2.1.json<br>
 &nbsp; &nbsp; Data prepartion->  
 1. We did the feature engineering to classfiy Primary and Secondary attributes 
 2. Finding the correlation between each champion type and their defining characteristics.(E.g Defensive stats contribute to attack while magical stats are inversely proportional to the attack stats..etc)
 3.Using different mechine learnign models to differentiate champion type
 For further findings and explanations, please refer to the Jupyter Notebook on Data Analysis on Champions

## 3.Methodology


## 4.Experiment

## 5 Conclusion
