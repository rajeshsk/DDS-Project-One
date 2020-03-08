# MSDS 6306: Doing Data Science - Case Study 01

## Group Members
- Thad Schwebke
- Rajesh Satluri
- Kris Ghimire

### Introduction

Using the Beer and Breweries data files provided by Budweiser, our group was able to uncover 
information that could be beneficial for Budweiser if they are considering entering the craft 
beer market in the United States. 

The information we focused on was breweries by State, beer styles, container sizes, Alcohol by 
Volume (ABV), and International Bitterness Units (IBU).

The data provided for this analysis consists of 2410 US craft beers from 558 US breweries. The 
data analysis that follows highlights the following in order to describe the current craft beer 
market:

The purpose this project is to provide descriptive information about the current craft beer market 
in the United States.


### The Data
Beers dataset contains a list of 2410 US craft beers and Breweries dataset contains 558 US
breweries. The datasets descriptions are as follows.
Beers.csv:
Name: Name of the beer.
Beer ID: Unique identifier of the beer.
ABV: Alcohol by volume of the beer.
IBU: International Bitterness Units of the beer.
Brewery ID: Brewery id associated with the beer.
Style: Style of the beer.
Ounces: Ounces of beer.

Breweries.csv:
Brew ID: Unique identifier of the brewery.
Name: Name of the brewery.
City: City where the brewery is located.
State: State where the brewery is located.

### Folder & File Information

- `analysis/` contains the reports generate when conducting the EDA.

  + `report.html` report generated by DataExplorer library. The report contains Basic Statistics, 
  Data Structure, Missing Data Profile, Univariate Distribution plots, Correlation Analysis, and 
  Principal Component Analysis.
  + `report_files` supporting files for the report.html report
- `data/` Containsthe data files used in this study.

  + `Beers.csv` list of 2,410 craft beers and their attributes.
  + `Breweries.csv` list of 558 breweries within the United States and their attributes.

- `docs/` contains all the background information important for understanding
the purpose of the study. This folder contains two files.

  + `CaseStudy01Sp2020_2.docs` the case study document that outlines the questions to be answered
  by this study.
  + `CaseStudy1 Rubric.docx` requirements document that contains the requirements the study must 
  contain upon submission.

- `final/` this folder contains the files required for the group project final submission.

  + `DS6306 Group Project 1 Final.pptx` final presentation used to share the findings for this study.

- `Case Study 01.rmd` the Rmarkdown with code and analysis for this study
- `Case Study-01.html` the Knit HTML version of the Case Study 01.rmd Rmarkdown file
- `DDS6306-Group-Project-1.Rproj` R project file for Case Study 01 project
- `README.md` the repo file and folder definition, and the answer to the analysis questions

# Analysis Questions

1.   How many breweries are present in each state?
The top 5 breweries make up 31.3% of the breweries in the US.

Colorado has 47 breweries which is 8 more than California which is second with 39 breweries. Within Colorado most of the breweries seems to cluster around two major cites Denver and Boulder. Within Boulder a breweries company call Avery Brewing alone holds nearly three times the average number of Colorado breweries. Many of these breweries offers free samples just for stepping inside. And this is what I found most interesting about why CO has the largest number of breweries. It is because Colorado’s water is extremely well suited for brewing great tasting beer, just the slight mineral adjustment and simple filtrations with very minimal treatment produces the best beer in the whole country. Which mean with just very little investment, you can produce best-in class beers with wide variety. Just the regular water along has 80-90% of water chemistry required to make Beer which is very fascinating. So what is there in CO water that makes it the best for brewing? CO water has the perfect mix of magnesium, sodium, sulfates, bicarbonates and calcium which determines the water's hardness and ultimately its suitability for brewing and great test. Hence water chemistry is a major reason why Colorado has so many breweries excelling in different styles of beer from round the world Lone Tree won a gold medal at the 2017 Great American Beer Festival

2.   Merge beer data with the breweries data. Print the first 6 observations and the last six observations to check the merged file.

