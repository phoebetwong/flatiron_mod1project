# Mod 1 Project: Learning What Films Perform the Best at the Box Office

## Team members: Allan Gayahan and Phoebe Wong

## Executive summary:

The goal of this project is to perform EDA (Exploratory Data Analysis) and present preliminary findings on the attributes of films that are currently doing the best at the box office. 

![Movie theater pic](Movie-Theater-PowerPoint-Background.png)

## Contents

- [Introduction](#Introduction)
    - [Problem statement](#Problem-statement)
    - [Dataset](#Dataset)
- [Analysis](#Analysis)
    - [Data cleaning](#Data-cleaning)
    - [Exploratory data analysis](#Exploratory-data-analysis)
- [Responsibilties](#Responsibilities)
- [Summary of Files](#Files-summary)


## Introduction

### Problem statement

Our goal is to identify attributes of movies that are associated with the best box office performance, in order to inform executives of a new movie studio what movies they should consider creating. 

### Dataset

The main dataset of this project has three main sources. 

Box office and budget data (production budget, domestic and worldwide gross box office) are collected from: 

- - Box Office Mojo
  - data
    - bom.movie_gross.csv.gz
  - documentation
    - Our course instructor scraped this dataset from [this page](https://www.boxofficemojo.com/yearly/chart/?view2=worldwide&yr=2010&p=.htm) (from 2010-2018).

- TheMovieDB.org
  - data
    - tn.movie_budgets.csv.gz
  - documentation
    - This comes from [The-Numbers.com](https://www.the-numbers.com/movie/budgets/all)
    - Our team has subsetted this dataset to 2010-2018.

Movie features data (e.g. genres, principal cast and crew, and their demographic characteristics) are collected from:

- IMDB
  - data
    - imdb.name.basics.csv.gz
    - imdb.title.akas.csv.gz
    - imdb.title.basics.csv.gz
    - imdb.title.crew.csv.gz
    - imdb.title.principals.csv.gz
    - imdb.title.ratings.csv.gz
  - documentation
    - All data has come from https://www.imdb.com/interfaces/, just filtered to only 2010-2018 movies.


## Analysis

### Data cleaning

Since the datasets with box office and budget data include only titles as identifier, and the titles do not appear consistently across the data sources (e.g. "The Lego Movie" vs "The LEGO Movie"), special treatment is needed to prevent either duplicating data with an outer join, or losing a substantial amount of data from an inner join. When merging data sets that do not include a title ID, we used the Levenshtein score that identify two different sets of strings that are most likely to be the same. The procedure of merging dataset, was as follows: 1. performed an inner join with the movie title as key, which merged the records with identical movie title spelling; 2. created a list of the movie titles from each dataset, and subtracted them from each other to obtain the respective list of movie titles that did not get merged; 3. using the StringDist package in Python, we created a list of Levenstein scores for each combination of unmatched movie title, which was combined as a dataframe with the respective movie titles from each dataset using a for loop function; 4. the movies titles that do not represent the same movie were deleted from the dataframe; 5. this dataframe with movie titles from both datasets is used as a map to merge each dataset. With this procedure, we were able to match most of our budget data with a title ID in the IMDB datasets.

After merging the budget data with the movie feature data, we also created multiple features not in the raw dataset for our analysis. By merging the dataset containing the casts' and crews' age with the principle cast and crew in each movie, we created features that could be correlated with box office demands such as the average age of principle actors and actresses in each movie when the movie was released, and the share of principle actresses in each movie.

We identified some errors in the Box Office Mojo dataset (some foreign box office observations do not have the correct scale), so Box Office Mojo data is used only when TheMovieDB.org data is not available for a movie that is included in the IMDB database. From this combined budget dataset, we created the foreign gross box Office variable by subtracting domestic box office from the worldwide box office. We also created a Profit variable, which is the difference between Worldwide Box Office and Production Budget. To better understand the demand of global movie market, we created a dummy variable that sorts movies according to their foreign box office as a share of worldwide box office, with movies that share over 50% labeled as 'Global' and those 50% or under labeled as 'Domestic'. As sensitivity test, we also created a dummy variable according to the total number of regions the movie was distributed, with over 10 regions as 'Global', and 10 or below as 'Domestic'.

### Exploratory data analysis

Phoebe's analysis is based primarily on how the movies with higher share of foreign box office (i.e. with more emphasis/success in their global distribution channels) performed differently than those with lower share. She found that differences in performance between the two groups based on density distribution of profit, the elasticity of profit with respect to production budget, some possible effects of the average age of principle actors and actresses on worldwide gross box office and profit, and the difference in box office performance by genres.


## Responsibilities:

- Phoebe Wong was responsible for the data cleaning file and Chart X to X.


## Summary of Files:

-
