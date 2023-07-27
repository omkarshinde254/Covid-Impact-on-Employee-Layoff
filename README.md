# Impact of COVID-19 and Layoff Rates on Company's Financial Performance and Employee Morale

## Table of Contents
- [Introduction](#introduction)
- [Problem](#problem)
- [Software Design and Implementation](#software-design-and-implementation)
- [Project Outcome](#project-outcome)
- [Data Sources](#data-sources)
- [Dependencies](#dependencies)
- [Usage](#usage)
- [Contributors](#contributors)
- [License](#license)

## Introduction
This repository contains the final project report for CS432/532, focusing on the impact of COVID-19 and layoff rates on a company's financial performance and employee morale. The project aims to analyze funding and acquisition rates of companies, investigate the vulnerability of low-funding companies to bankruptcy, and perform a data-driven analysis of COVID-19's impact on employee sentiments.

## Problem
The COVID-19 pandemic has caused significant disruptions to the global economy, leading to challenges for businesses of all sizes and industries. This project addresses the following key aspects:
1. Analyzing Funding and Acquisition Rates: Identify companies with high funding and low layoff rates during COVID-19, understanding their strategies for sustained growth and financial stability.
2. Investigating Low-Funding Companies' Vulnerability to Bankruptcy: Explore the impact of COVID-19 on low-funding companies with high layoff rates despite low COVID-19 cases.
3. Data-Driven Analysis of Employee Sentiments: Calculate employee morale based on funding, layoff rates, and COVID-19 cases to understand the impact on mental well-being.

## Software Design and Implementation
### NoSQL Database and Tools
- MongoDB: Used as the primary NoSQL database with data hosted on MongoDB Atlas Cluster.
- Python Libraries: 
  - pymongo: For interacting with MongoDB from Python.
  - scipy.stats: For statistical analysis.
  - matplotlib: For data visualization.
  - numpy: For numerical computations.

### Implemented Parts
1. Funding and Acquisition Analysis:
   - Objective: Identify companies that achieved sustained growth and maintained financial stability during the COVID-19 pandemic.
   - Steps:
     - Extracted data from the "covid_layoff_analysis" collection in the MongoDB database.
     - Filtered companies in Series A, Series B, Series C, Seed, and Growth stages with funding greater than 80% of the average funds raised by all companies.
     - Grouped the data by company, funding stage, funds raised, and industry.
     - Calculated COVID-19 cases, employee count, layoff count, and average layoff percentage for each group.
     - Filtered the data to include only companies with COVID-19 cases greater than or equal to 20,000, total employees less than or equal to 5,000, and average layoff percentage less than or equal to 5.
     - Sorted the data by average layoff percentage in ascending order and projected the relevant fields.
     - Formula used to calculate the company acquisition rate: `company_acquisition_rate = [((d['employee_total_count'] * (1 - (1/d['funds_raised'])) * (100 - d['avg_layoff_percentage'])) / d['covid_cases']) * 300 for d in result_1]`.

2. Vulnerability Analysis of Low-Funding Companies to Bankruptcy:
   - Objective: Assess the risk of bankruptcy for low-funding companies during the COVID-19 pandemic.
   - Steps:
     - Extracted data from the "covid_layoff_analysis" collection in the MongoDB database.
     - Filtered companies not in Seed, Series A, Series B, Series C, Acquired, Bankruptcy, Discontinued, or Growth stages with funding less than 80% of the average funds raised by other companies.
     - Grouped the remaining companies by company, funding stage, funds raised, and industry.
     - Calculated the sum of COVID-19 cases, maximum employee count, maximum layoff count, and average layoff percentage for each group.
     - Filtered the data to include only companies with no more than 20,000 COVID-19 cases and an average layoff percentage of at least 5.
     - Sorted the results by average layoff percentage in descending order and projected the relevant fields.
     - Formula used to calculate the company bankruptcy rate: `company_bankruptcy_rate = [((d['employee_total_count'] * (1 - (1/d['funds_raised'])) * (100 - d['avg_layoff_percentage'])) / d['covid_cases']) * 50 for d in result_2]`.

3. Data-Driven Analysis of COVID-19's Impact on Employee Sentiments:
   - Objective: Measure the impact of the pandemic, company performance, and layoff rates on employee morale.
   - Steps:
     - Extracted data from the "covid_layoff_analysis" collection in the MongoDB database.
     - Filtered companies not in Discontinued, Acquired, Bankruptcy, Growth, Private Equity, Private, or Public stages and with more than 0 employees.
     - Grouped the data by company, funding stage, and funds raised.
     - Calculated the sum of COVID-19 cases, maximum employee count, maximum layoff count, and average layoff percentage for each group.
     - Added a field for employee morale based on conditions derived from funds raised, layoff percentage, and COVID-19 cases.


## Project Outcome
The data analysis results are presented with easy-to-understand graphs and tables for each part of the analysis. The project provides valuable insights for businesses facing the challenges of the COVID-19 pandemic, helping them understand factors that contribute to financial instability and employee morale and providing strategies to navigate through uncertain times.

## Data Sources
- Layoff Dataset: [Layoffs.fyi](https://layoffs.fyi/)
- COVID-19 Dataset: [New York Times COVID-19 Data](https://github.com/nytimes/covid-19-data) (Data from 2020 to 2023)

## Dependencies
- MongoDB
- Python (>=3.6)
- pymongo
- scipy
- matplotlib
- numpy

## Usage
1. Clone the repository.
2. Required dependency would be installed as steps of collabrative environment.
3. Ensure you have access to the MongoDB Atlas Cluster and update the connection details in the Python code.
4. Run the Python scripts for each part of the analysis.

## Contributors
- Sapna Khatri
- Omkar Shinde

## License
This project is licensed under the [MIT License](LICENSE).

