# Assignment: Develop a Comprehensive ETL Process for Aircraft Maintenance Records

## Problem Statement
In the aerospace industry, effective data management is crucial for ensuring aircraft safety and performance. Your task is to develop a comprehensive ETL (Extract, Transform, Load) process for a dataset of aircraft maintenance records. This assignment will allow you to apply the concepts of data collection, processing, and storage discussed in the lecture "Overview of Data Engineering and its Role in Aerospace."

The dataset contains information about various aircraft, including maintenance dates, types of maintenance performed, and associated costs. Your ETL process should extract this data from a CSV file, transform it to ensure data quality and consistency, and load it into a database for further analysis.

## Starter Code
Below is a basic framework to get you started on your ETL process. You will need to expand upon this code by implementing the extraction, transformation, and loading steps.

```python
import pandas as pd
import sqlite3

# Step 1: Extract data from CSV file
def extract_data(file_path):
    # Load the maintenance records from the CSV file
    data = pd.read_csv(file_path)
    return data

# Step 2: Transform the data
def transform_data(data):
    # Example transformations
    # 1. Remove rows with missing values
    cleaned_data = data.dropna()
    
    # 2. Convert maintenance dates to datetime format
    cleaned_data['maintenance_date'] = pd.to_datetime(cleaned_data['maintenance_date'])
    
    # 3. Ensure cost is in float format
    cleaned_data['cost'] = cleaned_data['cost'].astype(float)
    
    return cleaned_data

# Step 3: Load data into SQLite database
def load_data(data, db_name='aircraft_maintenance.db'):
    # Connect to SQLite database (or create it if it doesn't exist)
    conn = sqlite3.connect(db_name)
    
    # Load data into a new table called 'maintenance_records'
    data.to_sql('maintenance_records', conn, if_exists='replace', index=False)
    
    # Close the connection
    conn.close()

# Main ETL function
def etl_process(file_path):
    # Extract
    raw_data = extract_data(file_path)
    
    # Transform
    transformed_data = transform_data(raw_data)
    
    # Load
    load_data(transformed_data)

# Test the ETL process with sample data
file_path = 'aircraft_maintenance_records.csv'  # Path to your CSV file
etl_process(file_path)
```

## Detailed Instructions
1. **Extract Data**:
   - Modify the `extract_data` function to include error handling for file reading (e.g., check if the file exists).
   - Ensure that the CSV file contains the necessary columns: `maintenance_date`, `maintenance_type`, and `cost`.

2. **Transform Data**:
   - Expand the `transform_data` function:
     - Add validation checks to ensure that all maintenance dates are within a reasonable range (e.g., not in the future).
     - Create a new column that categorizes maintenance types (e.g., 'Routine', 'Repair', 'Inspection') based on predefined criteria.

3. **Load Data**:
   - Modify the `load_data` function to create an index on the `maintenance_date` column in the SQLite database for faster querying.
   - Add functionality to handle potential duplicate entries based on unique identifiers (if applicable).

4. **Testing**:
   - Create a test CSV file with sample aircraft maintenance records to validate your ETL process.
   - After running your ETL process, query the database to ensure that the data has been loaded correctly.

## Criteria for Success and Evaluation
Your submission will be evaluated based on the following criteria:

- **Functionality**: The ETL process correctly extracts, transforms, and loads data without errors.
- **Data Quality**: The transformations ensure that the loaded data is clean, consistent, and ready for analysis.
- **Code Quality**: The code is well-structured, follows best practices, and includes comments explaining each step.
- **Documentation**: A brief report (1-2 pages) summarizing your ETL process, challenges faced, and how you addressed them.

### Success Criteria:
- The ETL process runs without errors and completes successfully.
- The transformed dataset in the database meets the quality standards set in the instructions.
- Code is clean and well-documented with clear explanations of each function's purpose.

This assignment will help you apply your advanced coding skills in Python while reinforcing your understanding of data engineering principles within the aerospace sector. Good luck!