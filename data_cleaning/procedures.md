# Data Cleaning Steps Documentation

## Section 1: Uploading .csv Files

### Upload to Google Cloud Big Query

1. [monthly_listeners.csv](https://github.com/JLeData/music-genre-and-artist-analysis/blob/main/datasets/monthly_listeners.csv)
2. [most_streamed_artist.csv](https://github.com/JLeData/music-genre-and-artist-analysis/blob/main/datasets/most_streamed_artists.csv)
3. [spotify_most_streamed.csv](https://github.com/JLeData/music-genre-and-artist-analysis/blob/main/datasets/spotify_most_streamed.csv)
4. [spotify_song_attributes.csv](https://github.com/JLeData/music-genre-and-artist-analysis/blob/main/datasets/spotify_song_attributes.csv)

-- Section 2: Data Cleaning and Preparation

### Step 1: Explore the Data
- Examine the structure and contents of the dataset.

### Step 2: Handling Fields

### monthly_listeners.csv
- **Keep all fields**
  - **Reasoning:**
    - **Artist:** Primary identifier connecting all datasets.
    - **Listeners:** Quantifies fan base.
    - **Daily Trend:** Tracks daily popularity changes.
    - **Peak:** Highlights historical performance peaks.
    - **PkListeners:** Quantifies listeners at the popularity peak.

### most_streamed_artist.csv
- **Keep all fields**
  - **Reasoning:**
    - **Artist:** Primary identifier connecting all datasets.
    - **Streams:** Quantifies overall popularity.
    - **Daily:** Indicates average daily streams.
    - **As lead:** Specifies streams for primary work.
    - **Solo:** Quantifies streams for solo projects.
    - **As feature:** Counts streams when featured.


### spotify_most_streamed.csv
- **Keep all fields**
  - **Reasoning:**
    - **Artist:** Primary identifier connecting all datasets.
    - **Title:** Lists names of popular songs on Spotify.
    - **Streams:** Quantifies total streams, reflecting song popularity.
    - **Daily:** Likely represents average daily streams, showing ongoing popularity.

### spotify_song_attributes.csv
- **Selected Fields:**
  - **artistName:** Identifies the artist.
  - **trackName:** Lists the song.
  - **genre:** Represents the song's genre.

### Note:
- Prioritizing simplicity and emphasizing track engagements.
- Though it provides a lot of interesting data, the file was included to connect artist and title with a genre.
- spotify_most_streamed.csv file to be removed. unable to modify table due to free trial of Big Query updates and changes still logged.
- dataset is similar to most_streamed_artist, spotify_song_attributes

## Step 3: Change Column Names
- Renaming tables to lowercase for consistent and oranized structure:

-- Rename columns for monthly_listerners
ALTER TABLE music-artist-411616.spotify.monthly_listeners
RENAME COLUMN artist_ref TO artist_table_1;

ALTER TABLE music-artist-411616.spotify.monthly_listeners
RENAME COLUMN Listeners TO listener_fans;

ALTER TABLE music-artist-411616.spotify.monthly_listeners
RENAME COLUMN Daily_Trend TO daily_trend;

ALTER TABLE music-artist-411616.spotify.monthly_listeners
RENAME COLUMN PEAK TO peak;

ALTER TABLE music-artist-411616.spotify.monthly_listeners
RENAME COLUMN PkListeners to peak_listeners;

-- Rename columns for most_streamed_artist
ALTER TABLE music-artist-411616.spotify.most_streamed_artists
RENAME COLUMN Artist TO artist_table_2;
	
ALTER TABLE music-artist-411616.spotify.most_streamed_artists
RENAME COLUMN Streams TO streams_by_artist;

ALTER TABLE music-artist-411616.spotify.most_streamed_artists
RENAME COLUMN Daily TO daily_streams;

ALTER TABLE music-artist-411616.spotify.most_streamed_artists
RENAME COLUMN As_lead TO as_primary_artist;

ALTER TABLE music-artist-411616.spotify.most_streamed_artists
RENAME COLUMN Solo TO solo_projects;

ALTER TABLE music-artist-411616.spotify.most_streamed_artists
RENAME COLUMN As_feature TO featured_guest;

-- Rename columns for spotify_most_streamed
ALTER TABLE music-artist-411616.spotify.spotify_most_streamed
RENAME COLUMN Artist_and_Title TO artist_table3_song_title;
--note: rename the field for now but plans on separating into their own columns

ALTER TABLE music-artist-411616.spotify.spotify_most_streamed
RENAME COLUMN Streams TO stream_song;
--note: chose this naming convention since there are other fields that has stream in it as well, but this one is based on the song played.

ALTER TABLE music-artist-411616.spotify.spotify_most_streamed
RENAME COLUMN Daily TO daily_song;
--note: same situation as stream_song

-- Rename columns for spotify_song_attributes
ALTER TABLE music-artist-411616.spotify.spotify_song_attributes
RENAME COLUMN trackName TO song_title;

ALTER TABLE music-artist-411616.spotify.spotify_song_attributes
RENAME COLUMN artistName TO artist_table_4;

## Step 4: Clean Up Fields and Data Types

### Clean Up Fields

-- Delete fields irrelevant to analysis
ALTER TABLE music-artist-411616.spotify.spotify_song_attributes
DROP COLUMN energy;
-- Testing to see if it runs

ALTER TABLE music-artist-411616.spotify.spotify_song_attributes
DROP COLUMN key,
DROP COLUMN mode;
-- Dropping multiple columns test - success

-- Alter table statements to drop columns
ALTER TABLE music-artist-411616.spotify.spotify_song_attributes
DROP COLUMN msPlayed,
DROP COLUMN danceability,
DROP COLUMN loudness,
DROP COLUMN speechiness,
DROP COLUMN acousticness,
DROP COLUMN instrumentalness,
DROP COLUMN liveness,
DROP COLUMN valence,
DROP COLUMN tempo,
DROP COLUMN type,
DROP COLUMN id,
DROP COLUMN uri,
DROP COLUMN track_href,
DROP COLUMN analysis_url,
DROP COLUMN duration_ms,
DROP COLUMN time_signature;

-- Attempt at using BEGIN, ROLLBACK, COMMIT, but an error message occurred saying transaction statements are not supported.
-- Alter table is a success, 3 columns remain: song_title, artist_table_4, and genre

-- Due to using the free version of Big Query, there are limitations on updating data types.

-- Example (not applicable due to limitations):
UPDATE music-artist-411616.spotify.most_streamed_artists
SET daily_streams = CEIL(daily_streams);

-- This query would have been utilized to update the floats into whole numbers for the analysis, but there is a restriction in the free version.
-- Changing data types is not allowed as well to make it consistent with the other fields.
-- A syntax error appears saying changes to data type can affect the data

-- Attempt to modify the data type (not applicable due to limitations):
ALTER TABLE music-artist-411616.spotify.most_streamed_artists
MODIFY daily_streams INTEGER;

-- This query can modify the data type, but unable to do so using the free version.
-- I will set limitations on this table, knowing that there are decimal values while looking at the results of the analysis.
-- It does not make much sense that it is not whole numbers as these are average results of these fields, but that will be taken into account.


-- Add two new columns to your table
ALTER TABLE music-artist-411616.spotify.spotify_most_streamed
ADD COLUMN artist_name_3 STRING,
ADD COLUMN song_title STRING;

-- Unable to update columns due to free trial limitation
-- This query would be able to separate artist from song title in spotify_most_streamed
-- Update the new columns by splitting the existing column
UPDATE music-artist-411616.spotify.spotify_most_streamed
SET
  artist_name_3 = SPLIT(artist_and_title, ' - ')[OFFSET(0)],
  song_title = SPLIT(artist_and_title, ' - ')[OFFSET(1)];

NOTE:
- plan on removal of spotify_most_streamed.csv
- data available in other tables and unable to split fields due to limitations of free trial access.

-- Remove spotify_most_streamed
DROP TABLE music-artist-411616.spotify.spotify_most_streamed

- Keep information in readme to show limitations on project and direction it has taken

## Step 5: Create tables for cleaning null values

### Table creation

1. Popular Genre Analysis
-- Create a new table for popular genre analysis by taking fields
-- artist_name, genre, streams_by_artist, song_title
CREATE TABLE music-artist-411616.combined.popular_genre_analysis AS
SELECT DISTINCT artist_table_2,
       genre,
       streams_by_artist,
       song_title
FROM music-artist-411616.spotify.most_streamed_artists AS two
JOIN music-artist-411616.spotify.spotify_song_attributes AS four
ON two.artist_table_2 = four.artist_table_4
JOIN music-artist-411616.spotify.monthly_listeners AS one
ON four.artist_table_4 = one.artist_table_1;

note: created separate file location to save combined fields

2. Artist Popularity Assessment

CREATE TABLE music-artist-411616.combined.artist_popularity_assessment AS
SELECT DISTINCT artist_table_1,
       listener_fans,
       daily_streams,
       daily_trend,
       streams_by_artist,
       peak,
       peak_listeners
FROM music-artist-411616.spotify.most_streamed_artists AS two
JOIN music-artist-411616.spotify.spotify_song_attributes AS four
ON two.artist_table_2 = four.artist_table_4
JOIN music-artist-411616.spotify.monthly_listeners AS one
ON four.artist_table_4 = one.artist_table_1;



3. popular genre analsyis

CREATE TABLE music-artist-411616.combined.emerging_genre AS
SELECT DISTINCT artist_table_1,
       genre,
       listener_fans,
       daily_trend,
       song_title
FROM music-artist-411616.spotify.most_streamed_artists AS two
JOIN music-artist-411616.spotify.spotify_song_attributes AS four
ON two.artist_table_2 = four.artist_table_4
JOIN music-artist-411616.spotify.monthly_listeners AS one
ON four.artist_table_4 = one.artist_table_1;


note: remade tables using DISTINCT to delete any duplicates
limitations: using the query above as an inner join means that null values from the different tables 
that do not match will not appear. since the data are from spotify but uploaded by different users, take
into consideration that some artist did not appear on the tables.

## Step 6: Null values
### Addressing the null values
-- look for amount of null values within each field
-- checking artist_popularity_asessment table
SELECT *
FROM music-artist-411616.combined.artist_popularity_assessment
WHERE listener_fans IS NULL
OR daily_streams IS NULL
OR daily_trend IS NULL
OR streams_by_artist IS NULL;
-- 1 artist with daily_streams as null

-- emerging_genre table
SELECT *
FROM music-artist-411616.combined.emerging_genre
WHERE artist_table_1 IS NULL
OR listener_fans IS NULL
OR daily_trend IS NULL
OR song_title IS NULL
OR genre IS NULL;
-- 80 null values under genre.

-- Popular_genre_analysis table
SELECT *
FROM music-artist-411616.combined.popular_genre_analysis
WHERE artist_table_2 IS NULL
OR streams_by_artist IS NULL
OR song_title IS NULL
OR genre IS NULL;
-- 80 null values under genre

-- addressing null values in genre
-- the plan to fill these null is to look up the songs on spotify and look at genres
-- find artist in existing table and match genre to others
-- limitations maybe that song potentially is not the same genre and be a mix of genres
-- Utilize website https://everynoise.com/ to find artist genre and replace null values

NOTE: Switch to Billing mode to access tools for Google Big Query since changing null values requires it for this project.

-- example of existing artist
UPDATE music-artist-411616.combined.emerging_genre
SET genre = 'chillwave'
WHERE artist_table_1 = 'ODESZA';
-- revise popular_genre_analysis as well
-- majority of nulls will be updated the same so all will not be posted
UPDATE music-artist-411616.combined.popular_genre_analysis
SET genre = 'edm'
WHERE artist_table_2 = 'Cheat Codes';

UPDATE music-artist-411616.combined.emerging_genre
SET genre = 'edm'
WHERE artist_table_1 = 'Cheat Codes';

-- setup to check for artist exist in table and rename genre
select *
from music-artist-411616.combined.popular_genre_analysis
where genre is null;
-- look for null values and artist
select *
from music-artist-411616.combined.popular_genre_analysis
where artist_table_2 = INSERT ARTIST NAME
-- check for artist if they have multiple songs and same genre
UPDATE music-artist-411616.combined.popular_genre_analysis
SET genre = INSERT GENRE NAME
WHERE artist_table_2 = INSERT ARTIST NAME

UPDATE music-artist-411616.combined.emerging_genre
SET genre = INSERT GENRE NAME
WHERE artist_table_1 = INSERT ARTIST NAME
-- change both tables since they both contain genre
-- updated all null values

## Step 7: Inserting new fields
-- Creating new fields to classify sub genres into generic genres
-- used chatgpt to help classify each sub genre
-- limitation: trusting chatgpt to classify each subgenre to the best of its abilities
-- provided information to chatgpt and the general genres to classify
-- if it does not fall into those categories, it will go into other

-- create new field
ALTER TABLE `music-artist-411616.combined.emerging_genre`
ADD COLUMN classification STRING;

-- update classification to generic genres
-- first test
UPDATE `music-artist-411616.combined.emerging_genre`
SET classification = 'pop'
WHERE genre IN ('pop','dance pop')
-- success
-- move on to the rest, list provided [here]

-- update pop
UPDATE `music-artist-411616.combined.emerging_genre`
SET classification = 'pop'
WHERE genre IN ('baroque pop','canadian pop','bedroom pop','folk-pop','australian pop',
        'classic bollywood','acoustic pop','clasic pakistani pop','la pop','gauze pop',
        'social media pop','gen z singer-songwriter','irish singer-song-writer','nyc pop',
        'inide pop','candy pop','chill pop', 'irish pop','nz pop','experimental pop',
        'modern alternative pop','latin pop','german pop','chinese pop','belgian pop',
        'bubblegum pop','bollywood','hawaiian','girl group','new wave pop')

-- will look back to see if any null values exist and re apply query
-- due to naming convention on chatgpt, some names are off and will have to be re-examined
-- will change the broader classifications and go back for the smaller ones

-- update rock
UPDATE `music-artist-411616.combined.emerging_genre`
SET classification = 'rock'
WHERE genre IN ('alt z','alternative metal','modern alternative rock','modern rock',
      'album rock','classic rock','piano rock','australian rock','alternative rock','grunge',
      'indie rock','glam metal','garage rock','permanant wave','jazz rock','blues rock',
      'plugg','lilith','new wave pop','dance rock','celectic rock','classsical rock',
      'british indie rock','melbourne bounce international','hard rock');

-- update edm
UPDATE `music-artist-411616.combined.emerging_genre`
SET classification = 'edm'
WHERE genre IN ('brostep','electropop','indietronica','electro house','australian dance',
      'dutch edm','eurodance','complextro','german dance','belgian dance','chicago house',
      'downtempo','brazilian bass','dancefloor dnb','bubblegum dance',
      'melbourne bounce international','electronic','minimal tech house','belgian edm',
      'nordic house','big room')

-- update hip-hop/rap
UPDATE `music-artist-411616.combined.emerging_genre`
SET classification = 'hip-hop/rap'
WHERE genre IN ('chicago rap','emo rap','melodic rap','hip hop','pop rap','atl hip hop',
      'desi hip hop','dfw rap','canadian hip hop','french shoegaze','australian hip hop',
      'indie pop rap','hip pop','drift phonk','conscious hip hop','punjabi hip hop',
      'reggaeton','metropopolis','ohio hip hop','latin hip hop','brooklyn drill',
      'canadian latin','alternative hip hop','deep underground hip hop','chill phonk',
      'melodic drill','memphis hip hop','aesthetic rap','hawaiian hip hop',
      'phonk brasileiro','indie pop rap','pluggnb');

--update r&b/soul
UPDATE `music-artist-411616.combined.emerging_genre`
SET classification = 'r&b/soul'
WHERE genre IN ('bedroom soul','canadian contemporary r&b','r&b','alternative r&b',
      'chill r&b','indonesian r&b','neo soul','british soul','soul jazz');

-- update classical
UPDATE `music-artist-411616.combined.emerging_genre`
SET classification = 'classical'
WHERE genre IN ('classical','art pop','british orchestra');

-- update lo-fi/chill
UPDATE `music-artist-411616.combined.emerging_genre`
SET classification = 'lo-fi/chill'
WHERE genre IN ('sad lo-fi','lo-fi chill','ambient worship');

-- update anime
UPDATE `music-artist-411616.combined.emerging_genre`
SET classification = 'anime'
WHERE genre IN ('pov: indie','anime','otacore');

--update other
UPDATE `music-artist-411616.combined.emerging_genre`
SET classification = 'other'
WHERE genre IN ('escape room','broadway','movie tunes','weirdcore','chutney');

-- go back and adjust null values
-- readjusted classifcations and null values
-- used chatgpt to help reclassify subgenres
-- genres are:
-- pop, rock, hip-hop/rap, film score, edm, metal, indie, classical, r&b/soul,other, country, jazz/blues 

-- decided to delete popular_genre_analysis as emerging genre contains enough data to use
ALTER TABLE music-artist-411616.combined.emerging_genre
RENAME TO genre_assessment
-- renamed table

### Data cleaning done and ready for analysis


