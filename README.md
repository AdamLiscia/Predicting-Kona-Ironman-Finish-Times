# Predicting-Kona-Ironman-Finish-Times
Exploring the effects of weather at the Ironman World Championship in Kona

![alt text](https://github.com/AdamLiscia/Predicting-Kona-Ironman-Finish-Times/blob/master/Daniela%20Ryf.png)

The Ironman is a triathlon consisting of a 2.4 mile swim, 112 mile bike, and 26.2 mile swim. Pro males tend to have finishing times just over 8 hours, and females tend to complete the course in around 9 hours. In 2017 Patrick Lange set a course record with a a time of 8:01:40 and Daniela Ryf won with a time of 8:50:47.

![alt text](https://github.com/AdamLiscia/Predicting-Kona-Ironman-Finish-Times/blob/master/Patrick%20Lange.jpg)

This past year, Partick Lange shattered the course record with a time of 7:52:39 (9min 1 sec faster), and Daniela Ryf did the same for the females with a time of 8:26:16 (24min 31 sec faster).

We wanted to look into the data to try to explain this. Questions we wanted to answer included:

- Was 2018 an anomaly?
- If not, can we predict pro finish times?
- What effects did weather have on performance?
- Does what part of the world you come from have an effect on time?


# Gathering Data
As with all projects, we needed data. Fortunately, Ironman provides all the results for on thier website for us to scrape. We also gathered all of our weather information from timeanddate.com.

# Data Exploration
Here is a graph showing the distrubution of times for the pro male athletes.  As we can see, they are normally distributed.

![alt text](https://github.com/AdamLiscia/Predicting-Kona-Ironman-Finish-Times/blob/master/Pro%20Times.png)

# Data Cleaning and Engineering
The first 2 days of our project were spent on cleaning our data and figuring out what how we wanted to represent our data.

Some issues we ran into:

-  Wind direction was given as S, SSW, SW, WSW, and W. This didn't seem to be exactly categorical because there are relationships between these directions. We decided to over come this by use sin and cos to break the wind direction and speed into it's X and Y components.
-  We had only 11 weather observations. This seemed low, but after speaking to our classmates we found that we can add these observed weather patterns to each result.
-  We first wanted to assess the finish times of all the athletes, but the data becomes skewed and the 17 hour cut off time starts to effect our data. That when we decided to limit our filed to just the pros who have a more normally distributed set of times.
-  We first wanted to try using each athlete's country as a feature, but then decided that continent was a much more meaningful feature to use instead.

# Feature Selection 
After prepping our data and adding raising the degree of our data, we were left with 350 different features.  With definitely had to do some feature selection to trip down the highly correlated features and remove noise.  We used the StandardScalar to preprocess, then applied a VarienceThreshhold to drop features.  After looing at the correlation matrix, were able to drop a few more highly correlated features, resulting in 17 final fetures to run a model with.  Here is the final correlation matrix:

![alt text](https://github.com/AdamLiscia/Predicting-Kona-Ironman-Finish-Times/blob/master/Correlation%20Matrix.png)
