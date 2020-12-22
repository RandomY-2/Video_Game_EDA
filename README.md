# Video Game Sales Prediction
 EDA on Kaggle Video Game dataset
 
## Description

In this notebook, I made an exploratory data analysis and a regressional analysis of global sales of video games using **Random Forest Regressor** on Kaggle's [Video Game Sales dataset](https://www.kaggle.com/gregorut/videogamesales). Specifically, I 

 - analyzed the **general shape and columns** of the dataset,
 - examined the **2 columns that contain missing values** and **selected machine learning model and features to impute missing values**,
 - made **univariate data analysis with 9 video game features** to find things such as which game has the best sales in each part of the world, 
 - used bivariate data analysis to **select 3 features that are correlated with global sale of a video game**, and 
 - evaluated **5 regression algorithms** and **predicted video game sales** using Random Forest Regressor. 
 
After selecting appropriate features and tuning the parameters, the model achieves a mean suqared error of 3.17. 
 
## EDA Samples

Here are some of the properties of the data I looked at for my EDA. 
<p align="left">
  <img width="800" height="500" src="https://github.com/RandomY-2/Video_Game_Regressional_Analysis/blob/main/images/dataset_info.jpg">
</p>

<p align="left">
  <img width="800" height="600" src="https://github.com/RandomY-2/Video_Game_Regressional_Analysis/blob/main/images/platform_dist.jpg">
</p>
 
<p align="left">
  <img width="800" height="600" src="https://github.com/RandomY-2/Video_Game_Regressional_Analysis/blob/main/images/NA_sales.jpg">
</p>

<p align="left">
  <img width="800" height="600" src="https://github.com/RandomY-2/Video_Game_Regressional_Analysis/blob/main/images/platform_global_sales.jpg">
</p>

## Prediction

### Year

The first prediction I did was to impute missing values in the Year column. Since there are only about 1 percent of the values missed, I found it inappropriate to just exclude this column. Thus, I first looked at the distribution of years.

<p align="left">
  <img width="800" height="600" src="https://github.com/RandomY-2/Video_Game_Regressional_Analysis/blob/main/images/year_dist.jpg">
</p>

There is not a single year that is very prevalent, so I don't want to fill missing values with the median or values like it. Therefore, I decide to use a classifier to predict which year a game belongs to. To accomplish this, I first found the correlations between year and quantitative variables. 

<p align="left">
  <img width="800" height="300" src="https://github.com/RandomY-2/Video_Game_Regressional_Analysis/blob/main/images/year_corr.jpg">
</p>

Rank and JP_Sales seem to correlate with the year a game is sold, so I selected these two numerical features. Next, I looked at the qualitative variables and their relationship with the year column. 

<p align="left">
  <img width="800" height="600" src="https://github.com/RandomY-2/Video_Game_Regressional_Analysis/blob/main/images/platform_year.jpg">
</p>

<p align="left">
  <img width="800" height="600" src="https://github.com/RandomY-2/Video_Game_Regressional_Analysis/blob/main/images/genre_year.jpg">
</p>

<p align="left">
  <img width="800" height="600" src="https://github.com/RandomY-2/Video_Game_Regressional_Analysis/blob/main/images/publisher_year.jpg">
</p>

It seems like platform and publisher are also indicative of the year since some platforms or publishers never released games before a certain year. So I used these two and Rank and JP_Sales as input to train the classifiers. The performances are as follows:

<p align="left">
  <img width="800" src="https://github.com/RandomY-2/Video_Game_Regressional_Analysis/blob/main/images/year_accuracy.jpg">
</p>

Since Random Forest has the best performance, I filled missing years with the values it predicts. 

### Global Sales

The next thing I want to do is to create a model that can predict global sales of a game. After looking at the associations between various features and the global sale column

Examples: 

<p align="left">
  <img width="800" height="500" src="https://github.com/RandomY-2/Video_Game_Regressional_Analysis/blob/main/images/genre_global_sales.jpg">
</p>

<p align="left">
  <img width="800" height="600" src="https://github.com/RandomY-2/Video_Game_Regressional_Analysis/blob/main/images/platform_global_sales.jpg">
</p>

I decided to train the model based on Platform, Genre, and Publisher columns. The performances of the models I tried are:

<p align="left">
  <img src="https://github.com/RandomY-2/Video_Game_Regressional_Analysis/blob/main/images/global_sales_models.jpg">
</p>

Because Random Forest is again the best baseline model, I used this one.






