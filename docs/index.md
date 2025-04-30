---
layout: default
---
![open data 2025](./docs/Open-DataWeek-2025-Logo-4-1024x513.webp)

# analyzing_urban_mortality_data
Final project for Pratt Institute course [INFO-664](https://gofilipa.github.io/664/intro.html) that aims to analyze the causes of death across various U.S. cities by leveraging publicly available datasets accessed through open city data portals.

## Introduction

*Project Title:* Analyzing Urban Mortality Data Through Open City APIs

*Project Description:* This project aims to analyze the causes of death across various U.S. cities by leveraging publicly available datasets accessed through open city data portals. Many municipalities now provide access to their data via APIs, often powered by platforms like Socrata, enabling efficient, programmatic retrieval of mortality-related statistics.

While a significant portion of recent mortality data centers around COVID-19, this project also aims to try to focus toward other impactful, but less-publicized causes of death (if data is available). These can possibly include drug overdoses and fatalities among incarcerated individuals, with an interest in understanding how these figures may reflect or be influenced by local governance, healthcare policy, and criminal justice systems. Where available, international datasets may also be integrated for broader comparative analysis.

*Project Rationale:* I am aiming to go beyond the surface-level data on mortality by exploring underlying causes that reflect societal issues such as substance abuse, public health policy, and industrial prison complex. Through comparative analysis and data visualization, the findings aim to spark discussion around local and national policy interventions, and promote a data-informed approach to improving public health outcomes.

## Key research questions may include *(dependent on available data)*:
 - How do drug-related deaths vary between major urban areas, and how might these trends align with local public health initiatives or policy decisions?
 - Are there identifiable disparities in mortality rates among incarcerated populations across different jurisdictions?
 - Based on COVID-19 city-level infection / mortality data, can this reveal deeper socio-economic or policy-driven disparities that warrant public policy reconsideration?

## Methods and Workflows:
To carry out this analysis, the project will use the following tools and technologies:

 - **Data Collection**: APIs provided by city open data portals will be accessed using [`soda.py`](https://pypi.org/project/sodapy/), a Python library for the [Socrata Open Data API](https://dev.socrata.com/). This will allow for structured and automated data retrieval.
 - **Data Cleaning**: Any inconsistencies or gaps in the data will be managed using [OpenRefine](https://openrefine.org/), which excels at detecting and correcting anomalies in tabular datasets.
 - **Data Analysis and Visualization**: Cleaned datasets will be analyzed using Python libraries such as [`pandas`](https://pandas.pydata.org/docs/) for data manipulation and [`plot.ly`](https://plotly.com/) for interactive visualizations. This will enable the exploration of trends and correlations across different variables and cities.