---
layout: post
title:  "An Inside Look Into What Makes a Greatest Hit"
date:   2022-12-06
author: Nate Norton
description: A short story about Spotify data and Greatest Hits.
image: /assets/images/spotify_background.jpg
---

# What Makes a Greatest Hit?

Have you ever wondered makes a greatest songs great? What do all of the greatest hits have in common? The music industry makes billions of dollars each year and every artist is asking the same thing. How can I make a song that will become a hit? Luckily for us, we can use data and the Spotify API to find the answers to these questions. Spotify, an online music hosting platform, hosts millions of songs. Each song has its own "audio features", these features quantitatively rate the songs characteristcs. A few examples of these characterestics are the following: tempo, energy, danceability, valence (how positive or negative a track is), and instrumentalness.

Over the past couple of blogs I have taken a deep dive into the data behind 1000 of the greatest hits from 1950 - 2010. The Spotify API made it possible to collect all of this information. After pulling it into Jupyter Notebooks, I cleaned and prepared the data. In order to be able to compare the different audio features, I had to standardize each score. Standardizing each score was done similar to how you calculate a Z-score, subtract the value by the mean and divide by the standard deviation. After doing this, I calculated the average for each decade.

# Greatest Hits Over the Decades

By standardizing the scores and finding the average for each variable in every decade, we are able to see the trends behind 1000 of the greatest songs ever. I found that songs from the 60's, 70's, and 80's are currently much more popular than greatest hits from the 90's, 00's, or 10's. Another interesting finding is that in 2000, the time with the least popular "greatest hits", songs scored above average in nearly every audio features. Hits from the 2000's had more energy, tempo, danceability, and valence (positivity). While this is an intersting find, truly the most significant finding comes from the standardized popularity averages per decade. While all of these songs are labeled as "greatest hits", the songs from the 60's, 70's, and 80's are much more popular than the rest. Songs from the 60's are currently the most popular among the "greatest hits". An interesting characteristic about songs from the 60's are that they are significantly less danceable and less energetic. While we cannot conlcude that the decrease in danceability and energy are the reason for the popularity, they certainly can be target areas for future research and statistcal analysis. Here is the graph that shows these findings. 

![Figure](https://raw.githubusercontent.com/nate-norton/stat386-projects/main/assets/images/data_story_1.png)  

# What's Next?

This is only the beginning of my research regarding what song reach "greatest hit" status. Certainly, there are many different factors and variables contributing to the success of a song. While, this dataset and analysis does not provide the answer, it's a great start. In the future, I would like to compare randomly selected songs to my dataset of greatest hits; comparing these two playlist would provide a deeper insight into what makes a song GREAT.

If you would like to join me in finding what makes a "greatest hit" great here is my [Git Hub Repo](https://github.com/nate-norton/Spotify-API-Repo). Please leave any comments if you have questions are insights! Thanks for reading!
