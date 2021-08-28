# COVID-19 pandemic Insight
### Data Engineering Capstone Project

#### Project Summary
The project follows the follow steps:
* Step 1: Scope the Project and Gather Data
* Step 2: Explore and Assess the Data
* Step 3: Define the Data Model
* Step 4: Run ETL to Model the Data
* Step 5: Complete Project Write Up

_________________

### Step 1: Scope the Project and Gather Data

#### Scope 
This Capstone Project's purpose is to preparing data for analysis and finding significant conncections between many aspects the associates with COVID19 pandemic, such as covid19 situation in each countries, accesses to vaccines and effects from COVID19 which are unemployment in many country and trend of world's happiness index 

#### Describe and Gather Data 
The project consists of the following data :
* COVID-19 World Vaccination Progress Data by Our World in Data
* COVID-19 World Vaccine Adverse Reactions(VAERS) by FDA and CDC 
* Unemployment rate by OECD
* World Happiness Report

_________________

### Step 2: Explore and Assess the Data
#### Explore the Data 
Identify data quality issues, like missing values, duplicate data, etc.
* Some dataframe have missing values in important column the will be used further
* Every dataframe collect data in string type
* Date format are different in each dataframe
* Vaccine name format are different in each dataframe

#### Cleaning Steps
* Scope and extract intersted column from each dataframe into specified table
* Drop rows with missing values in key columns
* Correct the data type of each columns
* Format the date column
* Format the vaccine name column
* Add date column to each World Happiness Report file and aggregate into a table

_________________

### Step 3: Define the Data Model
#### 3.1 Conceptual Data Model
Map out the conceptual data model and explain why you chose that model

### Schema:

|          Table name         |                                                                Columns                                                                |                             Description                            |       Type      |
|:---------------------------:|:-------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------:|:---------------:|
|     country_covidStatus     | date,iso_code,location,total_cases,new_cases, total_deaths,new_deaths,total_tests,new_tests, population,population_density,median_age |      stores covid-19 situation and information of each country     |    fact table   |
| country_vacInfoManufacturer |                                                location,date,vaccine,total_vaccinations                                               |            stores covid-19 vaccinations of each country            |    fact table   |
|      vacAdverse_vacInfo     |                                     VAERS_ID,VAX_NAME,VAX_MANU,VAX_DOSE_SERIES,VAX_ROUTE,VAX_SITE                                     | stores vaccine information of patients who has an adverse reaction | dimension table |
|      vacAdverse_patInfo     |                             VAERS_ID,AGE_YRS,SEX,DISABLE,ALLERGIES,VAX_DATE, RECOVD,DIED,DATEDIED,HISTORY                             |       stores patients information who has an adverse reaction      | dimension table |
|      vacAdverse_symInfo     |                                         VAERS_ID,SYMPTOM1,SYMPTOM2,SYMPTOM3,SYMPTOM4,SYMPTOM5                                         |         stores patients's adverse reaction from the vaccine        | dimension table |
|       unemploymentRate      |                                      country_code,INDICATOR,SUBJECT,MEASURE,FREQUENCY,TIME,Value                                     |              stores unemployment rate of each country              | dimension table |
|        happinessRate        |            country,happiness_score,gdp_per_capita,social_support, health,freedom,generosity,government_trust,continent,date           |                stores happiness rate of each country               | dimension table |
|  unemploy_CovidStatus |      date,iso_code,location,Value,total_cases,total_deaths,total_tests,population      | stores information about unemployment rate  and COVID-19 situation in each country | fact table |
| happiness_CovidStatus | date,iso_code,location,happiness_score,total_cases,total_deaths,total_tests,population |   stores information about happiness rate  and COVID-19 situation in each country  | fact table |

#### Tables Decision:

As stated above about the objectives of the project that is to find significant connections between diverse aspects about COVID-19 pandemic, So we must have the country_covidStatus and country_vacInfoManufacturer tables to store the key information and then we can integrate them with other aspects information to find data consistency. to do so efficiently, we need identifiers on all tables so they can be joined efficiently such as the date, iso_code, country name, vaccine name etc.

#### 3.2 Mapping Out Data Pipelines
List the steps necessary to pipeline the data into the chosen data model

1. Reads all the data from dataset using spark
2. Extracts data from datframe and transfroms to described schema
3. Aggregates data to find insight relation between each tables
3. writes the data to destination(in this case is local) in the parquet format.

_________________

### Step 4: Run Pipelines to Model the Data 
#### 4.1 Create the data model
Build the data pipelines to create the data model.

#### 4.2 Data Quality Checks
Explain the data quality checks you'll perform to ensure the pipeline ran as expected. These could include:
 * Integrity constraints on the relational database (e.g., unique key, data type, etc.)
 * Unit tests for the scripts to ensure they are doing the right thing
 * Source/Count checks to ensure completeness
 
Run Quality Checks

#### 4.3 Data dictionary 
Create a data dictionary for your data model. For each field, provide a brief description of what the data is and where it came from. You can include the data dictionary in the notebook or in a separate file.

_________________

#### Step 5: Complete Project Write Up
#### choice of tools and technologies for the project

        In this project I used Spark to visualize data because it's easier to do schema on read and I also use Spark to clean the data as well, At a later stage, I recommend using Spark to process the data with the better environment and support larger dataset such as Amazon Elastic Map Reduce (EMR). Also, to perform automated updates, I recommend integrating the ETL pipeline into an Airflow DAG.
    
        The Jupyter Notebook is used to show the steps how I structured the project and easier to markdown and explain in each step about what I did. Apart from this, Python is an often used programming language and was used because it is the language I am the most comfortable with.
    
    
#### how often the data should be updated and why

        The COVID-19 situation still continues to occur, and the vaccination and other informations are also necessary to assess and deal with such situations. thus, In my opinion. monthly update is what I recommended the most.
        
        
#### How I would handle the following sceanarios :
 * The data was increased by 100x.
     * Use Spark to process the data efficiently in a distributed way e.g. with EMR.
 * The data populates a dashboard that must be updated on a daily basis by 7am every day.
     * Use Airflow and create a DAG that performs the logic of the described pipeline.
 * The database needed to be accessed by 100+ people.
     * Use RedShift to have the data stored in a way that it can efficiently be accessed by many people.
     
_________________
