# Amazon_Vine_Analysis

## Overview of the analysis: 
The purpose of this analysis, ultimately is to determine if there is any bias toward favorable reviews from Vine members in an Amazon dataset of total reviews, which includes those who are paid to review and those who do it of their own volition.  We want to analyze the data and determine if there is any real difference between paid vs unpaid reviewers who assign the highest mark, a 5 Star rating.  Does the fact that some are paid give them a higher propensity to mark the review higher or are they as objective as unpaid reviewers.

## Technology Involved:
The technical side of this analysis involves executing the Extract, Transform and Load (ETL) processes.  However, we are utilizing PySpark, a big data solution that leverages a language very similar to Python to extract and transform the Amazon dataset and then we load it into a Postgres SQL Relational Data Service (RDS) on Amazon Cloud services.

We then export from the Postgres database, a .CSV file and read it into Python Pandas to transform it again to perform our analysis as indicated in the above overview.

## Results: 
The dataset we chose to review from Amazon was a set of reviews for outdoor equipment and tools.  The following image of the head and tail of the datafram for the vines_table.csv show over 2.3 Million total reviews:
![vines_df](/Resources/vines_df.png)

Also, see the following screen shots that shot from the total $2.3M reviews, how many were paid in total and how many were not paid in total.
![vines_df](/Resources/all_paid.png)
![vines_df](/Resources/not_paid.png)

As we refined this data to perform our analysis, the first step was to create a new datafram that only included product records that 20 or more reviews:
![vines_df](/Resources/20_votes.png)

Next, our data was further refined to include records where the ration of helpful_votes to total_votes was greater or equal to .5.  This takes our record count from $2.3M down to under 40,000 records:
![vines_df](/Resources/helful_ratio.png)

Now, we create two new dataframes from this data, 1) representing the total paid reviews that provided 5 star ratings and 2) the total unpaid reviews that provided 5 star ratings:
![vines_df](/Resources/paid_reviews.png)
![vines_df](/Resources/unpaid_reviews.png)

With our two final dataframes above, we can now create totals and calculate a percentage of the totals for both paid and unpaid reviews.  Following is our summary view:
![vines_df](/Resources/summary_view.png)

There were **3,137** total paid reviews out of the full data set.  There were **2,299,255** reviews that were unpaid from the total dataset.

Also as you can see, there were **107** 5 Star Vine reviews and **39,869** non-Vine 5 Star reviews.

The percentage of Vine reviews that were 5 stars is **52.33%** and the percentage of non-Vine reviews that were 5 stars is **52.68%**.

## Summary: 
In summary, there does not appear to be any positivity bias for reviews in the Vine program for the Amazon Outdoor Tools and Equipment reviews. The resultant percentages for paid vs unpaid reviews with 5 Stars is roughly the same. 

I would like to run the same process of to filter down to 5 Star ratings for paid and unpaid reviewers, but would like to look at only verified purchases.  I would like to know if there is still no positivity bias from paid reviewers who also were verified purchasers.