# Udacity Data Science Nanodegree Project 1: Write a Blog Post

<h2>Seattle Airbnb EDA: Are Airbnb management companies really worth it?</h2>

In the attached notebook I investigate whether property management companies offer better occupancy rates than individually-hosted listings. This analysis follows CRISP-DM methodology, as outlined in the following steps:

<h2>Business understanding</h2>

Should individuals let property management companies handle their Airbnb listings for a cut?
Questions:
1. Who are the hosts with the most property listings in Seattle?
2. What are the occupancy rates of these listings?
3. Are occupancy rates of investor-owned listings higher than that of individually-owned listings?

<h2>Data understanding</h2>

I explore data gathered by Inside Airbnb (http://insideairbnb.com/get-the-data.html):

1. seattle_listings: Characteristics of 3818 individual Airbnb listings in Seattle (e.g. listing IDs, price, average review, etc.)
2. seattle_calendar: 365 days of availability data for all 3818 listings between 2016-2017 (available = 't' or 'f')

<h2>Data preparation</h2>

- Renaming certain hosts to recognize that some property management companies list properties under a first name
- Constructing count DataFrame containing the values of total listings (column 'host_listing_counts') by host, for hosts with more than 10 total listings
- Plot total listings by host name
- Recognize that if the number of properties per host in seattle_calendar is different from their total listings (in 'host_listings_count') then we should make sure we know where these discrepancies are, especially because we'll need a measure of total listings to calculate occupancy rates by host.
- So we construct a representativeness (R-) index, where:

R-index value = (Calculated no. of listings in seattle_calendar)/(Reported value in host_listings_count)  ∈  [0,1]

- Plotting R-index values by host, we can tell that there is a sharp drop-off in values after 0.9, so we keep hosts with R-index values above this threshold (leaving us with 12 hosts from 20)

![R-index](https://github.com/alexsiebelmckenna/seattleairbnbEDA/blob/main/r-index.png)

- Calculate occupancy rates for both investor and non-investor groups
- Calculate their means; note that occupancy rates of individually-hosted listings are 19 percentage points higher (42%) than investor-hosted listings (23%). Is this difference statistically significant?
- Plot occupancy rates as a boxplot.
- Use a two-sample independent t-test to test the null hypothesis that the occupancy rates are the same vs. the alternative hypothesis that they are not.

<h2>Modeling</h2>

<h5>Question 1: Who are the hosts with the most property listings in Seattle?</h5>

Plotting hosts with more than 10 property listings:

![Number of hosts](https://github.com/alexsiebelmckenna/seattleairbnbEDA/blob/main/numberofhosts.png)

In the listings dataset, some of the biggest hosts were listed under first names — for example, Global Luxury Suite properties (502) were listed under the name Kara, and Turnkey properties (354) were listed under the name Bo. 

<h5>Question 2: What are the occupancy rates of these listings? </h5>

After whittling down the host list to account for R-index (please see the discussion above) and plotting occupancy rates over 2016:

![Occupancy rates](https://github.com/alexsiebelmckenna/seattleairbnbEDA/blob/main/occupancyrate_by_host.png)

On average, investor host listings have a mean occupancy rate of 23%. 

<h5>Question 3:  Are occupancy rates of investor-owned listings higher than that of individually-owned listings?</h5>

No, on the contrary - property listings hosted by the rest of the population (i.e. individual hosts) have a mean occupancy rate of 42%. The data tell us that individually-hosted listings are occupied, on average, 19 percentage points more of the time than investor listings.

![Boxplot](https://github.com/alexsiebelmckenna/seattleairbnbEDA/blob/main/boxplot.png)

Using the two-sample independent t-test, test the hypothesis that the mean occupancy rates are equal across investor and non-investor groups. This test yields a t-statistic of t-value is -3.127 and the associated p-value is 0.009, leading us to reject this null hypothesis in favor of the alternative hypothesis that the mean occupancy rates of investor-hosted listings are lower (by 19 percentage points) than occupancy rates of individually-hosted listings.

<h2>Evaluation</h2> 

We use an independent t-test to gauge whether mean occupancy rates between investor and non-investor groups have a statistically significant difference between them and conclude that on average, occupancy rates for investor-hosted listings are **lower** than those of non-investor-hosted listings (by 19 percentage points). As the appeal of property management companies lies in its promises of higher occupancy rates, the results of this analysis do not bode well for how effective this strategy turns out to be.

<h2>Acknowledgements</h2>

I'd like to acknowledge the good work that folks at Inside Airbnb do to make open source data more accessible (http://insideairbnb.com/get-the-data.html).

Accompanying description/article: https://alexsiebelmckenna.medium.com/are-airbnb-management-companies-really-worth-it-f21ac730c4c5

<h2>Libraries used</h2>

1. pandas
2. numpy
3. matplotlib 
4. seaborn
5. scipy

<h2>Files in this repo</h2>

Notebook:

1. airbnb_EDA.ipynb: Jupyter Notebook containing Python code used for this analysis

Images:

1. numberofhosts.png: Hosts with listing counts > 10, plotted against total listings per host
2. r-index.png: R-index (see above) values across host
3. occupancyrate_by_host.png: Occupancy rates across host
4. boxplot.png: Comparing occupancy rates of investor-hosted listings and individually-owned listings

Data:

1. seattle_calendar.csv.zip: Availability calendar
2. seattle_listings.csv: Listings dataset

