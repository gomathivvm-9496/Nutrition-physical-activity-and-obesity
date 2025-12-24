# Nutrition-physical-activity-and-obesity
# Project Overview 

This project focuses on analyzing publicly available health indicators related to nutrition habits, physical activity levels, and obesity prevalence across multiple demographic and geographic dimensions
# Project Objective

The primary objective of this analysis is to leverage the Nutrition, Physical Activity, and Obesity dataset to identify trends, risk patterns, and contributing factors to obesity using Power BI visual analytics.
# Data Sources

•	Source Description and Timeline: Data government and 2011-2023.

•	Data Source link: https://catalog.data.gov/dataset/

•	Domain: Public Health / Healthcare Analytics
# Problem Statement 

•	To understanding how nutrition habits, physical activity levels, and obesity rates vary across different regions and demographic groups.

•	To identify key lifestyle factors contributing to obesity

•	To Identify high-risk regions and populations

•	Provide actionable insights for health awareness and policy planning.

•	Provide insights to support public health strategies and awareness programs
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

•	Excel: Data cleaning, transformation, and Pivot Tables.

•	Power BI: Data modelling, DAX calculations, visualization, and interactive dashboard creation.
# Data Pre-Processing (Excel / Power Query) 

# Data Cleaning :

o	Removed duplicate records to avoid double counting.

o	Checked for missing or null values and handled them appropriately.
# Data Transformation:

o	Standardized state names to ensure accurate mapping in geographic visuals.

o	Cleaned and structured Stratification Category values (Age, Gender, Income,     Education, Race/Ethnicity).

o	Created new calculated columns where required, such as:Risk Level (High / Medium / Low),Risk Color codes for conditional formatting.
# Filtering & Sorting:

 Filtered the dataset to include only relevant indicators such as:Obesity,Physical Activity,Nutrition-related indicators
                   
•	Organized data to focus on relevant records

•	Convert the data into Fact and Dimension Table 

•	Pivot Tables : Generated Pivot Tables for data summarisation and initial insights
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
# Insights :
# Key Findings: 

•	 The average obesity rate is 32.83%, indicating obesity affects nearly one-third of the population.

•	Obesity prevalence shows a steady upward trend over the years, with no significant decline.

•	 Certain states consistently appear as high-obesity hotspots, forming clear geographic clusters.

•	 Middle-aged adults (45–64 years) experience the highest obesity levels.

•	 Lower physical activity is strongly associated with higher obesity rates.

•	Obesity risk is evenly distributed across high, medium, and low categories, suggesting a widespread issue rather than isolated cases.

•	Socio-economic factors such as income and education show a noticeable influence on obesity prevalence.
# Analysis Insights:
# Descriptive Analysis:

•	The national average obesity rate stands at 32.83%.

•	Several states exceed 35% obesity, placing them in the high-risk category.

•	Obesity is higher among middle-aged adults and slightly higher among males.

•	Physical activity levels remain moderate to low, compared to obesity prevalence.

•	Obesity is widespread, persistent, and consistent across multiple demographics and regions.
 
# Diagnosis Analysis:

•	States with lower physical activity levels show significantly higher obesity rates.

•	Aging populations experience higher obesity due to reduced metabolism and lifestyle changes.

•	Income and education disparities indicate limited access to healthy food and awareness.

•	Behavioral and occupational differences contribute to gender-based obesity variation.

•	Obesity is driven by a combination of lifestyle, demographic, and socio-economic factors, not a single cause.

# Predictive Analysis:

•	Trend analysis indicates obesity will continue increasing if current patterns persist.

•	Medium-risk groups are likely to shift into high-risk categories.

•	Healthcare systems may face increased chronic disease burden related to obesity.

•	Without effective intervention, obesity will become an even greater public health challenge in the future.

# Prescriptive Analysis:

•	Implement targeted interventions in high-risk states and demographic groups.

•	Promote physical activity programs in workplaces, schools, and communities.

•	Launch nutrition education and awareness campaigns.

•	Address socio-economic barriers through policy and healthcare access improvements.

•	Use dashboards for continuous monitoring and evaluation.

•	Data-driven, targeted, and preventive strategies can significantly reduce future obesity risk.
# Conclusion:

The integration of Excel and Power BI proved highly effective for conducting end-to-end data analysis, transforming raw public health data into meaningful, interactive, and actionable insights. 

Through descriptive analysis, the study revealed that obesity prevalence is consistently high, with an average rate of 32.83%, affecting nearly one-third of the population. Geographic and demographic analysis identified specific states and population groups, particularly middle-aged adults and socio-economically disadvantaged groups, as high-risk segments.

Diagnostic analysis highlighted that low physical activity, age progression, and socio-economic factors are key contributors to rising obesity levels. 

Using trend and predictive analysis, the data indicated a steady upward trend in obesity rates over time, suggesting that without timely and effective intervention, obesity will continue to increase and place greater pressure on healthcare systems.

Finally, prescriptive analysis provided actionable recommendations, including targeted interventions for high-risk states, promotion of physical activity, nutrition education, and policy-driven public health strategies. The interactive Power BI dashboards enable continuous monitoring and support data-driven decision-making for policymakers and health professionals.








________________________________________

