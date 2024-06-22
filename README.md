# Flu-Vaccine-Locator

## Table contents

- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Tools used](#tools-used)
- [Data Cleaning/Preparation](#data-cleaningpreparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)

  
### Project Overview

The Vaccines.gov dataset provides detailed information on flu vaccine provider locations in the U.S., including contact details, operating hours, vaccine types, and stock leveThis data helps consumers find nearby vaccine providers and assists public health officials in ensuring vaccine availability.

### Data Source

This dataset contains comprehensive information about flu vaccine provider locations across the United States. This data includes details such as provider location ID, store number, contact information, operating hours, insurance acceptance, vaccine types, and stock levels.

[source link](https://data.cdc.gov/Flu-Vaccinations/Vaccines-gov-Flu-vaccinating-provider-locations/bugr-bbfr/about_data)

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

#### 1.Which zip code has the highest average supply value?
A Map view allows a geospatial context to vaccine distributors that makes it easy for them to understand how supply levels are distributed among various locations. 
Map showcasing vaccination locations with Latitude and Longitude.
- The size of markers represents Loc_Admin_Zipcode.
- The color gradient indicates the average supply level, ranging from orange (average supply level -1) to darker blue (average supply level 4).
#### Insights: 
- This will assist vaccine distributors in making well-informed decisions regarding vaccine allocation to meet increased demand in particular areas if zip codes with consistently high demand (darker shades) for vaccinations is identified. 
- When hovering over the darkest blue, it reveals that the zip code (54154) has the highest average supply level.
#### Executive summary: 
A clear understanding of supply distribution across various locations is made possible for vaccine distributors by the comprehensive overview provided by the geospatial map view. A color gradient from orange to darker blue indicates average supply levels, and markers sized by Loc_Admin_Zipcode provide a visual hierarchy using latitude and longitude coordinates. Distributors can more efficiently allocate resources and effectively address gaps in vaccine supply thanks to this user-friendly representation, which speeds up decision-making. Because of the dynamic features of the map, vaccine distribution efforts can be more strategically responsive in real time through monitoring and localized planning.

![](https://github.com/gouthamikandi210/Flu-Vaccine-Locator/blob/main/Screenshot%20(436).png)


#### 2.What are the differences between California and Illinois in terms of walk-in acceptance for flu shots on Mondays?
A Bar chart is an effective tool for comparing the number of walk-ins in various states and time slots. Users can easily recognize trends and patterns because each bar's length gives an easily understandable visual comparison.
- Applied a filter to select only ‘Flu shot’ vaccines from the "searchable name" column.
- X-axis: Different time slots throughout Monday.
- Y-axis: Count of walk-ins accepted.
- Utilized color markers to distinguish different counts of walk-ins within the selected time slots.
- Parameter 1: Loc_admin_state. Used a filter to narrow down the data to the states of California and Illinois
- Parameter 2: Monday Hours. Focused on Monday hours for the specific timing analysis.

- The calculation used the calculated field for both parameters:
CASE[Dimension]
WHEN "Loc Name" THEN [Loc Name]
WHEN "Loc Store No" THEN [Loc Store No]
WHEN "Loc Admin City" THEN [Loc Admin City]
WHEN "Loc Admin State" THEN [Loc Admin State]
WHEN "Searchable Name" THEN [Searchable Name]
WHEN "Quantity Last Updated" THEN STR(DATE([Quantity Last Updated]))
WHEN "Monday Hours" THEN [Monday Hours]
WHEN "Tuesday Hours" THEN [Tuesday Hours]
WHEN "Wednesday Hours" THEN [Wednesday Hours] 
WHEN"In Stock" THEN STR([In Stock]) 
WHEN "N/A" THEN "" END

- By allowing users to explore the data according to their preferences or particular criteria, parameters give the dashboard its interactive quality. For instance, in Field1 we can use the dropdown to select different day hours apart from Monday Hours. 
- By using Filters, a more flexible evaluation is made possible by quickly switching between various states, vaccine types, and time slots.
#### Insights:
- Identifying the Monday timeslots when most walk-in patients receive flu shots. It is then possible for health providers to decide when to assign additional staff for effective walk-in service at busy times.
- The largest number of walk-ins (1276) in California occurred between 8 a.m. and 8 p.m., suggesting a high level of demand during regular business hours.
#### Executive Summary: 
The bar graph effectively compares the number of walk-in patients for the "Flu shot" in California and Illinois on Mondays during various time slots. It is simple to spot trends and patterns in walk-in traffic thanks to the visual clarity of bar lengths. When color markers are used, differences in the number of walk-ins during particular periods are easily visible. The filters that have been applied such as the limitation to "Flu shot" vaccinations, Parameter 1 (Loc_admin_state), and Parameter 2 (Monday Hours) ensure a targeted analysis that empowers distributors to decide the best way to allocate resources and develop strategic plans.

![](https://github.com/gouthamikandi210/Flu-Vaccine-Locator/blob/main/Screenshot%20(437).png)


#### 3.Which state has the highest and lowest number of accepted insurance?
The Line chart presents an in-depth analysis of insurance acceptance rates in various states.
- X-axis: States
- Y-axis: Count of Insurance Accepted
#### Insights:
- From the Line chart, it is clear that California stands out with the highest count of insurance accepted (17,384), indicating a significant demand or accessibility to insurance coverage. While North Dakota has the least count of insurance accepted (5) which was unexpected.
- A strategic distribution of resources is made possible by identifying weak performers, like North Dakota (5), and strong performers, like California. In the states with lower counts, this information can help prioritize efforts to improve insurance acceptance.
#### Executive Summary:
The line graph offers a thorough analysis of insurance acceptance rates in various states. With the highest number of insurance acceptances (17,384), California stands out as having a high demand for or accessibility to insurance coverage. North Dakota, on the other hand, shows an incredibly low count (5), which calls for more investigation into the underlying causes. This enables specific actions and allocation of resources to address differences in insurance acceptance among various states.

![](https://github.com/gouthamikandi210/Flu-Vaccine-Locator/blob/main/Screenshot%20(438).png)


#### Dashboard:
- The Line chart, map view, and bar chart were uploaded successfully to the Tableau dashboard. All interactive components, such as filters, parameter controls, and actions, are working without any difficulties. The Dashboard allows users to quickly explore the locations of flu vaccination providers, making it an interesting experience.
- In the Bar chart, using the parameter dropdown we can see changes in walk-ins for the Flu Shot vaccinations on other days of the week.
- For Map view, we can zoom in and out of the map to get more details or examine particular areas in more detail.
- In the Line chart, we can click on the data points to see more information in detail. 

![](https://github.com/gouthamikandi210/Flu-Vaccine-Locator/blob/main/Screenshot%20(439).png)
