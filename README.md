Child Mortality in a Changing World
A data-driven analysis of global child mortality trends and selected socioeconomic and health-related determinants
Project status: Completed
Tool: Microsoft Power BI
Analysis period: 2000–2024
Project type: Public health analytics / exploratory data analysis / data integration
Author: Samuel Johnson / Syma Tech Solutions

📌 Project Overview
Child mortality remains an important indicator of population health, socioeconomic development, and access to essential services.
This project began as a broad exploration of global child mortality, with the initial objective of examining long-term mortality trends and exploring relationships between child mortality and several socioeconomic and health-related indicators.
The initial analysis incorporated datasets covering:
Child mortality
GDP per capita
Population
Health expenditure
Water and sanita tion
Education
Income group
World Bank regions
Country geolocation
The first dashboard produced a broad analysis covering 1980–2011 and explored relationships between child mortality and several contextual variables.
However, the project changed direction after a deeper review of the underlying datasets revealed substantial differences in country and year coverage.
Rather than continuing to build on an uncertain analytical foundation, I returned to the data, conducted a country-year completeness assessment, reconsidered the scope, removed variables with insufficient coverage for the revised analysis, rebuilt the integrated dataset and produced a second version of the dashboard.
The final analysis focuses on 2000–2024 and examines child mortality alongside:
GDP per capita
Health expenditure
Population
Water and sanitation
The revised dashboard contains 212 countries in the analysed child-mortality dataset.

🎯 Research Question
The central question guiding the project is:
How has child mortality changed across countries over time, and what socioeconomic and health-related factors are associated with differences in child mortality?
The project is intentionally exploratory and descriptive.
It does not attempt to establish that any individual factor causes changes in child mortality.
Instead, it examines:
Global mortality trends
Differences between countries and regions
Country-level patterns
Associations between child mortality and selected contextual indicators
The quality and completeness of the underlying data

🧭 Project Objectives
The project was designed around six main objectives.
1. Understand the trend
Examine how child mortality has changed over the selected period.
2. Identify disparities
Explore differences in child mortality between countries and World Bank regions.
3. Examine potential determinants
Investigate associations between child mortality and:
GDP per capita
Health expenditure
Population
Water and sanitation
4. Assess data quality
Identify missing country-year observations before relying on integrated datasets for analysis.
5. Build an integrated analytical model
Combine multiple datasets into a country-year analytical structure suitable for Power BI.
6. Communicate the findings
Translate the analysis into an interactive dashboard and a public-facing data story.

🗂️ Project Evolution
One of the most important aspects of this project is that it went through two analytical versions.
Version 1 — Exploratory Analysis
The initial dashboard covered 1980–2011 and incorporated a wider range of explanatory variables, including education, GDP per capita, water and sanitation, and health expenditure.
The dashboard showed:
Global child mortality trends
Country rankings
Regional differences
GDP vs child mortality
Education vs child mortality
Water/sanitation vs child mortality
Health expenditure vs child mortality
Pearson correlation statistics
Initial dashboard
[Insert Screenshot / Preview Here]
![Initial Dashboard](images/dashboard-v1.png)
Power BI file: [Insert Power BI file link]

⚠️ The Problem I Discovered
The first dashboard looked reasonable from a visual perspective.
However, during a deeper review of the underlying datasets, I realised that the datasets did not share consistent country and year coverage.
This was important because a merged dataset can appear structurally complete while containing very different levels of availability across variables.
For example, the project datasets had different:
Numbers of countries
Observation periods
Country-year combinations
Missing-value patterns
This meant that simply joining the datasets and proceeding to analysis could lead to misleading comparisons.
The lesson
A dashboard can look correct while the analytical foundation underneath it is incomplete.
Rather than attempting to fix the dashboard visually, I went back to the data.

🔍 Data Quality Assessment
The second phase of the project therefore focused heavily on data profiling and completeness assessment.
The key unit of assessment became:
Country + Year
For each determinant, I generated the expected country-year combinations and compared them with the observations actually available in the source dataset.
The general audit logic was:
Expected Country-Year Combinations
                ↓
          Left Join
                ↓
       Actual Observations
                ↓
      ┌─────────┴─────────┐
      ↓                   ↓
  AVAILABLE             MISSING
This allowed me to identify missing observations systematically rather than discovering them after building the dashboard.

