# MHSAA Statistics Project

## Table of Contents

* [Data Source and Collection](#data-sources)


## Tableau Public Link to dashboard

https://public.tableau.com/app/profile/justin.smith2295/viz/MichiganHighSchoolSportsAtlas/Main_Dash

## Data Sources:
### Michigan High School Athletics Administration [Link to Site](http://www.MHSAA.com)

### Scraping Code: 
#### Scrape and Clean School Information 
- **Target - School Info Page:** Name, address, enrollment, nickname, colors, league and *MHSAA ID*
![School Info Example](images/readme_img/school_info.png)

**MHSAA_School_Info_scrape_workbook.ipynb [Link](Notebook/MHSAA_School_Info_scrape_workbook.ipynb)**
- **Data Scraping**: Extracts school details from the MHSAA website by iterating over a range of school IDs. Each school's information is fetched via a JSON response, which includes fields like school name, address, enrollment numbers, and sports details.
- **Data Transformation**: The raw JSON data for each school is parsed and transformed into a structured pandas DataFrame, making it easier to handle and analyze.
- **Efficiency**: Includes optimizations such as time delays between requests to manage server load and avoid being blocked by the website.

##### Output
- The output is a CSV file containing all collected school data, ready for further analysis or integration into other datasets.
- ![School Info Table](images/readme_img/school_info_gif.gif)




#### Scrape Sports Results (extract_data_by_sport_workbook.ipynb) [Link](Notebook/extract%20data%20by%20sport%20workbook.ipynb)
This notebook is dedicated to scraping and storing data from the Michigan High School Athletic Association (MHSAA) website. It is designed to efficiently gather results of high school sports across Michigan by automating the data collection process for various sports and academic years.

**Target: - Scores Page** to collect all avaiable results for a single sport for a single
![Single Sport Score Page Example](images/readme_img/scores_page.gif)


##### Features
- **Data Scraping**: The notebook uses Python requests to pull data for entire sports seasons from the MHSAA website. Each game's data is initially captured in a single row format.
- **Data Transformation**: Converts the season-wide data into aggregated statistics for home and away teams. This transformation mimics the format used in older scraping methods where each game had separate rows for home and away perspectives.
- **Dependencies**: Utilizes libraries such as pandas, numpy, and requests for data manipulation and HTTP requests.
- **URL Handling**: Constructs URLs dynamically to fetch data based on specific dates and sports categories.

##### Output: 
- Data can be stored in one of two ways
    - **Text files** containing raw JSON data.
    - **Pandas DataFrames / CSV files** containing structured results, ready for analysis and visualization in subsequent notebooks.
    - **Example:**
    ![2023 Baseball Table](images/readme_img/results_table.png)



### NCES National Center for Education Statistics
Data 
