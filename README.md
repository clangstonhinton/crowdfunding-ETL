# crowdfunding-ETL

Build an ETL pipeline using Python, Pandas, Python, Regex to extract, transform and load data into a SQl database.


## Approach

(1) After you transform the data, you'll create four CSV files and use the CSV file data to create an ERD and a table schema. Finally, you’ll upload the CSV file data into a Postgres database.
(2) Four dataframes were created from data imported from two CSV fils:  Category, Subcategory, Contacts and Campaigns.
(3) Transformed the data as follows:
    - CATEGORY & SUBCATEGORY DATAFRAMES:
        - Created numpy arrays from 1-9 for the categories and 1-24 for the subcategories
        - Used a list comprehension to add "cat" to each category_id and "subcat" to each subcategory_id
        - Exported the final dataframes to a CSV file 
    - CAMPAIGN DATAFRAME: 
        - Renamed columns blurb to description, launched_at to start_date, and deadline to end_date
        - Converted the goal and pledged columns to a 'float' data type from 'object' data type
        - Formatted launch_date and end_date columns to datetime format
        - Dropped unwanted columns
        - Merged the Campaign with the Category and the Subcategory dataframes
        - Exported the final dataframe to a CSV file
    - CONTACTS DATAFRAME was created using two approaches, Pandas and Regex
        - PANDAS:  Used pandas to convert the contacts CSV data from one column of values separated by commas into a dataframe, by doing the following:
            - Iterated through the Contact and convert each row to a dictionary
            - Iterated through each dictionary (row) and get the values for each row using list comprehension
            - Appended the list of values for each row to a list
            - Created a "first"name" and "last_name" column by splitting "name" column
            - Reordered the columns and exported final dataframe to a CSV file
        - REGEX: Used pandas to convert the contacts CSV data from one column of values separated by commas into a dataframe, by doing the following:
            - Extracted the contact_id with .str.extract
            - Converted the "contact_id" column to an int64 data type
            - Extracted the name of the contact using Regex and added it to a new column
            - Extract the email from the contacts using Regex and added the values to a new column
            - Dropped unwanted columns
            - Exported final dataframe to a CSV file
(4) Created a database in PostgreSQL with the exported CSV files
    - Created an ERD (entity relationship diagram) to depict the relationship between the tables
    - Created the tables and columns in SQL
    - Imported the values to the tables 


## Technology
- pandas
- JSON
- SQL
- PostgreSQL
- Regex