📊 Datasets
The original project considered the following datasets.
Dataset
Main Variables
Role
Child Mortality
Country, Year, CMR
Primary outcome
GDP per Capita
Country, Year, GDP per capita
Economic indicator
Health Expenditure
Country, Year, Health expenditure
Health-system indicator
Population
Country, Year, Population
Demographic context
Water & Sanitation
Country, Year, Water access
Infrastructure/public-health indicator
Education
Country, Year, Education indicators
Socioeconomic indicator
Income Group
Country, Year, Income group
Development classification
World Region
Country, Region
Geographic classification
Country Geolocation
Country, Latitude, Longitude
Mapping

Data sources
Note: Insert the exact original source URLs here before publishing.
Child mortality: [INSERT SOURCE LINK]
GDP per capita: [INSERT SOURCE LINK]
Health expenditure: [INSERT SOURCE LINK]
Population: [INSERT SOURCE LINK]
Water & sanitation: [INSERT SOURCE LINK]
Education: [INSERT SOURCE LINK]
Income group: [INSERT SOURCE LINK]
World Bank regions: [INSERT SOURCE LINK]
Country geolocation: [INSERT SOURCE LINK]

🔄 Scope Revision
After completing the data-quality assessment, I decided that the original scope was too broad for the available data.
In particular, the education dataset presented significant compatibility challenges because of its different temporal structure and country coverage.
Rather than forcing every collected dataset into the model, I narrowed the analysis.
Revised analytical period
2000–2024
Primary outcome
Child Mortality Rate
Selected contextual variables
GDP per capita
Health expenditure
Population
Water & sanitation
This revision made the project more focused and allowed the analysis to concentrate on variables that could be reasonably integrated within the revised period.

🧹 Data Cleaning & Preparation
The cleaning and integration process was performed entirely in Microsoft Power BI / Power Query.
Main steps
Raw datasets
     ↓
Data profiling
     ↓
Column standardisation
     ↓
Country identification
     ↓
Year standardisation
     ↓
Duplicate checks
     ↓
Missing-value assessment
     ↓
Country-year audit
     ↓
Scope revision
     ↓
Dataset integration
     ↓
Analytical fact table
Key transformations
The datasets were standardised around common identifiers:
CountryCode
CountryName
Year
Where possible, country-year observations were matched using:
CountryCode + Year
This was preferred over relying solely on country names because country names can vary between datasets.

🧪 Data Quality Audit
The audit was performed before the final analytical model was built.
For each major dataset, I created expected country-year combinations.
For example, for a dataset covering 2000–2024:
Country A × 2000
Country A × 2001
Country A × 2002
...
Country A × 2024

Country B × 2000
Country B × 2001
...
Country B × 2024
These expected observations were then compared against the actual source records.
Each country-year combination was classified as:
Available
Missing
This created a reproducible data-quality assessment rather than relying on a simple null count after merging.

🏗️ Data Model
The final analytical model was designed around a country-year fact table.
Grain
One row represents one country in one year.
The analytical fact table contains the primary outcome and selected contextual variables.
Conceptually:
                   DIM_DATE
                       │
                       │ Year
                       ▼
DIM_COUNTRY ───── FACT_CHILD_MORTALITY
                       │
             ┌─────────┼─────────┐
             │         │         │
            GDP      HEALTH     WATER
                       │
                   POPULATION
FACT_CHILD_MORTALITY
Core fields:
CountryCode
Year
ChildMortalityRate
GDP_Per_Capita
Health_Expenditure
Population
Water_Sanitation
DIM_COUNTRY
The country dimension contains contextual information such as:
CountryCode
CountryName
Region
IncomeGroup
Latitude
Longitude
DIM_DATE
Because the analysis is annual, the date dimension was intentionally kept simple:
Year

📐 Analytical Methodology
The analysis primarily uses:
Descriptive analysis
Averages
Trends
Country rankings
Regional comparisons
Time-series analysis
Child mortality was examined across the selected annual period.
Geographic analysis
Country-level CMR was visualised geographically using latitude and longitude.
Association analysis
Scatterplots and Pearson correlation were used to explore relationships between child mortality and selected variables.
The correlation coefficient is:
[
r =
\frac{
\sum (x_i-\bar{x})(y_i-\bar{y})
}{
\sqrt{\sum(x_i-\bar{x})^2
\sum(y_i-\bar{y})^2}
}
]
Where:
x = contextual variable
y = child mortality rate
r = Pearson correlation coefficient

