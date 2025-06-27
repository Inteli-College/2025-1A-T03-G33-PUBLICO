# 1. Introduction

Rede Gazeta, one of the leading communication groups in Espírito Santo, faces significant challenges in pricing its advertising spaces in the radio environment. The current model shows little flexibility to accommodate seasonal variations, demand fluctuations, and external factors that directly influence inventory occupancy. This limitation can lead to revenue losses, idle media spaces, and difficulty in offering more competitive commercial conditions for different advertiser profiles.

## 1.1 Project Objective

The Dynamic Pricing with AI project, developed in partnership with Rede Gazeta, aims to create an intelligent and automated solution for dynamic pricing of advertising spaces on the group's radio stations. The proposal involves using predictive models based on machine learning to adjust advertising insertion prices in real-time, taking into account factors such as occupancy history, seasonality, projected demand, and external market variables.

With this, it is expected not only to optimize the occupancy of the advertising inventory but also to provide greater agility to the commercial team, offer more competitive conditions to advertisers, and increase Rede Gazeta's revenue. In the long term, the solution may also be integrated with other channels of the group, such as television, newspapers, and digital media, expanding the strategic impact of the proposal.

## 1.2 Problem Contextualization

Traditional pricing of media spaces at Rede Gazeta is predominantly fixed, not taking into account demand fluctuations over time, specific seasonality (such as high season on the coast or elections), or changes in advertiser behavior. This rigidity negatively impacts the profitability of the operation, as it results in idle spaces during periods of low demand and undervaluation during periods of high demand.

At the same time, there is a cultural and operational challenge: many advertisers and team members are accustomed to traditional negotiation practices and may resist the adoption of automated technologies. This resistance, coupled with the technological complexity of the proposed solution, required a period fully dedicated to a deep understanding of the business, involved users, and the commercial rules governing the current company model.

## 1.3 Approach and Methodology Used

To build upon the strategic foundation established in Module 1, Module 2 focused on the practical and technical execution of the proposed solution. The objective was to begin the system’s data operations and infrastructure setup. The approach followed was still grounded in agile Scrum methodology, executed over a new sequence of sprints, but now oriented towards hands-on data handling and system design.

The first set of activities involved exploratory data analysis (EDA), where the team worked with data from Rede Gazeta to perform data profiling, evaluate data quality and consistency, and define governance policies. This included the creation of a data dictionary, detection of missing or inconsistent values, and evaluation of field types and distributions. To facilitate automation and future scalability, we also defined a data pipeline, including the ETL process and implemented a scheduler to orchestrate tasks.

The team used Python and Pandas on Google Colab to analyze the datasets, plot relevant graphs and tables, and compare historical performance indicators. This process enabled a clearer understanding of seasonality, trends, and pricing behavior—key inputs for the future dynamic pricing model.

In parallel, the system's initial architecture was designed, with a focus on scalability and integration with cloud services. The structure was visualized in a preliminary diagram and explained in detail, incorporating AWS services as the foundation for future deployment. The architecture addresses not only data flow and storage but also prepares the system for future integration with analytics and dynamic pricing modules.

These developments ensured that the groundwork is technically solid and aligned with the business requirements and constraints identified in Module 1, enabling a smoother transition to implementation in the next stages, and move to Module 3.

# 2. Project Planning and Structure

## 2.1 Team and Roles

The project was developed by a team of four students from the Institute of Technology and Leadership (INTELI): Izabella Faria, Mariana Silva, Lívia Coutinho, and Mateus Neves. Although the Scrum methodology was adopted as the organizational base, with roles such as Product Owner, Scrum Master, and Developers initially defined, the team adopted a collaborative approach in which all members actively participated in the construction of strategic artifacts, with a clear and balanced division of responsibilities.

## 2.2 Sprint Roadmap

The development of Module 1 was divided into five bi-weekly sprints, organized as follows:

- **Sprint 1**: Alignment with stakeholders, review of available data structures, and kickoff of internal task organization.  
- **Sprint 2**: Exploratory data analysis and governance policies, including data profiling (types, missing values, duplicates), creation of a data dictionary, and definition of LGPD-aligned data handling protocols.  
- **Sprint 3**: ETL and transformation pipeline development, with automated ingestion, cleansing, formatting, and feature engineering of the datasets to prepare for ML usage.  
- **Sprint 4**: Architecture design with a strong focus on modularity and future cloud deployment (AWS), including the definition of pipeline flow, storage model, and system components.  
- **Sprint 5**: Initial discussion of backend structure, interfaces, and scheduling strategies; documentation of current progress and definition of next priorities.

Despite some scope adjustments throughout the module, the overall schedule was successfully met, maintaining the focus on delivering a set of artifacts to support the next project cycle.

## 2.3 Alignment with the Partner

Throughout the second module, the team maintained contact with a representative from Rede Gazeta to support the receipt, interpretation, and validation of the data provided. This collaboration was essential for the correct understanding of the structure and meaning of the datasets, including clarifications on business rules, internal data flows, and specific fields critical to the pricing strategy.  
The continuous interaction allowed the team to validate assumptions, resolve doubts regarding the format and origin of certain information, and adjust the data processing steps based on real operational constraints.

