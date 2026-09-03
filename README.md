# Child Mortality in a Changing World

### A data-driven analysis of global child mortality trends and selected socioeconomic and health-related determinants

> **Project Status:** Completed
> **Analysis Period:** 2000–2024
> **Tool:** Microsoft Power BI
> **Project Type:** Public Health Analytics · Exploratory Data Analysis · Data Integration
> **Author:** Samuel Johnson · Syma Tech Solutions

---

## 📌 Project Overview

Child mortality remains an important indicator of population health, socioeconomic development, and access to essential services.

This project explores how child mortality has changed across countries over time and examines its association with selected socioeconomic and health-related indicators.

The project initially began as a broad analysis covering **1980–2011**, incorporating a wider range of variables, including:

* Child mortality
* GDP per capita
* Population
* Health expenditure
* Water and sanitation
* Education
* Income group
* World Bank regions
* Country geolocation

The initial dashboard provided useful exploratory insights. However, a deeper review of the underlying datasets revealed substantial differences in **country and year coverage** across the variables.

Rather than continuing with an analytical model built on inconsistent coverage, I returned to the underlying data, performed a **country-year completeness assessment**, reconsidered the project scope, removed variables with insufficient coverage, rebuilt the integrated dataset, and developed a revised dashboard.

The final analysis focuses on **2000–2024** and examines child mortality alongside:

* GDP per capita
* Health expenditure
* Population
* Water and sanitation

The final analytical dataset contains **212 countries**.

---

## 🎯 Research Question

> **How has child mortality changed across countries over time, and what socioeconomic and health-related factors are associated with differences in child mortality?**

The project is intentionally **exploratory and descriptive**.

It does not attempt to establish causal relationships between child mortality and any individual factor. Instead, it investigates:

1. Global child mortality trends
2. Differences between countries and regions
3. Country-level patterns
4. Associations between child mortality and selected contextual indicators
5. The completeness and quality of the underlying data

---

## 🧭 Project Objectives

The project was designed around six main objectives.

### 1. Understand the trend

Examine how child mortality changed across the selected period.

### 2. Identify disparities

Explore differences in child mortality between countries and World Bank regions.

### 3. Examine potential determinants

Investigate associations between child mortality and:

* GDP per capita
* Health expenditure
* Population
* Water and sanitation

### 4. Assess data quality

Identify missing country-year observations before relying on integrated datasets for analysis.

### 5. Build an integrated analytical model

Combine multiple datasets into a country-year analytical structure suitable for Power BI.

### 6. Communicate the findings

Translate the analysis into an interactive dashboard and a public-facing data story.

---

# 🔄 Project Evolution

One of the most important aspects of this project is that it went through **two analytical versions**.

## Version 1 — Exploratory Analysis

The first version covered **1980–2011** and incorporated a broader range of explanatory variables.

The initial dashboard explored:

* Global child mortality trends
* Country rankings
* Regional differences
* GDP vs. child mortality
* Education vs. child mortality
* Water and sanitation vs. child mortality
* Health expenditure vs. child mortality
* Pearson correlation statistics

### Initial Dashboard

<img width="2075" height="1200" alt="Dashboard_01_page-0001" src="https://github.com/user-attachments/assets/5ddea7b8-5eeb-432f-b4cf-7404f6eedb07" />


---

## ⚠️ The Problem I Discovered

The first dashboard looked reasonable from a visual perspective.

However, during a deeper review of the underlying datasets, I discovered that the datasets did **not share consistent country and year coverage**.

This mattered because a merged dataset can appear structurally complete while individual variables have very different levels of availability.

The datasets differed in:

* Number of countries
* Observation periods
* Country-year combinations
* Missing-value patterns

Simply joining the datasets and proceeding to analysis could therefore produce misleading comparisons.

### The key lesson

> **A dashboard can look correct while the analytical foundation underneath it is incomplete.**

Instead of trying to fix the problem at the visualisation stage, I went back to the data.

---

# 🔍 Data Quality Assessment

The second phase of the project focused heavily on **data profiling and completeness assessment**.

