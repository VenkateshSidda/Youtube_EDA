**Exploratory Data Analysing Using Youtube Video Data from Most Popular Data Science Channels**

# 1. Aims, objectives and background

## 1.1. Introduction

Founded in 2005, Youtube has grown to become the second largest search engine in the world (behind Google) that processes more than 3 billion searches per month. [[1]](https://www.mushroomnetworks.com/infographics/youtube---the-2nd-largest-search-engine-infographic/). It is, however, generally a myth how the Youtube algorithm works, what makes a video get views and be recommended over another. In fact, YouTube has one of the largest scale and most sophisticated industrial recommendation systems in existence [[2]](https://dl.acm.org/doi/10.1145/2959100.2959190). For new content creators, it is a challenge to understand why a video gets video and others do not. There are many "myths" around the success of a Youtube video [[3]](https://vidiq.com/blog/post/5-youtube-algorithm-myths-youtubers-need-to-know-about/), for example if the video has more likes or comments, or if the video is of a certain duration. It is also worth experimenting and looking for "trends" in the topics that Youtube channels are covering in a certain niche.

Having recently stepping into the content creation world with a new Youtube channel on data analytics and data science, I decided to gain some insights on this topic which might be useful for other new content creators. The scope of this small project is limited to data science channels and I will not consider other niches (that might have a different characteristics and audience base). Therefore, in this project will explore the statistics of around 10 most successful data science Youtube channel.

## 1.2. Aims and objectives

Within this project, I would like to explore the following:

- Getting to know Youtube API and how to obtain video data.
- Analyzing video data and verify different common "myths" about what makes a video do well on Youtube, for example:
    - Does the number of likes and comments matter for a video to get more views?
    - Does the video duration matter for views and interaction (likes/ comments)?
    - Does title length matter for views?
    - How many tags do good performing videos have? What are the common tags among these videos?
    - Across all the creators I take into consideration, how often do they upload new videos? On which days in the week?
- Explore the trending topics using NLP techniques
    - Which popular topics are being covered in the videos (e.g. using wordcloud for video titles)?
    - Which questions are being asked in the comment sections in the videos

## 1.3. Steps of the project
1. Obtain video meta data via Youtube API for the top 10-15 channels in the data science niche (this includes several small steps: create a developer key, request data and transform the responses into a usable data format)
2. Prepocess data and engineer additional features for analysis
3. Exploratory data analysis
4. Conclusions

## 1.4. Dataset

### Data selection

As this project is particularly focused on data science  channels, I found that not many readily available datasets online are suitable for this purpose. The 2 alternative datasets I found are:

- [The top trending Youtube videos on Kaggle](https://www.kaggle.com/rsrishav/youtube-trending-video-dataset): This dataset contains several months of data on daily trending YouTube videos for several countries. There are up to 200 trending videos per day. However, this dataset is not fit for this project because the trending videos are about a wide range of topics that are not necessarily related to data science. 

- Another dataset is obtained from this [Github repo](https://gitlab.com/thebrahminator/Youtube-View-Predictor) of Vishwanath Seshagiri, which is the metadata of 0.5M+ YouTube videos along with their channel data. There is no clear documentation on how this dataset was created, but a quick look at the datasets in the repository suggested that the data was obtained using keyword search of popular keywords such as "football" or "science". There are also some relevant keywords such as "python". However, I decided not to use these datasets because they don't contain data for the channels I am interested in.

I created my own dataset using the [Google Youtube Data API version 3.0](https://developers.google.com/youtube/v3). The exact steps of data creation is presented in section *2. Data Creation* below.

### Data limitations

The dataset is a real-world dataset and suitable for the research. However, the selection of the top 10 Youtube channels to include in the research is purely based on my knowledge of the channels in data science field and might not be accurate. My definition is "popular" is only based on subscriber count but there are other metrics that could be taken into consideration as well (e.g. views, engagement). The top 10 also seems arbitrary given the plethora of channels on Youtube. There might be smaller channels that might also very interesting to look into, which could be the next step of this project.

### Ethics of data source

According to [Youtube API's guide](https://developers.google.com/youtube/v3/getting-started), the usage of Youtube API is free of charge given that your application send requests within a quota limit. "The YouTube Data API uses a quota to ensure that developers use the service as intended and do not create applications that unfairly reduce service quality or limit access for others. " The default quota allocation for each application is 10,000 units per day, and you could request additional quota by completing a form to YouTube API Services if you reach the quota limit.

Since all data requested from Youtube API is public data (which everyone on the Internet can see on Youtube), there is no particular privacy issues as far as I am concerned. In addition, the data is obtained only for research purposes in this case and not for any commercial interests.
