### Module Title: Introduction to Data Engineering in Aerospace

### Exercise Requirements

1. **Problem Statement**: 
   You are tasked with developing an ETL (Extract, Transform, Load) pipeline to analyze aircraft performance data collected from various sensors during test flights. The objective is to identify patterns that could lead to optimizing aircraft performance and enhancing predictive maintenance models. You will need to extract data from a CSV file containing flight logs, transform the data to clean and structure it, and then load it into a database for further analysis. This exercise will reinforce your understanding of the roles and responsibilities of data engineers in the aerospace sector.

2. **Fill-in-the-Blank Starter Code**: 
   Below is a starter code template that outlines the steps for creating an ETL pipeline. Fill in the blanks to complete the functionality.

```python
import pandas as pd
from sqlalchemy import create_engine

def extract_data(file_path):
    # Load flight data from CSV file
    data = pd.read_csv(file_path)
    return data

def transform_data(data):
    # Clean the data by removing rows with missing values
    cleaned_data = data.dropna()
    
    # Convert relevant columns to appropriate data types
    cleaned_data['flight_time'] = pd.to_timedelta(cleaned_data['flight_time'])
    
    # Calculate additional metrics, e.g., average speed
    cleaned_data['average_speed'] = cleaned_data['distance'] / cleaned_data['flight_time'].dt.total_seconds() * 3600  # km/h
    
    return cleaned_data

def load_data(cleaned_data, database_uri):
    # Create a database connection
    engine = create_engine(database_uri)
    
    # Load cleaned data into the specified table
    cleaned_data.to_sql('aircraft_performance', con=engine, if_exists='replace', index=False)

# Main ETL function
def etl_pipeline(file_path, database_uri):
    raw_data = extract_data(file_path)
    transformed_data = transform_data(raw_data)
    load_data(transformed_data, database_uri)

# Example usage
etl_pipeline('flight_logs.csv', 'sqlite:///aircraft_performance.db')
```

3. **Hints**: 
   - **Hint 1**: Remember to handle any potential errors during the data extraction process, such as file not found or incorrect file format.
   - **Hint 2**: When cleaning the data, consider what constitutes a valid entry for your dataset. Think about how missing values might affect your analysis.
   - **Hint 3**: Ensure that the database connection is properly configured to avoid issues during the loading phase.
   - **Hint 4**: Consider what additional metrics might be useful for your analysis based on the lecture content on data collection and processing.

4. **Expected Outcome**: 
   By completing this exercise, you should be able to fill in the blanks correctly, demonstrating an understanding of how to create an ETL pipeline tailored for aircraft performance data. The final solution should include:
   - Error handling for file operations.
   - Well-commented code explaining each step in the process.
   - A structured approach that adheres to best practices in data engineering.

### Integration
- Ensure that this exercise is formatted using markdown for clear readability.
- Include links to any necessary resources, such as sample CSV files or database connection documentation, to assist learners in completing the exercise effectively.