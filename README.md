# Health-Data-Analytics
## Table of contents 
- [Project Overview](#project-overview)
- [Problem Statement](#problem-statement)
- [Data Source](#data-source)
- [Tools Used](#tools-used)
- [Data Cleaning](#data-cleaning)
- [Data Analysis](#data-analysis)
- [Results](#results)
- [Recommendations](#recommendations)
### Project Overview
## Dataset Description
 Key fields in the dataset include:
- Location ID/Name: Identifies the geographical region.
- Year: Year of data collection (1990 and 2019).
- Age Group: "Age-standardized" grouping of health indicators.
- Indicator Name: Diseases or health indicators (e.g., Tuberculosis, Respiratory infections).
- HAQ Index: Health Access and Quality Index.
- Mortality-to-Incidence Ratio (MIR): The ratio of deaths to new cases of a disease.
- Confidence Intervals: Upper and lower bounds for reported values.


![DASHBOARD](https://github.com/user-attachments/assets/5db3196c-048b-4f46-9d63-4619e457b691)

### Problem Statement
#### The problems that need to be addressed are:
The following analysis areas and other ones:

○     Health Performance by HAQ Index: Which health sectors are performing well, and where can improvements be made?

○     Mortality-to-Incidence Ratios (MIR): Which diseases are deadliest in terms of mortality relative to incidence?

○     Risk-Standardized Death Rates (RSD): What are the most dangerous conditions based on standardized death rates?

○     Top 5 Diseases: What are the top 5 diseases contributing to the highest mortality?

○     Uncertainty Analysis: How reliable is the data, and where are the biggest uncertainties?

### Data Source
The dataset used for this analysis is from data science nigeria.
### Tools Used
- PowerBi- Data analysis,Data visualization
- Excel- Data cleaning,Data validation
- Dashboard Design- Data ink ratio
- Data Analysis- Extraction,wrangling and Exploration
 ### Data Cleaning
 #### List of things checked and evaluated where necessary before performing data exploration
 - Converting text to columns and change of data types
 - cleaning operation
 - Creating new columns
 ### Data Analysis
```PowerBi
= Table.TransformColumnTypes(#"Promoted Headers",{{"location_id", Int64.Type}, {"location_name", type text}, {"year_id", Int64.Type}, {"age_group_id", Int64.Type}, {"age_group_name", type text}, {"haq_index_age_type", type text}, {"indicator_id", Int64.Type}, {"indicator_name", type text}, {"measure", type text}, {"val", type number}, {"upper", type number}, {"lower", type number}});

= Table.ReplaceValue(#"Changed Type","American Samoa","United States of America",Replacer.ReplaceText,{"location_name"});

= Table.Pivot(#"Duplicated Column", List.Distinct(#"Duplicated Column"[measure]), "measure", "val");
= Table.ReplaceValue(#"Pivoted Column",null,0,Replacer.ReplaceValue,{"location_id", "location_name", "year_id", "age_group_id", "age_group_name", "haq_index_age_type", "indicator_id", "indicator_name", "upper", "lower", "val - Copy", "Index", "Mortality-to-incidence ratios (MIR)", "Risk-standardised death rates (RSD)"});
= Table.AddColumn(#"Replaced Value1", "Confidence Intervals", each [upper]-[lower]);

```

### Results
INSIGHTS FROM THE ANALYSIS

- Variation in Healthcare Quality: The data highlights significant disparities in healthcare access and quality across countries
- Age-Related Disparities: The analysis reveals distinct age-related variations in health outcomes, with the 65-74 age group consistently demonstrating higher mortality rates.
- Importance of Early Intervention: The low Mortality to Incidence Ratio (MIR) in the 0-14 age group underscores the importance of early intervention and preventive healthcare measures in this population.
- Need for Targeted Interventions: The data highlights the need for targeted interventions and resource allocation to address the specific healthcare needs of different age groups and populations with high mortality rates.
- Learning from Best Practices: Countries with low HAQ indices can significantly benefit from learning from the strategies and best practices of high-performing nations with strong healthcare systems and high HAQ scores.

### Recommendations
Based on the obtained results from the analysis, the following recommendations are made:
1. Prioritize interventions for the 65-74 age group: To effectively reduce high Mortality to Incidence Ratios (MIR) and Relative Survival Differences (RSD), efforts should be concentrated on the 65-74 age range, which exhibited the highest values in both years.

2. Address key cancer types: Colon and rectal cancer, Hodgkin lymphoma, and cervical cancer, being the leading causes of high MIR in many countries, require increased attention through targeted prevention, early detection, and improved treatment strategies.

3. Foster knowledge exchange: Countries with low  (HAQ) indices and high MIR/RSD ratios should actively learn from the successful strategies of top-performing countries with high HAQ indices, particularly in areas of healthcare access, quality of care, and health system organization.

4. Invest in comprehensive healthcare support: Increased allocation of resources, enhanced public health campaigns, and improved access to medical facilities are crucial for countries with low HAQ indices, particularly with respect to the specific disease burdens and age-related health needs within their populations.


