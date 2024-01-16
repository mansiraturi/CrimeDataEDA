<b>Introduction </b>

The given dataset includes all reported criminal occurrences that have occurred in the City of Los Angeles between 2020 and the current year. Original crime reports, which are frequently recorded on paper, are the source of the statistics. There is a chance of errors or inconsistencies, similar to with any manually recorded data. This dataset is an invaluable tool for understanding the trends and patterns of crime in the city.

Data Source
The dataset is transcribed from original crime reports, which serve as the primary source of information for each incident. It is important to acknowledge that variations in reporting, data entry errors, or omissions may exist, and these can affect the accuracy of the data.
![image](https://github.com/mansiraturi/CrimeDataEDA/assets/83804789/78adcf8a-1c69-4544-9f3b-0ce344753bf8)

<b>Objectives </b>

Data Cleaning and Preparation: We begin with the essential step of data cleaning, rectifying inconsistencies, handling missing values, and ensuring the dataset's readiness for analysis. Here, we removed rows with all null values, 

Crime Type Analysis: We aim to identify the most common crime types within the dataset, shedding light on the areas of concern that demand heightened attention.

Demographic Insights: We delve into the demographic details of crime victims and perpetrators, exploring age and gender-based patterns.

Outlier Detection: By identifying outliers, we pinpoint unusual or extreme occurrences that may require specialized attention or investigation.

<b> <u>Data Cleaning </b> </u>

Identifying All-Null Rows: The first step in the process involved identifying rows within the dataset that consisted entirely of null values. This was achieved using the .isnull() method, which created a boolean mask marking rows with null values.

Dropping Rows with All Null Values: Rows identified as containing all-null values were subsequently removed from the dataset using the dropna() method with the parameter how='all'. This process effectively eliminated records that offered no substantive information due to complete data absence.

Dropping Duplicates: Duplicate rows were identified and removed using the drop_duplicates() method. This process ensured that only unique records remained in the dataset.


 <b >Handling Missing Values </b>

'Vict Sex' and 'Vict Descent' columns: Missing gender and descent information was filled with the placeholder 'X.'

'Weapon Desc' column: Missing weapon description information was filled with 'No Weapon Used.'

'Weapon Used Cd' column: Missing weapon code information was filled with 'NA.'

'Cross Street' column: Missing cross street information was filled with 'Info Not Recorded.'

'Premis Desc' column:  Missing values in this column may indicate a lack of information regarding the premises description associated with certain crimes filled with ‘Not Known’.

 

<b>Date and Time Formatting </b>

'Date Rptd' and 'DATE OCC' columns: Dates were converted to datetime objects using the format '%m/%d/%Y.'

'TIME OCC' column: The time information was standardized by adding leading zeros, replacing non-numeric characters with colons, and converting it to a datetime object with the format '%H:%M.'

<b>Deal with Outliers </>
![image](https://github.com/mansiraturi/CrimeDataEDA/assets/83804789/915c047a-1ce5-48b1-9cb1-43d28db006c5)
![image](https://github.com/mansiraturi/CrimeDataEDA/assets/83804789/a2cafa01-e0d2-482a-aec6-72ecfa40b76f)


One crucial aspect of data preprocessing in our crime data analysis project involved dealing with outliers in the 'Vict Age' column. Outliers, which are data points significantly deviating from the majority of observations, can distort our analysis and impact the reliability of our findings.

Box Plot Analysis:
To identify potential outliers, we conducted an initial box plot analysis of the 'Vict Age' column. The box plot visually presented the distribution of age values, highlighting any potential extreme values that might be considered outliers. Outliers were visualized as data points located outside the "whiskers" of the box plot.


X-axis Label Rotation: To enhance readability, the x-axis labels, which correspond to 'Vict Age,' are optionally rotated by 45 degrees. This rotation makes it easier to interpret the age-related data.

Findings

Box Plots for Victim Ages: The generated box plots offer a visual representation of the distribution of victim ages in the crime dataset. Each box plot presents key statistics, including the median, upper and lower quartiles, and potential outliers.


Standardization and Normalisation

Crime Count: Each crime is labeled with the year and month it occurred based on the ‘DATE OCC’ column. The data is then grouped by year which is then divided by the number of months the data is present for. This way, the years for which the crime rates haven’t been recorded throughout (for all the months), won’t be reflected in the dataset and uniform comparison could be made. 

Encode Categorical Data



Counting Non-Empty 'Crm Cd' Columns: The transformation process begins with counting the number of non-empty 'Crm Cd' columns (specifically, 'Crm Cd 1', 'Crm Cd 2', 'Crm Cd 3', and 'Crm Cd 4') for each row. This count is determined using the .count() method along the specified axis.

Mapping to 'Combined_Crime_Codes': The resulting count is then mapped to the 'Combined_Crime_Codes' column. This new column categorizes each crime incident based on the count of non-empty 'Crm Cd' columns. The values in Combined_Crime_Codes tell us the number of cases the crime falls under. 

Displaying the DataFrame: The DataFrame is displayed to show the relevant columns: 'Crm Cd 1', 'Crm Cd 2', 'Crm Cd 3', 'Crm Cd 4', and the newly created 'Combined_Crime_Codes' column. This data transformation enhances the dataset by simplifying the representation of the number of crime codes associated with each incident.
Another category is added to the dataframe, by classifying the crimes occurred on the basis of weapons used by the perpetrator

<b>Exploratory Data Analysis (EDA) </b>

Visualize overall crime trends from 2020 to the present year

![image](https://github.com/mansiraturi/CrimeDataEDA/assets/83804789/5c2012e8-0757-4c18-9e88-6cca07614fc1)



Filtering Data for the Specified Date Range: The dataset was filtered to retain only the records that fall within the specified date range. In this case, we selected the period from January 1, 2020, to the latest date available in the dataset. 

Visualizing the Data: Seaborn was used to construct a line plot in order to see the trends in crime incidents over time. Dates are plotted on the x-axis, while the number of crimes plotted on the y-axis. The visual depiction of the evolution of crime counts between 2020 and the present is offered by this line plot.

Findings
Crime Trends Over Time: The line plot illustrates the number of reported crimes over the years, highlighting any notable fluctuations, trends, or patterns. From the depiction we can conclude that the crime rate peaked in the year 2022 with the least being in the year 2020.




Analyze and visualize seasonal patterns in crime data


![image](https://github.com/mansiraturi/CrimeDataEDA/assets/83804789/f7c760db-0014-4b07-976b-b8f12257aa29)



Month Extraction: We converted the 'DATE OCC' column to datetime format and extracted the month and year. This allowed us to categorize the data by month and year for further analysis.

Grouping and Counting Crimes: We collected the total number of crimes for each month throughout several years, then sorted the data by year and month using.groupby(), and the number of offenses for each month was counted using.size(). A DataFrame with the columns "Year," "Month," and "Crime Count" was the end result.

Visualization: To visualize crime trends by month over multiple years, we created a line plot using Seaborn. The x-axis represents months (January to December), the y-axis represents the number of crimes, and the lines represent different years. This visualization provides insights into seasonal variations and long-term trends in crime reporting.

Findings
Seasonal Patterns: The line plot illustrates how the number of reported crimes varies by month over multiple years. It highlights any seasonal patterns or fluctuations, which can be valuable for law enforcement and policy planning.

Long-Term Trends: By considering data over several years, we can identify long-term trends in crime reporting, which is related to social, economic, or environmental factors.


The most common type of crime and its trends over time


![image](https://github.com/mansiraturi/CrimeDataEDA/assets/83804789/1de42fb7-93de-46b5-8bae-135b67ad4ffd)


Identifying the Most Common Crime: The first thing we did was classify the dataset according to the criminal descriptions included in the 'Crm Cd Desc' column. We were able to tally the instances of every distinct crime description thanks to this grouping. Following this operation, we discovered that, with 65,286 incidents, "BATTERY - SIMPLE ASSAULT" is the most frequent criminal type.
Filtering Data for the Most Common Crime: Next, we filtered the dataset to focus on data related to the most common crime type, "BATTERY - SIMPLE ASSAULT." This step allowed us to isolate and analyze this specific crime.

Yearly Trends: We then converted the 'DATE OCC' column to datetime format and extracted the year. Subsequently, we grouped the data by year, counting the number of occurrences of "BATTERY - SIMPLE ASSAULT" for each year.

Visualization: To present the trends over time, we created a line plot. The x-axis represents years, and the y-axis represents the number of "BATTERY - SIMPLE ASSAULT" cases. The latest date in the dataset, up to which the trends are shown.

Findings

Most Common Crime: The most common type of crime in the dataset is "BATTERY - SIMPLE ASSAULT," with a frequency of 65,286 occurrences. This indicates a high prevalence of this crime.

Trends Over Time: The line plot illustrates how the number of reported "BATTERY - SIMPLE ASSAULT" cases has changed over the years. This visualization provides insights into the temporal variations in this specific crime type.


<b>Differences in crime rates between regions or cities </b>

![image](https://github.com/mansiraturi/CrimeDataEDA/assets/83804789/e29a2f56-ab6c-4814-8b2f-aafd67cfa0cf)



Categorical Plot: We used Seaborn's catplot function to create a categorical plot. The x-axis represents "AREA NAME," while the y-axis represents the count of crime incidents in each area. This type of visualization helps visualize the relative frequency of crime incidents in different geographic regions.

Aspect and Label Rotation: We adjusted the aspect ratio to 2.0, which maximizes the readability of the figure size, to guarantee an aesthetically pleasing and educational plot. In addition, the set_xticklabels function was used to rotate the x-axis labels by 45 degrees, which improved the area names' readability.

Findings

Distribution of Crime Incidents:From the visualisation it can be concluded that the ‘Central’ area had the highest number of crimes over the years, with the foothill area being the safest of them all.

Correlations between economic factors and crime rates
Selection of Economic Factors: Datasets were chosen based on the factors that might have an influence over the crime rates. We selected 3 datasets- gdp dataset(could data only for 2020 and 2021), unemployment data and poverty data (for 2020 and 2021 only) for the county of Los Angeles.




1) Crime Rate and GDP


![image](https://github.com/mansiraturi/CrimeDataEDA/assets/83804789/fd82374e-a866-4fcb-bff5-90e6958563c9)


Visualization: The trend was plotted for the two datasets by mapping them for the common years in the dataset to clearly analyze the trend for the two columns (the datasets were merged and the values plotted accordingly)
Findings: From the graph much can’t be inferred as the data we have for GDP is limited (restricted to only 2020 and 2021), failing in generating a trend.

2) Crime rate and Unemployment Rate
![image](https://github.com/mansiraturi/CrimeDataEDA/assets/83804789/704fd69b-6e56-4a3f-8eb6-58e349af033e)



Correlations: The correlation heatmap shows the correlation coefficients between the Crime Rate and Unemployment Rate. Strong negative correlations are represented by coefficients ranging from -1 to 1, strong positive correlations by coefficients of 1, and no correlations by coefficients of 0. From the visualizations it can be concluded that with the increase in unemployment, the crime rates may decrease BUT they are influenced by other factors as well which could have resulted in such an outcome. 

Frequency of crime by days of the weeks

![image](https://github.com/mansiraturi/CrimeDataEDA/assets/83804789/106a3416-24b5-490d-9e25-d895b6aa375a)


Day of the Week (DoW): First, we took the date of the criminal incident and used it to determine the day of the week in the 'DATE OCC' column. 

Data Visualization

Countplot: Using Seaborn, we produced a countplot in which the number of crime incidents was represented by the y-axis and the day of the week (DoW) by the x-axis. 

Findings:

1. Day of the Week Extraction:
We first extracted the day of the week from the 'DATE OCC' column in our dataset. By using the pd.to_datetime function, we converted the date values into a format that allowed us to extract the day names. The resulting 'dow' column in our dataset contained the day of the week for each recorded crime.
2. Defining Day Order:
To ensure that the days of the week were displayed in a logical order in our visualizations, we defined the 'day_order' list. This list specifies the order in which the days of the week should be arranged.
3. Creating a Countplot:
We used the Seaborn library to create a countplot, a type of bar plot, to visualize the distribution of crimes by day of the week. The 'x' parameter was set to "dow," representing the 'dow' column in our dataset, and the 'data' parameter was set to 'crime.'
4. Customizing Labels:
To enhance the clarity and readability of our plot, we customized the x-axis labels. We set the x-axis labels to be the day abbreviations, such as 'Mon' for Monday, 'Tue' for Tuesday, and so on. This step improved the compactness of the visualization and made it easier for the audience to interpret.
5. Final Visualization:
The resulting countplot provided a clear representation of the distribution of crimes across the days of the week. By ordering the days of the week according to our predefined 'day_order' list, we ensured that the plot displayed the days in a logical sequence, starting from Monday to Sunday.



4.7 Major policy changes on crime rates:


1. Data Preparation:
We began by loading two primary datasets. The first dataset, 'covid_data,' contains information about the COVID-19 pandemic, including the date and the number of reported cases. The second dataset, 'crime,' includes crime data with a 'Year' column indicating the year in which each crime was reported.
We then performed the following data preparation steps:
Converted the 'date' column in the 'covid_data' dataset into a datetime data type.
Extracted the 'Year' from the 'date' column to facilitate annual analysis.
Identified the last date of each year using the 'groupby' operation to ensure we had the most recent data for each year.
Selected and consolidated relevant columns ('Year,' 'date,' 'cases') in the 'covid_data' dataset.
Created a new dataset, 'policy,' that combined the COVID-19 cases and crime count based on the 'Year' column.
2. Data Visualization:
We visualized the results by creating a line plot that showcased the COVID-19 cases and crime count over the years. To provide better context and clarity, we used a dual-y-axis approach, displaying COVID-19 cases on the primary y-axis (blue) and the crime count on the secondary y-axis (red).
3. Interpretation:
The resulting plot reveals the trends and relationships between the two indicators over the years. We observed variations and potential correlations between the number of COVID-19 cases and crime rates. This information is crucial for evaluating the effects of major policy changes, such as lockdowns, social distancing measures, and economic impacts, on crime patterns.

This analysis can help inform policymakers and law enforcement agencies about the potential impact of public health measures on crime rates during critical times, such as the COVID-19 pandemic.


4.8 Demographic Factors:


1. Status of Crime by Area:
The first plot illustrates the distribution of crime status by area. It uses a countplot to showcase the counts of different crime statuses within various geographic regions. The 'Status' is categorized by color, and the 'Area' is displayed on the x-axis. The key observations include:
Understanding how different crime statuses (e.g., 'Invest Cont' and 'Adult Other') are distributed across different areas.
Identifying areas with higher instances of specific crime statuses.
2. Distribution of Crime Types by Gender:
The second countplot focuses on the distribution of crime types by gender. It aims to explore the gender distribution of individuals involved in different types of crimes. The 'Gender' is displayed on the x-axis, and the 'Count of Crimes' is on the y-axis. Key takeaways include:
Analyzing how different crime types (e.g., 'Robbery' and 'Burglary') are distributed among genders.
Identifying any gender-specific trends or patterns related to certain crime types.

3. Time Series Forecasting of Crime Trends:
The last plot demonstrates time series forecasting of crime trends over time. This analysis involves fitting a SARIMAX model to historical crime data and predicting future crime trends. Key components of this analysis include:
Splitting the data into training and testing sets.
Fitting a SARIMAX model to the training data, which considers seasonal patterns.
Forecasting future crime trends and obtaining predicted values.
Comparing the predicted values to the actual values to assess the accuracy of the forecast.

4.9 Patterns between Demographic Factors and Specific Type of Crimes:

1. Heatmap of Combined Crime Codes and Vict Sex:

The first analysis involves creating a heatmap that showcases the relationship between combined crime codes and victim gender. The heatmap is designed to provide insights into how different crime codes are distributed across genders. Key observations include:
Identification of patterns in crime occurrences based on both crime codes and victim genders.
Highlighting the areas where specific crimes may have a gender-related association.

2. Count of Victims by Weapon Category and Sex:

The second part of the analysis is a countplot that focuses on the distribution of victims based on weapon categories and gender. The plot aims to answer questions like the victims involved in incidents where weapons were used 

3. Weapon Category by Age Group:

In this analysis, a new column 'Age_Group' is created based on age categorization, dividing victims into 'Minors,' 'Adults,' and 'Senior Citizens.' A countplot is then used to visualize the relationship between weapon categories and age groups. The visualization helps answer questions like certain age groups more involved in incidents with weapon use
4. Top 10 Crime Types by Vict Sex:


The final analysis explores the top 10 crime types based on crime descriptions ('Crm Cd Desc') and their relationship with victim gender. A countplot is created to visualize the distribution of these top 10 crime types. Key takeaways include:
Understanding how gender differences may exist within specific crime types.
Identifying any patterns or disparities in the distribution of these crimes among genders.

5. ARIMA Model
![image](https://github.com/mansiraturi/CrimeDataEDA/assets/83804789/907f17da-039b-4aad-a5b4-732b42b23dc1)

![image](https://github.com/mansiraturi/CrimeDataEDA/assets/83804789/2dc42f23-7b90-4f85-887f-de01eed5dd4c)



In this code, we are performing a time series forecasting using an ARIMA (AutoRegressive Integrated Moving Average) model for crime data. 
The steps are as follows:

1. Data Preprocessing:
We start by converting the 'DATE OCC' column to a datetime data type and setting it as the index of the DataFrame.
The crime data is then resampled at a daily frequency ('D') and counted to get the number of crimes for each day. We fill any missing values with zeros.

2.Modeling:
We create an ARIMA model with an order of (5, 1, 0). This represents the autoregressive (AR) order, differencing (I) order, and moving average (MA) order for the time series data.

3. Fitting the Model:
The ARIMA model is fit to the resampled crime data.

4. Forecasting:
We perform a short-term forecast by calling the forecast method of the fitted model. In this code, we forecast the next 30 days of crime data.

5. Extended Forecast:
The code then extends the forecast to a longer period, in this case, for 6 months (approximately 21 business days).

6. Plotting:
Lastly, we create a time series plot to visualize the original crime data and the forecasted data for the extended 6-month period.




