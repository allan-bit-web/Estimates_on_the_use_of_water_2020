# Estimates_on_the_use_of_water_2020

🌍 Integrated Project: Access to Drinking Water
📌 Project Overview

This integrated project investigates access to safe and affordable drinking water worldwide, aligned with United Nations Sustainable Development Goal 6 (Clean Water and Sanitation).

The project demonstrates data analytics skills using spreadsheets, focusing on data understanding, cleaning, and preparation for analysis.

📂 Dataset Overview

The dataset used is WHO/UNICEF Joint Monitoring Programme (JMP) Estimates on the Use of Water (2020).

It contains 16 features (columns) describing population characteristics and water service levels for national, rural, and urban populations.

🧾 Dataset Features
## A. Becoming familiar with the dataset.
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

## B. Importing the Data
### Step 1: Import into Google Sheets

Import the CSV file into the spreadsheet.

### Step 2: Fix Separator Issues

We observe that some rows use semicolons (;) as separators instead of commas as the rest, causing incorrect column separation.

Solution:

Go to Data → Split text to columns

Select Semicolon (;) as the separator

Confirming that the dataset has 16 columns (A–P)

Isolate and fix the incorrectly imported cells

## Data Cleaning and Validation
### Step 1: Count Values per Row

We create a new column called value_cnt and use:

=COUNTA(A2:P2) - counts regardless of whether the value is a text or a number


This counts the number of non-empty cells in each row.

### Step 2: Identify Incorrect Rows

Apply a filter to the value_cnt column.

Hide rows where value_cnt = 16 (correct rows).

Remaining rows are incorrectly imported.( 5 are 15)

### Step 3: Fix Incorrect Rows

Move misplaced values into the correct columns.

NB:this can overwrite adjacent cells so we add a column to the left,then cut and move cells to correct column then delete the excess column we had added.

Use Split text to columns again where needed.

Remove the filter and confirm all rows have value_cnt = 16.

NB:FREEZE ROW 1:CLICK ROW ONE AND RIGHT CLICK - VIEW MORE ROW ACTION - FREEZE UP TO ROW 1

## C. Investigating population size

### Research Questions

How does the dataset population compare to the estimated world population?

How does the urban population share compare to the rural population?

In 2020, the estimated global population was 7.821 billion, with 55% living in urban areas.(4.30155 billion living in urban areas)

## A. Comparing Dataset Population to Global Estimates
### Step 1: Create a Global Summary Sheet

Create a new sheet named Global 2020 Report.

Calculate the total national population from the dataset using pop_n.(since it is in thousands, we divide by 1M to make it into billions = 7.786695108 billion)

Add the estimated world population (7.821 billion) for comparison.

### Step 2: Calculate Urban Population in the Dataset

Create a new feature in the dataset sheet called pop_u_val, representing the number of people living in urban areas per country.

    excel
    =pop_n / 1000000 * (pop_u / 100)( in billions)

Notes:

pop_n is in thousands, so divide by 10000000.

pop_u is a percentage, so divide by 100 before multiplying.

### Step 3: Total Urban Population(dataset)

In the Global 2020 Report sheet, calculate the total urban population of dataset using SUM(pop_u_val).-(becomes 4.375308463 billions)

### Step 4: Estimate Global(world) Urban Population

Calculate the estimated global(world) urban population:

    excel
    =7.821 * 0.55 (becomes 4.30155 billions) 

### Step 5: Calculate Urban Share in the Dataset

Global(world) urban share - 55%.

Compute the urban share from the dataset:
    
    excel
    =Total_Urban_Population / Total_National_Population  -(becomes 56.18954386% )

### Step 6: Percentage Difference Calculation

Calculate the percentage difference between dataset and global estimates:

1.urban total world pop vs urban total dataset pop
2.urban world share percentage vs urban dataset share percentage.

    =(ABS(V2 - V1) / ((V2 + V1) / 2)) * 100%

Use Google Sheets:
    =ABS(value2 - value1)

### Key Insight

The dataset population values closely match global estimates, but small percentage differences occur due to coverage gaps, rounding, and dataset scope differences.

## B. Urban vs Rural Population Visualization
### Step 1: Create Rural Population Share

Create a new feature called pop_r:
    excel
    =100 - pop_u

### Step 2: Create a Line Chart

X-axis: national population size (pop_n)

Y-axis: population share percentages ( pop_u (urban share) and pop_r (rural share) )

Add appropriate chart and axis titles.
(comparison of share of the national population living in urban versus rural areas. )

### Key Insight

![Population Growth Chart](./comparison%20of%20share%20of%20the%20national%20population%20living%20in%20urban%20versus%20rural%20areas.png)

We find that our data visualization is not very comprehensible due to some of our pop_n values being
much larger than our other values, in other words, outliers.

### Step 3: Handling Outliers

Large population values make the chart hard to read. Three options were considered:

Option A: Remove Outliers

