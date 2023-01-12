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

