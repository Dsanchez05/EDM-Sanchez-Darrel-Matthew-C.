# Midterm Lab Task 2 - Data Cleaning and Preparation using Excel
In this activity, we cleaned an excel sheet fill of errors and redundancy using different excel features.
## Step 1 Data Cleaning and Transformation Using Power Query Editor
- Download the copy of the raw dataset (Uncleaned_DS_jobs.csv) 
- Load the Data in Excel – Open Excel – Goto Data – New Query Open File – text/csv
- Load – Edit the Dataset using Power Query Editor
- Duplicate the raw data 
- Salary Estimate Column
- Create 2 New Columns (From the Salary Estimate) Min Sal and Max Sal
- ADD COLUMN – Role Type 
- SPLIT COLUMNS by Delimeter 
- Select Location column (SPLIT columns by , Delimeter)
- Copy the APPLIED steps as proof of your Data Cleaning Activities -> 

## Here is the Image of the applied steps

## Step 2 Data Normalization
- Create a duplicate of the raw data Right Click Unclean DS Jobs select 
duplicate (Queries pane) 
- Rename the duplicate with “Sal By Role Type dup”
- Rename the reference with “Sal By Role Size ref”
- Mapping Other Files and include in the current queries
- Rename the reference with “Sal By State ref”
- To view dependencies and References of the QUERIES
## Step 3 Before
![Screenshot 2025-03-13 001802](https://github.com/user-attachments/assets/cf660661-af3c-4a91-a8b9-783f8fb998be)

## Step 4 After
![Screenshot 2025-03-13 002333](https://github.com/user-attachments/assets/e2ae5476-53ad-448c-86a1-4f39518beedc)

## Here's the Physical Data Model
![Screenshot 2025-03-13 010343](https://github.com/user-attachments/assets/03768004-8aba-4ee6-a6da-7c6080e24522)
