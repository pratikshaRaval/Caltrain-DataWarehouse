# Caltrain-DataWarehouse
Business Intelligence and Data Warehousing Project to analyze Caltrain Ridership in the Bay Area 
- Tools: MySQL, Pentaho Integration Tool (ETL), Tableau, AWS Redshift, S3 Storage 

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
![SwimLane](SwimLane.png)

### Analytical Measures
#### Lead Measures:
1. The most popular fare types per quarter (over payment amount)
2. The most popular cities per quarter
3. The most popular payment type per quarter
4. Average ticket orders per day.
5. Highest payment amount for the fare type – which fare type that brought the most total payment
#### Lag Measures:
1. Finding payment amount generated for a quarter/year.
2. Average of ticket orders and payment amount per year.
3. Rider type differentiation based on the number of ticket counts – Adult, Disables, Medicare, Senior and Youth.

### Descriptive Analysis:
1. What time and day are busiest and why?
2. What events cause spikes? (holidays, Christmas, etc.)
3. Rider type age distribution
4. Which are the most popular cities?
5. Revenue generated by the top 5 locations
### Predictive Analysis:
1. Revenue forecast for the upcoming days.
2. Payment and ticket count forecast for the next 2 quarters.
3. The total revenue that can be generated with or without the discount?
4. What procedures are they doing to cope with the COVID pandemic?

# Phase 2: Data Modeling

### OLTP Schema Design
OLTP systems record business interactions as they occur in the day-to-day operation of the organization. This OLTP schema is designed to have the below tables: Employee, Train, Train_Schedule, Station, Ticket
![OLTP](OLTP_final.jpeg)

### OLAP Schema Design
Data warehouse tables: This will be the main Fact & Dimension tables. This Schema will help in planning and problem-solving.
![OLAP](OLAP_Final.png)

# Phase 3: ETL Implementation
Data Sources used for implementation
1. MySQL Database
2. CSV
3. Text File
4. Excel

### Data Sets
A portion of the live data provided by Caltrain Business Authorities (https://www.caltrain.com/main.html) We also used mockaroo.com to manually create employee
and ticket data.
#### Part 1: Extract data from data sources to OLTP schema
Order of generating data in tables in the OLTP schema, caltrain.
Table creation for caltrain schema in below order:
1. Employee
2. Station
3. Train
4. Ticket
5. Train Schedule
#### ETL Transformations for caltrain schema
Data Source 1: Load data into employee table from employee data csv file. Split the name field from the data source and load as first name and last name into the employee table.
### Data Source 1:
Load data into employee table from employee data csv file. Split the name field from the datasource and load as first name and last name into the employee table.
![ETL1](ETL1.png)

MySQL Result for Data Source 1: Sample of employee table with data shown below.
![SQL1](SQL1.png)

### Data Source 2:
Load data into station table from station data csv file.
![ETL2](Transformation2.png)

### Data Source 3:
Load data into train table from train data excel file.
![ETL3](ETL3.png)

MySQL Result for Data Source 3: Sample of train table with data shown below.
![SQL3](sql3.png)

### Data Source 4:
Load data into ticket table from ticket data excel file. Transformation does a lookup of the station id from the station table and loads station id as a
foreign key in the ticket table.
![ETL4](ETL4.png)

MySQL Result for Data Source 4: Sample of ticket table with data shown below.
![SQL4](SQL4.png)

### Data Source 5:
Load data into train_schedule table from train schedule data csv file.
![ETL5](ETL5.png)

## Part 2: Load data from the caltrain schema to the data warehouse schema
Order of generating data in tables in the data warehouse schema, caltrain_dw.
### Table creation for caltrain_dw schema in below order:
1. Date
2. Fare
3. Rider
4. Station
5. Ticket Payment
6. Ticket Purchase
7. Train Operation
8. Fact Caltrain Ticket
### ETL Transformations for caltrain_dw schema
## Dimension Tables
![Dim1](Dimension_ETL/Dim_ETL1.png)

![Dim2](Dimension_ETL/Dim_ETL2.png)

![Dim3](Dimension_ETL/Dim_ETL3.png)

![Dim4](Dimension_ETL/Dim_ETL4.png)

![Dim4-1](Dimension_ETL/Dim_SQL4.png)

![Dim5](Dimension_ETL/Dim_ETL5.png)

![Dim6](Dimension_ETL/Dim_ETL6.png)

![Dim7](Dimension_ETL/Dim_ETL7.png)

## Fact Table

![Dim8](Dimension_ETL/FactTable.png)

# Phase 4: Tableau Implementation

## Dashboard 1 – Lag Measures:
1. Finding payment amount generated for a quarter/year.
2. Rider type differentiation based on the number of ticket counts – Adult, Disables, Medicare, Senior and Youth.
3. Average of ticket orders and payment amount per year.
![Dashboard1](Tableau/LagMeasures.png)

## Dashboard 2 – Lead Measures
1. The most popular fare types per quarter
2. The most popular cities per quarter
3. The most popular payment type per quarter
4. Average ticket orders per day.
5. Highest payment amount for the fare type – which fare type that brought the most total payment
![Dashboard2](Tableau/LeadMeasures.png)

## Dashboard 3 – Descriptive Analytics
1. Total ticket count by rider types through 2018 – 2020
2. Passenger’s age distribution
3. Passenger’s locations by city
4. Payment received based on direction per year
![Dashboard3](Tableau/Descriptive.png)

## Dashboard 4- Predictive Analytics
1. Payment and total ticket count forecast for next 2 quarters
2. Total payment that is generated With and Without discounts
![Dashboard4](Tableau/Predictive.png)

# Conclusion
The business intelligence tools can integrate with many different sources such as csv, excel, text, aws and python scripts, including the data warehouse. The tools provide an easy way to query the data in order to analyze data for trends and insights. It can also make it easy to visualize and share data using dashboards and reports. These three steps, built on top of a good data warehouse foundation, will make it easier to follow through on the core promise of
business intelligence: providing everyone in your organization with the ability to understand and act on data. It’s good to learn that the visualization needs to present values to the shareholders, rather than just provide some fancy charts.

# Future Enhancements
For more precise predictions, we can include price metrics as raw data and give discounts on price metrics. We can also import weekend data to make comparisons with weekday data, and come up with more findings.

# Key Learnings
1. Keep a simple view of success
  i. We can easily add more elements(data, fields, tables) but keeping focus on the end goal and not straying too far away from scope and goal.
  ii. This is especially the case for our class time table but in the real world other factors like budget and resources can create challenges.
2. Be flexible
  i. We started specifically with clipper cards to be simple but we added to analyze all payment types caltrain accepts to get more diverse comparable data.
3. Good to have and must have, always build later
  i. Weekend data not included. Limitation of our analysis. Will add in the future knowing our work is done successfully for weekday
4. Transformations in pentaho was a challenge especially loading date string to date format
5. Keep in mind the stakeholders

Overall take time to understand the business in the analysis and planning phase as it will provide a sense of understanding and adjustment when met with challenges.