# 3 Data Governance

## 3.1 Policies Adopted

To ensure confidentiality and responsible use of the data provided by Rede Gazeta, the team established internal data governance policies aligned with the principles of Brazil's General Data Protection Law (LGPD). Although the datasets did not contain sensitive personal information such as CPF or email addresses, they did include identifiable company names and sales executives. These identifiers were handled with care and confidentiality to prevent any form of exposure or misuse.  
Data access was strictly restricted to the project team and the academic advisor, with all files stored locally and explicitly prohibited from being uploaded to public platforms (e.g., GitHub). When necessary, additional protection mechanisms, such as identifier masking or encryption, were considered to further safeguard confidential fields.

## 3.2 Structure and Documentation

Given the nature of the data (spreadsheets with records of advertising insertions), we adopted a structured documentation process. Each dataset received metadata annotations, and we tracked usage contexts to ensure transparency in processing. The data pipeline was designed to enforce minimization of data, processing only the fields strictly necessary for the analysis and modeling phases of the project.

## 3.3 Data Quality Evaluations

Even in the absence of direct access to a live database or data catalog, we carried out quality checks on the received files. These included:

- Detection of null or inconsistent values  
- Format standardization of fields (e.g., dates and text casing)  
- Deduplication of entries where necessary  
- Preliminary anomaly detection to flag outliers in insertion volumes or pricing  

These evaluations supported both the reliability of insights generated and the design of the data pipeline to be integrated in later stages.

# 4. Data Processing and Analysis

In this phase of the project, we conducted a series of exploratory data analysis (EDA) activities to better understand the structure, characteristics, and quality of the advertising insertion data provided by Rede Gazeta. This initial analysis was essential to identify potential issues, understand the behavior of key variables, and prepare the dataset for more advanced modeling in future modules.  
We performed the following main steps:

- **Dataset inspection**: Evaluated the dataset's dimensions, the types of variables present, and overall structure. This included commands to view the number of records and columns, data types, and completeness.  
- **Descriptive statistics**: Used to understand the distribution of both numerical and categorical variables, helping us identify trends, outliers, and inconsistencies in the data.  
- **Duplicate detection**: Assessed the presence of duplicate entries to ensure data integrity and avoid bias in future calculations and predictions.

These steps allowed the team to identify and document potential data cleaning needs, while also building an understanding of the dataset's behavior over time, including:

- Variation in insertion volumes  
- Patterns in advertiser behavior  
- Occupation trends across time slots

The code used for this analysis included basic Pandas functions such as `.shape`, `.info()`, `.describe()`, and `.duplicated()`, which enabled a clear and structured overview of the data.  
This stage laid the groundwork for defining the ETL flow, visualizations, and modeling logic that will be implemented in the next steps of the solution development.

# 5. ETL Pipeline

The Extract, Transform, Load (ETL) process was a key component of this project, ensuring that data from various sources was properly structured, cleaned, and prepared for analysis, reporting, and eventual deployment in a cloud-based environment.

## 5.1 Structure

The ETL pipeline was designed to handle semi-structured advertising insertion data provided by Rede Gazeta, initially in the form of spreadsheets and CSV files. Even though the solution is currently running in a local environment, the pipeline is modular and cloud-ready, allowing for a seamless transition to services like AWS S3, Glue, or Redshift in future stages.

## 5.2 Extraction

The extraction step collects advertising data from standardized local directories, scanning recursively for `.xlsx` and `.csv` files. All discovered files are loaded into a single unified Pandas DataFrame. This automated process ensures that data from multiple campaigns, broadcasting stations, and time periods is captured consistently and without manual intervention.

## 5.3 Transformation

Once extracted, the raw data is refined through a series of transformation steps:

- Column names are standardized to `snake_case`.  
- Duplicate records are removed.  
- Date fields are converted to datetime objects and enriched with derived attributes (year, month, weekday).  
- Original date columns are dropped to avoid redundancy.  
- Financial values are cleaned (e.g., removing thousand separators, standardizing decimal points), missing values are imputed using the median, and numeric fields are standardized using z-score normalization.  
- Textual fields (e.g., region, format, program, client, executive, status) undergo normalization — accent removal, lowercasing, and whitespace trimming.  
- Categorical fields are one-hot encoded using sparse matrices to optimize memory usage.

## Loading

The processed output is a sparse matrix (scipy.sparse) combining both numerical and categorical features. While currently not connected to AWS cloud services, the structure is optimized for performance and scalability. It is ready to support downstream applications such as:

- Machine Learning models  
- Revenue dashboards  
- Campaign performance reports

Additionally, the pipeline design supports integration with orchestration tools and job schedulers, laying the foundation for future automation via cloud-native services like AWS Step Functions, Lambda, or Apache Airflow.

# 6. System Architecture

The initial architectural design was developed to ensure clarity, scalability, and ease of future integration with cloud infrastructure — specifically AWS services. It reflects the logical structure of the system, connecting key components from data ingestion to frontend delivery.

