# Netflix Recommender System

## Introduction

![My Project Logo](/images/Netflix_logo.png)

Netflix was originally launched as a mail-based rental service in 1997 and transitioned to streaming media services, offering video on demand, in January 2007. Since then, Netflix has provided a wide array of movies and TV shows across various genres from different distributors in multiple languages. 
<br>

However, for many years, Netflix struggled to enhance the personalized viewing experience for its users. In 2007, the company offered $1 million to any team that could improve its Collaborative Filtering algorithm by 10%. Over the next two years, BellKor's Pragmatic Chaos achieved an improvement of 10.06% in RMSE value, thus winning the challenge. 
<br>

Over the years, Netflix has developed additional algorithms, such as Category Interest, personalized algorithms, and custom thumbnail art based on users' taste preferences. These advancements aim to better understand user patterns and trends, thereby improving retention rates and keeping subscribers engaged and satisfied. 
<br>

Despite these efforts, Netflix continues to struggle with viewership ratings, and users often find it difficult to discover new content that aligns with their ever-changing tastes and preferences. 
<br>

## Problem Statement 
> "Netflix Recommender System by using Content-based Filtering to help new users discover movies effectively"

## Datasets 

There are two files: <br> 
- tmdb_5000_credits.csv: 4 Columns by 4,803 Rows (Consists of Movie ID, Title, Cast and Crew)
- tmdb_5000_movies.csv: 20 Columns by 4,803 Rows (Consists of Movie ID, Title, Genre, Language, Popularity, Revenue, Vote Average, Vote Count, Overview, etc)

## Data Cleaning 
1. Merged two datasets using the common identifier 'Movie ID.'  
2. Extracted and reformatted a list of dictionaries for columns such as Genre, Production Companies, Cast, and Keywords.  
3. Reformatted language columns to change abbreviations to full terms.  
4. Checked for null and duplicate values.  
5. Imputed 'Unknown' for Home Page, Tag Line, Overview, and Run Time where applicable.  
6. Removed duplicate Movie Titles.  
7. Created a new data frame to contain all essential columns for analysis and modeling.

## Predictive Modelling 

![Content-based Filtering](/images/CBF.png) 

**Content-based Filtering** is a recommendation system that <u>uses one or more attributes from a user's profile</u>, including preferences and tastes, to suggest movies based on similar or closely related characteristics. This approach delivers highly personalized recommendations. For instance, in a movie recommendation system, the input may consist of textual details such as the overview, genre, keywords, cast, director, and more. Text processing, or Natural Language Processing (NLP), is needed to assess the significance of each word in relation to the entire dataset which consists of unique Movie ID.
<br>

Using the technique known as Term Frequency-Inverse Document Frequency (TF-IDF) adds weights to important terms, helping to differentiate between common and unique words that are crucial. This results in the creation of a large, sparse matrix. The numerical values within the matrix correspond to the scores of each term. A higher score indicates that a word appears frequently in a specific document but is rare across the entire dataset. <br> 

A) First Predictive Modelling using **'overview'** as the first feature. <br> 

![Feature_One](/images/Feature_One.png)

The function performs lemmatization by grouping words with the same intended meaning, allowing them to be processed and analyzed as a single item. <br>

Let's take a look at the movie recommendations we will receive after watching John Carter. <br>
![Feature_One_JohnCarter](/images/F1_JC.png)
<br>

Getting Recommendations for 'John Carter':
![Feature_One_Recommendations](/images/F1_JC_Rec.png)
<br>

Breakdown for 'John Carter':
![Feature_One_Breakdown](/images/F1_JC_Breakdown.png)
<br>

It is evident that the movies recommended after watching John Carter are based on the first feature we used, as common words like 'Carter' and 'Military' appear in the movies' overviews. <br> 

Let's take a look at the movie recommendations we will receive after watching The Avengers. <br>
![Feature_One_TheAvengers](/images/F1_TA.png)
<br>

Getting Recommendations for 'The Avengers': 
![Feature_One_Recommendations](/images/F1_TA_Rec.png)
<br>

Breakdown for 'The Avengers': <br>
![Feature_One_Breakdown](/images/F1_TA_Breakdown.png)
<br>

It is evident that the movies recommended after watching The Avengers are based on the first feature we used, as common words like 'Unexpected', 'Threatened', 'Peacekeeping' and 'Global' appear in the movies' overviews. <br>

Let's take a look at the movie recommendations we will receive after watching The Dark Knight Rises. <br>
![Feature_One_TheAvengers](/images/F1_TDKR.png)
<br>

