# Midterm Lab Task 2 - Data Cleaning and Preparation using Excel
In this activity, we cleaned an excel sheet fill of errors and redundancy using different excel features.
## Step 1 Data Cleaning
- Salary Estimate Column
- Create 2 New Columns (From the Salary Estimate) Min Sal and Max Sal
- ADD COLUMN – Role Type 
- SPLIT COLUMNS by Delimeter 
- Select Location column (SPLIT columns by , Delimeter)
- Copy the APPLIED steps as proof of your Data Cleaning Activities -> 
- let
    Source = Csv.Document(File.Contents("C:\Users\Matthew Sanchez\Downloads\Uncleaned_DS_jobs.csv"),[Delimiter=",", Columns=15, Encoding=65001, QuoteStyle=QuoteStyle.Csv]),
    #"Promoted Headers" = Table.PromoteHeaders(Source, [PromoteAllScalars=true]),
    #"Changed Type" = Table.TransformColumnTypes(#"Promoted Headers",{{"index", Int64.Type}, {"Job Title", type text}, {"Salary Estimate", type text}, {"Job Description", type text}, {"Rating", type number}, {"Company Name", type text}, {"Location", type text}, {"Headquarters", type text}, {"Size", type text}, {"Founded", Int64.Type}, {"Type of ownership", type text}, {"Industry", type text}, {"Sector", type text}, {"Revenue", type text}, {"Competitors", type text}}),
    #"A. Extracted Text Before Delimiter" = Table.TransformColumns(#"Changed Type", {{"Salary Estimate", each Text.BeforeDelimiter(_, "("), type text}}),
    #"Inserted Text Between Delimiters" = Table.AddColumn(#"A. Extracted Text Before Delimiter", " Min Sal", each Text.BetweenDelimiters([Salary Estimate], "$", "K"), type text),
    #"B.Inserted Multiplication" = Table.AddColumn(#"Inserted Text Between Delimiters", "Max Sal", each Number.From([#" Min Sal"]) * 1.2481751824817517, type number),
    #"C.Added Custom" = Table.AddColumn(#"B.Inserted Multiplication", "Role Type", each if Text.Contains([Job Title], "Data Scientist") then  
"Data Scientist" 
else if Text.Contains([Job Title], "Data Analyst") then  
"Data Analyst" 
else if Text.Contains([Job Title], "Data Engineer") then  
"Data Engineer" 
else if Text.Contains([Job Title], "Machine Learning") then  
"Machine Learning Engineer" 
else  
"other"),
    #"Changed Type1" = Table.TransformColumnTypes(#"C.Added Custom",{{"Role Type", type text}}),
    #"E.Split Column by Delimiter" = Table.SplitColumn(#"Changed Type1", "Location", Splitter.SplitTextByDelimiter(",", QuoteStyle.Csv), {"Location.1", "Location.2"}),
    #"Changed Type2" = Table.TransformColumnTypes(#"E.Split Column by Delimiter",{{"Location.1", type text}, {"Location.2", type text}}),
    #"V.Replaced Value" = Table.ReplaceValue(#"Changed Type2","Anne Rundell","MA",Replacer.ReplaceText,{"Location.2"}),
    #"Renamed Columns" = Table.RenameColumns(#"V.Replaced Value",{{"Location.2", "State Abbreviations"}}),
    #"Inserted Text Before Delimiter" = Table.AddColumn(#"Renamed Columns", " MinCompanySize", each Text.BeforeDelimiter([Size], " "), type text),
    #"Inserted Text Between Delimiters1" = Table.AddColumn(#"Inserted Text Before Delimiter", "MaxCompanySize", each Text.BetweenDelimiters([Size], " ", " ", 1, 0), type text),
    #"Changed Type3" = Table.TransformColumnTypes(#"Inserted Text Between Delimiters1",{{"Max Sal", type text}}),
    #"Renamed Columns1" = Table.RenameColumns(#"Changed Type3",{{" Min Sal", "Min Sal"}}),
    #"Filtered Rows" = Table.SelectRows(#"Renamed Columns1", each ([Competitors] <> "-1") and ([Industry] <> "-1")),
    #"Trimmed Text" = Table.TransformColumns(#"Filtered Rows",{{"Company Name", Text.Trim, type text}}),
    #"Split Column by Delimiter" = Table.SplitColumn(#"Trimmed Text", "Company Name", Splitter.SplitTextByDelimiter("#(lf)", QuoteStyle.Csv), {"Company Name.1", "Company Name.2"}),
    #"Changed Type4" = Table.TransformColumnTypes(#"Split Column by Delimiter",{{"Company Name.1", type text}, {"Company Name.2", type number}}),
    #"Removed Columns" = Table.RemoveColumns(#"Changed Type4",{"Company Name.2", "Job Description"}),
    #"Changed Type5" = Table.TransformColumnTypes(#"Removed Columns",{{"Min Sal", Currency.Type}, {"Max Sal", Currency.Type}})
in
    #"Changed Type5"
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
