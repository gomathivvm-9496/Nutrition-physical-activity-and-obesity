# Nutrition & Obesity Analysis using Power BI
# Project Overview 

This project focuses on analyzing publicly available health indicators related to nutrition habits, physical activity levels, and obesity prevalence across multiple demographic and geographic dimensions
# Project Objective

To analyze how nutrition and physical activity influence obesity levels.

# Problem Statement 
-	To understanding how nutrition habits, physical activity levels, and obesity rates vary across different regions and demographic groups.
-	To identify key lifestyle factors contributing to obesity
-	To Identify high-risk regions and populations
-	Provide actionable insights for health awareness and policy planning.
-	Provide insights to support public health strategies and awareness programs
# Attribute (Column /Features) Details: 

| Attribute Name	| Data Type	| Description |
|-----------------|-----------|-------------|
| Year Start |	Integer |	Starting year of data collection |
| Year End	| Integer |	Ending year of data collection |
| Location Abbr	| Text | 	Abbreviation of the location (e.g., CA, NY) |
| Location Desc	| Text |	Full name of the location (state or region) |
| Class |	Text	| Category of health indicator (Nutrition, Physical Activity, Obesity) |
| Topic	| Text	| Broad topic under the class (e.g., Obesity / Weight Status) |
| Question	| Text	| Survey question asked to collect the data | 
| Data value	| Decimal	| Actual measured value (percentage or rate) |
| Low confidence Limit	| Decimal	| Lower bound of confidence interval |
| High confidence Limit |	Decimal	| Upper bound of confidence interval |
| Sample Size	| Integer	| Number of survey respondents |
| Latitude	| Decimal	| geographic location information | 
| Longitude	| Decimal	| geographic location information |
| Class ID	| Text	| Unique identifier for the class |
| Topic ID	| Text	| Unique identifier for the topic |
| Question ID	| Text	| Unique identifier for the survey question |
| Location ID	| Integer	| Unique identifier for the location |
| Stratification Category |	Text	| Category used for stratification (Gender, Age, Income, etc.) |
| Stratification 	| Text	| Specific stratification value (Male, Female, Age 18–24, etc.) |
| Stratification Category ID |	Text	| type of demographic stratification used to segment the data |
| Stratification ID	| Text	| specific coded value within the selected stratification category.
# Tools & Technologies
-	Excel: Data cleaning, transformation, and Pivot Tables.
-	Power BI: Data modelling, DAX calculations, visualization, and interactive dashboard creation.
# Data Pre-Processing (Excel / Power Query) 

# Data Cleaning :
-	Removed duplicate records to avoid double counting.
-	Checked for missing or null values and handled them appropriately # Data Transformation:
-	Standardized state names to ensure accurate mapping in geographic visuals.
-	Cleaned and structured Stratification Category values (Age, Gender, Income,     Education, Race/Ethnicity).
-	Created new calculated columns where required, such as:Risk Level (High / Medium / Low),Risk Color codes for conditional formatting.
# Filtering & Sorting:
 Filtered the dataset to include only relevant indicators such as:Obesity,Physical Activity,Nutrition-related indicators                  
-	Organized data to focus on relevant records
-	Convert the data into Fact and Dimension Table 
-	Pivot Tables : Generated Pivot Tables for data summarisation and initial insights
# Data Modelling and DAX (Power BI) 

•	Cardinality: One to many relationship
# Calculated Columns & DAX Measures: 

	average_Nutrition = CALCULATE(AVERAGE('Fact tab'[Data_Value]),FILTER('Topic dimension',CONTAINSSTRING('Topic dimension'[Topic],"Fruits and Vegetables")))

	average_obesity = CALCULATE(AVERAGE('Fact tab'[Data_Value]),FILTER('Topic dimension',CONTAINSSTRING('Topic dimension'[Topic],"Obesity / Weight Status")))

	average_physicalactivity = CALCULATE(AVERAGE('Fact tab'[Data_Value]),FILTER('Topic dimension',CONTAINSSTRING('Topic dimension'[Topic],"Physical Activity - Behavior"))

	Female Avg Value = CALCULATE( AVERAGE('Fact tab'[Data_Value]), 'Stratification dimension'[Stratification Category] = "Sex", 'Stratification dimension'[Stratification] = "Female")

	High_risk_obesity% = CALCULATE(COUNTROWS('Fact tab'),'Topic dimension'[Topic] = "Obesity / Weight Status",'Fact tab'[Data_Value] > 30)

	Risk Level = SWITCH(TRUE(),[Average_datavalue] >= 30, "High Risk" [Average_datavalue] >= 20, "Medium Risk","Low Risk")

	Total_obesity = CALCULATE(SUM('Fact tab'[Data_Value]),FILTER('Topic dimension',CONTAINSSTRING('Topic dimension'[Topic],"Obesity / Weight Status")))

	Total_records = COUNTROWS('Fact tab')

	Confidence_width = [Average_HCL]-[Average_LCL]

	Avg Value by Gender = CALCULATE(AVERAGE('Fact tab'[Data_Value]),'Stratification dimension'[Stratification Category] = "Sex")

	High Risk States = CALCULATE(DISTINCTCOUNT('location dim'[Location Desc]),
              'Fact tab'[Risk Level Column] = "High Risk")

# Key Findings: 

- The average obesity rate is 32.83%, indicating obesity affects nearly one-third of the population.
-	Obesity prevalence shows a steady upward trend over the years, with no significant decline.
-	Certain states consistently appear as high-obesity hotspots, forming clear geographic clusters.
- Middle-aged adults (45–64 years) experience the highest obesity levels.
-	Lower physical activity is strongly associated with higher obesity rates.
-	Obesity risk is evenly distributed across high, medium, and low categories, suggesting a widespread issue rather than isolated cases.
-	Socio-economic factors such as income and education show a noticeable influence on obesity prevalence.

# Key Insights
- Higher obesity levels observed in low-activity populations
- Physical activity has strong negative correlation with obesity
- Nutrition score impacts obesity rates moderately
- Certain regions show higher health risk
# Recommendations
- Promote physical activity programs
- Target high-risk states
- Improve nutrition awareness
- Focus on middle-aged population
- Use dashboards for monitoring
# Conclusion:

Power BI analysis reveals that obesity is strongly influenced by physical activity, age, and socio-economic factors. The dashboard helps identify high-risk groups and supports data-driven public health decisions.








________________________________________

