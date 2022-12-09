# Data-603-Project
Team 3: Yelper <br>
Hemanth <br>
Vinay<br>
Utkarshika

# Yelp Data Analysis

The yelp data set is a trove of reviews, businesses, users, tips and check in data. In this project we are analyzing restaurant out of the other businesses found on yelp such as medical services, hotels etc. This notebook comprises of data for  years(Feb 2005-Jan 2022). 
We have used yelp data to visualize  the ratings and reviews for businesses in a particular area or industry. This could be a graphical representation that shows the average rating for each business, as well as the distribution of ratings across all businesses in the area. We also included other details, such as the number of reviews each business has received, and any significant trends or patterns that emerge from the data. This type of visualization could be useful for both consumers and businesses, as it provides a quick and easy way to understand the overall sentiment surrounding a particular area or industry.

![MicrosoftTeams-image (5)](https://user-images.githubusercontent.com/66125929/206588894-9a8fec57-053e-4dd0-a22b-b706d7aab238.png)


# Dataset description
Extraction- https://www.yelp.com/dataset

Our dataset is from Yelp.com. The dataset contains 5 JavaScript Object Notation(JSON) files. The yelp data set is a trove of reviews, businesses, users, tips and check in data all of whoch can be used for private, academic and educational purposes.
1. Business Dataset: 
Contains information about businesses, such as geographic information, attributes, rating, and categories. This dataset consists of 150346 rows and 14 columns (120 MB)
2. Review Dataset: 
Contains complete review text information, such as the user who authored the review and the business for which it was written. This dataset consists of 6.9 million rows and 9 columns (5.34 GB)
3. User Dataset:
 User dataset contains information about user, friend mapping and all the metadata associated with user. This dataset consists of 2 million rows and 22 columns (3.36 GB)
4. CheckIn Dataset: 
Information about user checking at the business locations. This dataset consists of  131930 rows and 2 columns 
5. Tip Dataset: 
user-written feedback on a company. Reviews are longer than tips, and tips typically contain brief recommendations. This dataset consists of 908915 rows and 5 columns.

# Objective
### Initial questions
We started with a vision to use the yelp restaurant dataset to build a recommender. Analyzing some of the questions ad digging into further investigations about the business and come up with recommendations that would help restaurant owners  to better decide where to open business as well as ways to improve their businesses.
During this process we discover the Yelp Dataset, dig deep and find interesting connections. We realized that our data only allowed us to take two tracks: analyze business or analyze user. Hence, we dug deeper into both kinds of data and came up with number of question before we decided to evaluate user data in greater detail.
Narrow our investigation to Fast Food chains and build a recommender for those based on location.

# About this Repository
This repository contains an ipynb file named Final_project containing the code, and the datasets used along with a readme file which contains all the project related information as well as the instructions.

# How to run the notebook:
As we have used pyspark it is necessary to have Pyspark, matplotlib and other basic libraries installed which are mentioned in the notebook. The whole code can be run at onces step by step , having the 5 datasets in the same enviroment so that it can be accessed.
Note:
1. The libraries necessary are all available in the notebook itself 
2. Pyspark must be installed

All the necessary libraries can be found in the notebook if not already installed follow the steps in the notebook.

<img width="733" alt="Screen Shot 2022-12-08 at 6 09 58 PM" src="https://user-images.githubusercontent.com/66125929/206586227-c5f0e1af-fe6e-4584-b964-d0f9e0a6c439.png">

# Moving forward to the steps followed in the analysis

## Firstly Setup AWS3: this is there in the notebook which needs to be run. Incase you can't run it from S3 we have used local storage as well because it would take a lot of time to load sometimes.
Follow the steps in Notebook.

## Step -1 (Extraction and Cleaning Data)
For the exploration, firstly we read the json files then define the schema for all the datasets we have. After that we only retain the columns that are required and drop all the unecessary columns.To begin the process of analysis we check for the null values and if any handle them by removing them. Then we look out for the dimension of data to check for the rows and columns we are working with. We have also filtered the dataset, changed the datatypes of some of the columns. Some of the columns used in the analysis are:

**business_id**

**categories**

**city**

**latitude**

**longitude**

**star**

**state**

<img width="1094" alt="Screen Shot 2022-12-07 at 9 03 25 PM" src="https://user-images.githubusercontent.com/66125929/206338522-2e5ff2a3-a546-4bd8-822d-41fe86a79729.png">


## Step -2( Exploring data for analysis)
We figured out during the cleaning process that there are alot of business types and categories that were present in the sample data we have. Hence to find out more about the restaurant business we created some visuals to see what relevant data do we have for the analysis. We filtered the datasets based on category as restaurants.

<img width="833" alt="Screen Shot 2022-12-07 at 9 10 14 PM" src="https://user-images.githubusercontent.com/66125929/206339327-9e69a166-3557-4f04-b77a-1a91e6ec5567.png">

From this our observation was that we are working with 35% of the businesses which are restaurants and the rest which come up to be 65% are hotels, hospitals etc.

## Step -3 (Analysis)
After understanding the datasets and the components we wanted to analyse the combination of the datasets and bring out meaningful information from it. Hence, we started to join the datasets. We have layers to our analysis which are shown below.
1. Reviews distribution: Our first finding was that out of total about 68% of the reviews that are on Yelp comprise of reviews for the restaurants and only 32% for other businesses, i.e 2/3 of the reviews.

![MicrosoftTeams-image (8)](https://user-images.githubusercontent.com/66125929/206598644-0bce0a29-3201-4ac4-a783-2b7804c4f352.png)

2. Tips are most in the restaurant data
<img width="718" alt="Screen Shot 2022-12-08 at 8 41 35 PM" src="https://user-images.githubusercontent.com/66125929/206603789-d3030bf6-e5b9-43cf-9826-c99908a02a7a.png">

3. Rating distribution: From our analysis we were able to see the overall rating or the distribution of ratings across the restaurants, where high number of restaurants saw a rating between 3.5 to 4.5
<img width="1117" alt="Screen Shot 2022-12-07 at 9 23 29 PM" src="https://user-images.githubusercontent.com/66125929/206340964-0f2158c5-35c5-4bcc-abfb-52e742c1f3a1.png">


4. Trend for checkin and review to the star ratings: Our observations for the Checkin_count and the review count for the restaurants which shows that becasue of the rating of the restaurants the checkins have been affected. The lesser number of stars the lower number of checkin_count.

## Step -3.1 (Location based Analysis)
We wanted to get location based data so, We found
1. where the restaurants were located
2. how many in a particular city (most and least number of restaurants in the cities)

<img width="687" alt="Screen Shot 2022-12-07 at 9 43 05 PM" src="https://user-images.githubusercontent.com/66125929/206343219-aae19ab0-fb99-4754-9fbc-f8847caaa359.png">
<img width="575" alt="Screen Shot 2022-12-07 at 9 43 36 PM" src="https://user-images.githubusercontent.com/66125929/206343295-6cf7e3c2-347a-4b48-bc0b-6ef8bd3ee36d.png">

3. Cities with most and least reviews

<img width="840" alt="Screen Shot 2022-12-07 at 9 44 09 PM" src="https://user-images.githubusercontent.com/66125929/206343363-ac942e2a-b1fc-4c4b-9ad1-a45131c95f52.png">

4. We also have a interactive heatmap to show the states and the restaurants in that area.
<img width="898" alt="Screen Shot 2022-12-07 at 9 45 48 PM" src="https://user-images.githubusercontent.com/66125929/206343543-1dade1fa-e369-4e82-93c9-4553cc773328.png">

## Step - 3.2 (Reviews)
We wanted to analyse the pattern of words that are used in the top rated(5 star) and worst rated( 1 star) using WordCloud.
We were able to fid out that both positive as well as negative meaning words are used in both the cases.

![image](https://user-images.githubusercontent.com/66125929/206587476-d86f084b-8ee2-4dbc-810e-0096aaa2d9bc.png)

![image](https://user-images.githubusercontent.com/66125929/206587535-3a79dec6-9419-4e1b-bb10-aff15911e266.png)

## Step -4(Fast food chains analysis)
We then narrowed out restaurant business to fasto food chain and analyse some questions like
1. Top 20 fast food chains in US
<img width="760" alt="Screen Shot 2022-12-07 at 9 57 03 PM" src="https://user-images.githubusercontent.com/66125929/206345089-de0195ce-b862-4076-87b8-9e602b5bf2fb.png">

Here we see that McDonald's is the number 1 fast food joint followed by Subway, Taco bell and so on. We then just took the most popular burger joints namely McDonald's, Burger King, Wendy's and Chick-fil-A for further analysis.


2. Ratings of the food chain business : To our surprise thought the food joints were the top the list the star ratings told a different story. The ratings for these were 1.5 to 2 stars. Among the 4 chosen burger joints Chick-fil-A was the most promising one with around 3.5 star rating.
<img width="705" alt="Screen Shot 2022-12-07 at 10 05 13 PM" src="https://user-images.githubusercontent.com/66125929/206346119-1ea3b5bb-908f-488f-8def-2f87947543f0.png">

The number of reviews were highest for McDonalds
![MicrosoftTeams-image (1)](https://user-images.githubusercontent.com/66125929/206588353-889e9c4a-7943-435b-95b6-5574d05953c4.png)

3. We analysed chick- fil-A which has the highest and the lowest rating and compared them .



![MicrosoftTeams-image (3)](https://user-images.githubusercontent.com/66125929/206588505-d299d494-de80-4a4c-99c7-ef6bf440d902.png)

<img width="1371" alt="Screen Shot 2022-12-08 at 8 14 09 PM" src="https://user-images.githubusercontent.com/66125929/206600786-428733b2-a8c4-4519-a6b3-4c8c03fe8760.png">

3.1 Review:
For Good Ratings
![MicrosoftTeams-image (6)](https://user-images.githubusercontent.com/66125929/206590633-14a518ed-db0e-40ea-9a42-69f949c69863.png)

 For Bad Ratings
 ![MicrosoftTeams-image (7)](https://user-images.githubusercontent.com/66125929/206590695-ca20c2d4-7cb7-42c3-bf6e-2c461bd1d793.png)



## Step -5 (Recommendation system based on location)
From the above we then created a recommendation system based on the location using sklearn,folium, geopandas and plotly.
Where in we found 
1. The top 10 restaurants
2. Scatter plot that shows the Restaurants based on the ratings
<img width="1270" alt="Screen Shot 2022-12-07 at 10 21 53 PM" src="https://user-images.githubusercontent.com/66125929/206348053-f78fb0e3-76dc-4a74-a757-4f9073f7780d.png">

3. The distribution of ratings by state

4. Since, Philadelphia consists of most number of high rated restaurants, the restaurant distribution has been divided into clusters using kmeans algorthm. Using silhouette score, the best number of clusters is chosen as 5. A function then helps in recommending the best restaurants given a certain co-ordinates. 
<img width="1295" alt="Screen Shot 2022-12-07 at 10 20 51 PM" src="https://user-images.githubusercontent.com/66125929/206347936-61efd405-c202-45dc-a1c9-fb992c872311.png">

6. top 5 recommendations

![MicrosoftTeams-image (4)](https://user-images.githubusercontent.com/66125929/206588625-0945d0d8-42be-4e67-8e60-68be679f8858.png)


# Conclusion and results
1. Among all the business that are found on yelp Restaurant business comprises of 35% of the total.
2. About 2/3rd of the reviews that can be found on yelp are comming from restaurants i.e 68%
3. Tips which are short reviews make up 71% from the restaurant business on yelp, which started from 2009
4. Majority of restaurants fall under 3.5 to 4.5 star ratings.
5. Star ratings have an impact on the checkins from customers.
6. Philadelphia, Tampa and indianapolis are the top 3 cities with highest number of restaurants
7. There are cities which have just 1 restaurant listed on yelp
8. Review count of Philadelphia is directly proportionate to it reviews and has the highest reviews for the restaurants.
9. To our surprise the top fast food/ burger joints have the worst rating. out of which Chick - fil- A is the best as of the average rating with 3.3.
10. Chick- fil- A though was the best among the others they also had ratings that were 1.5 and 5 in certain areas. Since we found 1.5 and 5 both are in the same area , location really doesnt play a significant role but it is the service that determines whether the business is good or bad.
11. We were able to come up with a model that gave us a location based recommendation where user gives the latitude and longitude.

## Suggestions for the restaurant business based on the analysis finding
1. Service is the most important factor, if you want to have better ratings or customer attraction you must improve on the service.
2. Hygiene is another factor that determines the likeness for the customers.
3. Businesses should look at their reviews and try to improve based on that given reviews as they say alot


# Challenges
1. Reading data from Hadoop after inserting data into HDFS.
2. While cleaning data for business- the same restaurant has multiple spellings listed(unique entries but is the same restaurant.
3. Not able to Use MLlib for clustering.






