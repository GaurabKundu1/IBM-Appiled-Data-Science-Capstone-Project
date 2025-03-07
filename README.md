# Winning-Space-Race-With-Data-Science

 <img src="https://user-images.githubusercontent.com/86102231/147546030-15970711-052f-43f9-a398-00ee8cdbac40.gif" width="800" height="500">

## Author : [GAURAB KUNDU](https://www.linkedin.com/in/gaurab-kundu-020803) 

### This Project is the Applied Data Science Capstone Project of the IBM Data Science Professional Certificate

<p align='center'> 
<img src="https://user-images.githubusercontent.com/86102231/147832455-de717f12-9b1f-4aa9-ba1a-56df633d4458.png" width= "200" height= "200"> 
</p>

# Project Description

In this project, we will predict if the Falcon 9 first stage will land successfully. SpaceX advertises Falcon 9 rocket launches on its website, with a cost of 62 million dollars; other providers cost upward of 165 million dollars each, much of the savings is because SpaceX can reuse the first stage. Therefore if we can determine if the first stage will land, we can determine the cost of a launch. This information can be used if an alternate company wants to bid against SpaceX for a rocket launch.


# Outline 

|       SL. NO        |                                    Outline                                      |
| :-----------------: | :-----------------------------------------------------------------------------: |
|          1          |                              [Executive Summary](https://github.com/GaurabKundu1/Winning-Space-Race-With-Data-Science/blob/main/README.md#executive-summary)                                 |
|          2          |                                 [Introduction](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/README.md#introduction)                                    |
|          3          |                                   [Objective](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/README.md#objective)                                     |
|          4          |                       [Hardware and Software Requirments](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/README.md#hardware-and-software-requirments)                         |
|          5          |                                  [Methodology](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/README.md#methodology)                                    |
|          6          |                  [Insights Drawn from Exploratory Data Analysis](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/README.md#insights-drawn-from-exploratory-data-analysis)                  |
|          7          |                        [Launch Sites Proximities Analysis](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/README.md#launch-sites-proximities-analysis)                        |
|          8          |                       [Build A Dashboard with Plotly Dash](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/README.md#build-a-dashboard-with-plotly-dash)                        |
|          9          |                       [Predictive Analysis (Classification)](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/README.md#predictive-analysis-classification-1)                        |
|          10         |                                  [Conclusion](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/README.md#conclusion)                                     |


# Executive Summary

This project utilized various data collection methods, including web scraping and API calls, to analyze SpaceX launch data. Through Exploratory Data Analysis (EDA) and machine learning, the goal was to develop a classification model that predicts whether the Falcon 9 first stage will successfully land.

The results showed that decision trees were the best model for predicting the success of the landings.


# Introduction

In the era of commercial space travel, reducing costs is crucial. SpaceX advertises its Falcon 9 rocket launches at a fraction of the cost of other providers, largely due to the reuse of the first stage. By predicting the success of these landings, companies can optimize their bids and potentially compete with SpaceX.


# Objective

## Background
 The project analyzes SpaceX’s launch data to explore how reusable rockets minimize launch costs and how these insights can be applied by other companies.

## Problem
 The key problem is predicting the landing success of the Falcon 9 first stage based on specific flight features.
 
## Question for Analysis
 - Can we predict the success of the Falcon 9 first-stage landing?
 - What features influence the success of these landings?


# Hardware and Software Requirments

## Hardware
The project utilizes IBM Cloud Pack for Data, requiring only a stable internet connection.

## Software
- IBM Watson Studio

- For local execution:
  
  - Programming Language: Python
  - IDE: Jupyter Notebook
  - Libraries/Packages: Pandas, Numpy, Scipy, Scikit-learn, Matplotlib, BeautifulSoup


# Methodology

## Data Collection
The data set used in the project is the [SpaceX Launch data](https://drive.google.com/file/d/1JsDQrujo-qdQPMIdjkXmkzmN8xQIQRig/view?usp=sharing).

The data set contains information about different flights including date, launch site, booster version and more.

The data is collected by two main approaches:

1. The SpaceX API

2. Web Scrapping

### Data Collection – SpaceX API

We’ll be collecting launch data from SpaceX API, First we request launch data from SpaceX API using the GET command (requests.get), then we create a pandas dataframe from the response, After that we make several sub requests to get more detailed and consistent information about the IDs stored in the dataframe. 

With the help of some helper functions, we save the responses into a dictionary, and then we transform it into a dataframe, which is our data set.

 <img src= "https://user-images.githubusercontent.com/86102231/147389192-9446f2a8-80db-468a-afcf-1de89a327010.png" width="1000" height="500">
 
### To see the code and step by step process of Data Collection using SpaceX API [CLICK HERE](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/Week%201/Data%20Collection/jupyter-labs-spacex-data-collection-api.ipynb)

### Data Collection - Web Scrapping

We will be performing web scraping to collect Falcon 9 historical launch records from a Wikipedia page. First we perform an HTTP GET( using requests.get command)method to request the Falcon9 Launch HTMLpage, as an HTTP response. Then we create a BeautifulSoup object from the HTML response, We extract the column names from the object and use it
as dictionary keys.

We parse the HTML tables and fill the dictionary keys with launch records from table rows, and finally we transform it into a dataframe.

<img src= "https://user-images.githubusercontent.com/86102231/147544733-7e925792-5529-4667-8c49-2509f6d53313.png" width="1000" height="500">

### To see the code and step by step process of Data Collection with Web Scrapping [CLICK HERE](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/Week%201/Data%20Collection/webscrapping.ipynb)

## Data Wrangling

Exploratory data analysis is an important step while preprocessing data, it is useful to find some patterns in the data and determine what would be the label for training supervised models.

This process was done in the following order:

1. First thing to do is to identify the data types of the columns.

2. Determine the number of values for each attribute.

3. Calculate the percentage of the missing values.

4. To determine the label, weapply zero/one hot encoding to the “Outcome” column to classify landing to either 1(Success) of 0 (Failure)

### To see the code and step by step process of Data Wrangling [CLICK HERE](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/Week%201/Data%20Wrangling/labs-jupyter-spacex-Data%20wrangling.ipynb)

## EDA with SQL 

In order to better understand the datasets, we ran the following SQL queries:

1. Display the names of the unique launch sites in the space mission.

2. Display 5 records where launch sites begin with the string 'CCA'.

3. Display the total payload mass carried by boosters launched by NASA (CRS).

4. Display average payload mass carried by booster version F9 v1.1 .

5. List the date when the first successful landing outcome in ground pad was achieved.

6. List the names of the boosters which have success in drone ship and have payload mass greater than 4000 but less than 6000.

7. List the total number of successful and failure mission outcomes.

8. List the names of the booster versions which have carried the maximum payload mass. Use a subquery.

9. List the failed landing outcomes in drone ship, their booster versions, and launch site names for in year 2015.

10. Rank the count of landing outcomes (such as Failure (drone ship) or Success (ground pad)) between the date 2010-06-04 and 2017-03-20, in descending order.

### To see the code and step by step process of EDA With SQL [CLICK HERE](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/Week%202/Exploratory%20Analysis%20Using%20SQL/jupyter-labs-eda-sql-coursera.ipynb)

## EDA with Data Visualization

In order to understand the relations between different features, we visualize the data by plotting scatter plots, bar charts and line charts, it helps finding hidden patterns in data and gain insights about the dataset.

1. Pay load mass against the Flight number.

2. Lunch site against the Flight number.

3. Lunch site against the Pay load mass.

4. Orbit type against Class success rate.

5. Flight number against Orbit type.

6. Orbit type against the Pay load mass.

7. launch success yearly trend.

### To see the code and step by step process of EDA with Data Visualization [CLICK HERE](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/Week%202/Exploratory%20Analysis%20Using%20Pandas%20and%20Matplotlib/jupyter-labs-eda-dataviz.ipynb)

## Build an Interactive Map with Folium

Here, we complete the interactive visual analytics using Folium.

First we create Folium map object, with an initial center location around Nasa Johnson space center, Houston-Texas.

 We add a circle on the map for each launch site from the dataset by creating a folium circle and folium marker, now the launch sites are marked on the map which means we can see which one is proximate to the equator line or close to a coastline.

 In order to mark the success/failure launches, we create a marker on the map for each launch record from the dataset, a green marker indicates a successful lunching and a red one indicates failure,

we need to explore and analyze the proximities of launch sites, we calculate the distance between the launch site and its proximities and then we draw a polyline between them.

### To see the code and step by step process of Build an Interactive Map with Folium [CLICK HERE](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/Week%203/Interactive%20Visual%20Analytics%20and%20Dashboard/lab_jupyter_launch_site_location.ipynb)

## Predictive Analysis (Classification)

Now that we finished the exploratory analysis, the next step is to determine the training labels and build a predictor using machine learning algorithms. After using the ‘Class’ column as the label, first thing to do is normalizing the data. We split the normalized data into test/train sets, The training data is divided into validation data, a second set used for training data.

For the model development phase, we use the following algorithms:

1. Logistic regression

2. Support vector machine

3. Decision trees

4. K nearest neighbor

We build a grid search object for each of the algorithms and f i t it to find the best parameters of the model(hyper parameters tuning), then we choose the most accurate model.

### To see the code and step by step process of Predictive Analysis (Classification) [CLICK HERE](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/Week%204/Predictive%20Analysis%20(Classification)/SpaceX_Machine%20Learning%20Prediction_Part_5.ipynb)

## Results

Success rate increased noticeably from 2013 and on.

Launch site and the orbit type are the features with the largest effect on the outcome.

KNN and SVM models have a validation set accuracy of 83% and an out of sample accuracy of 77%.

# Insights Drawn from Exploratory Data Analysis

## Flight Number vs. Launch Site

Scatter plot of Flight Number vs. Launch Site

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147827883-ab56d138-5a96-45d0-b0ba-4eab13334e36.png)

Flight with number range 0 to 20 and range 40 to 90 are more on site CCAPS SLC 40.

Flight with number range 21 to 39 is more on site KSC LC 39A.

## Payload vs. Launch Site

Scatter plot of Payload vs. Launch Site

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828033-ba762df8-2e09-4490-8d46-3e890bb277e9.png)

More data spread on payloas mass range 0 to 8000 kg.

When the payload is in the range of 15000, it looks more likely to land successfully.

## Success Rate vs. Orbit Type

Show a bar chart for the success rate of each orbit type

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828184-62cf26f3-d5fb-4138-88f9-c907e4ca34f8.png)

O rbit type ES L1, GEO, HEO, and SSO have the highest success rate, which is 1, that means it always succeeds.

Orbit type GTO have the lowest success rate, which is 0.5.

## Flight Number vs. Orbit Type

Show a scatter point of Flight number vs. Orbit type

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828246-c2db80ad-bb4d-4a29-9b76-4ec873bbc27e.png)

Orbit type LEO, ISS, PO, and GTO have more data spread on flight number range 0 to 60 .

## Payload vs. Orbit Type

Show a scatter point of payload vs. orbit type

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828392-82371725-d023-47a2-86a8-54f2a95d1f99.png)

Orbit type VLEO that has high success rate also has heavy payload.

There is a possibility that the heavier the payload, the higher the probability of success.

## Launch Success Yearly Trend

Show a line chart of yearly average success rate

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828424-7d048f28-dc00-4a83-8d66-cd910a1dfe44.png)

2019 is the year that has the highest success rate.

2010, 2012, and 2014 are the year that have lowest success rate.

## All Launch Site Names

N ames of the unique launch sites

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828488-a2a97304-f1a2-497f-b1e0-15eb63da4442.png)

There is 4 unique launch site.

That’s mean there is 4 kind of launch site too.

## Launch Site Names Begin with 'CCA'

5 records where launch sites with 'CCA'

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828523-6ed380cc-bc9b-4bf3-b4c5-71756a9c59b7.png)

There is 5 launch site begin with CCA which mission outcome all success.

There is 4 launch site that sponsored by NASA.

## Total Payload Mass

Calculate the total payload carried by boosters from NASA

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828560-860af98b-a3f0-4869-9f8b-4241f21fec88.png)

The total payload carried by booster from NASA is 45.596 kg.

## Average Payload Mass by F9 v1.1

Calculate the average payload mass carried by booster version F9 v1.1

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828627-f9e7b159-bfa9-4e6f-a274-47ffe3e5ef33.png)

The average payload mass shown is 2.928 kg for 90 payload mass withtotal payload is 45.596 kg.

## First Successful Ground Landing Date

Find the dates of the first successful landing outcome on ground pad

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828696-d3341d15-a7c6-4898-b78a-36e02fa53b80.png)