We merged the two data set into one and named it as 'mergeDF', the primary key being used is 'Brewery_id' from Beer data set, and 'Brew_ID' from Breweries data set. We also changed the two columns' name for clear understanding. The first and last 6 observations were showed there with head/tail command.

3.   Address the missing values in each column.

There are 62 observations where both ABV and IBU had  NA values. 943 observations where the IBU only are NA’s. We replaced 62 NA’s in ABV with state level median value. Replacing 1005 NA’s in IBU with state level median led to an 18% reduction in the accuracy of the correlation model. Predicted values from simple linear regression model are used to replace missing values in IBU to improve the accuracy of the model.

4.   Compute the median alcohol content and international bitterness unit for each state. Plot a bar chart to compare.

Median ABV and IBU data have been sorted and plotted. The median ABV per state appears fairly consistent with an overall ABV median of 0.056. Nevada falls in the middle with median ABV of 0.062 and Utah is at the bottom with 0.04. The median IBU per state appears to change considerably between states with an overall IBU median of 37. West Virginia falls in the middle with median value 57.5  and Kansas is at the bottom with value 22. Arkansas and Utah are tied for lowest ABV at 4.0%. Maine has highest ABV at 6.7%. Wisconsin has the lowest IBU @ 19. Maine has the highest IBU @ 61

5.   Which state has the maximum alcoholic (ABV) beer? Which state has the most bitter (IBU) beer?

Maximum ABV and IBU data have been sorted and plotted. The maximum ABV by state appears to have only a small variance. Colorado has the Maximum ABV at 0.128 and Delaware has the lowest at 0.055. The maximum IBU per state appears to vary between states with an overall median of all max values at 92.82. Oregon has the highest Max IBU at 138 and Arkansas has the lowest at 44.11.

6.   Comment on the summary statistics and distribution of the ABV variable.

The ABV clearly illustrates that the IPA variety has more Alcohol By Volume than other varieties.  This is across all can sizes with one exception (can size=19.2) in the “other” type. IPA style beer is the predominant variety when ABV exceeds 0.06. This again indicates that IPA beer tends to have higher alcohol content than other variety.

7.   Is there an apparent relationship between the bitterness of the beer and its alcoholic content? 
Draw a scatter plot.  Make your best judgment of a relationship and EXPLAIN your answer.

The point plot below illustrates what appears to a positive linear relationship between the ABV and IBU. The addition of line trend to the point plot below confirms the presence of a positive linear relationship between the ABV and IBU. The correlation between IBU and ABV is 0.757878, with a p-value < 2e-16, Multiple R-squared is 0.5744, meaning that 57% changes in exploratory variable ABV can explain the changes in response variable IBU. GGPairs Plot below shows a strong correlation between ABV and IBU across all styles of beers. The strongest correlation is in other beer style category at 0.787 followed by IPA at 0.689.

8.  Budweiser would also like to investigate the difference with respect to IBU and ABV between 
IPAs (India Pale Ales) and other types of Ale (any beer with “Ale” in its name other than IPA).  
KNN classification is used to investigate this relationship.  Provide statistical evidence 
one way or the other. Budweiser audience is comfortable with percentages … KNN is very easy to 
understand conceptually.

In addition, while you have decided to use KNN to investigate this relationship (KNN is required) 
you may also feel free to supplement your response to this question with any other methods or 
techniques used.  Creativity and alternative solutions are always encouraged.  

Our KNN model predicts the outcome with an accuracy of 83% which is pretty good. Optimized K value to 3 based upon 100 iterative run. 


9. Knock their socks off!  Find one other useful inference from the data that you feel Budweiser 
may be able to find value in. You must convince them why it is important and back up your conviction 
with appropriate statistical evidence. 

