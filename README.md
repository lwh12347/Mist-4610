# Mist-4610
Fantasy Football Team
### Group 2:
Sahil Panchal - 811952439 - https://github.com/SahilPnc/MIST-4610-Project-1-  
Dru Hunt - 811481261 - https://github.com/lwh12347/Mist-4610  
Yonatan Woldetenssaie - 811294688 - https://github.com/YonatanWoldetenssaie/FantasyFootball  
Kent Tran - 811696100 - https://github.com/Kenttra/MIST-4610-P1
#### Project Description
Our team decided to model a database that supports fantasy football analysis, focusing on player statistics, game outcomes, and team performance across multiple leagues. In our project's database design, we created 12 entities to encapsulate all relevant information, establishing relationships between these entities to form a comprehensive data model.From the perspective of a fantasy football league, we modeled teams, players, and games to represent the core components of player statistics and team performance. From there, we introduced entities that manage player scoring data, game results, and player rankings to facilitate performance tracking and comparison across teams.On the analysis side of the model, we created entities to evaluate player performance, such as weekly projections and player health status, helping to predict future outcomes and identify potential draft picks or trades. Additionally, we integrated a system to track league standings, manage team rosters, and evaluate player performance metrics, enabling more informed decisions for team management and roster adjustments.This scenario illustrates how our solution provides a comprehensive framework for managing fantasy football data, tracking player statistics, league performance, and optimizing team decisions. It helps identify trends in player performance, set up teams, and even predict future outcomes based on historical data.

