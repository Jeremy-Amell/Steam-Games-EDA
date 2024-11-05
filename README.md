# Steam Games EDA
![Steam Games](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/steam_games_logo.jpg)
# Table of Contents
**[__Project Overview__](#project-overview)**  
**[__Project Proposal__](#project-proposal)**  
**[__Source of Data__](#source-of-data)**  
**[__Data Cleaning and Transformation__](#data-cleaning-and-transformation)**  
**[__Contextual Visualizations__](#contextual-visualizations)**  
**[__Specific Visualizations - Results__](#specific-visualizations---results)**  
**[__Key Insights__](#key-insights)**  
**[__Recommendations__](#recommendations)**  
**[__Future Areas of Study__](#future-areas-of-study)**  

# Project Overview
Steam is a web-based service and application that provides a destination for buying, playing, discussing, and creating video games for the PC and Steam Deck. Steam's library consists of over 100k games from AAA to indie and everything in between. Additionally, Steam provides a service for PC software to include but not limited to:
image editing, video editing, and music production. Steam is a service that allows an individual to meet new people, join groups, form clans, chat in-game, and much more with nearly 100 million users worldwide. Additionally, no subscription is required and allows you to purchase games and software on your PC.

The intent of the project is to perform EDA on a data set created using Steam APIs from a data analyst. Furthermore, exploring the data will allow initial project intentions to expand as analysis is conducted. 

# Project Proposal
The approach for EDA on a Steam Games data set is to assess and find interesting correlations between video games and associated data. Initial review of the Steam Games CSV from Kaggle led to an approach to find a correlation of video game success related to review ratings (Metacritic Rating and Reviewer Rating). Additionally, the initial approach was to correlate these findings with data associated with a user completing the game. Furthermore, these findings were to be correlated with game tag categories. 

Further assessment of the data revealed that data associated with time to complete the game did not connect to how many users did in fact complete the game and any additional trophies. Additionally, cleaning of the Game Tags associated with each game revealed through research that game tags are numerous, weighted with an ordered process based on Steam Game guidelines, and would yield a skewed analysis of that portion of the data. 

These findings in initial EDA led to the final approach for this project. I would compare Metacritic Ratings, Reviewer Ratings, and Positivity Ratios. Did the higher or lower Metacritic Rating correlate with the Reviewer Ratings and Positivity Ratios? 

# Source of Data
The source of the data came from Kaggle Data Sets, specifically https://www.kaggle.com/datasets/gruffgemini/steam-games-dataset

This data set (steam_games_dataset, AKA steam_games_df) contained 11 columns of data points:  

**id:** Game ID on steam platform

**name:** Game name as appears on Steam platform  

**year:** Release year  

**metacritic_rating:** Metacritic rating (the larger the better)  

**reviewer_rating:** Game rating given by users on the 0-10 scale (the larger the better)  

**positivity_ratio:** Number of positive reviews divided by the number of negative reviews  

**to_beat_main:** Time required to beat the main plot of the game    

**to_beat_extra:** Time required to beat the main and optional objectives of the game  

**to_beat_completionist:** Time required to complete every single objective of the game including gathering all collectibles  

**extra_content_length:** The difference between completionist time and extra time

**tags:** User tags (features) of the game separated by vertical lines

# Data Cleaning and Transformation
The initial data set (steam_games_df) contained 63,543 rows and 11 columns. The first portion of the data cleaning involved removal of the game 'id', which would not be needed for the EDA. Afterwards, I reduced the 'tags' to only include the first tag listed. Initially I was going to group based on the tag type and perform analysis on these groupings. However, research into how Steam employs tags resulted in a stop on that approach of analysis. In short, tags can be created by developer, however tags can be added by users as well. The tag length on some games can be upwards of 20 plus tags and they are weighted based on a system explained in Steam documentation. This type of EDA would not perform the necessary script required to extract relevant data from the tags. I kept the tag information in the cleaned data frame, however did not use the column data. 

Once the data was cleaned with no ID, removal of any NaN values in the data was the next step. I dropped all rows that had any NaN values for any of the column data entries. This reduced the data frame from 63,543 rows and 11 columns to 2823 rows and 10 columns since the game ID was now gone. Setup was now ready with all 2823 rows having complete data for all 10 columns. From here my approach for the project goal was ready. 

Creation of overall description statistic visualizations occurred followed by deliberate extraction of Metacritic and reviewer ratings along with positivity ratio comparison to said data. 

I decided to approach the data comparison based on the Top 25 and Bottom 25 Games that had the highest and lowest Metacritic / reviewer ratings respectively. Additionally, this data was compared with positivity ratios to find correlation or outliers. 

# Contextual Visualizations
What visualizations are needed to understand the data?

Below is a Descriptive Statistics Chart that provides basic statistical information. We are able to see the values associated with statistical information related to the Metacritic ratings, reviewer ratings, and positivity ratios for our cleaned data frame.
Of note, we can see that there are some positivity ratios well beyond several standard deviations from the mean.

![Descriptive Statistics](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/descriptive_statistics_for_metacritc_reviewer_ratings_and_positivity_ratio.png)

Furthermore, we can see distribution charts of the Metacritic ratings, reviewer ratings, and positivity ratios of our cleaned data frame. This provides a clear graph of the descriptive statistics per category.

![Distribution of Metacritic Ratings](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/distribution_of_metacritic_ratings.png)

![Distribution of Reviewer Ratings](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/distribution_of_reviewer_ratings.png)

![Distribution of Positivity Ratio](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/distribution_of_positivity_ratios.png)

The following visualizations provide a better understanding of the top and bottom 25 games from our data set in relation to Metacritic and reviewer ratings. 

![Top 25 Games with Highest Metacritic Ratings](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/top_25_games_with_highest_metacritic_ratings_barchart.png)

![Top 25 Metacritic Ratings Games with Reviewer Scores](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/top_25_games_with_highest_reviewer_ratings_barchart.png)

![Bottom 25 Games with Lowest Metacritic Ratings](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/bottom_25_games_with_lowest_metacritic_ratings_barchart.png)

![Bottom 25 Metacritic Rating Games with Reviewer Scores](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/bottom_25_games_with_lowest_reviewer_ratings_barchart.png)

# Specific Visualizations - Results
This EDA led to the analysis of the positivity ratios in relation to the top and bottom 25 Metacritic ratings games. This analysis allowed us to confirm that top Metacritic rated games did indeed have positive positivity ratios and, in many cases, high ratios. The same is true for the bottom Metacritic rated games. However, this analysis led to outliers with extremely high positivity ratios in the top rated games and outliers with higher positivity ratings in the bottom rated games than expected. 

The following visualizations portray the positivity ratios independently.

![Positivity Ratio of the Top 25 Metacritic Ratings Games](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/positivity_ratio_of_the_top_25_metacritic_ratings_games.png)

![Positivity Ratio of the Bottom 25 Metacritic Ratings Games](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/positivity_ratio_of_the_bottom__25_metacritic_ratings_games.png)

The following visualizations overlay the Metacritic rating with the positivity ratio, which yields a clear picture of outliers in both the top and bottom 25 games. 

![Positivity Ratio of Top 25 Metacritic Ratings Games & Metacritic Rating](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/positivity_ratio_of_top_25_metacritic_ratings_games_and_metacritic_rating_overlay.png)

![Positivity Ratio of Bottom 25 Metacritic Ratings Games & Metacritic Rating](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/positivity_ratio_of_bottom_25_metacritic_ratings_games_and_metacritic_rating_overlay.png)

# Key Insights
The top and bottom 25 games based on Metacritic and reviewer ratings provided insight into what a user could expect from an experience perspective. However, this data set was reduced down to less than 3k games from 68k due to missing values. Although these games did in fact have high and low ratings, this data set does not include other games of similar ratings. More inclusive data sets and expanding the list beyond 25 will provide a better understanding of quality or poor-quality games based on these parameters. 

However, this data set did yield interesting results. As we can see in the top 25 positivity ratio charts, many of the highest Metacritic rated games had positivity ratios below 20 and even 10. These are still high ratios, meaning 10-20 positive to 1 negative, however, these games are among the highest Metacritic rated. Further insight into the reviewer comment sentiment will produce a better understanding of the quality of the game from the user perspective. 

Conversely, we can see some outliers in the bottom 25 games based on the positivity ratio overlay with Metacritic ratings. Specifically, the games (Shaq Fu: A Legend Reborn, Hello Neighbor, Super Duper Party Pooper, and Hatred) all had positivity ratios above 3. For games having such a low Metacritic review, we would not expect to have 3-1 users have a positive review.

# Recommendations
Although this analysis can be expanded with more complete data sets, it does yield an good way to search for games that will likely lead to a positive or negative experience. Specifically, games that have a high positivity ratio in conjunction with high Metacritic ratings should be a great experience for the end user if that genre of game is what they like. 

# Future Areas of Study
I postulate that data sets that have more complete information will yield similar results but for more games. Additionally, conducting EDA on how many of top or bottom games where the user completed the game should yield a better measure of analysis whether the game is good or not. If these data sets are not available, then getting permission from Steam to use their Steam APIs will be necessary to extract the data needed to conduct further analysis. 
