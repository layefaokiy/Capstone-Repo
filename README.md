
## Predicting Startup Funding Success
=========================

### Executive Summary

### The Problem Area

**Interest:**
The primary interest of this project is to leverage data science techniques to predict the likelihood of startups securing funding. This is crucial as funding is a significant factor in the growth and success of startups. Many startups struggle to attract investment due to the lack of comprehensive evaluation tools that can provide insights into their funding potential.

**Challenges/Opportunities:**
- **Challenges:** Startups face high failure rates, with approximately 90% failing within the first 10 years. Securing funding is a critical hurdle, with less than 1% of startups obtaining seed funding and around 0.05% receiving Series A funding. The unpredictability of the funding landscape poses a significant challenge for both startups and investors.
- **Opportunities:** There is an opportunity to utilize data science and machine learning to develop a predictive model that can provide startups with actionable insights into their funding potential. This model can also help investors identify promising ventures, thereby optimizing their investment decisions.

### The User

**Who Experiences These Problems?**
- **Startup Founders:** They need insights to improve their chances of securing funding and to understand the factors that influence their funding potential.
- **Investors:** They need tools to identify high-potential startups and make informed investment decisions, thereby reducing risks and maximizing returns.

**Benefits:**
- **For Startups:** Increased chances of securing funding by understanding investor preferences and improving their business strategies.
- **For Investors:** Enhanced ability to identify promising startups, leading to optimized investment portfolios and reduced risks.

### The Big Idea

**How Machine Learning Can Help:**
Machine learning algorithms can analyze historical funding data, market trends, and other relevant factors to predict the likelihood of a startup securing funding. This data-driven approach can provide more accurate and reliable predictions compared to traditional methods.

**Previous Approaches:**
Traditional methods of evaluating funding potential often rely on subjective judgments and limited data analysis. In contrast, machine learning models can process large datasets and uncover hidden patterns and insights that can significantly improve prediction accuracy.

### The Impact

**Societal or Business Value:**
- **For Startups:** Improved funding success rates lead to higher innovation and economic growth.
- **For Investors:** Better investment decisions result in optimized portfolios with better returns and reduced risks.

**Quantification:**
- **Success Rates:** Potential increase in the percentage of startups securing funding.
- **Economic Growth:** Enhanced startup success rates contribute to job creation and technological advancements.

### The Data

**Overview of Datasets:**
1. **Investments Data (investments.csv):** This dataset captures details about investment rounds, including the amounts raised and characteristics of the startups involved.
   - **Key Fields:** `funding_round_id`, `funded_object_id`, `investor_object_id`, `created_at`, `updated_at`
2. **People Data (people.csv):** This dataset contains information about individuals, including demographics and roles within the organization.
   - **Key Fields:** `object_id`, `first_name`, `last_name`, `birthplace`, `affiliation_name`
3. **Offices Data (offices.csv):** This dataset provides information about the organizational structure, including various offices and their attributes.
   - **Key Fields:** `object_id`, `office_id`, `description`, `region`, `address1`, `address2`, `city`, `zip_code`, `state_code`, `country_code`, `latitude`, `longitude`, `created_at`, `updated_at`
4. **Degrees Data (degrees.csv):** This dataset includes educational background information, which might correlate with the success of securing startup funding.
   - **Key Fields:** `object_id`, `degree_type`, `subject`, `institution`, `graduated_at`, `created_at`, `updated_at`
5. **Relationships Data (relationships.csv):** This dataset details the connections between people, indicating potential networking effects within the startup ecosystem.
   - **Key Fields:** `relationship_id`, `person_object_id`, `relationship_object_id`, `start_at`, `end_at`, `is_past`, `sequence`, `title`, `created_at`, `updated_at`
6. **Funding Rounds Data (funding_rounds.csv):** This dataset includes detailed information about various funding rounds that startups have gone through.
   - **Key Fields:** `id`, `funding_round_id`, `object_id`, `funded_at`, `funding_round_type`, `funding_round_code`, `raised_amount_usd`, `raised_currency_code`, `pre_money_valuation_usd`, `post_money_valuation_usd`, `participants`, `is_first_round`, `is_last_round`, `source_url`, `source_description`, `created_by`, `created_at`, `updated_at`