T he first successful landing outcome on ground ad at 2015 12 22 .

## Successful Drone Ship Landing with Payload between 4000 and 6000

List the names of boosters which have successfully landed on drone ship and had payload mass greater than 4000 but less than 6000

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828733-fd4a280c-cfde-48c6-8dac-f81d847966d7.png)

There is 4 booster version that successfully landed on drone ship and had payload range 4000 to 6000.

## Total Number of Successful and Failure Mission Outcomes

Calculate the total number of successful and failure mission outcomes

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828804-5bf8c641-c1c9-4223-865d-7e44b87dd878.png)

The total of successful mission outcome is 100 and failure in flight is 1.

## Boosters Carried Maximum Payload

List the names of the booster which have carried the maximum payload mass

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828862-54033de7-3fc1-4100-92e5-9915638e929f.png)

There is 12 booster version type that carried maximum payload mass.

## 2015 Launch Records

List the failed landing_outcomes in drone ship, their booster versions, and launch site names for in year 2015

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828896-060b86df-093c-4871-bd59-238582a946d9.png)

The failed landing outcomes in drone ship is always happen in CCAFS LC 40 launch site.

There are 2 type of booster that used when failed landing outcomes in drone ship.

## Rank Landing Outcomes Between 2010-06-04 and 2017-03-20