The key unit of assessment became:

> **Country + Year**

For each determinant, I generated the expected country-year combinations and compared them with the observations actually available in the source dataset.

### Audit Logic

```text
Expected Country-Year Combinations
                ↓
            Left Join
                ↓
       Actual Observations
                ↓
        ┌───────┴───────┐
        ↓               ↓
    AVAILABLE         MISSING
```

This allowed missing observations to be identified systematically rather than discovering them only after building the dashboard.

---

# 📊 Datasets

The project initially considered the following datasets:

| Dataset             | Main Variables                      | Role                                   |
| ------------------- | ----------------------------------- | -------------------------------------- |
| Child Mortality     | Country, Year, CMR                  | Primary outcome                        |
| GDP per Capita      | Country, Year, GDP per capita       | Economic indicator                     |
| Health Expenditure  | Country, Year, Health expenditure   | Health-system indicator                |
| Population          | Country, Year, Population           | Demographic context                    |
| Water & Sanitation  | Country, Year, Water access         | Infrastructure/public-health indicator |
| Education           | Country, Year, Education indicators | Socioeconomic indicator                |
| Income Group        | Country, Income group               | Development classification             |
| World Region        | Country, Region                     | Geographic classification              |
| Country Geolocation | Country, Latitude, Longitude        | Geographic mapping                     |

## Data Sources

> **Note:** Exact source URLs should be added before publishing the repository.

