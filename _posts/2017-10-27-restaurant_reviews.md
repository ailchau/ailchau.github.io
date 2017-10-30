---
layout: single
title: 'Wrangling with Restaurant Reviews'
---

What I most value in a restaurant is the quality and flavor of the food. I admit, prompt friendly service and a nice atmosphere, adds to a restaurant's appeal, but they are really count for bonus points. I have friends who don't share the same values, and appreciate more of a helpful smile and original decor. My motivations for the project was to examine the values of Toronto restaurant diners by identifying the latent topics underlying positive and negative restaurant reviews and clustering the reviews based on their topics. There were over 24,500 reviews for over 6,000 Toronto restaurants in [Yelp's data set](https://www.yelp.com/dataset/challenge).

All the code for this project is available in [this github repo](https://github.com/ailchau/Metis_Projects/tree/master/wrangling_with_restaurant_reviews).

{% raw %}
<iframe width="900" height="800" frameborder="0" scrolling="no" src="//plot.ly/~supercalifragilists/8.embed"></iframe>
{% endraw %}

A map identifying the restaurants included in this project.

- intro
- The objective of this project was to identify latent topics and cluster Toronto restaurant Yelp reviews using sentiment analysis, dimensionality reduction, and unsupervised clustering.

![center]({{ site.baseurl }}/images/pronouncingGIF/gif_count.png)

## Sentiment Analysis
After cleaning and standardizing all of the restaurant reviews, I first identified positive and negative by using Vader's sentiment analysis from NLTK. I chose to create a single unidimensional measure of sentiment by taking the difference between positive and negative scores. Many of the reviews had a positive and negative components. This combined sentiment score was positive when the sentiment of a review was generally positive, and negative when the sentiment of a review was generally negative. I found that this sentiment score performed better than the compound score.

Over 75% of the reviews had sentiment scores that were greater than 0. For the purpose of this project, I used the sentiment scores to divide reviews into positive and negative groups. Since I wanted to avoid neutral reviews, I decided positive reviews would have a sentiment score greater than 0.3 and negative reviews would have a sentiment score less than -0.2. There were about 30,000 positive reviews and 1,500 negative reviews.

For example:

> Positive review  
> Sentiment score: 0.865  
> Review: Elegant, comfortable, inspiring. Beautiful and delicious food. Always a smile.

> Negative review  
> Sentiment score: -0.711  
> Review: Terrible food. Flat beer. Bad service. Uncomfortable atmosphere. Gross.

There were a small number of cases were the sentiment scores that did not match the review. In the example below, "damn" was interpreted negatively, but in this context it was used positively.

> Sentiment score: -0.73  
> Review: Damn spicy. Damn greasy. Damn cheap. Damn tasty.

Overall, the sentiment scores reflected the sentiment of the reviews. I confirmed this by examining the positive and negative reviews (see [my notebook](https://github.com/ailchau/Metis_Projects/tree/master/wrangling_with_restaurant_reviews) for more details).

## Topic Modeling and Clustering

Topic modeling is a unsupervised method of revealing the underlying topics within a large set of text. A "topic" consists of a group of words that frequently occur together. I used topic modeling on the positive and negative reviews to reveal restaurant diners' values and preferences. Of the different topic modeling techniques I experimented with (e.g., term frequency–inverse document frequency (TF-IDF), latent semantic analysis (LSA), latent Dirichlet allocation (LDA), and non-negative matrix factorization (NMF)),TF-IDF and NMF revealed the most understandable collection of topics. I grouped reviews based on the similarity of their underlying topics using K-means clustering.

Positive reviews tended to be filled with positive adjectives, such as "good", "great", and "amazing". These positive adjectives appeared in all the topics. As I expected, diners typically complimented the quality of food and service. The largest cluster (about 1/3 of the positive reviews) was about the quality of food. There were smaller clusters focused on the quality of service, as well as, as the specific type of cuisine. Some diners also complimented the atmosphere or location of a restaurant.

![center]({{ site.baseurl }}/images/restaurant_reviews/positive_clusters.png)

Negative reviews tended to have negative adjectives, for instance "bad" and "horrible". Diners typically complained about the quality of service, such as the speed of service and the friendliness of the staff. They also complained to a lesser extent about the quality of food and cleanliness.

![center]({{ site.baseurl }}/images/restaurant_reviews/negative_clusters.png)

## Summary
Toronto restaurant diners valued quality of food and service the most. In their reviews, they typically complimented or complained about these two topics. To a lesser extent, diners commented about atmosphere and price. For this project, I didn't differentiate between different types of restaurants, such as fast food, casual dining, and fine dining. I expect that diners of different types of restaurants would value atmosphere and price to different degrees. Diners at fast food may be more forgiving about a lackluster atmosphere, whereas diners at fine dining restaurants may be more forgiving about the higher prices.

Overall, there a lot more positive reviews than negative reviews (almost 20 times more). There can be multiple reasons for this. In general, restaurant diners may have more positive than negative experiences; reviewers may be more inclined to post a review if they had a positive experience; or Yelp reviewers are a specific type of people (not representative of all restaurant diners), and they tend to have positive experiences or write positive reviews. These analyses were conducted on Toronto restaurant Yelp reviews and the results from these analyses may also not be applicable to restaurant reviews from other large cities.

## Future Steps
In the future, I would like to expand the cities included in the analyses and compare if different cities review similar topics in their restaurant reviews. I would also like to categorize restaurants based on type, and examine how restaurant reviews and expectations can differ within and between these types.