1. Player Table
Purpose: Holds details of individual NFL players, including their name, position, NFL team, and birthdate.
Key Fields:
PlayerID: Primary key, unique identifier for each player.
Name: Name of the player.
Position: The player's position (e.g., QB, RB, WR, etc.).
ProTeam: The NFL team to which the player belongs.
BirthDate: The player's birthdate.
Relationships:
Linked to PlayerStatistics through PlayerID to track individual game statistics.
Linked to Roster through PlayerID to assign players to fantasy football teams.
2. Team Table
Purpose: Represents fantasy football teams that participate in leagues.
Key Fields:
TeamID: Primary key, unique identifier for each fantasy team.
TeamName: The name of the fantasy team.
Owner: The name of the team’s owner.
LeagueID: Foreign key, linking each team to a league.
TotalPoints: The total points accumulated by the team across the fantasy season.
Relationships:
Linked to League through LeagueID to place the team in a specific league.
Linked to Roster through TeamID to manage which players are on the team.
Linked to TeamPerformance through TeamID to track the team's performance during the season.
Linked to Matchup through TeamID to participate in weekly matchups.
3. League Table
Purpose: Represents different fantasy football leagues in which teams compete.
Key Fields:
LeagueID: Primary key, unique identifier for each league.
LeagueName: The name of the fantasy football league.
Rules: Rules governing the league (e.g., PPR, standard).
Relationships:
Linked to Team through LeagueID to assign teams to specific leagues.
Linked to Matchup through LeagueID to manage weekly matchups within each league.
4. Roster Table
Purpose: Tracks the players assigned to each fantasy football team during a specific week.
Key Fields:
RosterID: Primary key, unique identifier for each roster record.
TeamID: Foreign key, linking the roster to a specific fantasy team.
PlayerID: Foreign key, linking the roster to a specific NFL player.
Week: The week number during which the player is part of the team.
Relationships:
Linked to Player through PlayerID.
Linked to Team through TeamID.
5. Game Table
Purpose: Tracks individual NFL games.
Key Fields:
GameID: Primary key, unique identifier for each NFL game.
Date: The date of the game.
HomeTeam: The home team in the game.
AwayTeam: The away team in the game.
Relationships:
Linked to PlayerStatistics through GameID to record player statistics for the game.
Linked to TeamPerformance through GameID to record team performance for the game.
6. PlayerStatistics Table
Purpose: Tracks the individual statistics for players in each game.
Key Fields:
StatID: Primary key, unique identifier for each player's statistics record.
PlayerID: Foreign key, linking the statistics to a player.
GameID: Foreign key, linking the statistics to an NFL game.
Points: Points scored by the player in the game.
Yards: Total yards gained by the player in the game.
Touchdowns: Total touchdowns scored by the player in the game.
Relationships:
Linked to Player through PlayerID.
Linked to Game through GameID.
7. TeamPerformance Table
Purpose: Tracks the performance of fantasy football teams during specific weeks.
Key Fields:
PerformanceID: Primary key, unique identifier for each performance record.
TeamID: Foreign key, linking the performance to a specific fantasy team.
Week: The week number during which the performance occurred.
PointsScored: Points scored by the team in a specific week.
OpponentTeamID: Foreign key, linking to the opposing team in the matchup.
Result: The result of the game (win/loss/tie).
Relationships:
Linked to Team through TeamID.
Linked to Game through GameID.
8. Matchup Table
Purpose: Tracks weekly matchups between fantasy football teams within a league.
Key Fields:
MatchupID: Primary key, unique identifier for each matchup.
Week: The week number of the fantasy season.
Team1ID: Foreign key, linking the matchup to the first team.
Team2ID: Foreign key, linking the matchup to the second team.
Result: The result of the matchup (e.g., Team 1 wins, Team 2 wins).
LeagueID: Foreign key, linking the matchup to a specific league.
Relationships:
Linked to Team through Team1ID and Team2ID.
Linked to League through LeagueID.
### Data Model 
![Data_Model](https://github.com/SahilPnc/MIST-4610-Project-1-/blob/main/Datamodel.png)
### Data Dictionary
![Dic 1](https://github.com/SahilPnc/MIST-4610-Project-1-/blob/main/Screenshot%202024-09-30%20at%201.02.33%20AM.png)
![Dic 2](https://github.com/SahilPnc/MIST-4610-Project-1-/blob/main/Screenshot%202024-09-30%20at%201.02.39%20AM.png)
![Dic 3](https://github.com/SahilPnc/MIST-4610-Project-1-/blob/main/Screenshot%202024-09-30%20at%201.02.43%20AM.png)
![Dic 4](https://github.com/SahilPnc/MIST-4610-Project-1-/blob/main/Screenshot%202024-09-30%20at%201.02.48%20AM.png)
![Dic 5](https://github.com/SahilPnc/MIST-4610-Project-1-/blob/main/Screenshot%202024-09-30%20at%201.02.58%20AM.png)
![Dic 6](https://github.com/SahilPnc/MIST-4610-Project-1-/blob/main/Screenshot%202024-09-30%20at%201.03.04%20AM.png)
![Dic 7](https://github.com/SahilPnc/MIST-4610-Project-1-/blob/main/Screenshot%202024-09-30%20at%201.03.10%20AM.png)
![Dic 8](https://github.com/SahilPnc/MIST-4610-Project-1-/blob/main/Screenshot%202024-09-30%20at%201.03.14%20AM.png)
### Queries
#1.This query joins Player and PlayerStatistics tables based on the PlayerID and retrieves player information, such as name, position and team and also retrieves their game statistics, such as yards and touchdowns. This is useful to compare each players statistics.
![Q1](https://github.com/Kenttra/MIST-4610-P1/blob/main/Q1)

#2.This query selects all columns from the Player table where the players position matches “QB” using REGEXP. This is useful to sort out each position in the data.
![Q2](https://github.com/Kenttra/MIST-4610-P1/blob/main/Q2)

#3.Selects all teams and finds their total number of wins. This is useful to see which teams are performing the best and worst at any given time. And the managers can decide whether or not they should trade.
![Q3](https://github.com/lwh12347/Mist-4610/blob/main/Q3.png)

#4.Selects only teams who score an average greater than 80 points. This query is useful for displaying scoring numbers across the league. This type of query is important for determining which teams perform at a certain level to show the general performance of the league while excluding outliers.
![Q4](https://github.com/lwh12347/Mist-4610/blob/main/Q4.png)

#5.This complex query identifies players who have at least played one game during the season and had noteworthy games where they scored a lot of points. Its results contain the team of the player, name of the player, how many points they score ,and the date they accomplished it. This would be used to help fantasy football players to choose players who are currently active and are relatively good to choose for their fantasy team. 


#6.This simple query shows player performance in a given game and how many fantasy points, a person would gain from having that player on their fantasy team. PlayerStatistics.GameID can be changed to equal any specific GameID, so that data from any game week can be tracked efficiently. 

#7.The query is designed to help identify players who have scored more points than the average player in their respective leagues. This query is useful to see which players are playing at a high level for those looking to improve their team

#8.The query is designed to help identify how much each position scores, on average, in each league. This query is useful to see which what positions might be lacking in certain leagues and if the leagues should look for better players at certain positions.

#9.This query finds teams whose average points scored are higher than league-wide average points scored by all teams. This query is useful for identifying high performing managers that drafted their teams well. 
![Q9](https://github.com/SahilPnc/MIST-4610-Project-1-/blob/main/Q9.png)

#10.This query shows the players that are available as free agents and sorts them by their positions for simplicity. This is useful in identifying which players are not currently on rosters and can be picked up on waivers to improve a fantasy roster in the event of underperforming players, bye weeks, or injury. 
![Q10](https://github.com/SahilPnc/MIST-4610-Project-1-/blob/main/Q10.png)

### Matrix
![Matrix](https://github.com/SahilPnc/MIST-4610-Project-1-/blob/main/Project%20Matrix.png)
