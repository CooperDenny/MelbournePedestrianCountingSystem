# MelbournePedestrianCountingSystem

This repository contains the code and data used for collecting and transforming pedestrian data from the City of Melbourne's Pedestrian Counting System, spanning from January 2010 to October 2024. The dataset is obtained via dynamically constructed URLs that link to monthly CSV files containing pedestrian counts recorded by sensors located throughout the city. The data is cleaned and aggregated into a single DataFrame for analysis.

Key processing steps include downloading and cleaning the data, checking for missing dates, and transforming the data into a long format for easier analysis of pedestrian counts per sensor. The project also incorporates geolocation data, mapping each sensor to its corresponding latitude and longitude coordinates for enhanced spatial analysis.

The resulting dataset can be used to analyze pedestrian movement trends across Melbourne over time. I have personally used the dataset to construct an interactive Power BI dashboard that showcases advanced data visualization and analysis techniques to provide insights into pedestrian traffic trends.

[View the Power BI Dashboard](https://cooperdenny.github.io/projects/melbourne-pedestrian-counting.html)