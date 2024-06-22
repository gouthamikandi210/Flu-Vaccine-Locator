# Flu-Vaccine-Locator
### Project Overview

The Vaccines.gov dataset provides detailed information on flu vaccine provider locations in the U.S., including contact details, operating hours, vaccine types, and stock leveThis data helps consumers find nearby vaccine providers and assists public health officials in ensuring vaccine availability.

### Data Source

This dataset contains comprehensive information about flu vaccine provider locations across the United States. This data includes details such as provider location ID, store number, contact information, operating hours, insurance acceptance, vaccine types, and stock levels.

[download here](https://data.cdc.gov/Flu-Vaccinations/Vaccines-gov-Flu-vaccinating-provider-locations/bugr-bbfr/about_data)

### Tools used

- Tableau prep - For data cleaning and preparation.
- Tableau - For data visualization and creating interactive dashboards.

### Data Cleaning/Preparation

Tableau provides initial recommendations to clean the data, which include:
- Update the data role of the web_address field to URL. This ensures that all values in this field are recognized as valid web addresses.
- Update the data role of the pre_screen field to URL. This standardizes the data as web addresses.
- Remove this field as it contains redundant information, streamlining the dataset.
- Ensure all values in the Loc_admin_city field are in uppercase to maintain consistency. For instance, correct any typos, such as changing "ALANTA" to "ATLANTA".
- Merge Fields: Enter the formula [Loc_admin_city] + ', ' + [Loc_admin_state] to merge these fields. After merging, a new field named Location is created, containing both city and state information in a single, unified field. Remove the original Loc_admin_city and Loc_admin_state fields to avoid redundancy.
- Remove unnecessary to maintain data accuracy.

### Exploratory Data Analysis

EDA involved exploring the vaccine data to answer these questions:

- Which zip code has the highest average supply value?
- What are the differences between California and Illinois in terms of walk-in acceptance for flu shots on Mondays?
- Which state has the highest and lowest number of accepted insurance?

### Data Analysis