Rank the count of landing outcomes (such as Failure (drone ship) or Success (ground pad)) between the date 2010 06 04 and 2017 03 20, in descending order

![Screenshot (189)](https://user-images.githubusercontent.com/86102231/147828931-f33f5e08-4f57-489d-b501-d932055e2568.png)

There are 9 landing outcomes that success ground pad and 5 landing outcomes that failure drone ship.

# Launch Sites Proximities Analysis

## Launch sites Marking

The markers on this maps show the launch site locations on the map.

![Screenshot (192)](https://user-images.githubusercontent.com/86102231/147829818-e184c01c-959d-4214-9cea-af5c476f6bc5.png)

## Mark the success/failed launches for each site on the map

A green marker represents a successful landing outcome, while a red one represents failure.

![Screenshot (193)](https://user-images.githubusercontent.com/86102231/147829822-4ee6b005-44f1-49ad-bbc9-561c76ce8f20.png)

## Distances between a launch site to its proximities

The blue line represents the distance between the lunch site and the closest coastline.

![Screenshot (194)](https://user-images.githubusercontent.com/86102231/147829825-349daf2a-e65c-4cfd-b3c1-e4afaf356399.png)

# Build A Dashboard with Plotly Dash

### To See the code for making the Dashboard using Plotly Dash [CLICK HERE](https://github.com/GaurabKundu1/IBM-Data-Science-Professional-Certificate-Capstone-Project-Winning-Space-Race-With-Data-Science/blob/main/Week%204/SpaceX_plotly.py) 

## Launch Success Dashboard for All Sites

Showing the screenshot of launch success count for all sites, in a Piechart.

![Screenshot (199)](https://user-images.githubusercontent.com/86102231/147830906-4bed284d-465b-4ec9-8ecd-68863f366dfa.png)

Showing the screenshot of option

![Screenshot (200)](https://user-images.githubusercontent.com/86102231/147830910-feea489d-fe67-43de-a07b-f0a0de5978f6.png)

## Piechart for The Highest Launch Success Site

Showing the screenshot of the piechart for the launch site with highest launch success ratio.

![Screenshot (201)](https://user-images.githubusercontent.com/86102231/147830912-abd00634-0e15-4399-ac8b-2a16d976df7a.png)

The highest total launches is KSC LC-39A site with 41.7%.

## Payload Vs Launch Outcome

### For 0 kg payload

![Screenshot (202)](https://user-images.githubusercontent.com/86102231/147830916-c1e33518-146a-4d00-a58a-8421937be995.png)

### For 2500 kg payload

![Screenshot (203)](https://user-images.githubusercontent.com/86102231/147830919-1f80a8cb-c419-45b1-b764-aebe9a066fb0.png)

### For 5000 kg payload

![Screenshot (204)](https://user-images.githubusercontent.com/86102231/147830921-1f11f6c6-6559-44ee-bc5b-0b2e2fb75477.png)

### For 7500 kg payload

![Screenshot (205)](https://user-images.githubusercontent.com/86102231/147830924-ae2cdcec-6d1d-4a9c-ab99-9450dbe48ea5.png)

# Predictive Analysis (Classification)

## Classification Accuracy

![Screenshot (201)](https://user-images.githubusercontent.com/86102231/147831308-07dbb446-e71c-4902-b7dd-648a4912cf9e.png)

## Confusion Matrix

These two graphs represent the confusion matrix for both the SVM and KNNmodels.

![Screenshot (202)](https://user-images.githubusercontent.com/86102231/147831309-0725ba69-130d-4685-9f0c-5ecc0dd2fa62.png)

These confusion matrices show the largest true positive and true negative values, as well as the least false positive and false negative values.

# Conclusion

Not all the data is important, the collected data may contain irrelevant columns and it is normal to drop them.
Visualizing data is a good way of determining what features have the strongest effect.
SQL queries provide wider scope to explore datasets in comparison with traditional EDA.
SVM and KNN models are the most reliable since they have the highest out of sample accuracy and f1-score.