⚠️ Important Analytical Constraint
The Pearson correlations should be interpreted as associations, not causal relationships.
For example:
A negative correlation between GDP per capita and child mortality does not mean that increasing GDP per capita alone causes child mortality to fall.
Many factors may interact simultaneously, including:
Healthcare access
Nutrition
Sanitation
Education
Poverty
Infrastructure
Maternal health
Public policy
Environmental conditions
Therefore, this project does not claim causal effects.

📊 Dashboard — Version 2
The revised dashboard focuses on the 2000–2024 analytical period.
It contains:
Global child mortality trend
Country-level mortality comparison
Geographic distribution
GDP vs child mortality
Health expenditure vs child mortality
Population vs child mortality
Water/sanitation vs child mortality
The revised report contains 212 countries analysed.
Dashboard preview
![Final Dashboard](images/dashboard-final.png)
Power BI report
[View / Download Power BI Report — INSERT LINK]

📈 Key Findings
1. Child mortality has declined
The revised dashboard shows a downward global trend in average child mortality during the 2000–2024 period.
The displayed average child mortality value in the final dashboard is 3.59.
[INSERT YOUR FINAL INTERPRETATION OF THE TREND HERE]

2. Progress is uneven
The decline in child mortality is not uniform across countries.
The country comparison in the revised dashboard highlights substantial differences, with countries including Nigeria, Niger, Somalia and Chad appearing among the higher-mortality countries in the displayed ranking.
[INSERT FINAL COUNTRY/REGIONAL INSIGHT AFTER YOUR FINAL REVIEW]

3. Water and sanitation
The revised analysis examines the relationship between water/sanitation access and child mortality.
The dashboard reports an average water/sanitation value of 64.64 across the analysed data.
[INSERT FINAL CORRELATION VALUE AND INTERPRETATION FROM YOUR FINAL MODEL]

4. GDP per capita
The project examines the relationship between GDP per capita and child mortality using country-year observations.
The initial analysis produced a Pearson correlation of −0.22 between GDP per capita and child mortality.
However, this value belongs to the initial analytical version and should not automatically be presented as the final result of the revised 2000–2024 model.
[INSERT FINAL GDP–CMR CORRELATION FROM VERSION 2]

5. Health expenditure
Health expenditure was included as another contextual indicator.
The initial analysis reported a Pearson correlation of −0.52 between health expenditure and child mortality.
Again, this was generated under the original analytical setup.
[INSERT FINAL HEALTH EXPENDITURE–CMR CORRELATION FROM VERSION 2]

🔎 What Changed Between Version 1 and Version 2?
Area
Version 1
Version 2
Analytical period
1980–2011
2000–2024
Scope
Broad
Focused
Education
Included
Removed from final analysis
GDP
Included
Included
Health expenditure
Included
Included
Population
Contextual
Included
Water/sanitation
Included
Included
Data audit
Limited
Country-year completeness audit
Model
Exploratory
Rebuilt analytical model
Objective
Explore broadly
Produce a more defensible analysis

The first dashboard should therefore be viewed as an exploratory version, not simply a failed version.
The second dashboard represents the result of the project's data-quality reassessment.

💡 Lessons Learned
1. Start with the data, not the dashboard
One of my biggest lessons was that visualisation should come after understanding the structure and quality of the data.
A beautiful dashboard cannot correct poor data assumptions.

2. Define the grain early
Understanding what one row represents is fundamental.
For this project, the analytical grain became:
Country × Year
This made the integration and missing-value assessment much more systematic.

3. Missing data is an analytical problem
Missing observations are not simply something to remove.
They can change:
Sample size
Comparability
Correlations
Country rankings
Trend interpretation
Therefore, missingness needs to be investigated before analysis.

4. Scope reduction can improve an analysis
Initially, I wanted to include as many variables as possible.
The data forced me to reconsider that approach.
The final project became more focused because I removed variables that could not adequately support the revised analytical period.
More variables do not necessarily mean better analysis.

5. Correlation requires context
A correlation coefficient is useful for describing relationships, but it does not explain why those relationships exist.
This project reinforced the importance of distinguishing:
Association ≠ causation

6. Iteration is part of the analytical process
The first version of the project was not wasted work.
It exposed weaknesses in my approach.
The project therefore followed:
Explore
   ↓
Build
   ↓
Question
   ↓
Audit
   ↓
Revise
   ↓
Rebuild
   ↓
