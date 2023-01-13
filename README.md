# R Project - Analyzing the Spotify Global Top 200 Weekly Charts and Building Linear Models

**Data sources:** 

<a href="https://spotifycharts.com/regional/global/weekly/latest">Spotify Charts</a>

<a href="https://developer.spotify.com/documentation/web-api/reference/#/operations/get-track">Spotify Audio Features</a>

<a href="https://www.rcharlie.com/spotifyr/">spotifyr R-Wrapper</a>

**Size of the dataset:** 9,500,447 bytes  (9.5 MB on disk)

---

## 1. Introduction

Spotify is the world's largest on-demand audio streaming subscription service that serves users with access to millions of songs from artists and podcasts across the globe. It has over 406 million monthly active users, out of which 180 million are paying subscribers (Spotify For the Record, 2022). With more than 82 million songs that are available in 180+ countries, Spotify has truly changed the means by which we interact with music(Spotify For the Record, 2022). With so much music available in one platform that dominates the music industry, the record labels and artists have to control the factors, if there are any, that could maximize their profits.

In the past, music lovers would have to buy CDs and vinyls for a particular song or an album by an artist. So, even if they just wanted to listen to one or two songs, they'd have to buy the whole album CD. But now, with the power of streaming, people just have to buy a subscription to get access to any song at any given time from anywhere. Furthermore, before Spotify came to the limelight, music sharing sites like Limewire and Napster bred ground for illegal sharing of pirated songs for free. This caused a huge loss to the music industry. This problem was solved by Spotify, as it was a paid subscription, out of which, parts were paid to the record labels and artists.

Spotify, being the leader of the music industry currently, has left artists and record labels to compete in maximizing their profit by getting more streams. The more streams a song has, the more successful the song can be considered. Spotify uses the number of streams as a metric to determine song popularity. Furthermore, it has a Spotify Global Top 200 Weekly Charts that gets posted on its spotify charts website every Friday. The chart contains 200 songs with the highest number of streams in that week over the globe. Currently, the website has data from 2016-12-23 to 2022-04-29 (over 279 weeks). The data from the chart will be used as the main source for my dataset. 

For every song in Spotify, it also has a database of individual audio features of the song. In this project, I will be determining whether these audio features have any impact on the popularity of the song. The popularity of the song will be determined by the peak position of the song in the chart and the number of weeks the song spent in the chart.

### Questions to Explore

So, the goals of this project are to analyze trends in Spotify, how the top songs have changed from 2017 to present and studying factors that influence the Spotify Global Top 200 Weekly Charts. I will also look at what makes a hit on the Spotify Chart? Is it based on the features of the song like the tempo, time signature, key of the song, how positive or negative the emotion it expresses? Or is it based on what record label the song was released by? Then finally, I will make predictions for a newly released song’s peak rank and the number of weeks it might spend in the chart based on the analysis.


---

## 2. Ethical Considerations

The dataset that I am using for the project has been made available by Spotify itself on their website. Since, I am working with a dataset regarding songs, I have access to the audio features of songs that are created by Spotify itself. I don't think there are any concerning consequences because the artists and record labels consent to that data being public when they put their song on Spotify. The stakeholders of this data are Spotify, artists, and record labels. The dataset has a lot of potential to benefit the stakeholders rather than harm them. Artists and record labels could analyze what factors lead to a hit song and can focus on those factors to maximise their profits.

---

## 3. Data Explanation and Exploration

Initially, this is what the dataset looks like:

<img width="1413" alt="image" src="https://user-images.githubusercontent.com/112485986/212206658-8d033f65-4822-4088-bf54-e38aaceb1ca8.png">

<img width="1413" alt="image" src="https://user-images.githubusercontent.com/112485986/212206683-05935dad-79ef-4ba6-9681-9c21c81a0c47.png">

The Position variable means the position in the chart for a particular week, it ranges from 1 to 200. We also have the track names, artist names, and the number of streams a song got that week. The songs can be individually identified by their song id and the week can be identified by the start and end dates. I also added a year variable for yearly analysis. Then, we have the individual audio features of a song.

## Audio Features: 

Here is a list of the audio features variable in the dataset (detailed explanation in the codebook):

- **Danceability (0 to 1)**
- **Energy (0 to 1)**
- **Key (-1 to 11)**
- **Loudness (in dB)**
- **Mode (0 or 1)**
- **Speechiness (0 to 1)**
- **Acousticness (0 to 1)**
- **Liveness (0 to 1)**
- **Instrumentalness (0 to 1)**
- **Valence (0 to 1)**
- **Tempo (in bpm)**
- **Duration (in ms)**
- **Time Signature (¾ to 7/4)**

I will be using some of these as predictor variables in the upcoming linear models.

The spotify_charts_weekly_top_200 dataset has over 55,000 rows, so it has a lot of duplicate songs in it. In order to analyze songs individually, unique songs were retrieved and some summary statistics were calculated. After that, we have 3 new variables, which are later going to be used as dependent variables for the models:

- **Peak_Position**

It is the highest rank a song achieves in the chart, which ranges from 1 to 200. It will help to track how popular a song was at that point of time.

- **Number_of_Weeks**

It is the maximum number of weeks a song survives in the chart, which ranges from 1 to 279. It helps to determine the intensity and length of the song’s popularity

- **Total_Streams**

It is the total number of streams a song has over the 279 weeks of data. It will be the actual metric to compare the popularity of songs. This value however doesn't account to the actual number of streams a song has because the dataset doesn't have number of streams from before 2017 and also, some songs may not have been in the chart for the full 279 weeks.

## Here are some figures and graphs of my exploration of the project:

<img width="1281" alt="Total Top 200 Global Weekly Spotify Streams from 2017 to 2021" src="https://user-images.githubusercontent.com/112485986/212208632-e79f7a29-0cdc-4ee4-856f-ca9b21d6b756.png">
<img width="1281" alt="Screen Shot 2022-04-26 at 7 49 37 AM" src="https://user-images.githubusercontent.com/112485986/212208489-5163b4e2-702d-40ff-823a-4c43fbefe90a.png">
<img width="1279" alt="Top 10 Most-Streamed Artists" src="https://user-images.githubusercontent.com/112485986/212208493-bd5faba2-153e-4e26-ad21-0974f20219dc.png">
<img width="1281" alt="Top 10 Most-Streamed Songs in a Single Week" src="https://user-images.githubusercontent.com/112485986/212208494-c83ded60-0d61-47f3-91ce-ea31fdc3d24d.png">
<img width="1281" alt="Top 10 Most-Streamed Songs Overall" src="https://user-images.githubusercontent.com/112485986/212208495-9f3f9550-69e3-4ae6-b00e-3368a51dd791.png">

![Average Song Tempo over the years](https://user-images.githubusercontent.com/112485986/212208891-0ddb2190-f27e-4e0d-9647-a26ead5d25fa.png)
![Average Song Valence over the years](https://user-images.githubusercontent.com/112485986/212208893-fdb54abb-acab-4e2f-aff4-3a5d18a88e60.png)
![danceability histogram](https://user-images.githubusercontent.com/112485986/212208895-3bd1e454-57e1-42f5-a13e-34265cb1d2bf.png)
![key barchart](https://user-images.githubusercontent.com/112485986/212208897-52320d0b-3b0e-4945-803c-c9e44e771061.png)







