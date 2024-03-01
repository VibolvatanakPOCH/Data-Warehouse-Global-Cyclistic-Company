![Architechture(1)](https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/2a4e778f-c55f-443b-9f1b-2ab0fbb90e5b)

# Global Cycling Company Data Warehouse 🚴‍♂️

Welcome to the Global Cycling Company Data Warehouse by AdventureWorks 2016!
From data collection to insightful reporting, our process involves gathering data from various sources, integrating it into a centralized platform, transforming it for analysis, storing it efficiently, applying advanced analytics techniques like Slowly Changing Dimension (SCD), generating insightful reports and visualizations, and continuously improving the warehouse to meet evolving business needs and technological advancements.

# Overview 🌟

The Global Cycling Company Data Warehouse project involves the following key components:

- **Data Consolidation**: Gathering data from transactional databases, external feeds, spreadsheets, and online sales platforms to centralize information for enhanced reporting and analytics.
- **Optimized Utilization**: Structuring and organizing data to ensure accessibility and facilitate insightful analysis.
- **Purposeful Insights**: Leveraging the data warehouse to gain deeper insights into sales trends, customer behavior, inventory management, and market dynamics.
- **Decision Support**: Empowering decision-makers with data-driven strategies for better forecasting, inventory optimization, targeted marketing, and predictive analytics.


# 💾 Dataset 

**AdventureWorks** is a database provided by Microsoft for free on online platforms. It is a product sample database initially published by Microsoft to demonstrate the supposed design of a SQL server database using SQL Server 2019. Here are some key points to know about AdventureWorks:
- AdventureWorks database supports a manufacturing MNC named Adventure Works Cycles.
- It is a sample Online Transaction Processing (or OLTP) database, a type of data processing where multiple transactions occur concurrently. Microsoft ships these with all of their SQL server products.

> This project uses the **Lightweight (LT) data**: a lightweight and pared-down version of the OLTP sample. [Download here](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver16&tabs=ssms)


# Architecture 🏗️

Utilizes a star schema design with a central fact table surrounded by dimension tables optimized for query performance and simplicity.

![schema](https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/5bc6218c-050c-442f-a444-6d480826cf0a)



# Tools and Technologies 🛠️

- **SQL Server Management Studio 2019 and MySQL (SSMS)**: For deployment and scheduling.
- **ODBC and OLEDB Drivers**: For database connections.
- **Visual Studio 2019 (ETL)**: To automate the extraction, transformation, and loading processes.
  
# Purpose and Impact 📈

The purpose of our data warehouse is to:
- Gain deeper insights into sales trends and customer behavior 
- Improve inventory management through better forecasting and optimization 
- Enhance decision-making processes with data-driven strategies 
- Facilitate targeted marketing campaigns based on customer segmentation 
- Enable predictive analytics to anticipate market changes and customer preferences 

# Benefits 🎉

By implementing the Global Cycling Company Data Warehouse, we expect to:
- Make informed, strategic decisions to drive business growth 
- Improve operational efficiency through data-driven insights 
- Enhance customer satisfaction by understanding their preferences and needs better 

# Challenges and Limitations ⚠️

While implementing the data warehouse, we may encounter challenges such as:
- Data quality issues leading to inaccurate analysis 
- Complex ETL processes requiring careful management 
- Integration of data from diverse sources may pose compatibility challenges 


# Buidling Phases 

## 1. Define Requirements 📝

- **Understand Business Goals**: Research our company to grasp our business model, focusing on sales trends, customer demographics, and inventory optimization.
- **Identify Data Sources**: Enumerate potential sources like transactional databases, external feeds, and spreadsheets.
- **Define Data Granularity and Architecture**: Determine the detail level for data (e.g., daily sales data) and outline the data warehouse architecture, including ETL workflow and schema design.

## 2. Documentation 📄

- Provide guidelines covering ODBC driver installation, source data extraction, and SQL script for DW creation, including key definitions and data mapping specifications.

## 3. ETL Workflow 🔄

- **Extract**: Identify and prepare data from MySQL and SQL Server 2019.
- **Transform**: Clean data, ensuring consistency and correct format, especially for keys.
- **Load**: Populate the Global Cycling Company Data Warehouse (DW), focusing on incremental data loading and critical transformations.