7. **Objects Data (objects.csv)**: 
   - This dataset contains information about various objects related to startups and their attributes.
   - **Key Fields**: `object_id`, `name`, `category_code`, `status`, `founded_at`, `closed_at`, `domain`, `homepage_url`, `city`, `region`, `state_code`, `country_code`, `latitude`, `longitude`, `created_at`, `updated_at`

**Data Quality Concerns:**
- **Missing Values:** Identified and handled missing values in key fields.
- **Duplicates:** Checked for and removed duplicate entries.
- **Data Types:** Ensured correct data types for each field.

**Preliminary EDA Findings:**
- **Univariate Analysis:** Distribution of funding amounts and acquisition values.
- **Bivariate Analysis:** Relationships between funding rounds and total funding amounts.
- **Correlations:** Initial correlation analysis to identify key relationships between variables.

**Data Dictionary:**

#### Investments Data
| Field Name       | Description                                  |
|------------------|----------------------------------------------|
| funding_round_id | Unique identifier for the funding round      |
| funded_object_id | Unique identifier for the funded entity      |
| investor_object_id | Unique identifier for the investor        |
| created_at       | Date when the record was created             |
| updated_at       | Date when the record was last updated        |

#### People Data
| Field Name       | Description                                  |
|------------------|----------------------------------------------|
| object_id        | Unique identifier for the individual         |
| first_name       | First name of the individual                 |
| last_name        | Last name of the individual                  |
| birthplace       | Birthplace of the individual                 |
| affiliation_name | Name of the organization the individual is affiliated with |

#### Offices Data
| Field Name       | Description                                  |
|------------------|----------------------------------------------|
| object_id        | Unique identifier for the office             |
| office_id        | Unique identifier for the office             |
| description      | Description of the office                    |
| region           | Region where the office is located           |
| address1         | First line of the office address             |
| address2         | Second line of the office address            |
| city             | City where the office is located             |
| zip_code         | ZIP code of the office location              |
| state_code       | State code where the office is located       |
| country_code     | Country code where the office is located     |
| latitude         | Latitude of the office location              |
| longitude        | Longitude of the office location             |
| created_at       | Date when the office record was created      |
| updated_at       | Date when the office record was last updated |

#### Degrees Data
| Field Name       | Description                                  |
|------------------|----------------------------------------------|
| object_id        | Unique identifier for the degree             |
| degree_type      | Type of the degree                           |
| subject          | Subject of the degree                        |
| institution      | Institution where the degree was obtained    |
| graduated_at     | Graduation date                              |
| created_at       | Date when the degree record was created      |
| updated_at       | Date when the degree record was last updated |

#### Relationships Data
| Field Name       | Description                                  |
|------------------|----------------------------------------------|
| relationship_id  | Unique identifier for the relationship       |
| person_object_id | Unique identifier for the individual         |
| relationship_object_id | Unique identifier for the related entity |
| start_at         | Start date of the relationship               |
| end_at           | End date of the relationship (if applicable) |
| is_past          | Indicator if the relationship is in the past |
| sequence         | Sequence number of the relationship          |
| title            | Title of the individual in the relationship  |
| created_at       | Date when the relationship record was created|
| updated_at       | Date when the relationship record was last updated |


#### Funding Rounds Data
| Field Name             | Description                                  |
|------------------------|----------------------------------------------|
| id                     | Unique identifier for the record             |
| funding_round_id       | Unique identifier for the funding round      |
| object_id              | Unique identifier for the funded entity      |
| funded_at              | Date when the funding was secured            |
| funding_round_type     | Type of funding round (e.g., series-a, series-b) |
| funding_round_code     | Code of the funding round                    |
| raised_amount_usd      | Amount raised in USD                         |
| raised_currency_code   | Currency code of the raised amount           |
| pre_money_valuation_usd| Pre-money valuation in USD                   |
| post_money_valuation_usd| Post-money valuation in USD                 |
| participants           | Number of participants in the funding round  |
| is_first_round         | Indicator if this is the first round         |
| is_last_round          | Indicator if this is the last round          |
| source_url             | URL of the source                            |
| source_description     | Description of the source                    |
| created_by             | Creator of the record                        |
| created_at             | Date when the record was created             |
| updated_at             | Date when the record was last updated        |

