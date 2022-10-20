---
layout: post
title:  "Using Spotify's API to create a dataset of '1000 of the Greatests Hits Ever'"
date:   2022-10-20
author: Nate Norton
description: This is a cool project.
image: /assets/images/spotify_dev.png
---


![Figure](https://raw.githubusercontent.com/nate-norton/stat386-projects/main/assets/images/spotify_capture2.png)
                                      
Have you ever wondered how Spotify has achieved it's success? I know I have and by accessing their API, I was able to gain a deeper understanding of the music streaming giant. Through gathering an incredible amount of data on each of the 80 million songs on their platform, Spotify is able to using data science and machine learning to understand their users. Spotify can use paramaters such as danceability, energy, speechiness, instrumentalness, and many others to understand why you listen to the music you do. Among many things, this data collection and analysis allows them to recommend music to you that is likely to keep you listening. Keep reading to learn how to access the Spotify API using the Python package Spotipy. 
                                      

![Figure](https://raw.githubusercontent.com/nate-norton/stat386-projects/main/assets/images/python.png)
![Figure](https://raw.githubusercontent.com/nate-norton/stat386-projects/main/assets/images/spotify_dev.png)     

# Accessing the API                          
In 2014 Spotify made their metadata about artists, albums, playlists, and songs publicly available for anyone to access. One of the reasons they did this was so that external developers could access this data and write programs for apps, smart home gadgets, and anything linked to Spotify. The provide easy documentation of how to access their API on this [Website](https://developer.spotify.com/documentation/web-api/_.

In order to access their API you need register with Spotify. This requires you to go to [https://developer.spotify.com/dashboard/login](https://developer.spotify.com/dashboard/login). After logging in you need to navigate to the page with the information of your "Client ID" and "Client Secret ID". All of the next steps can be done in python.

The package "spotipy" was a package created to allow to explore the metadata in Python. Make sure that you have installed it before you start!

This step is unique to Spotify. The cid and secret(id) must be entered in order to give you access to their API. I have replaced mine with "x"'s but you get the idea.
```
cid = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
secret = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
client_credentials_manager = SpotifyClientCredentials(client_id= cid, client_secret= secret)
sp = spotipy.Spotify(client_credentials_manager = client_credentials_manager)
```

After doing this, you are ready to explore Spotify's expansive metadata.

In our case, we are going to be selecting a specfic playlist and grabbing all the data for each specific track. After choosing a playlist, copy the end of the URL and the username that created the playlist. 

I chose to grab a playlist titled "1000 of the greatest hits ever", created by "Iris Fernanda"
```
# 1000 of the greatest hits ever: Iris Fernanda 0hKruppKCtqPcSYgnCCVBg
```
In order to collect the information I was looking for I had to create two functions.

The first function would was created to collect the entire playlist. I was running into a problem that prevented me from pulling more than 100 songs at once, and this function allowed me to get past that and collect all 1000 songs. This function was then called in the second function.

Included below is some of the code from the function get_songs. This code would loop through each song and extract it's features adding them to a dataframe.
```  
playlist = get_playlist_tracks(username, playlist_id)
    
for track in playlist:
   # Create dictionary
   playlist_features = {}
   # Get metadata
   playlist_features["artist"] = track["track"]["album"]["artists"][0]["name"]
   playlist_features["album"] = track["track"]["album"]["name"]
   playlist_features["track_name"] = track["track"]["name"]
   playlist_features["track_id"] = track["track"]["id"]
   
   # Get audio features
   audio_features = sp.audio_features(playlist_features["track_id"])[0]
   for feature in playlist_features_list[4:]:
       playlist_features[feature] = audio_features[feature]
```
# Conclusion
This is the resulting dataframe after calling the function. It includes basic information about each song including unique measurements that Spotify has created such as: danceability, loudness, speechiness, and insturmentalness.
![Figure](https://raw.githubusercontent.com/nate-norton/stat386-projects/main/assets/images/spotify_table.png)

I really enjoyed learning how to scrape data from the Spotify API. It gave me a behind the scenes look into the workings of the Spotify's algorithms and company. In my next post I will be doing an exploratory data analysis of this dataframe to answer questions such as: What makes a song a greatest hit? Does danceability have a greater effect than speechiness? What are the key indicators to a greatest hit?

If you would like to see my code and final dataset, here is a [Git Hub Repo](https://github.com/nate-norton/Spotify-API-Repo).
