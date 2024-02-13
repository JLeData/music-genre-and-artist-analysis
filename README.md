# Music-Genre-and-Artist-Analysis

## Table of Contents

- [Project Overview](#project-overview)
- [Objectives](#objectives)
- [Data Source](#data-source)
- [Tools](#tools)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results and Findings](#results-and-findings)
- [Limitations](#limitations)
- [References](#references)
- [Personal Goals](#personal-goals)

## Project Overview

This project delves into the analysis of multiple music datasets sourced from Kaggle, focusing on understanding Spotify listeners' preferences. The primary goal is to uncover insights into genre and artist popularity dynamics and their impact on overall music consumption trends within the platform. By conducting thorough analyses, the project aims to shed light on emerging patterns and trends within the music industry.

## Objectives


1. Genre Popularity Analysis:
   - Analyze music genre popularity on Spotify using Kaggle data. Determine the most popular genre by total listeners and explore genre diversity.

2. Artist Popularity Assessment:
   - Assess top 25 artist popularity on Spotify with Kaggle data. Analyze metrics like total listeners and daily streams.

3.Top Trending Artists:
   - Identify trending Spotify artists from Kaggle data. Explore overlap with top 25 artists, assessing potential for continued rise.

## Data Source

The project utilizes multiple datasets related to the Spotify app, encompassing information on the top 200 streamed songs, artist details, listener engagement metrics, and additional contextual data.

**Data Source:**

1. [Spotify Song Attributes](https://www.kaggle.com/datasets/byomokeshsenapati/spotify-song-attributes)

2. [Spotify most streamed songs](https://www.kaggle.com/datasets/meeratif/spotify-most-streamed-songs-of-all-time)

3. [Spotify Stats](https://www.kaggle.com/datasets/meeratif/spotify-most-streamed-artists-of-all-time)

4. [Spotify top artists by monthly listeners](https://www.kaggle.com/datasets/meeratif/spotify-top-artists-by-monthly-listeners)

## Tools
- Excel: Retrieve data
     - [Files here](https://github.com/JLeData/music-genre-and-artist-analysis/tree/main/datasets)
       
- SQL: Data cleaning
     - Google Cloud BigQuery
       
- Tableau: Create dashboards and visuals
     - Tableau Public
 
## Data Cleaning and Preparation

Perform the following tasks:

1. Data loading and inspection

2. organize fields and records

3. Handle missing values

4. Data cleaning and formatting

Cleaning log can be found [here.](https://github.com/JLeData/music-genre-and-artist-analysis/blob/main/data_cleaning/procedures.md)
## Exploratory Data Analysis

Answer key questions:

1. What is the most popular genre?

2. Who is the most popular artist?

3. Is there any correlation between the two?

4. Who are the top 5 potential upcoming artist not in the top 25?


## Data Analysis

Visual created for data analysis

Present links to Tablea Public and screenshots of data visualizations in this section.

### Genre Popularity Assessment

![Genre Analysis](https://github.com/JLeData/music-genre-and-artist-analysis/blob/main/visuals/Genre%20and%20Song%20Distribution.png)

This is an interactive dashboard. [Click here to interact with it.](https://public.tableau.com/app/profile/jordan.le6101/viz/artistgenreanalysis/GenreandSongDistribution)

### Top Artists by Spotify Listeners

![Top Artist](https://github.com/JLeData/music-genre-and-artist-analysis/blob/main/visuals/Artist%20Bar%20Chart.png)

[Link to visual.](https://public.tableau.com/app/profile/jordan.le6101/viz/artist_assessment/Sheet1)

### Top Trending Artists

![Top Trending](https://github.com/JLeData/music-genre-and-artist-analysis/blob/main/visuals/Trending%20Artists.png)

[Link to visual.](https://public.tableau.com/app/profile/jordan.le6101/viz/ArtistsbyTrending/TrendingArtists)

## Results and Findings

1. What is the most popular genre?
   - Pop seems to be the most popular genre according to data from Spotify Listeners.

2. Who is the most popular artist?
   - By Listeners and fan count, The Weeknd with the genre of R&B / Soul is the most popular artist on Spotify.

3. Is there any correlation between the two?
   - Pop might indicate a broader appeal among Spotify listeners with many artists being on the top 25 listeners.
   - The Weeknd has a large presence as the only R&B / Soul artist in the top 25 having the highest listener/fan base. Potential for a mixture of other genres with a main focus on R&B / soul has to be taken into consideration.
   - Pop may be a very dominate genre at have the most songs in the dataset, but other genres such as Rock and Hip-Hop / Rap appear at the top as well.

4. Who are the top 5 potential upcoming artist not in the top 25?
   - The top trending artists according to the visualizations are Olivia Rodrigo, Doja Cat, Cardi B, Kacey Musgraves, Dove Cameron, and Anirudh Ravichander. 3/5 are Pop genre, 1 Country, and last is Hip-Hop / Rap.
   - Of these 5 artists, Doja Cat is in the top 25 Spotify listeners and as of this dataset posting, the highest trending artist.
   - The other 4 artist seem to be high trending artist which Kacey Musgraves stands out the most since Country is on the lower end of the listener distribution. Being high up on trending shows the potential of this artist in a genre with very little listeners in comparison to, for example, Pop.

## Limitations

These were some limitations encountered during this project:

1. Data timeliness:
  - Information used is provided by Kaggle and has been updated in November of 2023.
  - Potential new artist and new songs after the dataset had been provided is not within the dataset.
  - Trend and listener count has much room for change over time and the potential impact of it.

2. Lack of primary keys:
  - Data provided is from Spotify, but connecting the data relies on the artist within it as the datasets are separate from each other.
  - The data is not 1:1, some values will not be matched with others which will result not being in the dataset and provides the challenge of cleaning it.
  - Null values will exist and have to be cleaned.

3. Google Big Query trial version constraint:
   - Initially started project in the trial version of Google Big query.
   - Limited on what functions were able to be used.
   - Upgraded needed to properly clean data and create new tables.
   - Not all datasets were used due to trying to use trial version.

4. Genre classification challenges
   - Categorization of music into specific genres can be subjective and may vary between different sources.
   - Potential for genre-based inconsistencies.
   - Artist categorized into one genre when there is potentially songs they branched out their music genre in. Dataset based on the majority of their music's genre classification was.
   - Chatgpt categorization of music genres to sub-genres may be inconsistent.

5. Data is limited source to Spotify users only.
   - There are many other music streaming services other than Spotify. This is strictly data in regards to Spotify users.
   - Findings may not fully represent the broader landscape of music consumption across various platforms.


## References

1. [Kaggle](https://www.kaggle.com/)
2. [Big Query](https://cloud.google.com/bigquery)
3. [Tableau Public](https://public.tableau.com/app/discover)
  
## Personal Goals

### Technical Skills:

1. SQL Mastery:
   - Enhance proficiency in SQL through data loading and cleaning with Google BigQuery.

2. Tableau Proficiency:
   - Strengthen visualization and storytelling skills using Tableau Public for insightful dashboards.
     
### Project Management:

1. Structured Analysis:
   - Apply a systematic approach from data acquisition to presentation in data analysis.

2. Iterative Learning:
   - Embrace iterative learning for continuous improvement in analysis techniques and visualization skills.

## End of Project

---

## Project Reflection

### Thank You

I would like to express my sincere gratitude to the following individuals and platforms for their contributions and support throughout this project:

1. **Kaggle Community**: Thank you to the Kaggle community for providing valuable datasets, resources, and a collaborative space for data enthusiasts.
  - Byomokesh Senapati for providing [Spotify Song Attributes](https://www.kaggle.com/datasets/byomokeshsenapati/spotify-song-attributes)
  - meer atif magsi for providing [Spotify most streamed songs](https://www.kaggle.com/datasets/meeratif/spotify-most-streamed-songs-of-all-time), [Spotify Stats](https://www.kaggle.com/datasets/meeratif/spotify-most-streamed-artists-of-all-time), and [Spotify top artists by monthly listeners](https://www.kaggle.com/datasets/meeratif/spotify-top-artists-by-monthly-listeners)  

3. **Google BigQuery**: Appreciation to Google BigQuery for the powerful data analytics capabilities and tools that significantly contributed to the success of this project.

4. **Tableau Public**: Special thanks to Tableau Public for enabling me to create engaging and insightful data visualizations for this analysis.

5. **Open Source Community**: A big thank you to the broader open-source community for creating and maintaining the tools and libraries that made this project possible.

6. **Peers and Mentors**: Gratitude to my peers and mentors who provided guidance, feedback, and support throughout the development of this project.

Your contributions and support have been invaluable, and I am truly thankful for the collaborative and inspiring environment that facilitated the success of this project.


