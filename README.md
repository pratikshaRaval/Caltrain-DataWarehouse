# Caltrain-DataWarehouse
Business Intelligence and Data Warehousing Project to analyze Caltrain Ridership in the Bay Area

## Project Summary
### Problem Statement
Caltrain is one of the busiest commuter rail systems in the San Francisco Bay Area and demand for its service is growing. Caltrain already provides a convenient and cost-effective alternative to driving, connecting passengers' jobs and housing in San Francisco, San Mateo, and Santa Clara counties. In 20 years, the Bay Area’s population is expected to grow by more than 40%, adding 2.4 million residents and 1.3 million jobs. The management team can better prepare itself for the COVID pandemic and make better business decisions using this analysis.
### Solution
The Caltrain IT Operations team has created a data warehouse to import data sources provided by Caltrain Business Plan. Our first dashboard provides lag measures, which show the payment trend as well as the average ticket count of fare types. The second dashboard shows the lead measures, it presents the information of payment vs fare type, city, and payment type. The last two dashboards provide information about the passenger segmentation overpayment amount by rider type, locations, and direction, as well as the forecast of total payment, and prediction of total payment with and without discounts.
### Technical Overview
Data warehouse implementation is done by designing a star schema with one fact table and some conformed dimensions. MySQL database is used for on-premise data injection. The Fare Dimension table has been implemented as Slowly Changing Dimension Type 2. Pentaho has been used to extract, transform, and load data. We used Tableau to create the dashboards to better visualize the business process. There are 4 phases in this project.
They are:
1. Business Analysis
2. Data Modeling
3. ETL Implementation
4. Tableau Implementation

# Phase 1: Business Analysis
In this phase, we identified the business needs and provided solutions to business problems. The solutions consist of process improvement, strategic planning to incur profits, and growth of the organization. The Business Scenario includes the details of Caltrain Business, the process and operation flow of the business, swim lane diagram, lead measures, lad measures, and Analytical use cases (Descriptive and Predictive Analysis).
### Key Information
Stakeholders: John (passenger), the conductor, the cleaning team
Service: Cal train experience
Infrastructure : Clipper card machine, Computer/Phone, Ticket Scanner, Cleaning tools
Additional Information: Cal train stations
Timeline: Arrived at 4 PM and left at 4:30 PM

### Swim Lane Diagram