This information is useful in that it can be used to target the beer consumers based on their consumption habits ( ABV  and Size of the beer) and location. By visualizing the Ounces of beer bottles and cross referencing this data with ABV we are able to see a pattern (we can clearly see that most of the 12 and 16 ounces). The pattern can then be layed over states to show which states may act as the largest consumers of beer products. Lighter blue circles that sit higher on the graph show high alcohol content consumption. We can see the trend that most consumed beer is 12 and 16 ounces


## Conclusions TODO<write the final conclusion>

The primary objective of our project is to take two different dataset, beer data set containing a list of 2410 US crafts beers and breweries dataset containing 558 breweries an perform analysis. We transformed the data in CVS format into data frame using R-programming, inspected and analyzed the structure of the data, merged the two data frames, and performed analysis on the merged final data set.

As Data Scientist, it is very rare that we get to work only on a single perfect data. A large percentage of work is to accept different datasets and merge them into one final data frame before processing as it is illustrated in our project. After analyzing the data, statistical inference is then made.

The objective of our project is to provide some valuable information such as summary of two dataset, relation between International Bitterness Unit (IBU) and Alcohol By Volume (ABV), number of breweries in each state and how can be an important to Budweiser, and to compute the median and max IBU and ABV. 

Based on our team’s analysis, we found that majority of breweries appears to be clustered towards the west of the Mississippi river with California and Colorado being the top two states. Why do these states mostly CO has the highest number of Breweries? Water is the secrete ingredients making CO the top state for breweries in the world and also making 2017 gold medal winner. The water alone contains about 80-90% of water chemistry needed to make the best beers. CO water has the perfect mix of magnesium, sodium, sulfates, bicarbonates and calcium which determines the hardness of water and ultimately its suitability for brewing great testing beers. Hence, we believe that Budweiser should consider thinking about CO in their next project. 

Other state of interest, New Hampshire which we believe has the high potential for growth has the highest beer consumers due to no beer sale tax but do not have much breweries. Utah on the other hand has the lowest beer consumer and only allows ABV <4 % which could be due to it being a Mormon state. We were surprised at Nevada, being the home of Las Vegas has only two breweries. North and South Dakota are lowest in the number of breweries but are one of the highest in beer consumption capita. 

Our computation of the median IBU and ABV for each state shows that median IBU appears to vary considerably between the states. However, West Virginia falls in the middle with median IBU 37 and Arkansas at the bottom with IBU 7.8.  On the other hand, median ABV per state appears somewhat consistent, with Nevada being in the middle with median ABV of 0.0669 which kind of make sense because people who visit Las Vegas majority of the time likes to get drunk, gamble and enjoy their time. Utah again, being the lowest beer consumer also has the lowest ABV of 0.051. In term of Max ABV, all the state appears to have only a small variance. Colorado has the max ABV of 0.128 and Delaware the lowest at 0.055. 

IBU which stands for International Bitterness Units, a measure of the bitterness in beer. There is a saying spicier the better, same applies to the beers as well. Bitter the beer better is the taste. The bitterness in beer terms mean better flavor which is produced by adding aroma hop flowers. According to CNBC news, the reason for rise in craft beer sales is its high IBU among the home brewing company that’s growing from garage to thriving commercial company. Our analysis shows that max IBU by states appears to vary between the state ranging from 138 to 0, with Oregon being the highest (138) and Arkansas the lowest (44.11). The reason we believe Oregon has the highest IBU is because Oregon is known for homemade craft beer and they also add high-grade marijuana in their craft beers. However, according to new law, started in Jan 2020, they are avoiding THC or CBD in their beers due to health concern. Arkansas stands at the bottom for IBU. 

In a nutshell, our analysis of relationship between ABV and IBU shows that there is somewhat positive linear relation. In general, as the ABV rises so does the bitterness. IPA type has the highest ABV compared to other type also higher the Ounces higher the ABV. 

Ref: 
https://www.cnbc.com/2014/07/03/state-of-hopiness-how-many-ibus-in-your-ipa.html
https://apnews.com/640bcd2970430a6cdaa7c37166dac1c9S