✅ Clear visualization

❌ Loss of important country data

Option B: Set X-axis Cutoff

✅ Better readability

❌ Only partial dataset shown

Option C: Change Population Units (Selected)

✅ Keeps all data and improves readability

❌ Population differences become less granular

-We go with option c(since pop_n is in thousands ,we convert it into millions).

### Step 4: Convert Population to Millions

Create a new feature ( pop_n (m) ):
    excel
    =ROUNDUP(pop_n / 1000, 0)

This converts population from thousands to millions.( population size rounded up to the nearest million)

### Step 5: Update the Chart

Use pop_n (m) as the new x-axis.

Enable Aggregate → Average in the chart editor.(USE SMOOTH LINES AND ADD POINT REPRESENTATION)

![Population Growth Chart](./comparison%20of%20share%20of%20the%20national%20population%20living%20in%20urban%20versus%20rural%20areas%20(1).png)


Update axis titles accordingly.

### Why Use ROUNDUP Instead of ROUND?

ROUNDUP() ensures population values are not underestimated.

ROUND() could round down and reduce perceived population size.

### Why Aggregate Using Average?

Population is grouped into ranges (millions).

Averaging prevents overcounting and preserves proportional trends.

## Insights from the Visualization

Urban population share generally increases with population size.

Rural population share decreases as countries become more urbanized.

Large countries strongly influence global urbanization trends.

## Alternative Visualization

Since urban and rural shares always sum to 100%, a stacked area chart or stacked bar chart could also effectively represent population distribution.

## D.Investigating access by area

## 4. Investigating Access by Area
### Research Questions

What is the central tendency and spread of the different water access features?

How do these measures compare across national, rural, and urban areas?

This section uses measures of central tendency and spread to understand how access to water varies across different areas.

## A. National Water Access: Central Tendency and Spread
### Step 1: Calculate Maximum Values

In the Global 2020 Report sheet, calculate the maximum values for the four national service levels:

    wat_bas_n

    wat_lim_n

    wat_unimp_n

    wat_sur_n

    excel
    =MAX(range)

### Step 2: Fix Values Exceeding 100%

Some wat_bas_n values exceed 100%, which is not logically possible.

Create a Rounded Feature

In the dataset sheet, create a new column:

    excel
    wat_bas_n_rounded

Round only the decimal places where values exceed 100%.

Why Create a New Feature Instead of Using Toolbar Rounding?

  Toolbar rounding only changes display, not the underlying data.

  Creating a new column ensures data integrity and reproducibility.

Conditional Rounding to Cap at 100%

If you only want to cap values above 100%:
    =IF(wat_bas_n > 100, ROUND(wat_bas_n,0), wat_bas_n)

### Step 3: Handle Errors

Some rounding operations may return #VALUE!.

Fix:

Use filters to find #VALUE! entries.

Replace them with text "NAN" so calculations work.

### Step 4: Calculate Minimum Values

In the Global 2020 Report sheet, calculate minimum values:
    excel
    =MIN(range)

### Step 5: Calculate Central Tendency

For each national water access feature, calculate:

    excel
    =AVERAGE(range)   // Mean
    =MEDIAN(range)    // Median
    =MODE(range)      // Mode

### Step 6: Calculate Spread (IQR and Standard Deviation)
Quartiles and IQR

Google Sheets does not have a direct IQR function, so compute manually:

    excel
    =QUARTILE(range, 1)   // Q1
    =QUARTILE(range, 3)   // Q3
    =Q3 - Q1              // IQR

Standard Deviation

    excel
    =STDEV(range)

### Key Insight (National Level)

For _wat_bas_n_, we see that the mean is relatively high and the interquartile range is about a tenth of
the range, which indicates that our data are concentrated around a point closer to 100% than 0%. This
means that the majority of people represented in the data have access to at least basic water services
on a national level.

## C. Visualization: Box and Whisker Plot
### Step 1: Prepare Five-Number Summary

For each of the 12 features, compute:

Minimum

Q1

Median

Q3

Maximum

### Step 2: Create Box and Whisker (Candlestick) Chart

In Google Sheets, use a Candlestick chart to represent the box and whisker plot.

Interpretation of Chart Elements

Low / High: Minimum and Maximum values (whiskers)

Open / Close: Q1 and Q3 (box boundaries)

Mean: Located inside the box

Box Width: Interquartile range (IQR)

![Box and whisker Plot](./Access%20to%20water.png)

## Insights from the Box and Whisker Plot

Urban areas generally show higher median access to basic water services.

Rural areas show greater variability and lower median access, indicating inequality.

Surface and unimproved water access show wide spread, highlighting disparities in infrastructure.

National averages hide significant urban–rural inequality.

## Conclusion (Access by Area)

Measures of central tendency and spread reveal that basic water access is widespread globally, but inequality persists, especially in rural areas and for unimproved or surface water sources. Box plots effectively highlight disparities that are not visible from averages alone.