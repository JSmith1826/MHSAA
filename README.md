# MHSAA Statistics Dashboard



## Tableau Public Link to dashboard
![New Software Test 1](images/readme_img/gif_grab_test_1.gif)
![Ice Hockey](images/readme_img/ice_hockey1.gif)


[Link To Full Tableau Public Visualization](https://public.tableau.com/app/profile/justin.smith2295/viz/MichiganHighSchoolSportsAtlas/Main_Dash)


## Table of Contents

* [Data Source and Collection](#data-sources)
    * [MHSAA Website](#michigan-high-school-athletics-administration-link-to-site)
    * [NCES](#nces-national-center-for-education-statistics)


## Data Sources:
### Michigan High School Athletics Administration
- [MHSAA Homepage](http://www.MHSAA.com)

#### Game Result Collection and Transformation
The [`Yearly_data_frame_creator_v2.ipynb`](Notebook/Yearly_data_frame_creator_v2.ipynb) notebook impliments the final evolution of the scraping strategy. In addition to scraping the game results for a set range of years and lists of sports. After scraping the notebook classifies every game a number of ways. [Regular season/post season, Home/Away, Close game/blowout]. 
- You can see earlier iterations of the result scraping and exploration code [below](#depreciated-notebooks--steps-along-the-way)

##### Data Extraction and Preprocessing:
- Extracts sports data by constructing URLs dynamically based on academic year start and end dates.
- Defines functions for game situation categorization, including home/away, regular season/postseason, blowout/close games, and more.
- Preprocesses the data by standardizing school names and handling missing values.
##### Data Aggregation and Export:
- Aggregates individual sport datasets across different years into a unified master_df DataFrame.
- Adds columns for sport codes and season years.
- Aggregates situational statistics (e.g., home vs. away games, blowout vs. close games) on a year-by-year basis.


#### Output
- Saves the final aggregated dataset as a CSV file that is the basis for the Tableau visualization.

![All Sports After Classification](images/readme_img/all_sport_output.gif)

#### Scrape and Clean School Information 

**Notebook: [`MHSAA_School_Info_scrape_workbook.ipynb`](Notebook/MHSAA_School_Info_scrape_workbook.ipynb)** creates a table of all schools represented in the MHSAA database. Each school in the MHSAA database is assigned a 4 digit code.This notebook iterates over a range of possible school ID numbers, finds valid ones and collects the information contained on the school info page for each entry.

- **Target - School Info Page:** Name, address, enrollment, nickname, colors, league and *MHSAA ID*
![School Info Example](images/readme_img/school_info.png)

- **Data Scraping**: Extracts school details from the MHSAA website by iterating over a range of school IDs. Each school's information is fetched via a JSON response, which includes fields like school name, address, enrollment numbers, and sports details.
- **Data Transformation**: The raw JSON data for each school is parsed and transformed into a pandas DataFrame
- **Efficiency**: Includes optimizations such as time delays between requests to manage server load and avoid being blocked by the website.

##### Output
- The output is a CSV file containing all collected school data. The wide net cast, manually checking every possible school ID number, returns a dataset that includes every  school name that has appeared in a result in any sport in any of the specified years. This is going to include schools from neighboring states, schools that are no longer open and a handful of Jr High Schools whose results are stored in the same database.

This data will need to be throughly cleaned and filtered later in the school matching notebook
![School Info Table](images/readme_img/school_info_gif.gif)






### National Center for Education Statistics (NCES)
Demographic information for the schools was collected from the National Center for Education Statistics [(homepage)](http://nces.ed.gov). Data for public schools was downloaded as a csv using the NCES' Public School Search [link](https://nces.ed.gov/ccd/schoolsearch/) for all schools in the state of Michigan. Data for private schools was extracted the same way from the Private School section of the same site [link](https://nces.ed.gov/surveys/pss/privateschoolsearch/)

Beacause the dataset incudes all schools in the state of all grade levels a substancial amount of cleaning and standarization is required before joining with data from the MHSAA website.

[`Public_Private_School_Info_book.ipynb`](Notebook/Public_Private_School_Info_book.ipynb) 
- **Data Manipulation**: Several data manipulation steps are carried out to prepare the data for analysis, including adding a column to distinguish between public and private schools.
- **Data Analysis**: The notebook contains multiple cells dedicated to exploring the data, with a focus on demographic statistics and school types.
- **Visualization**: Various plots are generated to visualize comparisons between public and private schools, providing insights into their respective demographic distributions.

#### Output
- Cleaned table of demographic data for Michigan Schools, filtered to only contain schools that offer interscolastic sports at the high school level.






### Depreciated Notebooks / Steps along the way


#### Scrape Sports Results - Initial score scraping approach

The [`extract_data_by_sport_workbook.ipynb`](Notebook/extract%20data%20by%20sport%20workbook.ipynb)
notebook is dedicated to scraping and storing data from the Michigan High School Athletic Association (MHSAA) website. It is designed to efficiently gather results of high school sports across Michigan by automating the data collection process for various sports and academic years.

**Target: - Scores Page** to collect all avaiable results for a single sport for a single year.

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
