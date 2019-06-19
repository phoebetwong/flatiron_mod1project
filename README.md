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

We merged the datasets with some novel techniques and created multiple unique features for this analysis. For explanations on the methodology, see Mod1Proj_PW_AG.ipynb and for the code, see Mod1Proj_DataCleaning_FINAL_PW_AG.ipynb

### Exploratory data analysis

Phoebe's analysis is based primarily on how the movies with higher share of foreign box office (i.e. with more emphasis/success in their global distribution channels) performed differently than those with lower share. She found that differences in performance between the two groups based on density distribution of profit, the elasticity of profit with respect to production budget, some possible effects of the average age of principle actors and actresses on worldwide gross box office and profit, and the difference in box office performance by genres.

Allan's EDA was focused on the genres, movie gross, length, run time and gender of lead roles. Features focused on where the wordwide_gross, foreign gross, actor_ordering, actor_age, actress_age,actress_ordering, production_budget, splits of the genres feauture, and domestic_gross. Comparison was done in pairs that would provide insights on what type and parameters of the movie should be created. Insight garnered were:
	- top grossing genres with different gender for lead roles and lead ages
	- top grossing movies per genre in domestic, foreign and worlwide market
	- Profits for different movie budget and runtimes

## Responsibilities:

- Phoebe Wong was responsible for data cleaning and Figure 1 to Figure 5 in the Jupyter Notebook for nontechnical audience (Mod1Proj_PW_AG.ipynb).
- Allan Gayahan was responsible for Figure 6 to 9 in the Jupyter Notebook for nontechnical audience.


## Summary of Files:

- Mod1Proj_PW_AG.ipynb is the notebook for non-technical presentation. Below are the files of the graphs appear in that notebook:
1_Graph1DomFor1018.jpg                
2_PBHist.jpg                            
3_PBGScat.jpg                           
4a_WGGENR.jpg                           
4b_PGENR.jpg                            
5a_ACTRAGE.jpg                          
5b_ACTRAGE.jpg                         
GenreGross.jpg                          
LeadAge.jpg                             
Movie-Theater-PowerPoint-Background.png
MovieGross.jpg
ProfitParameters.jpg  

- Mod1Proj_DataCleaning_FINAL_PW_AG.ipynb is the notebook for technical audience, with all the codes that generated the graph and data cleaning, and comments on the process. 

- Mod1ProjData.csv is the final merged dataset used for our analysis.

- The reminder of the csv files are the unziped raw data files described in the Dataset section above.