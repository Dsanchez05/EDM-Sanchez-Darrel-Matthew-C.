# Midterm Lab Task 2 - Data Cleaning and Preparation using Excel
In this activity, we cleaned an excel sheet fill of errors and redundancy using different excel features.
# Step 1 Data Cleaning and Transformation Using Power Query Editor
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

# Before Cleaning

## Uncleaned Data 1
![Screenshot 2025-03-13 001802](https://github.com/user-attachments/assets/3a15c071-3f86-4d37-bacf-85fd7c08bfb3)

## Uncleaned Data 2
![Screenshot 2025-03-13 225815](https://github.com/user-attachments/assets/14b46909-1ea0-4e99-9a8f-0573ab7db64c)

# After Cleaning
## Clean Data 1
![Screenshot 2025-03-13 002333](https://github.com/user-attachments/assets/9db9eaba-c2e0-47dc-809c-9eb5c799c384)

## Clean Data 2
![Screenshot 2025-03-13 231101](https://github.com/user-attachments/assets/51c7bdc5-0827-4ab2-abba-2d6263c8c3e1)

# Here is the Image of the applied steps
![Screenshot 2025-03-13 224215](https://github.com/user-attachments/assets/91cbe5ed-a022-413f-8370-0c481974477d)

# Step 2 Reshape and Group the tables
- Create a duplicate of the raw data Right Click Unclean DS Jobs select 
duplicate (Queries pane) 
- Rename the duplicate with “Sal By Role Type dup”
- Rename the reference with “Sal By Role Size ref”
- Mapping Other Files and include in the current queries
- Rename the reference with “Sal By State ref”
- To view dependencies and References of the QUERIES

# Grouped Tables
## Sal By Role Type dup
![Screenshot 2025-03-13 231706](https://github.com/user-attachments/assets/f035c801-eea3-4603-a48a-350b0fd911be)

## Sal By Role Size ref
![Screenshot 2025-03-13 231718](https://github.com/user-attachments/assets/08e119c5-3c3d-45f7-8650-c782ab896aa6)

## States
![Screenshot 2025-03-13 231755](https://github.com/user-attachments/assets/89a9ecdf-8843-4623-b462-792be1bc14c6)

## Sal By State ref
![Screenshot 2025-03-13 231755](https://github.com/user-attachments/assets/58e7f31a-230b-48e7-ba76-8510bc997090)

## Sal By Size Role Type Dup
![Screenshot 2025-03-13 231755](https://github.com/user-attachments/assets/77f17a4a-2f4d-44d0-bf04-678c1b530f71)

# Step 3 - View dependencies and References of the QUERIES

- After completing all the previous steps, review the Query Dependencies in PowerQuery by navigating to the "View" tab and selecting "Query Dependencies."  
- Verify that they are correctly linked.

# Here's the Physical Data Model
![Screenshot 2025-03-13 233041](https://github.com/user-attachments/assets/449b0dd3-a4f4-4d39-bd53-ba522327da96)