### Objects Data

| Field Name          | Description                                                      |
|---------------------|------------------------------------------------------------------|
| id                  | Unique identifier for the object                                 |
| entity_type         | Type of entity (e.g., company, person)                           |
| entity_id           | Identifier for the entity                                        |
| parent_id           | Identifier for the parent entity, if applicable                  |
| name                | Name of the object                                               |
| normalized_name     | Normalized version of the name                                   |
| permalink           | URL-friendly version of the name                                 |
| category_code       | Category code classifying the type of object                     |
| status              | Current status of the object (e.g., active, closed)              |
| founded_at          | Date when the object was founded                                 |
| closed_at           | Date when the object was closed, if applicable                   |
| domain              | Domain name of the object’s website                              |
| homepage_url        | URL of the object's homepage                                     |
| twitter_username    | Twitter username of the object                                   |
| logo_url            | URL of the object's logo                                         |
| logo_width          | Width of the object's logo                                       |
| logo_height         | Height of the object's logo                                      |
| short_description   | Short description of the object                                  |
| description         | Detailed description of the object                               |
| overview            | Overview of the object                                           |
| tag_list            | List of tags associated with the object                          |
| country_code        | Country code where the object is located                         |
| state_code          | State code where the object is located                           |
| city                | City where the object is located                                 |
| region              | Region where the object is located                               |
| first_investment_at | Date of the first investment made by the object                  |
| last_investment_at  | Date of the last investment made by the object                   |
| investment_rounds   | Number of investment rounds the object has participated in       |
| invested_companies  | Number of companies the object has invested in                   |
| first_funding_at    | Date of the first funding received by the object                 |
| last_funding_at     | Date of the last funding received by the object                  |
| funding_rounds      | Number of funding rounds the object has received                 |
| funding_total_usd   | Total amount of funding received by the object in USD            |
| first_milestone_at  | Date of the first milestone achieved by the object               |
| last_milestone_at   | Date of the last milestone achieved by the object                |
| milestones          | Number of milestones achieved by the object                      |
| relationships       | Number of relationships the object has                           |
| created_by          | Identifier of the user who created the record                    |
| created_at          | Timestamp when the record was created                            |
| updated_at          | Timestamp when the record was last updated                       |


### Next Steps

**Data Processing:**
- **Data Sources**: Multiple datasets from Crunchbase including funding rounds, startup information, and founder details.
   - **Preprocessing Steps**:
     - Merging datasets based on common keys.
     - Handling missing values and duplicates.
     - One-hot encoding categorical variables.
     - Scaling numeric features.
     - Addressing class imbalance using SMOTE.

**Feature Engineering:**
-    - One-hot encoding categorical variables.
     - Scaling numeric features.
     - Addressing class imbalance using SMOTE.

**Baseline Modeling:**
- - **Baseline Models**: Logistic Regression.
   - **Evaluation Metrics**: Accuracy, Precision, Recall, F1-Score.
   - **Results**: Logistic Regression achieved an accuracy of 95.26%.

**Iterative Refinement:**
- Continuously refine models based on performance and feedback. Incorporate additional data sources as needed.

**Dashboard Development:**
- Build an intuitive dashboard for users to access predictions and insights.

## Flowchart

graph TD
    A[Start] --> B[Data Collection]
    B --> C[Data Preprocessing]
    C --> D[Exploratory Data Analysis]
    D --> E[Feature Engineering]
    E --> F[Model Training]
    F --> G[Model Evaluation]
    G --> H{Results}
    H --> I[Report Findings]
    H --> J[Advanced Modeling]
    J --> K[Model Deployment]
    K --> L[End]