Getting Recommendations for 'The Dark Knight Rises': <br>
![Feature_One_Recommendations](/images/F1_TDKR_Rec.png)
<br>

Breakdown for 'The Dark Knight Rises': <br>
![Feature_One_Breakdown](/images/F1_TDKR_Breakdown.png)
<br>

It is evident that the movies recommended after watching The Dark Knight Rises are based on the first feature we used, as common words like 'District', 'Attorney', 'Havery', 'Dent', 'Batman', 'Gotham', 'Dark', and 'Knight' appear in the movies' overviews. <br>

<u>Conclusion based on the first feature: </u> <br>

![Feature_One_Metrics](/images/F1_Metrics.png) <br>

By utilizing the 'overview' feature alone, the model is capable of accurately providing relevant movie recommendations that are also properly ranked. However, there is still room for improvement in terms of diversity and novelty. <br>

B) Second Predictive Modelling using **'title', 'genre', 'keywords', and 'cast'** as the second features. <br> 

Let's take a look again at the movie recommendations we will receive after watching John Carter using the second features. <br>
![Feature_One_JohnCarter](/images/F1_JC.png)
<br>

Getting Recommendations for 'John Carter':
![Feature_Two_Recommendations](/images/F2_JC_Rec.png)
<br>

Breakdown for 'John Carter':
![Feature_Two_Breakdown](/images/F2_JC_Breakdown.png)
<br>

It is clear that the movies recommended after watching John Carter are based on the second feature we used, as common words such as 'Action', 'Adventure', 'Science', 'Fiction', 'Space', 'Travel', 'Alien', and '3D' appear. Relying on this second feature alone provides a strong set of diverse movie recommendations that are similar in nature. <br> 

Let's take a look at the movie recommendations we will receive after watching The Avengers. <br>
![Feature_One_TheAvengers](/images/F1_TA.png)
<br>

Getting Recommendations for 'The Avengers': 
![Feature_Two_Recommendations](/images/F2_TA_Rec.png)
<br>

Breakdown for 'The Avengers': <br>
![Feature_Two_Breakdown](/images/F2_TA_Breakdown.png)
<br>

By comparing the movies recommended after watching The Avengers based on the second feature we used, we notice that more Marvel-related films are being suggested. However, the diversity among the recommended movies is limited, and users who watched The Avengers may already be familiar with other Marvel films. As a result, the recommended movies might not be ideal. <br> 

Let's take a look at the movie recommendations we will receive after watching The Dark Knight Rises. <br>
![Feature_One_TheAvengers](/images/F1_TDKR.png)
<br>

Getting Recommendations for 'The Dark Knight Rises': <br>
![Feature_Two_Recommendations](/images/F2_TDKR_Rec.png)
<br>

Breakdown for 'The Dark Knight Rises': <br>
![Feature_Two_Breakdown](/images/F1_TDKR_Breakdown.png)
<br>

By comparing the movies recommended after watching The Dark Knight Rises based on the second feature we used, it is evident that the diversity of the recommended movies is greater with this second feature compared to the first. This could be more favorable for users who prefer a wider range of recommendations that align with their personal preferences. <br>

<u>Conclusion based on the second feature: </u> <br>

![Feature_Two_Metrics](/images/F2_Metrics.png) <br>

By utilizing additional features, it becomes clear that both the diversity and novelty of the recommended movies vary significantly based on the movie watched. However, this should be studied in more detail, and a greater understanding of user data and preferences is needed to provide more tailored and personalized movie recommendations for each individual. <br>

To enhance the accuracy of predictive modeling, techniques such as word embedding (using synonyms or words with similar meanings) and collaborative filtering should be considered, especially when the dataset is larger and includes extensive user data based on multiple or hundreds of watched movies. <br>

## Limitations 
1. **No Data Accessibility** <br>
Netflix has stopped providing API access to public users since 2017. As a result, the data I need, which should include multiple watched movies per user, is difficult to obtain. <br>

2. **Outdated Data** <br>
The data is quite old, with the last movie entry being from February 2017. <br>

3. **Computational Limitations** <br>
Large computational tasks, such as creating a mapping matrix, are not feasible due to the limited processing power of my laptop. <br>

## Recommendations 
1. **Word Embedding** <br>
This technique utilizes synonyms or words with similar meanings. <br>

2. **Collaborative Filtering** <br>
Since the current model is only based on content relevant to new users, it requires just one input, the 'Movie ID.' However, to enhance the model's accuracy, collaborative filtering is recommended. This approach incorporates user data, allowing for more accurate movie recommendations based on similar types or user interests. <br>
