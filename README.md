# data-512-project
The study, "Understanding the Impact of Wildfires on Yakima, Washington," investigates the increasing frequency and intensity of wildfires in the western U.S., particularly in Yakima County. Recognizing the significant impact of these wildfires, fueled by climate change and land management practices, on public health, environmental quality, this comprehensive analysis aims to understand the full range of effects caused by wildfire smoke. It focuses on air quality deterioration and health impacts offering insights to help formulate mitigation and management strategies. The research provides valuable information for policymakers and community leaders, aiming to guide effective responses and planning, and enhance the resilience and preparedness of the Yakima community against future wildfire threats.


## Source Data
Combined wildland fire datasets for the United States and certain territories, 1800s-Present (combined wildland fire polygons) https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81

Wildfire Cities Assignment https://docs.google.com/spreadsheets/d/1cmTW5fgU3KyH6JbrRao-qWjzu2GovKk_BkA7a-poGFw/edit#gid=1247370552

US EPA API - Air Quality IndexDataset: https://aqs.epa.gov/aqsweb/documents/data_api.html

Asthma Data for 10th graders https://datacenter.aecf.org/data/tables/5072-percentage-of-tenth-graders-with-asthma?loc=49&loct=5#detailed/5/6947-6985/false/37,870,869,868,133,35,17/any/11494

## Description of Data

## Dataset Descriptions

### USGS_Wildland_Fire_Combined_Dataset.json
Note: Original wildfire data file, too big to be uploaded to Github.

| Feature            | Description                                |
|--------------------|--------------------------------------------|
| Fire_Year          | The year in which the wildfire occurred    |
| GIS_Acres          | Area of land burnt (in 10^7 acres)         |
| Assigned_Fire_Type | Type of wildfire (e.g., wildfire, prescribed fire) |

### aqi.csv
Note: File generated from calling AQS API.

| Feature | Description                                  |
|---------|----------------------------------------------|
| Year    | All years for which AQIs are available       |
| avg_aqi | Average yearly AQI values around Yakima     |

### smoke_estimate_yakima.json
Note: File generated after generating smoke estimates, too big to be uploaded to Github.

| Feature        | Description                                  |
|----------------|----------------------------------------------|
| Fire_Year      | The year in which the wildfire occurred      |
| distance       | Distance of fire from North Platte           |
| smoke_estimate | Computed impact of smoke in Yakima County    |

### Additional Data Columns

| Column Name   | Description                                  |
|---------------|----------------------------------------------|
| LocationType  | Type of geographical location                |
| Location      | Specific location within Washington          |
| TimeFrame     | Year                                         |
| DataFormat    | Here the format is percentage                |
| Data          | Prevalence percentage of Asthma in 10th graders |


# Methodology and Coding Process
In my project, I first tackle a large 2.8GB dataset from USGS about wildfires, focusing on events since 1963 near Yakima, WA, and creating a detailed smoke impact assessment. This part of the work produces a big file, smoke_estimate_yakima.json, which is too large for Github.

Next, I acquire Air Quality Index (AQI) data by using an EPA API key to fetch historical air quality records. Since Yakima lacks local weather stations, I have to cast a wider net, searching up to 250 miles away to find relevant data. This effort results in a comprehensive aqi.csv file covering the years 1985-2022.

Lastly, I analyze the wildfire data and AQI, visualizing the findings and predicting future smoke levels with a forecast extending 25 years, thanks to the Prophet forecasting tool. All these steps are detailed in a separate Reflections document.


