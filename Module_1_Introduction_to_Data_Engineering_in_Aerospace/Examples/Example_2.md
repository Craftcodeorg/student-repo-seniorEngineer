# Module Title: Introduction to Data Engineering in Aerospace

## Example 2: Data Cleaning Techniques in Python

### 1. Introduction
Data cleaning is a critical step in data analysis, especially within the Aerospace and Defense sectors, where accuracy and reliability are paramount. The significance of this process lies in its ability to ensure that the data used for decision-making is free from errors and inconsistencies, which can lead to costly mistakes or safety issues. In this module, we will explore data cleaning techniques in Python, building upon the core concepts discussed in the lecture on key concepts in data analysis and engineering.

### 2. Code Snippet
Below is a well-commented Python code snippet that illustrates data cleaning techniques using the Pandas library. This example demonstrates how to handle missing values, remove duplicates, and ensure data integrity, which are essential practices for maintaining high-quality datasets in aerospace applications.

```python
import pandas as pd

# Load flight data from a CSV file
try:
    data = pd.read_csv('drone_flight_data.csv')
    print("Data loaded successfully.")
except FileNotFoundError:
    print("Error: The file 'drone_flight_data.csv' was not found.")
    exit()

# Display the first few rows of the dataset for initial inspection
print("Initial data preview:")
print(data.head())

# Check for missing values
missing_values = data.isnull().sum()
print("\nMissing values in each column:")
print(missing_values)

# Fill missing values with the mean of the column for numerical data
for column in data.select_dtypes(include=['float64', 'int64']).columns:
    mean_value = data[column].mean()
    data[column].fillna(mean_value, inplace=True)
    print(f"Missing values in '{column}' filled with mean: {mean_value}")

# Clean the data by dropping duplicate entries
initial_count = data.shape[0]
data.drop_duplicates(inplace=True)
final_count = data.shape[0]
print(f"\nDuplicates removed: {initial_count - final_count}")

# Save the cleaned data to a new CSV file
cleaned_file_path = 'cleaned_drone_flight_data.csv'
data.to_csv(cleaned_file_path, index=False)
print(f"\nCleaned data saved to '{cleaned_file_path}'.")

# Analyze average altitude
average_altitude = data['altitude'].mean()
print(f'Average Flight Altitude: {average_altitude} meters')
```

### 3. Explanation
- **Loading Data**: The code begins by attempting to load a CSV file containing drone flight data. It includes error handling to ensure that if the file is not found, a meaningful message is displayed and the program exits gracefully.
  
- **Initial Data Preview**: After loading the data, it prints a preview of the first few rows. This step is crucial for understanding the structure of the dataset and identifying any immediate issues.

- **Checking for Missing Values**: The code checks for missing values across all columns and prints out the count of missing entries. This is essential in aerospace applications where missing data can lead to inaccurate analyses.

- **Handling Missing Values**: For numerical columns, missing values are filled with the mean of that column. This technique helps maintain the integrity of the dataset while minimizing bias introduced by removing rows with missing values.

- **Removing Duplicates**: The code counts the initial number of entries, removes duplicates, and then displays how many duplicates were found and removed. This step ensures that each entry in the dataset represents a unique flight instance.

- **Saving Cleaned Data**: Finally, the cleaned dataset is saved to a new CSV file for further analysis or use in modeling.

- **Calculating Average Altitude**: The code concludes by calculating and printing the average altitude from the cleaned dataset, showcasing a practical application of the cleaned data.

### 4. Application
In Aerospace and Defense, effective data cleaning techniques are vital for ensuring that flight performance metrics are accurate. For instance, when analyzing flight paths for military drones, any erroneous or missing data could lead to flawed assessments of flight efficiency or safety risks. By employing robust data cleaning methods as demonstrated above, engineers can derive reliable insights that inform design improvements and operational strategies.

This process not only enhances aircraft performance but also contributes to predictive maintenance models by ensuring that historical flight data is accurate and complete. As you work towards your goal of developing a comprehensive data model for predictive maintenance in military aircraft, mastering these techniques will be crucial in your journey towards becoming a lead data engineer in aerospace.

---

This structured content provides a comprehensive understanding of data cleaning techniques using Python within the context of Aerospace and Defense, aligning with your career goals and learning preferences.