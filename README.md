# Earthquake Azure Data Engineering Pipeline

## Overview and Architecture

### Business Case

Earthquake data is incredibly valuable for understanding seismic events and mitigating risks. Government agencies, research institutions, and insurance companies rely on up-to-date information to plan emergency responses and assess risks. With this automated pipeline, we ensure these stakeholders get the latest data in a way that’s easy to understand and ready to use, saving time and improving decision-making.

### Architecture Overview

This pipeline follows a modular architecture, integrating Azure’s powerful data engineering tools to ensure scalability, reliability, and efficiency. The architecture includes:

1.**Data Ingestion**: Azure Data Factory orchestrates the daily ingestion of earthquake data from the USGS Earthquake API.

2.**Data Processing**: Databricks processes raw data into structured formats (bronze, silver, gold tiers).

3.**Data Storage**: Azure Data Lake Storage serves as the backbone for storing and managing data at different stages.

4.**Data Analysis**: Synapse Analytics enables querying and aggregating data for reporting.

5.**Optional Visualization**: Power BI can be used to create interactive dashboards for stakeholders.

### Data Modeling

We implement a medallion architecture to structure and organize data effectively:

1.**Bronze Layer**: Raw data ingested directly from the API, stored in Parquet format for future reprocessing if needed.

2.**Silver Layer**: Cleaned and normalized data, removing duplicates and handling missing values, ensuring it’s ready for analytics.

3.**Gold Layer**: Aggregated and enriched data tailored to specific business needs, such as adding in country codes.

### Understanding the API

- The earthquake API provides detailed seismic event data for a specified start and end date.

- **Start Date**: Defines the range of data. This is dynamically set via Azure Data Factory for daily ingestion.

- **API URL**: https://earthquake.usgs.gov/fdsnws/event/1/

### Key Benefits

- **Automation**: Eliminates manual data fetching and processing, reducing operational overhead.

- **Scalability**: Handles large volumes of data seamlessly using Azure services.

- **Actionable Insights**: Provides stakeholders with ready-to-use data for informed decision-making.

## Step 1: Create an Azure Account

1.Sign up for an Azure account if you do not already have one.

## Step 2: Create a Databricks Resource

1.Create a Databricks resource in Azure.

2.Select the Standard LTS (Long Term Support) tier. Avoid using ML or other specialized tiers.

## Step 3: Set Up a Storage Account

1.Create a Storage Account and enable hierarchical namespaces in the advanced settings.

2.Navigate to the Storage Account resource:

- Go to Data Storage > Containers > + Containers.

- Create three containers: bronze, silver, and gold.

3.Configure access:

- Go to IAM > Add role assignment > Storage Blob Data Contributor.

- Click Next > Managed Identity > Select Members.

- Select Access Connector for Azure Databricks as the managed identity.

- Click Review + Assign.