### Module Title: Introduction to Data Engineering in Aerospace

### Exercise Requirements

#### 1. Problem Statement
You are tasked with cleaning and preprocessing a sample aircraft dataset that contains information from various drone flights. This dataset includes critical parameters such as altitude, speed, flight duration, and environmental conditions (temperature, humidity). The goal is to prepare this data for further analysis to enhance flight safety and optimize performance based on the principles discussed in the lecture. 

Your specific tasks include:
- Identifying and removing any duplicate entries in the dataset.
- Handling missing values appropriately by either filling them in or dropping the affected rows.
- Correcting any inaccuracies in the altitude readings, ensuring they fall within a realistic range for drone operations.

This exercise will require you to apply the concepts of data cleaning and preprocessing covered in the lecture, reinforcing your understanding of their importance in aerospace applications.

#### 2. Fill-in-the-Blank Starter Code
Below is a starter code snippet that you will need to complete. Fill in the blanks with the appropriate code to perform the required data cleaning tasks.

```python
import pandas as pd

# Load flight data
data = pd.read_csv('sample_aircraft_data.csv')

# Step 1: Remove duplicates
cleaned_data = data.drop_duplicates()

# Step 2: Handle missing values
# Fill missing altitude values with the mean altitude
cleaned_data['altitude'].fillna(______, inplace=True)

# Step 3: Correct inaccuracies in altitude
# Define realistic altitude limits (e.g., between 0 and 5000 meters)
cleaned_data = cleaned_data[(cleaned_data['altitude'] >= 0) & (cleaned_data['altitude'] <= 5000)]

# Display the cleaned data
print(cleaned_data.describe())
```

#### 3. Hints
- For Step 2, think about how you can calculate the mean of a column in a Pandas DataFrame. Use the appropriate Pandas function to achieve this.
- In Step 3, consider how to filter a DataFrame based on conditions. Remember that you can use boolean indexing to keep only the rows that meet your criteria.
- Ensure that after cleaning, you check the summary statistics of your cleaned dataset to confirm that your operations have had the desired effect.

#### 4. Expected Outcome
By completing this exercise, you should be able to:
- Demonstrate your ability to clean and preprocess a dataset relevant to aerospace applications.
- Understand how data cleaning impacts the quality of insights derived from data analysis.
- Produce a cleaned dataset that is ready for further analysis, showcasing best practices in data handling.

The final solution should include error handling for potential issues (e.g., file not found errors) and be well-commented to explain your reasoning for each step taken in the cleaning process. This will reflect your understanding of the core concepts discussed in the lecture and their application in real-world scenarios within Aerospace and Defense.

### Integration
- Ensure this exercise is formatted using markdown for clarity and ease of reading.
- Include links to any necessary resources or datasets that students may need to access.
- Structure the exercise with clear headings and sections for easy navigation within the learning platform.