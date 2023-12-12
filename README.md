# Data512-Final-Project

# Project Goal
The goal of this study is to present a thorough understanding of the potential effects of wildfires and climate change on visitor experiences and recreation habits. I aim to discover adaptation techniques and policy recommendations by exploring the implicit benefits of outdoor recreation, which include gains in well-being, as well as the explicit benefits, which include monetary revenue. These insights will be critical to maintaining Lewiston's outdoor recreation industry's sustainability and strengthening the community's ability to withstand environmental setbacks. This investigation, conducted in cooperation with local communities, government agencies, and researchers, aims to produce useful data that will protect Lewiston's identity as a popular travel destination and maintain the core of its outdoor experiences for future generations. 

# Data Acquistion and API Documentation

## Data Acquistion
The section below details the steps for data acquistion. We have:

### Phase I
1. A geojson [file](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81) dataset collected and aggregated by the US Geological Survey. This contains fire polygons for wildfires that have occurred across the USA. 
2. An [API](https://aqs.epa.gov/aqsweb/documents/data_api.html) which returns a response to obtain the Air Quality Estimates for regions in the USA.
3. A [spreadsheet](https://docs.google.com/spreadsheets/d/1cmTW5fgU3KyH6JbrRao-qWjzu2GovKk_BkA7a-poGFw/edit?usp=drive_link) listing the assignments of people to different cities.

### Phase II 
1. **Bureau of Transportation - Airline On-Time Statistics and Delay Causes**
   - **License:** CC-BY
   - DOT strongly encourages researchers to deposit data under the Creative Commons CC-BY Attribution or an equivalent license, whenever possible.
   - The CC-BY license allows others to distribute, remix, tweak, and build upon the work, even commercially, as long as they credit the original creator.
   - **Relevant Columns:**
     - year: the year in which the flight arrived
     - month: the month in which the flight arrived (values range from 1-12)
     - carrier_name: the name of the airline carrier of the flight that arrived at the airport
     - airport: abbreviation of the airport name that the flight arrived at
     - airport_name: full name of the airport that the flight arrived at
     - arr_flights: the total number of flights that arrived at this airport for the specified month and carrier
   - *Note:* There are 15 more columns in this dataset that specify delay causes and the number of minutes of delay. However, since this information is out of the scope and relevance of this study, it will not be used.

2. **Idaho Park Visitation and Recreation Statistics - Visitation Statistics**
   - **License:** Custom 
   - The Idaho Department of Parks and Recreation assumes no liability for any loss that may result from the use of this data. The Idaho Department of Parks and Recreation, as a general rule, may modify or delete any of the information that is included in this data without advance notice. The Idaho Department of Parks and Recreation may also interrupt or halt access to this data when deemed necessary. The Idaho Department of Parks and Recreation shall assume no liability for any damages resulting from modification or deletion of this dataset or interruption or halting access to this data.
   - **Columns:**
     - year: the year to match with the visitation number
     - visitation: the visitation number for that year for Idaho state parks 

3. **U.S. Bureau of Labor Statistics - Employment Data for the Leisure/Hospitality Industry (1990 - 2023)**
   - **License:** Custom
   - The Bureau of Labor Statistics (BLS) is a Federal government agency and everything that we publish, both in hard copy and electronically, is in the public domain, except for previously copyrighted photographs and illustrations. You are free to use our public domain material without specific permission, although we do ask that you cite the Bureau of Labor Statistics as the source.
   - **Columns:**
     - Year: the year for which employment numbers are counted
     - January: employment numbers for the month of January for each year
     - February: employment numbers for the month of February for each year
     - March: employment numbers for the month of March for each year
     - April: employment numbers for the month of April for each year
     - May: employment numbers for the month of May for each year
     - June: employment numbers for the month of June for each year
     - July: employment numbers for the month of July for each year
     - August: employment numbers for the month of August for each year
     - September: employment numbers for the month of September for each year
     - October: employment numbers for the month of October for each year
     - November: employment numbers for the month of November for each year
     - December: employment numbers for the month of December for each year


# Platform
This project was run on jupyter notebook on localhost. 

# Steps to Reproduce these Results
Data Acquistion, Data Preparation, and Data Analysis are key phases within this project:

* Step 1: Obtaining the Smoke Estimate through the Wildfire Data 
  - All the cells of the notebook - wildfire_data_analysis.ipynb, can be run to obtain the smoke estimate and visualizations from Phase I of the analysis. More information about how to run these cells and the respective data sources this uses can be found in this [repository](https://github.com/mshash8/data-512-project/tree/main).
* Step 2: Data Acquisition for Phase II of Analysis
  - The data for the second phase of analysis is obtained through three data sources mentioned above. This data needs to be downloaded to carry out further analysis.
* Step 4: Data Preprocessing
  - Once the data is acquired for analysis, it needs to be preprocessed into pandas dataframes to conduct further analysis.
* Step 5: Modeling and Correlations
  - With the data preprocessed, the research study to identify correlations between the tourism industry and the smoke estimate can be further studied by calculating correlations and modeling coefficients.
* Step 5: Visualization and Analysis
  - Visualizations and Analysis are done to ensure that the results and findings of the study are communicated effectively to the audience. 
    
# Limitations
* The lack of tourism industry and outdoor recreation data hinders the ability to make stronger claims and generalize results.
* The data provided by Idaho Parks and Recreation includes cumulative data for parks in Idaho and the analysis of such data may not directly apply solely to Lewiston.
* The collected data covers only shorter periods, failing to span a significant number of years as intended for this project.
* I attempted a Linear Regression analysis with normalized variables, acknowledging that the assumptions made by linear regression models might have been too stringent for this analysis. Given my beginner-level approach to statistical analysis, I am uncertain whether the assumptions of linear regression are fully satisfied, and I cannot confirm the presence of a linear association between the predictor and response variables. Nevertheless, I undertook this modeling effort as a foundational step in statistical analysis.
* The wildfire dataset provided by the USGS does not include data for the years 2021, 2022, and 2023 within a distance of 1250 miles from Lewiston, Idaho.
* In the AQI API, there is no information available for gaseous matter at stations near Lewiston, Idaho, even within the bounding box.
* There is no station directly in Lewiston, Idaho, in the AQI API, and the stations within the bounding boxes also provide information for a limited period, specifically from 1986 to 2023.
* The smoke estimate values range from 3.084128e-10 to 1.435315e+02. Most values are extremely small because many fires burn very small areas located at a significant distance from the city of interest. This potentially lowers the average smoke_estimate, despite the possibility of poor air quality.



# Documentation
This project adheres to recommended best practices for replication and documentation:

Jupyter Notebook: detailed comments for data acquistion, processing, and analysis.

README File: Offers a general overview of the project, outlining its objectives, data sources, data processing procedures, and standards for reproducibility.

LICENSE File: Contains the MIT LICENSE for the project's code, ensuring it is freely usable and the [Creative Commons License](https://creativecommons.org/licenses/by/4.0/). 

# Special Considerations
* The GeoJSON dataset from USGS is extensive, containing approximately 136,000 fire occurrences that require thorough analysis. Although loading this data was made more straightforward with the Reader written by Dr. David W. McDonald, filtering the data required parsing through these rows to include only those fire occurrences falling within the scope of this assignment, which consumed a significant amount of time.

* Extensive error handling was also necessary, as not all fields were present in every data row. For instance, the 'rings' parameter needed to be verified and handled accordingly.

* It is also important to note that data is available for all years except for 2021, 2022, and 2023 for the analysis.

* The AQI data presents its own set of challenges. For instance, in the city of study, Lewiston, Idaho, there are no stations within the city or within a 25-mile radius of it. The closest station is located 50 miles from the city. Additionally, there is no data available for all the years in a single station. Data from multiple station responses must be appended.

* Due to variations in the years of operation for different weather stations, data consolidation is necessary across two distinct stations.

* Furthermore, the response from the EPA API does not always contain the 'aqi' parameter, requiring exception handling. In my city locations, there was also an absence of data for gaseous pollutants, with only particulate pollutants available. This specific scenario also calls for separate handling.

# License
This project is open-source and follows the MIT License. You are free to use and modify the code according to the terms of the MIT License. This code examples used in the notebooks were developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons License](https://creativecommons.org/licenses/by/4.0/). Revision 1.1 - September 5, 2023

# Scripts 
1. **Path:** Scripts/wildfire_data_analysis.ipynb - This file contains the data acquistion, preparation and analysis of the wildfire data from USGS.
2. **Path:** Scripts/aqi_data_acquistion.ipynb - This file contains the data acquistion and API call for the AQI data. This creates an output json of AQI for each year which is read back into the notebook above to create visualizations.
3. **Path:** Scripts/recreation_lewiston.ipynb - This file contains the data acquistion, preparation and analysis for phase II of this analysis - quantifying the impact of wildfire smoke on the tourism industry in Lewiston.

# Data Files 

1. **Path:** Data/predicted_values.json - This file contains the predictions of smoke in Lewiston, Idaho for the years 2024-2049.

  * year (int) : predicted_smoke_estimate (int)
  * The year field is the year that the smoke_estimate prediction is for
  * The predicted_smoke_estimate is the smoke_estimate for that particular year as predicted by the model

2. **Path:** Data/aqi_lewiston.json - This file contains the AQI estimates near Lewiston, Idaho for the years 1986-2023.

  * year (int) : aqi_estimate (int)
  * The year field is the year for each aqi estimate
  * The aqi_estimate is the aqi as returned by the API exposed by the EPA
    
3. **Path:** extension_plan/Airline_Delay_Cause.csv - This dataset is published by the Bureau of Transportation and contains information about flights that are delayed versus those that are on time. For the purpose of this analysis, I am concerned with the total number of flights arriving at the Lewiston airport and not particularly with delay statistics and causes. Therefore, this dataset can be used for that purpose.
4. **Path:** extension_plan/leisure_bls.csv - This dataset is published by the US Bureau of Labor Statistics. It records employment numbers (in thousands) for each month from 1990 to 2023.
5. **Path:** extension_plan/visitation.csv - This dataset is published by the Department of Parks and Recreation of Idaho. The data resides in a small section of the link posted above under the heading: Visitation Statistics. It counts the number of visitation totals representing combined usage between day-use and overnight camping for state parks in Idaho.

# Helpful Links
1. [Metadata for Wilfire Polygon Data](https://www.sciencebase.gov/catalog/file/get/61aa537dd34eb622f699df81?f=__disk__d0%2F63%2F53%2Fd063532049be8e1bc83d1d3047b4df1a5cb56f15&transform=1&allowOpen=true)

2. [Documentation for the the US Environmental Protection Agency (EPA) Air Quality Service (AQS) API](https://aqs.epa.gov/aqsweb/documents/data_api.html)

3. [Statsmodels AutoReg Documentation](https://www.statsmodels.org/stable/generated/statsmodels.tsa.ar_model.AutoReg.html)

4. [Wildfire Data Reader Python Module](https://drive.google.com/file/d/1TwCkvdaw0MxJzW7NSDg6XxYQ0dvaS44I/view)

5. [Python Notebook for geodetic distance computation](https://drive.google.com/file/d/1qNI6hji8CvDeBsnLDAhJXvaqf2gcg8UV/view)

6. [Python Notebook to call EPI Air Quality History Data](https://drive.google.com/file/d/1bxl9qrb_52RocKNGfbZ5znHVqFDMkUzf/view?usp=sharing)

# References
1. Alexander Maas and Katherine Himes (2021). [Idaho Climate-Economy Impacts Assessment Recreation and Tourism Report](https://www.uidaho.edu/-/media/UIdaho-Responsive/Files/president/direct-reports/mcclure-center/iceia/iceia-recreation-tourism-report-2021.pdf?la=en&hash=205BCA5F5D9EB63DD8F0F0C7555ACF7D8C0FB8EB).
2. E. M. White, S. G. Winder, S. A. Wood (2023). [Applying novel visitation models using diverse social media to understand recreation change after wildfire and site closure](https://www.tandfonline.com/doi/full/10.1080/08941920.2022.2134531). https://www.tandfonline.com/doi/full/10.1080/08941920.2022.2134531.

# Research Implications
The objective of this study is to quantify and analyze the impact of wildfire smoke on the tourism industry in Lewiston. I used three data sources that I think could best capture the tourism industry and outdoor recreation in Lewiston - visitation data to parks, flight activity data at the Lewiston airport and Leisure industry employment. My hypotheses were to understand the correlation and association between these three aforementioned variables and wildfire smoke. 






