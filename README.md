# Daily Temperatures EDA (Global, Europe, Austria)

This exploratory analysis looks at global temperatures between 1995 and 2019 and explores Europe and Austria in more detail.

After cleaning the dataset, the data is explored on three levels: on a global, European, and Austrian one. To visualize the data in order to answer the questions below, the libraries seaborn and matplotlib are used, including lineplots, barplots, boxplots, violinplots, histograms, and heatmaps.

### Global

<b>1. How did yearly/monthly global temperatures change between 1995 and 2019?</b>

<p align="center">
  <img width="1080" height="576" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/avg_global_temps.png">
</p>

<b>2. How do average temperatures of different regions in the world differ from each other and how did they change over time?</b>

<p align="center">
  <img width="1080" height="576" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/avg_temp_regions.png">
<p align="center">
  <img width="950" height="670" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/dist_temps_kde.png">
</p>

<b>3. What are the hottest and coldest countries in the world?</b>

<p align="left">
  <img width="220" height="300" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/3a_.png">
</p> <p align="left">
  <img width="170" height="300" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/3b_.png">
</p>


### Europe

<b>4. How are average European temperatures distributed?</b>

<p align="center">
  <img width="720" height="360" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/dist_temps_europe.png">
</p>

<b>5. How do average temperatures of different European countries compare to each other?</b>

<p align="center">
  <img width="1440" height="450" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/dist_temps_europe_box.png">
<p align="center">
  <img width="1080" height="576" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/avg_temps_europe_country.png">
</p>

<b>6. How did yearly/monthly average temperatures change in Europe between 1995 and 2019?</b>

<p align="center">
  <img width="1000" height="500" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/avg_temps_europe_heatmap.png">
</p>


### Austria

<b>7. How are average Austrian temperatures distributed?</b>

<p align="center">
  <img width="720" height="504" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/dist_temps_austria.png">
</p>

<b>8. How did yearly/monthly temperatures change in Austria between 1995 and 2019?</b>

<p align="center">
  <img width="1000" height="500" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/avg_temps_austria.png">
<p align="center">
  <img width="1000" height="500" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/avg_temps_austria_heatmap.png">
</p>

<b>9. What are the average temperatures in Austria each month?</b>

<p align="center">
  <img width="1080" height="576" src="https://github.com/HeleneFabia/daily-temperatures-eda/blob/master/images/month_temps_austria.png">
</p>


### Problems I faced and how I solved them
- Some countries, above all in Africa, had a lot of missing temperature values (as  high as 80%). Thus, I decided to fill any missing temperatures with the mean temperature of the respective month and city. However, this was not possible for every city, since some of them lacked entire months of temperature data. So for those countries, I filled the missing values with the overall mean of the respective city. Another idea would have been to fill the missing temperature with the temperature of the previous day (however, for those cities with entire months missing, this again could have proven problematic).
- Since I am not very familiar with temperatures in Fahrenheit, I converted them to Celsius. However, I overlooked the fact that missing temperature values (stored as -99) were also converted (to -72.78). So when I then turned to handling missing temperature values and converting them to NaN values, 'df.loc[df.AvgTemperature == -99, 'AvgTemperature'] = np.nan' did not apply to any data anymore - equally when filling NaN values with the mean (see above). When plotting and analyzing the data, however, the many temperature values of -72.78 distorted many of the plots, especially in Africa, where a lot of data is missing. Only after carefully analyzing what was going on was I able to find my mistake. I fxied this by first coverting -99 to Nan, and only then converting the temperature values from Fahrenheit to Celsius.
  
Data from: https://www.kaggle.com/sudalairajkumar/daily-temperature-of-major-cities
