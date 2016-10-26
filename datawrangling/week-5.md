---
layout: tutorial
title: Week 5 (November 6 - 12)
permalink: data_wrangling/week-5
---

The last couple of weeks we have been working with data frames.  Data frames are the most common way of storing data in R and, generally, is the data structure most often used for data analyses; it is R's version of an Excel spreadsheet. This week we are going to put more focus on working with this style of data.  Specifically, we are going to concentrate on the following:

1. Understand the basics of dealing with data frames
2. Comprehend a new concept known as *"tibbles,"* which makes working with data frames even easier
3. Learn how to organize your data in a *tidy* way
4. Manage relational, but separate, data frames

## Tutorials & Resources

Please work through the following tutorials prior to Saturday’s class. The skills and functions introduced in these tutorials will be necessary to complete your assignment, which is due at the beginning of Saturday’s class, and will also be used in Saturday’s in-class small group work.

**Data frames:** Basic understanding of data frames is essential. To understand the fundamentals of working with data frames read and work through the [*Managing Data Frames* tutorial](http://uc-r.github.io/dataframes).  You should also read through the [*Dealing with Missing Values* tutorial](http://uc-r.github.io/missing_values) so that you understand how to handle missing values in your data frames.

**Tibbles:**  As Hadley Wickham states *"tibbles are data frames, but they tweak some older behaviours to make life a little easier."*  Read and work through *[Chapter 10: Tibbles](http://r4ds.had.co.nz/tibbles.html)* to understand the difference between a basic data frame and a tibble. 

**Tidy data:**  A tremendous amount of time is spent on fundamental preprocessing tasks to get your data into the right form in order to feed it into the visualization and modeling stages. This typically requires a large amount of reshaping of your data. If you understand the proper way to organize your data up-front you will save yourself a lot of time during the analysis phase. Read and work through [*Chapter 12: Tidy Data*](http://r4ds.had.co.nz/tidy-data.html) to learn how to consistently organize your data.

**Relational data:** It’s rare that a data analysis involves only a single data set. Typically you have many sets of data and you need to join them to perform your analysis and answer the questions that you’re interested in. To learn how to work with joining relational data read and work through [*Chapter 13: Relational Data*](http://r4ds.had.co.nz/relational-data.html).


## Homework

Create an HTML R Markdown document named “week-5.Rmd”. Title this HTML document “Week 5 Homework” and be sure to include your name in the YAML.  Download this data: XX. There are multiple data sets[^data] in this file and a short decription of each variable is provided in the footnotes.

With these available data sets perform the following exercises:

1. Import the `bomber_wide.rds` file so that it is a tibble and turn this data from a wide format to a long format so that you have the following columns: *Type, MD, Year,* & *FH*.
2. Import the `bomber_long.rds` file so that it is a tibble and turn this into a wider format so that you have the following columns: *Type, MD, FY, Cost, FH,* & *Gallons*.
3. Import the `bomber_combined.rds` file so that it is a tibble and separate the *AC* variable into *"Type"* and *"MD"*
4. Import the `bomber_prefix.rds` file so that it is a tibble and unite the *prefix* and *number* variables into an *"MD"* variable
5. Import the `bomber_mess.rds` file so that it is a tibble.  Clean this data up by making it contain the following variables: 
    - *Type*
    - *MD* which combines the *prefix* and *number* variable (i.e. "B-1")
    - *FY* which is the left part of the *Metric* variable
    - *Cost* which is captured in the right part of the *Metric* variable
    - *FH* which is captured in the right part of the *Metric* variable
    - *Gallons* which is captured in the right part of the *Metric* variable

For #5, perform the required actions by stringing together the all necessary functions with the [pipe operator](http://uc-r.github.io/pipe) (`%>%`). The final data should look like:
    
```
# A tibble: 57 × 6
     Type    MD    FY      Cost    FH   Gallons
*   <chr> <chr> <chr>     <int> <int>     <int>
1  Bomber   B-1  1996  72753781 26914  88594449
2  Bomber   B-1  1997  71297263 25219  85484074
3  Bomber   B-1  1998  84026805 24205  85259038
4  Bomber   B-1  1999  71848336 23306  79323816
5  Bomber   B-1  2000  58439777 25013  86230284
6  Bomber   B-1  2001  94946077 25059  86892432
7  Bomber   B-1  2002  96458536 26581  89198262
8  Bomber   B-1  2003  68650070 21491  74485788
9  Bomber   B-1  2004 101895634 28118 101397707
10 Bomber   B-1  2005 124816690 21859  78410415
# ... with 47 more rows
```

For #5, plot the historical trends of this data in ggplot2 with a __line chart__ such that the plot is __facetted__ by the *Cost, FH,* and *Gallons* variables and each facet compares the different MDs ("B-1", "B-2", "B-52").

6. Import the `ws_programmatics.rds` & `ws_categorization.rds` data so that they are tibbles and perform the following steps in sequence using the [pipe operator](http://uc-r.github.io/pipe) (`%>%`). 
    1. Join the `ws_categorization` data to the `ws_programmatics` data
    2. Filter for only __FY__ 2014 data at the following __Base__: *"Minot AFB (ND)"*
    3. Filter for only *"AIRCRAFT"* or *"MISSILES"* __Systems__
    4. Calculate the total sum of the *Total_O.S* and *End_Strength* variables at the __System__ level

7. Once again, join the `ws_programmatics.rds` & `ws_categorization.rds` data and identify which *Base* had the largest cost per flying hour (defined as $$CPFH = \frac{Total\text{_}O.S}{FH}$$ which requires you to create a new variable) in 2014.  Using a __bar chart__ in ggplot2, plot these values for the top 10 bases with the largest cost per flying hour.

8. Using __scatter plots__ in ggplot2, assess the relationship between the end strength (*End_Strength*) variable and total costs (*Total_O.S*).  Provide three scatter plots that visually assesses this replationship from different angles (by *FY*, *System*, etc).  



[^data]: Note that these are fictional data sets and none of this data represents actual information regarding United States Air Force assets. This artificial data was originally generated for instructional purposes for an R programming course at the Air Force Institute of Technology.