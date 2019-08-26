---
layout: post
title:      "Module 4 - Forecasting House Prices"
date:       2019-08-25 20:22:43 -0400
permalink:  module_4_-_forecasting_house_prices
---

So here you are, a new and upcoming Data Scientist, hired by a real-estate investment firm to allocate millions of their dollars into various houses around the nation. You’ve got more than 14,000 zip codes and more than 20 years of monthly average house price data to work with. How would you convince the firm on what the 5 best zip codes are to invest in?

Amazingly, Facebook Prophet will do the job for us. Facebook Prophet is a forecasting tool that utilizes past data to predict the future. Facebook Prophet is capable of producing a graph of real data and forecasted data, yearly trends, monthly trends, daily trends, and most importantly, a DataFrame of desired forecast values based on the user’s settings. 

Let’s talk about each of these capabilities. Yearly trends will tell us in 2007, the housing market started to crash and 2012 is when it bottomed out and started to grow. Monthly trends will tell us what month of the year was the best time to purchase or sell a house. Daily trends are not really relevant in terms of housing prices because the day of the week should not affect the housing price. A DataFrame of forecast values gives us the predicted value, lower bound predicted value, and upper bound predicted value. 

What makes Facebook Prophet so great is the ability to customize the parameters. If the output is not satisfactory, tweaks can be made to the settings to retrieve the desired output. Uncertainty intervals can be adjusted to have higher or lower bounds. A higher interval_width will have upper and lower bounds that are more polarizing to the predicted value, while a lower interval_width will have bounds that are hardly different from the predicted value. Another customizable criteria is the ‘make_future_dataframe’ option. The user can choose how far into the future he or she wants to predict by adjusting the number of periods and the frequency of each period. For our forecasted house prices, we chose 36 periods of monthly frequency to predict 3 years into the future.  

How can we use this to our advantage to find the best zip code? We can use all the monthly average house prices from April 1996 to April 2018 to predict up to April 2021. Because Facebook Prophet will not adjust to future anomalies similar to the 2008 housing market crash,  it’s never a good idea to predict too far into the future. In my opinion, 3 years or 36 periods of future data is the perfect medium for a housing price project.

Here is the problem. Facebook Prophet can only predict one zip code at a time but we have exactly 14,723 zip codes to predict! While it is possible to find the 5 best zip codes in the nation, I did not have the time nor did I believe in my computer to handle such a tremendous task. Being a NYC native, I decided to focus my attention on the Metropolitan area of New York.

I decided the best way to tackle this scenario is to find the 3 best counties to invest in. Then for each of the 3 counties, find the 3 best zip codes giving us 9 potential zip codes. Because Facebook Prophet can only predict one dataset at a time, we would need to average out all the zip codes data for each time period within the county. For example, for the 6 zip codes in Manhattan, I averaged the zip codes for each month. Then using a for loop, I used the Facebook Prophet model on all 12 counties. The top 3 counties to potentially invest in were Manhattan, Brooklyn, and Queens.

Now to do the same with each zip code in all 3 counties. In the end, I found that Brooklyn had 4 out of top 5 zip codes to invest amongst all NY counties. The top zip code, 11222, show an increase of 40.8% from April 2018 to April 2021. That would be a much better investment than the national average housing increase of 13.8%.

Although netting a positive return on investment is always a good thing, if the average housing price increases, it’s our job as data scientists to find the zip code with the highest increase. If the average housing price decreases, we should be able to choose a zip code with the lowest decrease. With the proper models and predictions, we are able to find the zip codes with the highest yield and lowest risk.

