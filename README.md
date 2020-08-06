daily-temperatures-eda
# Project No. 3: Daily Temperatures EDA (Global, Europe, Austria)

This exploratory analysis looks at global temperatures between 1995 and 2019 and explores Europe and Austria in more detail.

After cleaning the dataset, the data is explored on three levels: on a global, European, and Austrian one. To visualize the data in order to answer the questions below, the libraries seaborn and matplotlib are used, including lineplots, barplots, boxplots, violinplots, histograms, and heatmaps.

### Global

<b>1. How did yearly/monthly global temperatures change between 1995 and 2019?</b>

![1a](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/1a.png)
![1b](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/1b.png)

<b>2. How do average temperatures of different regions in the world differ from each other and how did they change over time?</b>

![2a](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/2a.png)
![2c](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/2c.png)

<b>3. What are the hottest and coldest countries in the world?</b>

<p align="eft">
  <img width="220" height="300" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/3a_.png">
</p> <p align="left">
  <img width="170" height="300" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/3b_.png">
</p>


### Europe

<b>4. How are average European temperatures distributed?</b>

![4a](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/4a.png)
![4b](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/4b.png)

<b>5. How do average temperatures of different European countries compare to each other?</b>

![5a](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/5a.png)
![5b](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/5b.png)

<b>6. How did yearly/monthly average temperatures change in Europe between 1995 and 2019?</b>

![6a](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/6a.png)
![6b](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/6b.png)


### Austria

<b>7. How are average Austrian temperatures distributed?</b>

![7a](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/7a.png)

<b>8. How did yealry/monthly temperatures change in Austria between 1995 and 2019?</b>

![8a](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/8a.png)
![8b](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/9b.png)

<b>9. What are the average temperatures in Austria each month?</b>

![9a](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/9a.png)
![9b](https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/8b.png)


### Problems I faced and how I solved them
- Some countries, above all in Africa, had a lot of missing temperature values (as  high as 80%). Thus, I decided to fill any missing temperatures with the mean temperature of the respective month and city. However, this was not possible for every city, since some of them lacked entire months of temperature data. So for those countries, I filled the missing values with the overall mean of the respective city. Another idea would have been to fill the missing temperature with the temperature of the previous day (however, for those cities with entire months missing, this again could have proven problematic).
- Since I am not very familiar with temperatures in Fahrenheit, I converted them to Celsius. However, I overlooked the fact that missing temperature values (stored as -99) were also converted (to -72.78). So when I then turned to handling missing temperature values and converting them to NaN values, 'df.loc[df.AvgTemperature == -99, 'AvgTemperature'] = np.nan' did not apply to any data anymore - equally when filling NaN values with the mean (see above). When plotting and analyzing the data, however, the many temperature values of -72.78 distorted many of the plots, especially in Africa, where a lot of data is missing. Only after carefully analyzing what was going on was I able to find my mistake. I fxied this by first coverting -99 to Nan, and only then converting the temperature values from Fahrenheit to Celsius.
  
Data from: https://www.kaggle.com/sudalairajkumar/daily-temperature-of-major-cities
