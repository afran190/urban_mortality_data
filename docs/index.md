---
layout: default
---
![open data 2025](https://opensocialclusters.eu/wdev/wp-content/uploads/2020/04/external-content.duckduckgo.com_.png)

# analyzing_urban_mortality_data
Final project for Pratt Institute course [INFO-664](https://gofilipa.github.io/664/intro.html) that aims to analyze the causes of death across various U.S. cities by leveraging publicly available datasets accessed through open city data portals.

## Introduction

*Project Title:* Visible Deaths, Invisible Data: Mapping Mortality and its Gaps Across Cities

*Project Description:* This project aims to analyze the causes of death across various U.S. cities by leveraging publicly available datasets accessed through open city data portals. Many municipalities now provide access to their data via APIs, often powered by platforms like Socrata, enabling efficient, programmatic retrieval of mortality-related statistics.

 The research focuses on creating a comparative narrative instead of building a unified dataset by studying which causes of death different jurisdictions track and which remain unrecorded, or hidden, or inaccessible. Through utilizing open data APIs and data visualization tools, it will examine mortality patterns including overdose-related deaths, deaths in custody, and/or COVID-19 related deaths while exposing structural gaps in official records. Findings will focus equally on the missing data points as much as it does on the recorded information.

*Project Rationale:* Public knowledge and civic accountability depend heavily on government-mandated open data portals, which [NYC Open Data](https://opendata.cityofnewyork.us/) represents, as a fundamental resource. These systems demonstrate the policy-based priorities and exclusionary practices that exist within them. The New York City requirement of [Local Law 11](https://opendata.cityofnewyork.us/open-data-law/) demands public dataset publication, but Rikers Island along with other institutions remain in a state of inconsistent data disclosure. The process of making deaths visible in public discourse raises essential questions about transparency and oversight, and which deaths become visible to the public. The aim of this research is to investigate these tensions through the available data in municipalities across the country to analyze structural omissions and recordkeeping political dynamics in U.S cities.


## Key Research Questions:
 - What causes of death are publicly recorded in major city open data portals, and which categories (e.g., in-custody deaths, overdose deaths) are consistently missing or incomplete?
 - How does the availability and granularity of mortality data vary across cities, and what policies or legal mandates shape this availability?
 - In what ways do patterns of data omission correlate with social marginalization, such as incarceration, homelessness, or poverty?


## Methods and Workflows:
To carry out this analysis, the project used the following tools, technologies, and methodologis:

### Sources: 
- APIs provided by city open data portals (e.g., NYC, Chicago, San Francisco, and Austin) have been accessed using [`soda.py`](https://pypi.org/project/sodapy/), a Python library for the [Socrata Open Data API](https://dev.socrata.com/). This allowed for structured and automated data retrieval.
     - These cities were selected to represent different geographic regions of the United States and because they are generally regarded as progressive municipalities with strong commitments to transparency and civic data infrastructure. The assumption was that these cities would be more likely to publish comprehensive and well-maintained datasets.
     - While searching through each open data portal, a wide range of keyword variations had to be used across the three subject categories (incarceration-related deaths, COVID-19 deaths, and drug-related deaths), in order to surface any relevant records, where available.


 - **Data Collection**: I utilized the NYC_data.ipynb Jupyter Notebook I created as the template for related investigations into other U.S. cities. NYC was selected as the foundational case study because it is the only city that offered (at least partial) data across all three of the research categories. 

     - *Setting up Socrata*:
          - To access datasets through city portals using the Socrata platform, I first created a user account, which enables access across any open data site powered by Socrata. 
          - To avoid API rate limits, I also requested and configured an “App Token” for authenticated access—an example of which is provided later in this notebook. 
          - Finally, I installed the required Python library, sodapy, directly into my Jupyter notebook using the following command:
          `!pip install sodapy`

     - *Calling in APIs*:
          - Began with authenticatication via the Socrata Open Data API for each data set I called in. In total nine data sets across the 4 cities were retrieved, although some returned data that did not align with my research scope:
```python
from sodapy import Socrata
client = Socrata(
    "data.cityofnewyork.us",  # varies based on URL of each city 
    "YOUR_APP_TOKEN",         # Replaced with my personal app token
    username="your_email@example.com",
    password="your_password"
)
```
- Then I pulled each individual date set through the below identifiers:
          
```python
results = client.get("f64t-5yiv", limit=1000)  # changed each Data Set Identifier and limit based on each data set
results_df = pd.DataFrame.from_records(results)
```

 - **Data Cleaning**: Any format inconsistencies in the data will be managed using [OpenRefine](https://openrefine.org/), which excels at detecting and correcting anomalies in tabular datasets. This ensures accurate filtering and visualization.

 - **Data Analysis and Visualization**: Cleaned datasets will be analyzed using Python libraries such as [`pandas`](https://pandas.pydata.org/docs/) for data manipulation and [`plot.ly`](https://plotly.com/) for interactive visualizations. This will enable the exploration of trends and correlations across different variables and cities.

 - **Documentation of Absences**: When a city does not provide a dataset on a particular type of death (e.g., in-custody fatalities), this absence will be noted and visually flagged, building a broader picture of structural omission.

 ## Findings and Analysis:

 Insert plot.ly visualizations and answers to research questions here 

 ## Future Uses and Continuation of Research:
This project offers a foundation for multiple options of future research or expansion:

- **Comparative Policy Analysis**: Researchers can build on this work to study how data transparency laws differ across municipalities and how these differences affect public knowledge.

- **Watchdog Tools**: Journalists or advocacy organizations could use the codebase to monitor cities’ compliance with open data laws or track patterns of omission.

- **Public Interfaces**: With further development, the visualizations and findings could be adapted into a public-facing website or dashboard tracking absence of or lack of updates in municipal death records.


 ## Project Files:
  - *New York City Data Sets*
     - **NYC_Data.ipynb**: Python Notebook containing NYC Open Data APIs calling data sets of Inmate, COVID-19, Drug-related deaths; accompained by different plot.ly data visualizations unique to each data set 
     - **NYC_inmate_data_unclean.csv and NYC_covid_data_unclean.csv**: saved csv's with uncleaned data pulled from NYC Open Data
     - **NYC_inmate_data_uncleaned.csv, NYC_covid_data_clean.csv, NYC_drug_data.csv**: cleaned data post-OpenRefine transformations

- *San Francisco Data Sets*
     - **SF_Data.ipynb**: Python Notebook containing SF Open Data APIs calling data sets of COVID-19 and Drug-related deaths; accompained by different plot.ly data visualizations unique to each data set, *if applicable*. 
     - **SF_drug_data_unclean.csv and SF_covid_data_unclean.csv**: saved csv's with uncleaned data pulled from SF Open Data
     - **SF_drug_data_uncleaned.csv and SF_cvoid_data_clean.csv**: cleaned data post-OpenRefine transformations

- *Austin Data Sets*
     - **Austin_Data.ipynb**: Python Notebook containing Austin Open Data APIs calling data sets of Inmate and Drug-related deaths; accompained by different plot.ly data visualizations unique to each data set, *if applicable*. 
     - **Asutin_drug_data.csv: saved csv's with data pulled from Austin Open Data; no OpenRefine cleaning needed
   
- *Chicago Data Sets*
     - **Chicago_Data.ipynb**: Python Notebook containing Chicago Open Data APIs calling data sets of COVID-19 and Drug-related deaths; accompained by different plot.ly data visualizations unique to each data set, *if applicable*. 
     - **Chicago_covid_data_unclean.csv and Chicago_drug_data_none.csv**: saved csv's with uncleaned data pulled from Chicago Open Data
     - **Chicago_covid_data_clean.csv**: cleaned data post-OpenRefine transformations
     - **Chicago_covid_data_sums.csv**: trasnformed data from Chicago_covid_data_clean.csv dataset 
     - **Chicago_covid_data_sums_clean**: cleaned data post-OpenRefine transformations

- *City Data Availability Tracker*
     - **city_available_data_sets_tracker.csv**: A tracker I built to record which data and demographic details on inmate, COVID-19, and drug-related deaths are available, or missing, for each city. It includes special research notes highlighting anomalies and outdated datasets.
     - **city_data_tracker**: Python Notebook containing plot.ly visualization based on data pulled from city_available_data_sets_tracker.csv

