##### country_covidStatus_table
* date : Date of observation
* iso_code : ISO 3166-1 alpha-3 – three-letter country codes
* location : Country name for which the vaccination information is provided;
* total_cases : Total confirmed cases of COVID-19
* new_cases : New confirmed cases of COVID-19
* total_deaths : Total deaths attributed to COVID-19
* new_deaths : New deaths attributed to COVID-19
* total_tests : Total tests for COVID-19
* new_tests : New tests for COVID-19
* population : Population in 2020
* population_density : Number of people divided by land area, measured in square kilometers, most recent year available
* median_age : Median age of the population, UN projection for 2020

##### country_vacInfoManufacturer_table
* location : Country name for which the vaccination information is provided;
* date : Date of observation
* vaccine : Vaccine type
* total_vaccinations :  Total number of vaccinations at the time

##### vacAdverse_vacInfo_table
* VAERS_ID : VAERS Identification Number
* VAX_NAME : Vaccine Name
* VAX_MANU : Vaccine Manufacturer
* VAX_DOSE_SERIES : Number of doses administered
* VAX_ROUTE : Vaccination Route
* VAX_SITE : Vaccination Site

##### vacAdverse_patInfo_table
* VAERS_ID : VAERS Identification Number
* AGE_YRS : Age in years
* SEX : Sex
* DISABLE : Disability
* ALLERGIES : Allergies to medications,food, or other products 
* VAX_DATE : Vaccination Date
* RECOVD : Recovered
* DIED : Died
* DATEDIED : Date of death
* HISTORY : Chronic or long-standing health conditions

##### vacAdverse_symInfo_table
* VAERS_ID : VAERS Identification Number
* SYMPTOM 1-5 : Reported symptom text

##### unemployRate_table
* country_code : ISO 3166-1 alpha-3 – three-letter country codes
* INDICATOR : Indicator used in observation
* SUBJECT : Subject
* MEASURE : Measurement
* FREQUENCY : Frequency
* TIME : Date of observation
* Value : Index to specify rate of unemployment

##### happinessRate_table
* country : Country name which observation took place
* happiness_score : Index to specify happiness level from 6 following factors
* gdp_per_capita : Economic production of the country
* social_support : Social support from the government
* health : Life expectancy
* freedom : Freedom in living within the country
* generosity : Generosity of the government
* government_trust : Absence of corruption of the government
* continent : Continent of the country which observation took place
* Datetime : Date of observation