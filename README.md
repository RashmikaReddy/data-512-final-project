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


# Methodology

The project was methodically segmented into clear steps for ease of understanding and execution.

## Step 1: Wildfire Data Sourcing
- **Data Source**: 'USGS_Wildland_Fire_Combined_Dataset.json' from the US Geological Survey.
- **Dataset Size**: 2.8GB.
- **Parsing Method**: Used GeoJSON reader libraries.
- **Focus**: Fires post-1963 within a 1250-mile radius of Yakima, WA.
- **Calculation**: Smoke Estimate = (AreaBurnt*FireIntensity)/DistanceFromCity.
  - Factors in fire's distance, area burned, and intensity.
  - Different fire types are weighted according to their intensity.

## Step 2: Air Quality Index (AQI) Retrieval
- **Data Source**: US AQS database accessed through a generated API key.
- **Data Range**: Historical AQI data from 1985 to 2022.
- **Methodology**: Created a spatial bounding box up to 250 miles from Yakima, encompassing data from multiple stations. 
- **Data Processing**: Yearly data collection involved averaging out AQI values.

## Step 3: Impact Analysis of Wildfire Data
- **Data Used**: Collected smoke estimate data.
- **Analysis Tools**: Visualizations such as histograms and time series graphs.
- **Focus**: Examined the spread and impact of wildfires in the vicinity of Yakima and the correlation of smoke estimates against AQI.

## Step 4: Project Extension for Public Health Insights
- **Data Source**: Children's Alliance Provider dataset on asthma prevalence among tenth graders.
- **Objective**: To understand the health impacts of smoke on local adolescents.
- **Analysis Focus**: Offers a longitudinal view of health trends in the backdrop of environmental changes.

## Step 5: Analysis of Asthma Rates with Smoke
- **Data Integration**: Merged asthma data with previously calculated Smoke Estimate Data.
- **Renaming for Clarity**: Renamed 'es_aqi' to 'smoke_estimate'.
- **Analysis Method**: Performed correlation analysis using Pearson's correlation coefficient between Smoke Estimate and asthma_rate.
- **Key Analysis**: Asthma Rate Trends Over Time with Smoke Estimate.
  - Compared historical and predicted AQI values.


