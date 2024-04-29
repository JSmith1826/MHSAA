# MHSAA Statistics Project

## Table of Contents

* [Data Source and Collection](#data-sources)


## Tableau Public Link to dashboard

https://public.tableau.com/app/profile/justin.smith2295/viz/MichiganHighSchoolSportsAtlas/Main_Dash

## Data Sources:
### Michigan High School Athletics Administration [Link](http://www.MHSAA.com)
- Data available from the Official MHSAA Website:
School Info: Name, address, enrollment, nickname, colors, league and *MHSAA ID*
![School Info Example](images/readme_img/school_info.png)

- Use The Search for Scores page to collect all avaiable results for a single sport for a single
![Single Sport Score Page Example](images/readme_img/scores_page.gif)

#### [Link To MHSAA Scraping Code](Notebook/extract%20data%20by%20sport%20workbook.ipynb)
This notebook is dedicated to scraping and storing data from the Michigan High School Athletic Association (MHSAA) website. It is designed to efficiently gather results of high school sports across Michigan by automating the data collection process for various sports and academic years.

#### Features
- **Dynamic URL Construction**: Constructs URLs dynamically to fetch sports results for specific dates and sports. The notebook includes an example of constructing a URL to scrape girls' basketball data for the academic year 2022-2023.
- **Data Collection**: Utilizes the `requests` library to send queries to the constructed URLs and fetch data in JSON format. This data includes detailed contest results, which are then stored in a text file and loaded into a Pandas DataFrame for further manipulation.
- **Data Storage**: Outputs the scraped data into JSON files, which are then converted into Pandas DataFrames. This structure facilitates easy access and manipulation for subsequent analysis and visualization tasks.

#### Output
- Text files containing raw JSON data from the MHSAA website.
- Pandas DataFrames containing structured results, ready for analysis and visualization in subsequent notebooks.



- NCES National Center for Education Statistics

