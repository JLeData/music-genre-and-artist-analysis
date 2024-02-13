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
- [Project Reflection](#project-reflection)

## Project Overview

This project aims to analyze various music datasets from Kaggle, with a focus on understanding the preferences of Spotify listeners. The primary objective is to uncover insights into the dynamics of genre and artist popularity and their influence on overall music consumption trends on the platform. Through comprehensive analyses, the project seeks to reveal emerging patterns and trends within the music industry.

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

4. Genre classification challenges:
   - Categorization of music into specific genres can be subjective and may vary between different sources.
   - Potential for genre-based inconsistencies.
   - Artist categorized into one genre when there is potentially songs they branched out their music genre in. Dataset based on the majority of their music's genre classification was.
   - Chatgpt categorization of music genres to sub-genres may be inconsistent.

5. Data is limited source to Spotify users only:
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

I want to give a big shoutout to these platforms for being awesome and helping me out during this project:

1. **Kaggle Community**: Acknowledgment to the Kaggle community for providing valuable datasets, resources, and a collaborative space.
   - Byomokesh Senapati for providing [Spotify Song Attributes](https://www.kaggle.com/datasets/byomokeshsenapati/spotify-song-attributes)
   - meer atif magsi for providing [Spotify most streamed songs](https://www.kaggle.com/datasets/meeratif/spotify-most-streamed-songs-of-all-time), [Spotify Stats](https://www.kaggle.com/datasets/meeratif/spotify-most-streamed-artists-of-all-time), and [Spotify top artists by monthly listeners](https://www.kaggle.com/datasets/meeratif/spotify-top-artists-by-monthly-listeners)  

2. **Google BigQuery**: Utilization of Google BigQuery's data analytics capabilities.

3. **Tableau Public**: Utilization of Tableau Public for creating data visualizations.
   
### Lessons Learnt

During this project, I really got the hang of using data analysis tools. It was fascinating to see how powerful they are for sorting and cleaning up loads of data. I found the process of tracking and tidying up data interesting and fun. Even though I ran into quite a few challenges, I had a blast working on it.

One thing that really stood out to me was how you can combine data from different sources. When I was doing the Google Data Analytics certificate, I learned a lot about using primary keys to link datasets. But in this project, there weren't any primary keys to work with. Did that leave room for mistakes? Definitely. But I took it as a chance to learn and figure things out. It was really satisfying to see all the data come together into something new and clean in the end.

Tableau Public turned out to be quite a different experience for me. As someone who's used to working with laser cutters and creating my own projects, I thought I'd naturally connect with Tableau's visualization tools. However, it ended up being the most challenging aspect of the project. Despite my creative nature, I found Tableau's interface and functions to have a steeper learning curve than I anticipated. While there are numerous tools available, navigating them didn't feel very intuitive.

With Tableau Public, there's a plethora of features and options at your fingertips, but figuring out how to use them effectively was a bit overwhelming at first. From creating interactive dashboards to designing visually appealing charts, there's a lot to learn and explore. However, with each attempt, I gained a deeper understanding of the software and its capabilities.

Throughout the project, I recognized the potential of Tableau Public and the possibilities it offers for creating impactful visuals. As someone with a creative nature, I was particularly drawn to the idea of using Tableau to unleash my creativity and transform data into compelling stories. However, I also realized that I need more practice to fully harness its capabilities and unleash my creativity to its fullest extent.

Despite the initial challenges, I'm eager to dive deeper into Tableau and refine my skills in data visualization. I believe that with continued practice and exploration, I'll be able to leverage Tableau to create visually stunning and insightful dashboards that truly resonate with audiences. As with any new tool or skill, practice makes perfect, and I'm excited to continue honing my abilities with Tableau Public in future projects

### What Would I Have Done Differently

I learned about using APIs to gather data from a friend midway through the project. It's something I'm interested in exploring further, especially for recording data from the Spotify API to get a more accurate representation. While I'm grateful for the Kaggle dataset for practice, tapping into the Spotify API seems like it could provide richer information.

Using the trial version of Google BigQuery at the start wasn't the best move. It was quite limiting in terms of what I could do with the data, and some datasets ended up unused because of it. Eventually, I upgraded to access all the tools, which was essential because the trial version didn't offer much.

With Tableau Public, I got a better sense of its potential for creativity in making visualizations. I think the visuals in this project could be much more appealing. Tableau Public has tools similar to Inkscape and Xtool, which I use often for laser cutting. However, it takes some digging to find those tools and figure out how to work with them while keeping the data visible. It's a bit challenging, but I see it as a task to tackle in the future.

### Overall

This project was a fascinating blend of my love for music and my interest in data analytics. It was eye-opening to see how diverse musical preferences can be, highlighting the unique connection each person has with music. Exploring this intersection provided valuable practice and deepened my understanding of data analysis tools. It's given me a clearer vision of how to leverage these tools in future projects.

