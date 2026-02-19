# Estimates_on_the_use_of_water_2020
![Population Growth Chart](./chart%20(1).png)
🌍 Integrated Project: Access to Drinking Water
📌 Project Overview

This integrated project investigates access to safe and affordable drinking water worldwide, aligned with United Nations Sustainable Development Goal 6 (Clean Water and Sanitation).

The project demonstrates data analytics skills using spreadsheets, focusing on data understanding, cleaning, and preparation for analysis.

📂 Dataset Overview

The dataset used is WHO/UNICEF Joint Monitoring Programme (JMP) Estimates on the Use of Water (2020).

It contains 16 features (columns) describing population characteristics and water service levels for national, rural, and urban populations.

🧾 Dataset Features
### General Information

name – Country or area name

income_group – Country classification by income level

pop_n – National population size (in thousands)

pop_u – Urban population share (%)

### National Water Access Indicators

wat_bas_n – Share with at least basic water service (%)

wat_lim_n – Share with limited service (%)

wat_unimp_n – Share with unimproved service (%)

wat_sur_n – Share using surface water (%)

### Rural Water Access Indicators

wat_bas_r – Rural share with basic service (%)

wat_lim_r – Rural share with limited service (%)

wat_unimp_r – Rural share with unimproved service (%)

wat_sur_r – Rural share using surface water (%)

### Urban Water Access Indicators

wat_bas_u – Urban share with basic service (%)

wat_lim_u – Urban share with limited service (%)

wat_unimp_u – Urban share with unimproved service (%)

wat_sur_u – Urban share using surface water (%)

🧠 Understanding the Data

The dataset contains both categorical and numerical data:

Categorical: country name, income group

Numerical: population size and percentage shares

A total of 12 columns represent water service-level percentages.

📥 Importing the Data
### Step 1: Import into Google Sheets

Create a new blank spreadsheet in Google Sheets.

Download the dataset as a CSV file.

Import the CSV file into the spreadsheet.

### Step 2: Fix Separator Issues

Some rows use semicolons (;) instead of commas, causing incorrect column separation.

Solution:

Go to Data → Split text to columns

Select Semicolon (;) as the separator

Confirm the dataset has 16 columns (A–P)

🧹 Data Cleaning and Validation
### Step 1: Count Values per Row

Create a new column called value_cnt and use:

=COUNTA(A2:P2)


This counts the number of non-empty cells in each row.

### Step 2: Identify Incorrect Rows

Apply a filter to the value_cnt column.

Hide rows where value_cnt = 16 (correct rows).

Remaining rows are incorrectly imported.

### Step 3: Fix Incorrect Rows

Move misplaced values into the correct columns.

Use Split text to columns again where needed.

Remove the filter and confirm all rows have value_cnt = 16.

🎯 Project Objectives

Analyze global access to drinking water

Compare rural vs urban water access

Investigate access by population size and income group

Demonstrate spreadsheet-based data cleaning and analytics skills

🛠 Tools and Technologies

Google Sheets / Microsoft Excel

CSV data import

Spreadsheet functions (COUNTA, filters, split text to columns)

📊 Future Analysis

Visualize water access by region

Compare national vs rural annual rates of change

Analyze correlation between income level and water access

Create dashboards and charts for insights