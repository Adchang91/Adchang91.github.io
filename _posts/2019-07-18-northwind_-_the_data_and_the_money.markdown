---
layout: post
title:      "Northwind - The Data and the money"
date:       2019-07-18 17:03:14 -0400
permalink:  northwind_-_the_data_and_the_money
---


This project is a treasure hunt. We’re given a database map and expected to search every nook and cranny of the data to find all the Easter eggs.  Luckily for us, this is just an exercise and we only needed to do 4 hypothesis tests but even with a small sample database, the potential questions are endless.  

As a data analyst, I’m used to using SQL Server language to manipulate and wrangle my data but working with sqlite3 and Pandas has been liberating. Using pd.read_sql_query to assign a variable to SQL tables and using pd.merge to join tables has been a blast to use. Additionally, the interface of Jupyter Notebook feels cleaner than SQL Server, in my opinion of course. However, forgive me for saying this, querying in Microsoft Access is the easiest and fastest to use because of its GUI. At least for now, until I become more familiar with Pandas. But add in the fact that Python has tools such as Numpy, Matplotlib, Seaborn, Statsmodels and it becomes a no brainer.

The Northwind Traders Database has 13 tables all intertwined with unique ID keys. Each table describes a different facet of the company. You got your products, suppliers, employees, customers, etc. that all connect to map the company’s business. No business model is perfect and that’s where I, The Data Scientist, come in. This where I shine to find the, aforementioned, nooks and crannies.

Did I find it within my 4 hypothesis tests? Not really, but the attempt was there. If time was on my side and salary was dependent on this project,  running through 100s of hypothesis tests will eventually find the golden gems. The 4 hypothesis tests that I ran were…
 
1)	Do discounts effect the number of products customers order? Does discount level matter?
2)	Do some regions have higher average order sales than other regions?
3)	All products increased price on the same day, did that effect the number of products that customers order?
4)	Do some employees have higher total sales per quarter than others?

Even though we can create graphs and visualize the differences of the samples for each the questions, we need math and statistics to confirm our beliefs. Just because Mr. Chang averages $10,000 with a standard deviation of $2,000 worth of sales a quarter compared to Mr. Son who averages $8,000 with a standard deviation of $3,000 worth of sales a quarter, is Mr. Chang a better salesman statistically? This is where I introduce the phenomenon of t-tests.

First and foremost, once we know the question, we have to set the null and alternative hypothesis. The null hypothesis, denoted as Ho, is when there is no statistical significance between the two or more variables. The Alternative hypothesis, denoted as Ha, is when there is a statistical significance between the two or more variables. Once we formed the hypothesis, we can move on to the experiment.
	 
In order to conduct an experiment, we need to gather the necessary data. As said before, SQL tables, pd.read_sql_query, pd.merge, and data is now ours to experiment. What we are trying to prove is the alternative hypothesis, or in a more scientific correct way, reject the null hypothesis. Also, we have to set the significance level, also known as the alpha value. This value will be used to compare to the p-value to decide if we choose to reject the null hypothesis. For this project, we set the significance level to 0.05 for all the experiments. A well-structured experiment will account for all the mistakes and randomness that can happen. A T-Test can tell us if there is a statistical difference between the means of two variables. The t-test looks at the t-statistic and t-distribution values to determine the p-value.
	
The p-value is the number of all numbers. This value is the ultimate decider if we should reject the null hypothesis or fail to reject the null hypothesis. The p-value is the calculated probability of randomness. In other words, a lesser p-value means there is a smaller chance the results are due to randomness. Remember that significance level from before? Well now we use it to compare to the p-value. If the p-value is smaller, we can reject the null hypothesis and accurately say that there is a statistically significant relation between the variables. If the p-value is larger, we fail to reject the null hypothesis so there is no relation between the variables. Although this may sound bad, proving that there is no relation can be as important as proving there is a relation, so it’s not all bad.
	
There you have it. Now you’ve either proved or disproved the relation between two or more variables. Using this, a company can see that increasing one aspect can cause an affect on another aspect. More discounts… more sales. Slower shipping… less sales. October has higher sales than other months… look into the reasoning. Jerry has higher sales than everyone else… everyone copy Jerry. These are the hidden gems that Data Scientists are tasked to find.