## 6.1 Initial Design and Decisions

The architecture is composed of five main layers:

- **Data Governance Layer**: Responsible for ensuring responsible data handling and visibility. It includes data visualization tools and supports governance strategies aligned with privacy laws (e.g., LGPD).  
- **Data Pipeline**: Centralized ingestion and transformation of both real-time and historical data. It prepares inputs for analytics and forecasting modules.  
- **Database Layer**: Designed with modular support for both PostgreSQL and Google BigQuery. The dual compatibility allows for flexibility in choosing between relational databases and scalable analytics engines.  
- **Machine Learning / Analytics**: Consumes processed data to generate demand forecasts and pricing suggestions. The output can be used for reporting, dashboards, and direct decision support.  
- **Backend/API + Frontend**: A Python-based API bridges the data/ML layers with a user-facing dashboard. The interface enables visualization and interaction with model outputs and forecasts.

## 6.2 Cloud Integration (Focus on AWS)

While the current system operates in a local or semi-cloud setup, it was designed with AWS-native services in mind:

- S3 for centralized storage of raw and processed data.  
- AWS Glue or Apache Airflow on MWAA for orchestrating ETL jobs.  
- Amazon SageMaker for training and hosting ML models.  
- Amazon RDS (PostgreSQL) for transactional storage.  
- Amazon QuickSight or Looker Studio (via BigQuery) for visualization.  
- AWS Lambda + API Gateway to serverlessly expose Python APIs.  
- Amazon CloudWatch for monitoring and logs.

This design ensures the solution is portable to a cloud-native environment with minimal changes.

## 6.3 Scalability and Modularity

The architecture was intentionally structured with modularity in mind:

- Each module (ETL, ML, API, frontend) can be independently deployed or scaled.  
- ML modules are decoupled from preprocessing logic, allowing reuse across projects or services.  
- The database layer supports both vertical (PostgreSQL) and horizontal (BigQuery) scaling strategies.  
- The system can evolve to include real-time data ingestion (e.g., using Kinesis or Kafka) if necessary.

This modular, loosely-coupled design not only supports easier maintenance but also allows for iterative development — integrating new models, external APIs, or analytics dashboards with minimal rework.

# 8. Learnings and Adjustments

## 8.1 Challenges Encountered

Throughout the second phase of the project, we faced several practical and technical challenges that required flexibility and strategic problem-solving:

- **Data Accessibility and Confidentiality**: Initial delays in accessing the datasets limited early hands-on experimentation. Additionally, once received, the data contained sensitive identifiers, which demanded strict internal data governance policies to comply with LGPD standards.  
- **Heterogeneity and Inconsistency in Data**: The structure of advertising insertion records varied across files, requiring extensive normalization efforts during the transformation stage.  
- **Absence of a Centralized Data Source**: Without a data lake or centralized system from the client, automated ingestion had to rely on local directory traversal and preprocessing logic tailored to ad-hoc Excel and CSV files.

## 8.2 Adaptations Made

To address these challenges and ensure continued progress:

- We implemented a local ETL pipeline capable of recursively ingesting and transforming heterogeneous data sources, preparing them for analysis and future cloud migration.  
- Data masking and minimization techniques were applied to ensure compliance with governance requirements, while still allowing for exploratory and statistical analysis.  
- To mitigate the lack of structured cloud infrastructure, we simulated key AWS components (e.g., storage, orchestration, model serving) to define a modular and scalable architecture that can be deployed when cloud access is granted.  
- Additional effort was invested in producing documentation and architectural designs, anticipating a seamless transition to production environments in the future.

## 8.3 Insights Gained

This module provided significant insights, both technical and strategic:

- The importance of data readiness became clear early on; governance and standardization are not only legal or ethical concerns, but essential enablers for analytics and machine learning.  
- The hands-on process of building a custom ETL pipeline revealed nuances in the data structure and commercial logic of the radio industry that were not evident during theoretical planning.  
- Frequent collaboration with the client—even in a limited capacity—proved essential to clarify assumptions, validate interpretations, and align expectations.  
- Finally, this phase reinforced the value of modular thinking, ensuring that the components developed today remain useful and scalable as the project matures in future modules.

# 8. Next Steps / Module 3 Preview

During this module, we had to reprioritize several activities due to challenges in accessing, understanding, and validating the dataset, as well as the effort required to ensure data governance and prepare the technical foundation for the system. As a result, some components originally planned for Module 2 will now be addressed in Module 3.

### Focus for Module 3

The next module will concentrate on delivering the core intelligence of the system, with emphasis on:

- **Model Development**: Training, validation, and deployment of forecasting models and the pricing engine, using the cleaned and structured dataset prepared in this module.  
- **Integration of Pricing Engine**: Incorporating the dynamic pricing logic into a modular architecture that allows for future experimentation and adjustments based on user feedback and business objectives.  
- **API and Front-End Planning**: Designing and starting the implementation of user-facing components, particularly the API for serving recommendations and the interface for monitoring results, supporting decision-making by the commercial team.