### Dimension Tables
<img width="914" alt="Dimension + slowly changing dimensions" src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/1cb6ac61-0c00-4910-be9b-c5342baf7111">

> Incremental Load and Full Load.

#### Currency
<img width="917" alt="dimcurrency" src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/3618d869-ed54-4810-9973-c1b19c2c1650">

> Look up to DWH to avoid data duplication.

### Slowly Changing Dimension (SCD)

<img width="908" alt="migratw to dimproduct" src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/b3078d9e-7969-4b18-b19e-ebaeb6e9059b">

> Split into three conditions: SCD 0, SCD 1, and SCD 2 based on the incoming data criteria of Dim.Product.

<img width="899" alt="updates sdc1" src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/3c2858a0-0888-4d64-b55e-c87cdb1f32f6">

<img width="918" alt="update scd 1 - sql query" src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/a3575d33-1c1c-45d3-817e-c2ff72d99c27">

> If the criteria meet SCD 1, it will update the existing data.

![image_2024-03-01_21-06-30](https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/374493a0-d59b-40a0-9939-ff7fa68d12c2)

> If the criteria meet SCD 2, it will insert new data and keep history.

### Fact Tables
<img width="919" alt="Fact" src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/bcd2ef29-1189-4359-b664-e44b1978d408">
 
> Full load and Truncate each time. 

#### Online Sale
<img width="909" alt="factonlinesales" src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/f69e6159-f0d5-4980-90cb-a64e70c5982b">
 
> explain

#### Store Sale
<img width="905" alt="factstoresale" src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/2c5106e9-3eb7-4866-b7b8-0e28c79e16c3">
 
> explain


## 4. Testing and Deployment 🛠️

- **Unit Testing**: Test ETL processes, data validation, and reporting.
- **Integration Testing**: Validate the entire data pipeline for correctness and logic.
- **Deployment**: Deploy the data warehouse in a production environment, monitoring performance and functionality.

#### ELT deployment
<img width="966" alt="deployment" src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/35d5e7b4-863f-4068-ae4d-459962bd0f78">

> explain

#### Execute Task Dimension
<img width="1093" alt="deploy-execute dimension " src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/1a4a00c8-9615-4c57-b518-594fa82fd2a4">

> explain


#### Execute Task Fact
<img width="1083" alt="deploy-execute fact" src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/91a37e6b-b1f2-42af-a589-3f781965dc50">

### Job Schedule 
#### Create Task for Dimension Table
<img width="1044" alt="deploy-task dimention" src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/52eda3d9-8215-45fc-b9c8-1f2a8969026c">

> explain

#### Create Task for Fact Table
<img width="1045" alt="deploy-task fact" src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/f2dd71ec-275b-4a2e-8f95-2b18bea8eb4a">

> explain 

#### Job schedule
<img width="621" alt="job-schedule" src="https://github.com/Vatanak8/Data-Warehouse-Global-Cyclistic-Company/assets/95983559/25e8fc58-c03d-4598-9253-83ad3e9c23d4">

> explain

# Future Productions 🔍🌟

With the data warehouse in place, we can expect to:
  - Gain deeper insights into sales trends and customer behavior.
  - Improve inventory management through better forecasting and optimization.
  - Enhance decision-making processes with data-driven strategies.
  - Facilitate targeted marketing campaigns based on customer segmentation.
  - Enable predictive analytics to anticipate market changes and customer preferences.


<h3 align="left">Connect with me:</h3>
<p align="left">
<a href="https://www.linkedin.com/in/vibolvatanak-poch-507007157/" target="_blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="LinkedIn" height="30" width="40" /></a>
<a href="https://medium.com/@pochvibolvatanak" target="_blank"><img align="center" src="https://simpleicons.org/icons/medium.svg" alt="Medium" height="30" width="40" /></a>
<a href="https://t.me/VibolVatanak" target="_blank"><img align="center" src="https://upload.wikimedia.org/wikipedia/commons/8/82/Telegram_logo.svg" alt="Telegram" height="30" width="40" /></a>
</p>

For further inquiries or to discuss potential collaborations, please feel free to connect with me.
