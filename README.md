# The Manufacturing-Industry-Data-Extractor

An ETL pipeline designed to help users analyze and monitor economic developments across sectors of the German manufacturing industry. Two Python functions automate data extraction, cleaning, transformation, and storage, providing reliable, analysis-ready data so users can focus directly on their analysis.

## General Description

Whether a user works in the manufacturing of metalworking machinery or automotive parts and wants to quickly access reliable historical data on their own industry's turnover, sales markets, and employment trends to compare their company's performance with the industry average, or whether a company or investor is considering investments in a specific sector of the manufacturing industry and needs a data-driven basis for decision-making.

The functions are also designed for consulting companies specializing in the manufacturing industry that want to analyze both overall economic developments and the market structure of different manufacturing sectors.

For all these users, my functions provide a straightforward way to access relevant data, automate much of the data preparation process, and move directly to the analysis!

## Project Structure

README: Project description.

Industry-Codes.pdf: Contains a list of manufacturing sectors and their WZ codes. The WZ code is used by the functions to extract data regarding the selected sector.

Presentation.pptx: The presentation of my project.

Functions.ipynb: The heart and soul of this project. This notebook contains the two functions that extract data from the GENESIS database, a description of the requirements, the information users have to provide to the functions, and how they work.

## Database

The data used is extracted from two tables provided by the Federal Statistical Office of Germany. The following tables form the foundation:

Table 42111-0026 – Monthly data: Contains monthly data on employment and turnover by economic sector. The original columns include the reporting period, industry classification, statistical indicator, and value. The data covers topics such as total turnover, domestic and foreign turnover, employment, and the number of reporting units.

Table 48121-0003 – Annual data: Contains annual business statistics by economic sector and company size. The data covers the number of enterprises, turnover, persons employed, gross investment in tangible fixed assets, and gross value added.

For the functions to work, you have to enter the WZ code, not the sector name. You can find a list of the available sectors in the PDF provided in the repository. This list is based on the code list provided by GENESIS. Please keep in mind that codes may change or be deleted by the Federal Statistical Office. Always check after each function run whether the data was stored successfully.

## Requirements and Installation

The following requirements must be met to use the functions:

- Python and the required libraries (pandas, requests, sqlalchemy, and pymysql).
- A valid GENESIS-Online account to access the API. --> https://genesis.destatis.de/datenbank/online/#modal=login
- A running MySQL server and valid login credentials.
- Sufficient MySQL permissions to create databases and tables and insert data.

Install the required Python libraries using pip:
pip install pandas requests sqlalchemy pymysql

## How to use the functions

Get the required information to run the functions and choose the manufacturing sector your interested in (look into the Industry-codes.pdf).

Open Functions.ipynb in Jupyter Notebook or VS Code and execute the cells containing the function definitions.

Run the desired function:

df_monthly = Funktion_monthly()
df_annual = Funktion_annual()

Follow the prompts to enter the required information, select the industry code, define the data period, and configure the database connection.

For detailed information about the required inputs, data processing, and database configuration, see the function descriptions in Functions.ipynb.

## Limitations

- One industry per function run: Each function downloads data for only one economic sector per execution. For comparative analyses, the functions must be executed separately for each sector of interest.

- Limited data availability: Table 48121-0003 has a limited time range, which restricts the historical analysis of annual business statistics.

## Technologies Used

Data Extraction & Cleaning: VS Code (Pandas)

ETL Pipeline Construction: VS Code (requests, getpass, sqlalchemy)

Data Storage: MySQL Workbench and BigQuery

Dashboard Construction: Data Studio, based on BigQuery queries.

Presentation: Google Slides

Machine learning: ChatGPT

## Data overview

This schema serves as an overview of the available Variables provided by the functions:

![Database Schema](Data%20overview.png)

## Dashboard example

![Manufacturing Industry Dashboard](Dashboard.png)

This interactive dashboard was built in Looker Studio using data stored in BigQuery. It allows users to explore the economic development of selected German manufacturing sectors and compare their performance across different indicators. It serves as an example of what a user can do with the data.

The dashboard includes:

- Monthly Trends: Track changes in turnover and employment over time.
- Industry Comparison: Compare the development of the machine tools industry (WZ08-284), the weapons and ammunition industry (WZ08-254), and the automotive parts industry (WZ08-293).
- Economic Indicators: Examine turnover, employment, gross investment in tangible fixed assets, and gross value added at factor cost.
- Interactive Filters: Select different indicators and explore the data according to the selected industry and time period.

## Future work

- Integration of additional GENESIS tables: The limited historical availability of Table 48121-0003 makes it useful to expand the ETL pipeline with additional statistics on the German manufacturing industry.

- More detailed economic indicators: Further GENESIS tables provide additional information on investment and cost factors. Integrating these data sources would allow for more comprehensive analyses of the economic development and cost structures of individual manufacturing sectors.

- Extended analytical possibilities: Combining additional data sources would enable more detailed comparisons between manufacturing sectors and provide a broader basis for data-driven decision-making.