* Child mortality: `https://data.unicef.org/topic/child-survival/under-five-mortality/`
* GDP per capita: `https://data.worldbank.org/indicator/NY.GDP.MKTP.CD`
* Health expenditure: `https://data.worldbank.org/indicator/SH.XPD.CHEX.GD.ZS`
* Population: `https://data.worldbank.org/indicator/SP.POP.TOTL`
* Water & sanitation: `[[INSERT SOURCE LINK]](https://ourworldindata.org/clean-water-sanitation)`
* Education: `https://ourworldindata.org/global-education`
* Income group: `https://data.worldbank.org/indicator/NY.GNP.MKTP.CD`
* World Bank regions: `https://ourworldindata.org/grapher/world-regions-according-to-the-world-bank?overlay=download-data`[New_Dashboard.pdf](https://github.com/user-attachments/files/31809572/New_Dashboard.pdf)


---

# 🔄 Scope Revision

Following the data-quality assessment, I concluded that the original scope was too broad for the available data.

The education dataset presented significant compatibility challenges because of differences in temporal structure and country coverage.

Rather than forcing every collected dataset into the analytical model, I narrowed the scope.

## Revised Analytical Period

> **2000–2024**

## Primary Outcome

> **Child Mortality Rate**

## Selected Contextual Variables

* GDP per capita
* Health expenditure
* Population
* Water and sanitation

This revision produced a more focused analytical framework and allowed greater attention to be placed on data comparability.

---

# 🧹 Data Cleaning & Preparation

Data cleaning and integration were performed using **Microsoft Power BI / Power Query**.

### Workflow

```text
Raw Datasets
     ↓
Data Profiling
     ↓
Column Standardisation
     ↓
Country Identification
     ↓
Year Standardisation
     ↓
Duplicate Checks
     ↓
Missing-Value Assessment
     ↓
Country-Year Audit
     ↓
Scope Revision
     ↓
Dataset Integration
     ↓
Analytical Fact Table
```

### Key Transformations

The datasets were standardised around common identifiers:

* `CountryCode`
* `CountryName`
* `Year`

Where possible, country-year observations were matched using:

```text
CountryCode + Year
```

This was preferred over relying solely on country names because country names can vary between datasets.

---

# 🧪 Data Quality Audit

The audit was conducted before building the final analytical model.

For a dataset covering 2000–2024, expected country-year observations were generated systematically.

For example:

```text
Country A × 2000
Country A × 2001
Country A × 2002
...
Country A × 2024

Country B × 2000
Country B × 2001
...
Country B × 2024
```

These expected observations were then compared against the actual source records.

Each country-year combination was classified as:

* **Available**
* **Missing**

This approach created a reproducible completeness assessment rather than relying on a simple null-value count after merging datasets.

---

# 🏗️ Data Model

The final analytical model was designed around a **country-year fact table**.

### Analytical Grain

> **One row represents one country in one year.**

Conceptually:

```text
                 DIM_DATE
                    │
                    │ Year
                    ▼
             FACT_CHILD_MORTALITY
                    │
          ┌─────────┼─────────┐
          │         │         │
         GDP      HEALTH     WATER
                    │
               POPULATION
                    │
                    ▼
              DIM_COUNTRY
```

### FACT_CHILD_MORTALITY

Core fields:

```text
CountryCode
Year
ChildMortalityRate
GDP_Per_Capita
Health_Expenditure
Population
Water_Sanitation
```

### DIM_COUNTRY

The country dimension contains contextual information such as:

```text
CountryCode
CountryName
Region
IncomeGroup
Latitude
Longitude
```

### DIM_DATE

Because the analysis is annual, the date dimension was intentionally kept simple:

```text
Year
```

---

# 📐 Analytical Methodology

The project primarily uses descriptive and exploratory analytical techniques.

## Descriptive Analysis

* Averages
* Country rankings
* Regional comparisons
* Summary statistics

## Time-Series Analysis

Child mortality was examined across the selected annual period to identify long-term trends.

## Geographic Analysis

Country-level mortality was visualised geographically using latitude and longitude.

## Association Analysis

Scatterplots and Pearson correlation were used to explore relationships between child mortality and selected contextual variables.

### Pearson Correlation

The Pearson correlation coefficient was used to quantify the strength and direction of linear association between two variables.

```text
              Σ(xᵢ - x̄)(yᵢ - ȳ)
r = ─────────────────────────────────
    √[Σ(xᵢ - x̄)² × Σ(yᵢ - ȳ)²]
```

Where:

* `x` = contextual variable
* `y` = child mortality rate
* `r` = Pearson correlation coefficient

---

# ⚠️ Analytical Constraint: Association ≠ Causation

The Pearson correlations in this project should be interpreted as **associations rather than causal relationships**.

For example:

> A negative correlation between GDP per capita and child mortality does not mean that increasing GDP per capita alone causes child mortality to fall.

Child mortality is influenced by multiple interacting factors, including:

* Healthcare access
* Nutrition
* Sanitation
* Education
* Poverty
* Infrastructure
* Maternal health
* Public policy
* Environmental conditions

The project therefore does **not** claim causal effects.

---

# 📊 Dashboard — Version 2

The final dashboard focuses on the **2000–2024** analytical period.

It contains:

* Global child mortality trend
* Country-level mortality comparison
* Geographic distribution
* GDP vs. child mortality
* Health expenditure vs. child mortality
* Population vs. child mortality
* Water/sanitation vs. child mortality

### Final Dashboard

<img width="2075" height="1200" alt="New_Dashboard_page-0001" src="https://github.com/user-attachments/assets/574168d2-9532-4cf0-a7bd-35dcc789661c" />


### Dataset Coverage

> **212 countries analysed**

### Power BI Report
<img width="2075" height="1200" alt="Dashboard_01_page-0003" src="https://github.com/user-attachments/assets/87832b37-c01f-44f4-9b25-b6f882021137" />

<img width="2075" height="1200" alt="New_Dashboard_page-0002" src="https://github.com/user-attachments/assets/84ac35df-c3eb-4832-b54f-6caf491bd354" />


---

# 📈 Key Findings

## 1. Child Mortality Has Declined

The revised dashboard shows a downward global trend in average child mortality during the **2000–2024** period.

The displayed average child mortality value in the final dashboard is:

> **3.59**
<img width="2075" height="1200" alt="New_Dashboard_page-0002" src="https://github.com/user-attachments/assets/7e8ea3c1-4fad-461c-9882-02cd2d6ad059" />

---

## 2. Progress Is Uneven

The decline in child mortality is not uniform across countries.

The country comparison highlights substantial differences, with countries including **Nigeria, Niger, Somalia, and Chad** appearing among the higher-mortality countries in the displayed ranking.

<img width="2075" height="1200" alt="New_Dashboard_page-0002" src="https://github.com/user-attachments/assets/dd7879d2-a8ee-4cad-8d77-b02bd30d4fb2" />


---

## 3. Water & Sanitation

The revised analysis examines the relationship between water/sanitation access and child mortality.

The dashboard reports an average water/sanitation value of:

> **64.64**

> **[INSERT FINAL CORRELATION VALUE AND INTERPRETATION FROM FINAL MODEL]**

---

## 4. GDP Per Capita

The project examines the relationship between GDP per capita and child mortality using country-year observations.

The initial analysis produced a Pearson correlation of:

> **r = −0.22**

However, this value belongs to **Version 1** and should not automatically be reported as the final result of the revised 2000–2024 model.

<img width="2075" height="1200" alt="Dashboard_01_page-0002" src="https://github.com/user-attachments/assets/d10d29f9-5ee4-410c-b2d3-bc5e9b26b2f7" />


---

## 5. Health Expenditure

Health expenditure was included as another contextual indicator.

The initial analysis reported:

> **r = −0.52**

This result was generated under the original analytical setup and should therefore be distinguished from the final Version 2 analysis.


---

# 🔎 Version 1 vs. Version 2

| Area               | Version 1       | Version 2                              |
| ------------------ | --------------- | -------------------------------------- |
| Analytical period  | 1980–2011       | **2000–2024**                          |
| Scope              | Broad           | **Focused**                            |
| Education          | Included        | **Removed**                            |
| GDP                | Included        | Included                               |
| Health expenditure | Included        | Included                               |
| Population         | Contextual      | Included                               |
| Water/sanitation   | Included        | Included                               |
| Data audit         | Limited         | **Country-year completeness audit**    |
| Model              | Exploratory     | **Rebuilt analytical model**           |
| Objective          | Explore broadly | **Produce a more defensible analysis** |

Version 1 should therefore be viewed as an **exploratory analytical stage**, rather than simply a failed attempt.

Version 2 represents the result of the project's data-quality reassessment and scope refinement.

---

# 💡 Lessons Learned

## 1. Start With the Data, Not the Dashboard

One of the biggest lessons from this project was that visualisation should come after understanding the structure and quality of the underlying data.

A beautiful dashboard cannot correct poor data assumptions.

---

## 2. Define the Grain Early

Understanding what one row represents is fundamental to analytical modelling.

For this project, the analytical grain became:

> **Country × Year**

This made data integration, completeness checks, and analysis much more systematic.

---

## 3. Missing Data Is an Analytical Problem

Missing observations are not simply values to remove.

Missingness can affect:

* Sample size
* Comparability
* Correlations
* Country rankings
* Trend interpretation

Therefore, missingness needs to be investigated before drawing conclusions.

---

## 4. Scope Reduction Can Improve an Analysis

The initial objective was to include as many relevant variables as possible.

However, the data demonstrated that more variables do not necessarily produce a stronger analysis.

Removing variables with insufficient compatibility resulted in a more focused analytical model.

> **More variables do not necessarily mean better analysis.**

---

## 5. Correlation Requires Context

A correlation coefficient is useful for describing relationships, but it does not explain why those relationships exist.

This project reinforced the importance of distinguishing:

> **Association ≠ Causation**

---

## 6. Iteration Is Part of the Analytical Process

The first version of the project was not wasted work.

It exposed weaknesses in the initial approach and created an opportunity to improve the analytical framework.

The project therefore evolved through:

```text
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
```

That iteration became one of the most valuable outcomes of the project.

---

# ⚠️ Limitations

Several limitations should be considered when interpreting this analysis.

### Data Completeness

The underlying datasets have different country and year coverage. Although a country-year audit was performed, missing observations remain an important consideration.

### Country-Level Aggregation

Country-level analysis can mask substantial variation within individual countries.

### Correlation

Pearson correlation measures linear association and does not establish causality.

### Confounding Factors

Child mortality is influenced by many interacting factors that are not included in this analysis.

### Data-Source Differences

The datasets were collected from different sources and may use different methodologies, definitions, and reporting standards.

### Analytical Period

The final dashboard focuses on **2000–2024**. Conclusions should therefore not automatically be extrapolated to earlier periods.

---

# 🛠️ Tools & Techniques

## Primary Tool

**Microsoft Power BI**

## Power BI Components

* Power Query
* DAX
* Data modelling
* Data visualisation
* Geographic visualisation
* Data profiling

## Analytical Techniques

* Data cleaning
* Data integration
* Missing-value assessment
* Country-year completeness auditing
* Descriptive statistics
* Trend analysis
* Pearson correlation
* Exploratory data analysis

---

# 📁 Repository Structure

```text
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
```

---

# 📚 Data Dictionary

A separate `data-dictionary.md` file should document the variables used in the final analytical model.

| Field                | Description                        | Type    |
| -------------------- | ---------------------------------- | ------- |
| `CountryCode`        | Standard country identifier        | Text    |
| `CountryName`        | Country name                       | Text    |
| `Year`               | Observation year                   | Integer |
| `ChildMortalityRate` | Child mortality indicator          | Numeric |
| `GDP_Per_Capita`     | GDP per capita                     | Numeric |
| `Health_Expenditure` | Health expenditure indicator       | Numeric |
| `Population`         | Population                         | Numeric |
| `Water_Sanitation`   | Water/sanitation indicator         | Numeric |
| `Region`             | World Bank regional classification | Text    |
| `IncomeGroup`        | Income classification              | Text    |
| `Latitude`           | Country latitude                   | Numeric |
| `Longitude`          | Country longitude                  | Numeric |

> **Note:** Exact definitions, units, and source-specific methodologies should be added before publishing the repository.

---

# 🔗 Project Links

### Power BI

`[INSERT POWER BI PUBLICATION LINK]`

### GitHub Repository

`[INSERT GITHUB REPOSITORY LINK]`

### LinkedIn Project Story

`[INSERT LINK TO LINKEDIN STORY 1]`

### LinkedIn Final Findings Carousel

`[INSERT LINK TO LINKEDIN STORY 2]`

### Portfolio

`[INSERT SYMA TECH SOLUTIONS PORTFOLIO LINK]`

---

# 📚 Related LinkedIn Posts

This project was developed publicly through a series of posts documenting the analytical process.

* **Project Introduction:** `[INSERT LINK]`
* **Data Collection:** `[INSERT LINK]`
* **Data Cleaning & Integration:** `[INSERT LINK]`
* **Data Quality Audit:** `[INSERT LINK]`
* **Version 1 — What Went Wrong:** `[INSERT LINK]`
* **Version 2 — Revised Analysis:** `[INSERT LINK]`

---

# 👤 About the Author

## Samuel Johnson

**Data Analyst | Data Analytics & Business Intelligence**

I work with data to transform complex datasets into practical insights through data cleaning, analysis, visualisation, and business intelligence.

This project reflects my approach to analytical work:

> **Question the data. Validate the assumptions. Build systematically. Communicate the findings clearly.**

**LinkedIn:** `[INSERT LINK]`
**Portfolio:** `[INSERT LINK]`
**Email:** `[INSERT EMAIL]`

---

# 📜 Disclaimer

This project is an independent analytical exercise intended for educational, portfolio, and exploratory purposes.

The findings should not be interpreted as causal estimates or formal public-health policy recommendations.

All interpretations are based on the datasets, definitions, and analytical methods used in this project.

---

# ⭐ Final Reflection

> **This project started as an attempt to understand child mortality through data. It ended up teaching me something broader about data analytics.**

> The hardest part was not building the dashboard.

> It was recognising when the dashboard was built on assumptions that needed to be questioned.

> Going back to the drawing board was not a setback. It was part of the analysis.

> **Good analysis is not simply about producing an answer. It is about making sure the answer is worth trusting.**
