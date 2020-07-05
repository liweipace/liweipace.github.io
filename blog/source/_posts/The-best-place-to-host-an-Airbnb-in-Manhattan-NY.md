---
title: 'The best place to host an Airbnb in Manhattan, NY'
date: 2020-03-30 22:19:03
tags:
- Python
- Kmeans
---

![airbnb](https://i.loli.net/2020/03/30/cFBZaKAt48e3OoP.jpg)

## 1. Introduction
### Business Problem
Airbnb is becoming a serious business in recent years. Other than individual hosts who share their own places, companies around the world also step in thisa new business. Reports showed that about 2 million people stay in Airbnb rentals across the world during an average night in 2018. In this project, we want to find out what is the best place to host an Airbnb in Manhattan, New York. Furthermore, we are also interested in the patterns behind those bestsellers. We can implement those patterns in other cities afterward.
All of the data came from [kaggle.com](https://www.kaggle.com/dgomonov/new-york-city-airbnb-open-data).

### Interested Audience
Any companies or individuals who want to do serious business on the Airbnb platform. Actually, Airbnb itself has an Airbnb PLUS plan to give better service with the authorized hosts. Those professions should find this very useful as choosing a location ahead of starting a business.

## 2. Data Collection
**Target Data**:
  * List of Boroughs and neighborhoods of Manhattan with latitude and longitude
  * List of Airbnb houses in Manhattan with Latitude and longitude
  * List of attendance of each Airbnb
  * Venues for each Manhattan neighborhoods

**Data source and Preprocessing**:
  * Use Foursquare and geopy data to map top 10 venues for all Manhattan neighborhoods and clustered in groups
  * Use kaggle.com find an open dataset including details about Airbnb hosts in Manhattan.
  * Use Foursquare and geopy data to map the location of rental places

I used the python folium library to visualize the geographic details of Manhattan, New York. Each circle represents an Airbnb host. I used latitude and longitude values to get the visual as below:
![Part of Manhattan Airbnb Locations](https://i.loli.net/2020/03/30/lAzbc5jPhQ9CXy7.png)

## 3.Methodology

With the help of Foursquare API, I went through every Airbnb host place to explore the neighborhood. The limit is 100 venue and the radius is 500 meters for each neighborhood from their given latitude and longitude information. The head of the list Venues name, category, latitude, and longitude information is showed below :

![Venues Details](https://i.loli.net/2020/03/30/xqiofMJDPVcENy7.png)

Utilizing One-hot coding, I figured out the most common venue of each neighborhood. Then I used unsupervised learning K-means algorithm to cluster the neighborhoods. 

![Common Venue](https://i.loli.net/2020/03/30/xqiofMJDPVcENy7.png)

In the final section, I created a choropleth map to explicitly show the pattern between those clusters and Airbnb popularity:

![Clusters in Manhattan Area, the scale shows the Airbnb sales in color](https://i.loli.net/2020/03/30/AFVStO9b38dfWU6.png)

## 4.Conclusion
  * The Harlem and Hell's Kitchen are currently the best neighborhoods to start an Airbnb Business. 
  * Coffee shops and restaurants are very densely distributed near Harlem and Hell's Kitchen. We can assume those two as key factors.
![Most Common Venue around Harlem](https://i.loli.net/2020/03/30/ksXcERgLezropQD.png)

![Most Common Venue around Hell's Kitchen](https://i.loli.net/2020/03/30/Zlv82CLcEQObDTd.png)

  * Some area like the Theater District has too many hotels which are poisonable towards Airbnb. Even if this neighborhood is super close to the popular Hell's Kitchen, hotels and theaters could be too competitive and noisy for Airbnb.
![Theater District Venue](https://i.loli.net/2020/03/30/o6pZvOYxyE7mnDI.png)


