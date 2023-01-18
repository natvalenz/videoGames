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

Wow, the best-selling video games were released between 1985 to 2017! That's quite a range; I used data from the reviews table to gain more insight on the best years for video games.

2. Missing review scores

First, it's important to explore the limitations of the database. One big shortcoming is that there is not any reviews data for some of the games on the game_sales table.

How many games in the game_sales table are missing both a user_score and a critic_score?
I joined the game_sales and reviews tables together so that all games from the game_sales table are listed in the results, whether or not they have associated reviews.
Then I selected the count of games where both the associated critic_score and the associated user_score are null.

Count: 31

It looks like a little less than ten percent of the games on the game_sales table don't have any reviews data. That's a small enough percentage that I continued the exploration, but the missing reviews data is a good thing to keep in mind as I move on to evaluating results from more sophisticated queries.

3. Years that video game critics loved

There are lots of ways to measure the best years for video games! I started with what the critics think.

I found the years with the highest average critic_score by selecting the release year and average critic score for each year; rounded the average critic score for each year and aliased it as avg_critic_score. Then I joined the game_sales and reviews tables so that only games which appear on both tables are represented.
Grouped the data by release year and finally I order the data from highest to lowest avg_critic_score and limited the results to the top ten years.

![alt text](https://github.com/natvalenz/videoGames/blob/main/images/3.jpg)

The range of great years according to critic reviews goes from 1982 until 2020: I was no closer to finding the golden age of video games!

Hang on, though. Some of those avg_critic_score values look like suspiciously round numbers for averages. The value for 1982 looks especially fishy. Maybe there weren't a lot of video games in the dataset that were released in certain years.

I updated the query and found out whether 1982 really was such a great year for video games.

4. Was 1982 really that great?

I queried game critics' ten favorite years, this time with the stipulation that a year must have more than four games released in order to be considered.

I started with the query from the previous task, updated it so that the selected data additionally includes a count of games released in a given year, and aliased this count as num_games. Then I filtered the query so that only years with more than four games released were returned.

![alt text](https://github.com/natvalenz/videoGames/blob/main/images/4.jpg)

That looks better! The num_games column convinced me that the new list of the critics' top games reflects years that had quite a few well-reviewed games rather than just one or two hits. But which years dropped off the list due to having four or fewer reviewed games? I identified them so that someday I can track down more game reviews for those years and determine whether they might rightfully be considered as excellent years for video game releases!

5. Years that dropped off the critics' favorites list

It's time to brush off my set theory skills. To get started, I created tables with the results of the previous two queries:

![alt text](https://github.com/natvalenz/videoGames/blob/main/images/5_1.jpg)

I used set theory to find the years that were on the first critics' favorite list but not the second.

I selected the year and avg_critic_score for those years that were on the first critics' favorite list but not the second due to having four or fewer reviewed games.
Finally I ordered the results from highest to lowest avg_critic_score.

![alt text](https://github.com/natvalenz/videoGames/blob/main/images/5_2.jpg)

It looks like the early 1990s might merit consideration as the golden age of video games based on critic_score alone, but I needed to gather more games and reviews data to do further analysis.

I moved on to looking at the opinions of another important group of people: players!

6. Years video game players loved

I created a query very similar to the one in Task Four, except this one will look at user_score averages by year rather than critic_score averages.

Meaning I updated the query from Task Four so that it returns years with ten highest avg_user_score values.

I selected year and a rounded and aliased as avg_user_score average of user_score for each year; also I included a count of games released in a given year, aliased as num_games.
Then I included only years with more than four reviewed games; grouped the data by year.
Finally I ordered data from highest to lowest avg_user_score, and limited the results to the top ten years.

![alt text](https://github.com/natvalenz/videoGames/blob/main/images/6.jpg)

Alright, I had a list of the top ten years according to both critic reviews and user reviews. Are there any years that showed up on both tables? If so, those years would certainly be excellent ones!

7. Years that both players and critics loved

I used the top_critic_years_more_than_four_games table, which stores the results of our top critic years query from Task 4:

![alt text](https://github.com/natvalenz/videoGames/blob/main/images/7_1.jpg)

I also saved the results of the top user years query from the previous task into a table:

![alt text](https://github.com/natvalenz/videoGames/blob/main/images/7_2.jpg)

Then created a list of years that appear on both the top_critic_years_more_than_four_games table and the top_user_years_more_than_four_games table.

Using set theory, I selected only the year results that appear on both tables.

![alt text](https://github.com/natvalenz/videoGames/blob/main/images/7_3.jpg)

Looks like three years that both users and critics agreed were in the top ten! There are many other ways of measuring what the best years for video games are, but I stuck with those yearso. I knew that critics and players liked these years, but what about video game makers? Were sales good?

8. Sales in the best video game years

I used the query from the previous task as a subquery in this one! This is a great practice, as I won't always have write permissions on the database I'm querying.

I added a column showing total games_sold in each year to the table I created in the previous task.

Then I selected the year and the sum of games_sold, aliased as total_games_sold; ordered the results by total_games_sold descending.
Filtered the game_sales table based on whether the year is in the list of years I returned in the previous task, using the code from the previous task as a subquery.
Finally I grouped the results by year.

![alt text](https://github.com/natvalenz/videoGames/blob/main/images/8.jpg)