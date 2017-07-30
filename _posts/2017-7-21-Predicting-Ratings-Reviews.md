---
title: Predicting Book Ratings vs. Reviews
tags:
- metis
- projects
- Goodreads
---

The goal of my second project at Metis was to predict the ratio between the number of book ratings and the number of book reviews on Goodreads using information about the book, such as average book rating, years since publication, genre, number of pages, and awards won. High ratios would indicate that there were a higher number of ratings compared to reviews, whereas low ratios would indicate that there were similar number of ratings and reviews. In the data set, the smallest ratio was 1. For every review, there was at least 1 or more ratings. This makes sense, because when people submit book reviews, they are likely to also give the book a rating. However, the reverse isn't necessarily true. Rating a book out of five takes relatively little time compared to writing a book review.  I've noticed that this isn't true of just books on Goodreads, but also other sites that have customer ratings, like Amazon or Yelp.

## Data Collection  
For this project, I web scraped over 15,000 book profiles from the Goodreads website using Beautiful Soup. However, once I narrowed down the data to include only fiction books written in English, I had just under 7,000 books in my data. Since one of the objectives of this project was to gather data though web scraping, I wasn't able to use their API.

To minimize the amount of time I would spend cleaning the data afterwards, I tried to be organized and strategic about how I collected the data. I cleaned the data as I was web scraping and was careful not to exclude valuable information. The collected book information was stored in dictionaries, making them easy to convert into a data frame. I also learned to really appreciate try and except clauses. Without them, I would have had a lot of trouble  dealing with missing information in the book profiles.

## Model Fitting
Before model fitting, I examined the distribution of the features and outcome variable (i.e., ratio between the number of ratings and reviews) to make sure that there were no unusual trends that would lead to violations to the assumptions of linear regression. Since many of the features and the outcome variable were skewed, a log transformation was applied. The data was less skewed and resembled a normal distribution after the transformation.

In order to avoid overfitting and evaluate model performance accurately, I divided the data into training and testing sets and used cross-validation while model fitting. Compared to lasso, ridge, and elastic net regression models, I found that the linear regression model provided the best fit and ease of interpretability. This model had an R-squared of 33.4, indicating that the model explained 33.4% of the ratio between the number of ratings and reviews. In this model, there were 8 statistically significant predictors: the average rating of the book, years since publication, genre (i.e., fantasy, classics, or historical fiction), number of pages, voter score, and awards won. For instance, for every 1% increase in average rating, we would expect a 0.46% increase in the number of ratings over the number of reviews. Conversely, if a book falls under the genre of classics or historical fiction, we would predict about a 30% decrease in the number of ratings compared to reviews.

Here is final equation of the model:
-1.22(Intercept) + 0.46*(Average Rating) + 0.44*(Years Since Publication) + 0.28*(Fantasy) + 0.10*(Number of Pages) + 0.06*(Voter Score) - 0.06*(Awards Won) - 0.30*(Classics) - 0.31*(Historical Fiction)

![center]({{ site.baseurl }}/images/goodreads_coefficients.png)
