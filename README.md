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
Steam is a web based service and application that provides a destination for buying, playing, discussing, and creating video games for the PC and Steam Deck. Steam's library consists of over 100k games from AAA to indie and everything in between. Additionally, Steam provides a service for PC software to include but not limited to:
image editing, video editing, and music production. Steam is a service that allows an individual to meet new people, join groups, form clans, chat in-game, and much more with nearly 100 million users worldwide. Additionally, no subscription is required and allows you purchase games and software on your PC.

The intent of the project is to perform EDA on a data set created using Steam APIs from a data analyst. Furthermore, exploring the data will allow initial project intentions to expand as analyis is conducted. 

# Project Proposal
The approach for EDA on a Steam Games data set is to assess and find interesting correlations between video games and associated data. Initial review of the Steam Games CSV from Kaggle led to an appoach to find a correlation of video game success related to review ratings (Metacritic Rating and Reviewer Rating). Additionally, the intial approach was to correlate these findings with data associated with a user completing the game. Furthermore, these findings were to be correlated with game tag categories. 

Further assessment of the data reveled that data associated with time to complete the game did not connect to how many users did in fact complete the game and any additional trophies. Additionally, cleaning of the Game Tags associcated with each game revealed through research that game tags are numerous, weighted with an ordered process based on Steam Game guidelines, and would yield a skewed analysis of that portion of the data. 

These findings in initial EDA led to the final approach for this project. I would compare Metacritic Ratings, Reviewer Ratings, and Positivity Ratios. Did the higher or lower Metacritic Rating correlate with the Reviewer Ratings and Positivity Ratios? 

# Source of Data
The source of the data came from Kaggle Data Sets, specifically https://www.kaggle.com/datasets/gruffgemini/steam-games-dataset

This data set (steam_games_dataset, AKA steam_games_df) contained 11 columns of data points:
### id: Game ID on steam platform

### name: Game name as appears on Steam platform  

### year: Release year  

### metacritic_rating: Metacritic rating (the larger the better)  

### reviewer_rating: Game rating given by users on the 0-10 scale (the larger the better)  

### positivity_ratio: Number of positive reviews divided by the number of negative reviews  

### to_beat_main: Time required to beat the main plot of the game    

### to_beat_extra: Time required to beat the main and optional objectives of the game  

### to_beat_completionist: Time required to complete every single objective of the game including gathering all collectibles  

### extra_content_length: The difference between completionist time and extra time

### tags: User tags (features) of the game separated by vertical lines

# Data Cleaning and Transformation

The initial data set (steam_games_df) contained 63,543 rows and 11 columns. The first poriton of the data cleaning involved removal of the game 'id', which would not be needed for the EDA. Afterwards, I reduced the 'tags' to only inlcude the first tag listed. Initially I was going to group based on the tag type and perform analysis on these groupings. However, research into how Steam employs tags resulted in a stop on that approach of analysis. In short, tags can be created by developer, however tags can be added by users as well. The tag length on some games can be upwards of 20 plus tags and they are weighted based on a system explained in Steam documentation. This type of EDA would not perform the necessary script required to extract relevant data from the tags. I kept the tag information in the cleaned data frame, however did not use the column data. 

Once the data was cleaned with no ID, removal of any NaN values in the data was the next step. I dropped all rows that had any NaN values for any of the column data entries. This reduced the data frame from 63,543 rows and 11 columns to 2823 rows and 10 columns since the game ID was now gone. Setup was now ready with all 2823 rows having complete data for all 10 columns. From here my approach for the project goal was ready. 

Creation of overall description statistic visualizations occured followed by deliberate extraction of metacritic and reviewer ratings along with positivity ratio comparison to said data. 

I decided to approach the data comparison based on the Top 25 and Bottom 25 Games that had the highest and lowest metacritic / reviewer ratings respectively. Additionally, this data was compared with positivty ratios to find correlation or outliers. 

# Contextual Visualizations
What visualizations are needed to understand the data?

![Descriptive Statistics](https://github.com/Jeremy-Amell/Steam-Games-EDA/blob/main/images/descriptive_statistics_for_metacritc_reviewer_ratings_and_positivity_ratio.png)