Analyse
That iteration became one of the most valuable outcomes of the project.

⚠️ Limitations
This project should be interpreted within several limitations.
Data completeness
The underlying datasets have different country and year coverage. Although a country-year audit was performed, missing observations remain an important consideration.
Country-level aggregation
Country-level analysis can hide substantial differences within countries.
Correlation
Pearson correlation measures linear association. It does not establish causality.
Confounding factors
Child mortality is influenced by many interacting factors that are not included in this analysis.
Data-source differences
The datasets were collected from different sources and may use different methodologies, definitions and reporting standards.
Analytical period
The final dashboard focuses on 2000–2024, meaning conclusions should not automatically be extrapolated to earlier periods.

🛠️ Tools Used
Primary tool
Microsoft Power BI
Power BI components
Power Query
DAX
Data modelling
Power BI visualisation
Geographic visualisation
Data profiling
Analytical techniques
Data cleaning
Data integration
Missing-value assessment
Country-year completeness auditing
Descriptive statistics
Trend analysis
Pearson correlation
Exploratory data analysis

📁 Repository Structure
I recommend structuring the GitHub repository like this:
child-mortality-analysis/
│
├── README.md
│
├── data/
│   ├── raw/
│   │   └── README.md
│   │
│   ├── cleaned/
│   │   └── README.md
│   │
│   └── audit/
│       └── README.md
│
├── powerbi/
│   ├── child-mortality-v1.pbix
│   └── child-mortality-final.pbix
│
├── documentation/
│   ├── data-dictionary.md
│   ├── methodology.md
│   └── data-quality-audit.md
│
├── images/
│   ├── dashboard-v1.png
│   ├── dashboard-final.png
│   ├── data-model.png
│   └── linkedin/
│       ├── story-01.png
│       └── carousel/
│
└── LICENSE

📚 Data Dictionary
Create a separate data-dictionary.md file containing:
Field
Description
Type
CountryCode
Standard country identifier
Text
CountryName
Country name
Text
Year
Observation year
Integer
ChildMortalityRate
Child mortality indicator
Numeric
GDP_Per_Capita
GDP per capita
Numeric
Health_Expenditure
Health expenditure indicator
Numeric
Population
Population
Numeric
Water_Sanitation
Water/sanitation indicator
Numeric
Region
World Bank regional classification
Text
IncomeGroup
Income classification
Text
Latitude
Country latitude
Numeric
Longitude
Country longitude
Numeric

Note: Add the exact definitions and units from each original data source before publishing.

🔗 Project Links
Power BI
[INSERT POWER BI PUBLICATION LINK]
GitHub Repository
[INSERT GITHUB REPOSITORY LINK]
LinkedIn Project Story
[INSERT LINK TO LINKEDIN STORY 1]
LinkedIn Final Findings Carousel
[INSERT LINK TO LINKEDIN STORY 2]
Portfolio
[INSERT SYMA TECH SOLUTIONS PORTFOLIO LINK]

📌 Related LinkedIn Posts
This project was developed publicly through a series of posts documenting the analytical process.
Project introduction
[INSERT LINK]
Data collection
[INSERT LINK]
Data cleaning & integration
[INSERT LINK]
Data quality audit
[INSERT LINK]
Version 1 — What went wrong
[INSERT LINK]
Version 2 — Revised analysis
[INSERT LINK]

👤 About the Author
Samuel Johnson
Data Analyst | Data Analytics & Business Intelligence
I work with data to transform complex datasets into practical insights through data cleaning, analysis, visualisation and business intelligence.
This project represents my approach to analytical work: question the data, validate the assumptions, build systematically and communicate the findings clearly.
LinkedIn: [INSERT LINK]
Portfolio: [INSERT LINK]
Email: [INSERT EMAIL]

📜 Disclaimer
This project is an independent analytical exercise intended for educational, portfolio and exploratory purposes.
The findings should not be interpreted as causal estimates or as formal public-health policy recommendations.
All interpretations are based on the datasets, definitions and analytical methods used in this project.

⭐ Final Reflection
This project started as an attempt to understand child mortality through data. It ended up teaching me something broader about data analytics.
The hardest part was not building the dashboard.
It was recognising when the dashboard was built on assumptions that needed to be questioned.
Going back to the drawing board was not a setback. It was part of the analysis.
Good analysis is not simply about producing an answer. It is about making sure the answer is worth trusting.

