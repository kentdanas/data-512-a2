# An Exploration of Sources in Bias in Data
This repository contains the code, resulting data, analysis, and discussion for an exploration of sources of bias in Wikipedia articles on political figures from a variety of countries. This work was originally completed as part of the University of Washington's DATA 512 course in Autumn 2018. The goal of this assignment was to identify bias in Wikipedia data and complete a discussion of the potential sources and consequences of such bias.

## Project Organization
This repository contains a jupyter notebook with all code required to complete this analysis, one csv with raw data from one of the data sources, one csv with all combined and processed data, as well as a license and the readme. The repository has the following structure:

```
data-512-a2/
  |- data_clean/
     |- final_article_dataset.csv
  |- data_raw/
     |- page_data.csv
  |- .gitignore
  |- LICENSE
  |- README.md
  |- hcds-a2-bias.ipynb
```

## Source Data
The data used to complete this analysis included data on English Wikipedia articles on politicians, as well as population data. The datacame from two different sources:

#### Article Data
The data on English Wikipedia articles about politicians is available on figshare and can be found at this link: https://figshare.com/articles/Untitled_Item/5513449

The data contains the name of the article, the country the article was written about (country of the politician) and the ID of the last revision made to the page.

This data is released under the CC-BY-SA 4.0 license (https://creativecommons.org/licenses/by-sa/4.0/). Because this license allows for sharing and redistributing the data, I have included the downloaded data in the 'raw_data' folder of this repository.

#### Population Data
The population data used for this analysis is available on DropBox and can be found here: https://www.dropbox.com/s/5u7sy1xt7g0oi2c/WPDS_2018_data.csv?dl=0

The data contains the name of the country, and the population, in millions, as of mid-2018. 

The data is originally from the Population Reference Bureau (PRB); more information on the data can be found on their website, here: https://www.prb.org/2018-world-population-data-sheet-with-focus-on-changing-age-structures/. This data set is not specifically licensed, but it is covered by the copyright on PRB's website. Because the data is not licensed to allow sharing or redistribution, I have not included it in this repository; however, it can be easily downloaded from either of the links above.

## Results
The results of this analysis include a final .csv with processed data, and four tables:

 - Top 10 countries ranked by proportion of articles per capita as a percentage
 - Bottom 10 countries ranked by proportion of articles per capita as a percentage
 - Top 10 countries ranked by proportion of high quality articles as a percentage
 - Bottom 37 countries ranked by proportion of high quality articles as a percentage (note that this table shows the bottom 37 countries because there were 37 countries with zero high quality articles)

The tables can be found in the jupyter notebook (hcds-a2-bias.ipynb) included in this repository; they are not copied here due to markdown's lack of table functionality.

## Discussion
I've split this discussion of the results of this analysis into two sections: 1) potential sources of bias in this analysis, 2) how the results show/do not show these sources of bias. Throughout both sections I discuss potential reasons for these sources of bias.

#### Potential Sources of Bias
Before completing this analysis and reviewing any results, I identified two major sources of bias that could impact the results. The first source of bias, which could impact the results on the proportion of articles per capita by country, could be in the underlying article data itself. Political topics are typically highly sensitive, and there are many different political systems around the world. I would expect this to result in uneven results when looking at the coverage in articles on politicians by country. I would also expect this to be especially true for a data source like Wikipedia, for which anybody can write the articles (and most are not written professionally). For example, politicians themselves could be writing the articles, and depending on how many politicians there are in various countries, this could skew the data. Writing an article like this also requires English literacy, and a reliable internet connection; these things are certainly not uniform throughout the world, and so I would expect this to have an impact on the results.

The second main source of bias I would expect for this analysis, which would impact the results on the proportion of "high quality" articles per country, could be from the ORES model used to classify the articles' quality. The ORES documentation (https://www.mediawiki.org/wiki/ORES#Article_quality) indicates that the model is trained using comments from Wikipedia pages that have been deleted; it also indicates that the model is trained to replicate human quality assessments using structural characteristics of the article as training features. This could potentially introduce bias since the model is based on human classification (and humans can easily be biased!). How the model classifies could be highly dependent on what types of articles were used to train it (e.g. were there any political articles used in training, and do political articles follow the same structural patterns as other articles?), as well as what humans have decided is "high quality" and how this applies accross articles of many different topics.

#### How the Results Show Bias
While this analysis is pretty brief, and certainly can't bring to light any/all bias present in this data or the analysis, I do think it shows some clear signs of the data not being perfectly unbiased or random. Taking first into consideration the proportion of articles per capita: this is something that I would expect to be relatively consistent across countries if there were no bias present. However, this is not at all what the results show - the proportions range from 0.000081% - 0.55%, which is a huge range! In addition, the 10 lowest countries are not ones with particularly low populations, but instead seem to contain countries that are or have been dictatorships, have restrictions on media access, or have widespread poverty; the fact that these things might impact the amount of Wikipedia contributions the population is making is not surprising, and could certainly indicate bias in the data. The countries with the highest proportions, on the other hand, seem to be countries with very low populations. I found this surprising, as I would have expected that a per capita analysis would remove any trends with population, but that doesn't seem to be the case here. Note that this analysis does not consider exactly who is writing the articles - so it may be that articles written about politicians in a particular country are actually written by people in a different country, which could partially explain why the per capita figures for very low population countries are relatively high. 

I found the analysis of the proportion of high quality articles per country to be less conclusive. There were 37 countries with zero high quality articles according to the ORES predictions. Looking at these countries, I don't see any particular patterns; some of them are high population, some are lower, and they represent many points along the geographic and economic spectrums. For countries with a high proportion of high quality articles, the fact that the United States was the only western country on the list suprised me, given that western countries have often have longer established democracies, more resources (higher rates of internet access, spoken English, etc.), freedom of speech laws, etc. that I would expect to lead to more "high quality" political coverage. This would lead me to question whether the model has any bias built in that would impact the predictions. I think a more detailed analysis, including a deep-dive into the data used to train the model would be required to really answer that question.
