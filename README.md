
# Module 2 Final Project


## Introduction

For this project, my main objective was to analyze a housing data of a county in Seattle and see which variables corresponded the most to the price of the house. To accomplish this, I had to 
    1. clean the data
    2. analyze the data
    3. build a model
    4. validate that model
I also had two other follow-up questions for the dataset in question
    1. Does having a more recent renovation change housing price significantly?
    2. Are there patterns on the map of the county itself for housing price?

## Motivation

I have just recently learned how to apply python functions with linear regression, so this is a perfect opportunity for me to put that knowledge to practical use. Also, it's just interesting to see what factors are the most important to a house's price and whether there are distinguished patterns in location.

## Objectives
* Clean and understand the dataset in question
* Test and see whether there are correlations with price
* See whether the model is significant or has multicollinearity 
* Perform feature engineering if neccesary 
* Cross Validate the model
* Test the two individual questions with the relevant data

## Questions

* Does having a more recent renovation change housing price significantly?
* Are there distinguished patterns on the map for housing price?
* Which variables correlate the greatest with housing price?

## The Dataset

* Does having a more recent renovation change housing price significantly?

     1. number of bathrooms: some correlation here, will be used 
     2. date of house sold: not relevant
     3. bedroom number: seems to be somewhat predictive
     4. square foot of lot: random correlation
     5. floors total: no linear predictive model
     6. view: no good predictive qualities
     7. sqare foot besides the basement: good correlation with price
     8. year built: no correlation
     9. year renovated: no correlation
     10. latitude and longitude: good for showing where hotspots of price differentials are
     11. square foot of living space for nearest 15 neighbors: good correlation with price
    


### Question 1

* Which factors predict price the most?

For this part, I started with plotting a scatter matrix of all the variables and looked for significant correlations. The ones that passed the eye-test the most were square feet, square feet besides basement, square feet of neighbors, bathrooms, and grade. 

However, an OLS regression test showed high multicollinearity. This was the most pronounced between the square feet measurements and of bathrooms and grade. To subvert this, I combined the dataframes after standardization. This greatly reduced my conditional number and gave me an R-squared value of 0.504, not the best but still somewhat predictive. I double-checked the model by running cross validation on it, and the means returned were within 5% of each other. 

### Question 2

* Does having a more recent renovation affect housing price significantly?

I approached this problem initially by attempting to plot year of renovation against price. However, the dataset contained a bunch of missing values. Consequentially, I dropped all the rows with missing values. This greatly reduced the size of my dataset however, but I decided to plot the points irregardless. The returned chart did not seem to show that much correlation, and an OLS test returned a R-squared value of 0.10. Ultimately, I did not find the year of renovation to affect housing price.

### Question 3

* Are there distinguished patterns on the map for housing price?

For this, I simply charted latitude vs longitude while including price in the heatmap. This gave me a visual representation of the houses in King County with their respective prices. And while looking at the map, there are distinguished areas of expensive houses grouped together throughout the waterfront while the cheaper houses are tend to be at more of the outskirts of the county. The most expensive houses do tend to group up extremely, perhaps in a "Beverley Hills" equivalent in Seattle or something. 

## Validation

To confirm my model, I ran crossfold validation with c=10, returning me an array of:

    1.-0.56965929,
    2.-0.59881259
    3.-0.45797895
    4.-0.62435808
    5.-0.44039516
    6.-0.44757261
    7.-0.45154343
    8.-0.48245291
    9.-0.50894227
    10.-0.56741696
* relatively good results for MSE

## Conclusions and Summary

From the dataset, I was able to make a model that somewhat predicts housing price with some variables. The R-squared value was not the greatest but I was able to reduce multicollinearity. My model was significant and had appropriate skew and kurtosis. I attempted to get a better R-squared value by removing outliers but that just seemed to reduce it as a lot of the outliers were actually relatively linear.

Generally, this model can only be explicitly applied to houses residing in King County. For a better model on a country-wide scale, we'd need data from random samples across the country while including more variables to make up for the differences inherently shown between houses in different areas.


