# Crime Trends Analysis Tool
The Crime Trends Analysis Tool analyzes crime trends and surfaces problematic crime conditions, enabling commanders to begin problem-solving immediately.

### The Problem: 
Firstly, Commanders are often not immediately aware that a particular crime type is spiking above normal levels in their command.  There is typically a delay between the time a crime condition emerges and when that condition is actually identified by the command. Why? Precinct commanders and their staff do not have the resources nor the expertise to conduct statistical analyses on a weekly basis. As a result, commanders can be slow to react to crime problems.

Secondly, while the CompStat book provides valuable information by comparing crime counts from the same period a year ago, the CompStat book doesn't indicate whether a percent increase or decrease in crime is significant. Is an 8% increase in robbery in the 28th precinct compared to last year a spike? Perhaps, but maybe last year was experiencing a historic low. Is a 10% decrease in grand larceny in the 20th precinct significant? Perhaps, but maybe last year was an all-time high and this year is also experiencing a high that happens to be lower than last year. The fundamental difference between this tool and the CompStat book is that this report looks at averages of crimes over time, which may provide a better understanding of "normal" levels of that crime.

### Our Solution:
Alerting commanders of new crime trends enables them to immediately begin problem-solving to address problematic conditions.  By automating statistical analyses of any number of crime types across all precincts, crime problems can be rapidly identified. Commanders and executives can then be alerted with relevant trend details, leading them to take action, whether it be through a new deployment strategy, refocusing investigative resources, or a community outreach effort.

### How does it work?
Historical crime data is analyzed to identify "normal" and statistically abnormal levels of crime. In mathematical terms, for each crime type in each precinct, several rolling means and standard deviations of 28-day crime counts are calculated. We use a slight variation of [z-score](https://en.wikipedia.org/wiki/Standard_score) called the [Poisson z-score](http://journals.sagepub.com/doi/abs/10.1177/1461355716642781?journalCode=psma) (Source: Andrew P Wheeler) to determine how far from the mean a given 28-day period lies. We calculate Poisson z-scores for the rolling 52-week period, rolling 26-week period, rolling 12-week period and the same week of the year over the last several years. We then take the average of those four p-zscores and classify crime trends into five categories (from least to most concerning): major reduction, decrease, normal, condition, and spike.

### What can I expect in v3.0?
The current approach attempts to account for seasonality effects as well as short(er) term trends. In future versions, I would like to test [Facebook's Prophet](https://facebookincubator.github.io/prophet/) package and [Azavea's](https://www.hunchlab.com/) approach in a January 2006 White Paper entitled "Crime Spike Detector: Using Advanced GeoStatistics to Develop a Crime Early Warning System."

### Feedback
If you find any bugs or suggestions on how to improve the tool, please share your feedback. We welcome any and all improvements.

**Author:** Benjamin Singleton

**Published:** September 15, 2017

## User Guide
1. Download Anaconda Python 3.6+ [(download link)](https://www.anaconda.com/download/)
2. Create the project environment by type `conda env create -f environment.yml` in the console. This will install all of the packages required for the notebook to load properly.
3. Activate the environment `source activate crime_trends` in the console.
4. Start a Jupyter Notebook `jupyter notebook` in the console in the directory where this project is located.
