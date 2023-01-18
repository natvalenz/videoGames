# When Was the Golden Age of Video Games? 
Use SQL joins and set theory to discover the best years for video games!

## Project Description
In this project, I analyzed video game critic and user scores as well as sales data for the top 400 video games released since 1977. I searched for a golden age of video games by identifying release years that users and critics liked best, and I explored the business side of gaming by looking at game sales data.

My search involved joining datasets and comparing results with set theory. I also filtered, grouped, and ordered data. 

Photo by Dan Schleusser on Unsplash.
![alt text](https://github.com/natvalenz/videoGames/blob/main/images/video_game.jpg)

Video games are big business: the global gaming market is projected to be worth more than $300 billion by 2027 according to Mordor Intelligence. With so much money at stake, the major game publishers are hugely incentivized to create the next big hit. But are games getting better, or has the golden age of video games already passed?

In this project, I explored the top 400 best-selling video games created between 1977 and 2020. I compared a dataset on game sales with critic and user reviews to determine whether or not video games have improved as the gaming market has grown.

The database contains two tables. I limited each table to 400 rows for this project, but you can find the complete dataset with over 13,000 games on Kaggle.

![alt text](https://github.com/natvalenz/videoGames/blob/main/images/1.jpg)

Let's begin by looking at some of the top selling video games of all time!

## Good to know
This project uses techniques in SQL, including left and inner joins, set theory concepts such as union and intercept, and subqueries. SQL concepts such as how to select columns from a table, filter rows where they meet a criterion, use aggregation functions, perform calculations on groups of rows, and filter grouped data.

## Project Tasks
1. The ten best-selling video games

I selected all columns for the top ten best-selling video games (based on games_sold) in game_sales and ordered the results from the best-selling game down to the tenth best-selling game.

![alt text](https://github.com/natvalenz/videoGames/blob/main/images/2.jpg)


2. Missing review scores

How many games in the game_sales table are missing both a user_score and a critic_score?
I joined the game_sales and reviews tables together so that all games from the game_sales table are listed in the results, whether or not they have associated reviews.
Then I selected the count of games where both the associated critic_score and the associated user_score are null.

Count: 31

3. Years that video game critics loved


4. Was 1982 really that great?


5. Years that dropped off the critics' favorites list


6. Years video game players loved


7. Years that both players and critics loved


8. Sales in the best video game years
