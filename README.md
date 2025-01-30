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