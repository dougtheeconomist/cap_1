# Taxation And Economic Health

During my last trip through Minnesota I visited with a good friend of mine who is a resident there and in discussing the local economy(which happens to be quite strong) he asserted the theory that this strength comes from the fact that Minnesota has one of the highest tax rates in the U.S. and that the public support that these taxes pay for creates an environment that is conducive to economic prosperity. Having recently read a book published by several political scientists that posited the same theory at the time, I considered this theory to have some validity to it. This explanation does however run counter to one that many make in arguing the case for lower taxes; that policy should focus not on building up an environment in which business can thrive, but instead lowering the costs of operating a business in as much as possible by lowering their tax burden. 

The aim of this study is to examine state level data in order to empirically say which theory about the effects of higher taxes (if either) actually holds weight, and if a pattern of statistical significance is found to say something about the practical significance, or size of any correlation present. In addition to being able to validating (or invalidating) a friend’s hypothesis, this study is much more broadly relevant in the realm of public policy, as the answering of this question would have practical significance not only to the policy makers who set tax rates in an effort to best support their economies, but to any stakeholders within that economy who are directly impacted by it’s performance. 

# Data

In order to accomplish this goal I collect and merge data published by the federal government by way of the U.S. Census Bureau, as well as the Bureaus of Economic Analysis and Labor Statistics, to form a dataset on which correlation analysis and hypothesis testing can be performed.
In order to effectively examine the relationship between taxation and economic health I need data on economic indicators and taxation levels. In assessing the economic health of an area I utilize the indicators of gross domestic product and unemployment rate of a given state. I also gather demographic information on population levels to serve as a measure of the size of a state as I expect the overall size of the economy in question to be a factor that would bias my results if not taken into account; one would reasonably expect California to have higher GDP and tax income that Rhode Island. 
I gather data across the years 2016, 2017 and 2018 as I am able to find information across these years for all of my data. The resulting dataset contains 150 unique observations; each one representing one of the fifty U.S. states in one of these three years. The reasoning for taking multiple years into account is to get a look at how much variation is going on over time rather than just looking at one instance, and to increase the amount of observations I have to work with. After importing and aggregating my dataset in an excel csv file, I import it into Python as a pandas dataframe to conduct my exploratory data analysis and primary statistical analysis. 

# Methodology

The first hurdle to overcome conceptually in order to effectively shed light on this issue is the fact that the amount of revenue brought in from taxes will be directly dependent upon the size of GDP and for states that have income taxes, the size and percentage employed of the areas workforce. What I want to measure is the other factor that directly impacts tax revenue size, which is the actual state tax rate. The way I control for the first factor to isolate the different rate of taxation between states is to collect data on federal tax revenue from each state in addition to collecting a state's tax revenue. The assumption I explicitly make is that the rate that the federal government taxes each state is going to be the same. Therefore by comparing the state's collections to the federal government's collection from the same area, we can get a comparable measure of how much higher one state sets it’s tax rates than another. I form this measure of taking the ratio of state revenue to federal revenue. The higher this ratio is, the higher the state’s tax rates are compared to the federal tax rates, which are assumed to be the same across all state. 

This assumption may not be perfectly accurate to the real world, in reality there is some difference between the industries and types of business entities that generate income from one state to another, and if these industries are taxed differently which I suspect they may be, then the effective federal tax rate would vary some by state. For this study, I am content to make this assumption, because I believe that this variation will be negligible, but a direction of further study would be to group states with like industries and to then compare across these sub-groups to mitigate any bias that this may introduce into my analysis. 
When testing my hypothesis, I conduct tests for each of the three years of data as well as across all three years of data.  
To ascertain whether or not there is statistical evidence to support my friend’s claim, I first look at correlations between the taxation ratio and my economic indicators to get a feel for whether or not there is any relationship present. I then conduct formal hypothesis testing to find if the means for the economic variables are significantly different for the group of states in the top 25% bracket of tax rates and the group of states in the bottom 25% bracket of tax rates. 

# Findings

## EDA

I start by looking at descriptive statistics and scatter plots of the data. When I graph gdp and population against the ratio of state to federal tax income, I find that the state of California is a consistent outlier, although when I view a similar plot of per capita gdp I find that while California is one of the larger values, it no longer stands out; there are four states here that are higher when accounting for population. 
When I graph the annual means of my monthly unemployment rate against my tax ratio I see that this is much more flat than the other graphs; there is much less variation of unemployment rates across states with different tax rates. There is again an obvious outlier here; this is Alabama, who has much higher unemployment than anyone else. 
Upon isolating variance of the monthly unemployment rates and then merging this in with the overall dataset and graphing this, I see that there is again not as obvious a trend as with the gdp data. There is again an obvious outlier here; this is Alabama, who has much higher unemployment than anyone else; by at least a factor of over two. It seems to fall just right of center of the graph as far as the tax ratio goes, so I’m not sure that this will actually skew my results. 
As I examine this data further, specifically by each year I find that it is only in 2017 that Alabama is an outlier, it falls into the range of normal during the next two years. The state of West Virginia spikes higher in 2016 and 2018 making it a yearly outlier in these years, though it isn’t by enough to stand out when looking at the total three year variance the way that Alabama does. 

![hopefully_scatter_plots](/images/te_scatter.png)
Format: ![Alt Text](url)

I also generate histograms of my variables to see how they are distributed, and I find that none of my variables of interest are normally distributed; the tails of the distribution are either much too fat, or in the case of the population estimate variable and the variance of the unemployment rate, appears to be exponentially distributed. This finding would be problematic if I were to attempt to model these factors using linear regression techniques, but as this is outside the scope of this study, I don’t worry about it here.  

## Primary Analysis

Upon preliminary examination I find that there is a positive correlation between the ratio of state revenue to federal revenue and both state gdp and per capita state gdp. This correlation was stronger with per capita gdp. As one would expect there are extremely high correlations between state gdp and both state and federal revenues, which would seem to justify the use of the ratio of the two rather than simply using state income by itself to attempt to get a sense of the level of taxation that accounts for a measure of economic activity as a proxy variable for actual tax rates. 
I then look at the correlation of this variation with the taxation ratio, and I see that there is a negative correlation here, but not a huge one. We see a coefficient here that rounds out to -0.1, which is higher than the correlation of this variance against either state or federal taxation. 

# Conclusion


