---
layout: post
title: Project 1 - MTA Subway Data
---

This week I finished my first project at Metis!

#### The Project

Our goal for the project was to help WomenTechWomenYes (WTWY), a fictitious organization, devise a strategy to build public awareness about their organization and mission. In less than a week, my partner and I explored the New York MTA subway data to make our recommendations of locations to place street teams at entrances to subway stations.

Keeping in mind that WTWY had limited resources and a tight schedule, we approached this problem by identifying areas with high concentrations of women and individuals in the tech industry, who would be most likely to be interested in WTWY’s mission. In the end, we recommended high traffic subway stations located in tech hubs, areas with a high number of tech companies, start ups, and bootcamps. We also recommended subway stations in residential areas with higher numbers of women and tech employees (based on census data).

Here are a few fun things we found while exploring the data:

Between 8 am to 10 pm, the Grand Central - 42nd St Station was by far the busiest subway station.

![top15_busiest]({{ site.baseurl }}/images/top15_busiest.png)

Half of all the subway stations have over 500 people entering the station per hour. The black line indicates the median.

![hourly_avg_histogram]({{ site.baseurl }}/images/all_stations_histogram.png)

As we expected, stations are the busiest during the week compared to the weekend.

![weekday_stations]({{ site.baseurl }}/images/weekday_stations.png)

#### Reflections

This project was a great exercise to practice using numpy and pandas to manipulate and explore the data. Although the MTA subway data was publicly available online, there were many inconsistencies in how the data was collected and recorded. I was able to appreciate how data scientists spend a lot of their time cleaning and organizing data. Best of all, I learned to pickle objects using the pickle module to save my clean data frame for future use. This little gem saved me some time when restarting my jupyter notebook.

I used also matplotlib and seaborn to visualize the data. This was my first time using seaborn, and I enjoyed it. When it comes to plots, I typically prefer a minimalistic style without extraneous colors or elements. Plots created for presentations should be easy to read and convey a single message (which can be challenging). Of course, these plots are different from the ones created during exploratory data analysis, which tend to have many elements and take more time to understand. I found that seaborn was similar to ggplot2 in R, which I have used many times before, in that it has clean default style but still allows for customization.

There are many more avenues my partner and I could have explored with the MTA subway data, but due to our time constraint, we had to be strategic about which questions to tackle. Overall, I thought that Project 1 was a great learning experience. There were python gems I learned along the way that will be useful for future projects.
