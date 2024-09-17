### Assignment: Analyze and Visualize Trends in Aircraft Performance Data Using Python Libraries

#### Problem Statement:
In the aerospace industry, understanding aircraft performance is crucial for enhancing safety and operational efficiency. This assignment requires you to analyze and visualize trends in aircraft performance data, specifically focusing on altitude and speed metrics collected from drone flights. You will apply the data analysis and visualization techniques discussed in the lecture to extract meaningful insights from the data.

#### Objective:
Utilize Python libraries such as Pandas and Matplotlib to clean, analyze, and visualize aircraft performance data. Your goal is to identify trends in altitude and speed over time and present your findings through visualizations.

---

### Starter Code:
Below is a basic framework to get you started. You will need to expand upon this code to complete the assignment.

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load flight data
data = pd.read_csv('drone_flight_data.csv')

# Step 1: Clean the data by dropping duplicates and handling missing values
cleaned_data = data.drop_duplicates()
cleaned_data = cleaned_data.dropna()

# Step 2: Analyze average altitude and speed
average_altitude = cleaned_data['altitude'].mean()
average_speed = cleaned_data['speed'].mean()

# Print the averages
print(f'Average Flight Altitude: {average_altitude} meters')
print(f'Average Flight Speed: {average_speed} m/s')

# Step 3: Visualize altitude and speed trends over time
plt.figure(figsize=(12, 6))

# Plotting altitude
plt.subplot(2, 1, 1)
plt.plot(cleaned_data['time'], cleaned_data['altitude'], label='Altitude', color='blue')
plt.title('Aircraft Altitude Over Time')
plt.xlabel('Time')
plt.ylabel('Altitude (meters)')
plt.legend()

# Plotting speed
plt.subplot(2, 1, 2)
plt.plot(cleaned_data['time'], cleaned_data['speed'], label='Speed', color='red')
plt.title('Aircraft Speed Over Time')
plt.xlabel('Time')
plt.ylabel('Speed (m/s)')
plt.legend()

# Show the plots
plt.tight_layout()
plt.show()
```

---

### Detailed Instructions:
1. **Data Cleaning**:
   - Ensure that the dataset does not contain any duplicate entries or missing values. If there are missing values, decide on a strategy to handle them (e.g., removing or filling them).
   
2. **Data Analysis**:
   - After cleaning the data, calculate the average altitude and speed as shown in the starter code.
   - Additionally, compute the maximum and minimum values for both altitude and speed.

3. **Data Visualization**:
   - Use Matplotlib to create two separate plots: one for altitude over time and another for speed over time.
   - Ensure your plots have clear titles, axis labels, and legends for better readability.

4. **Enhancements**:
   - Modify the visualization to include markers for significant events (e.g., takeoff, landing) if such data is available in your dataset.
   - Add gridlines to your plots for improved clarity.

5. **Documentation**:
   - Comment your code thoroughly, explaining what each section does.
   - Write a brief summary of your findings based on the visualizations you created.

---

### Criteria for Success and Evaluation:
- **Functionality**: The code must run without errors, accurately calculating averages, maximums, and minimums, and producing clear visualizations.
- **Code Quality**: The code should be well-structured, clean, and well-documented with comments explaining key sections.
- **Visualization**: The plots must be clear, informative, and visually appealing. They should effectively communicate trends in the data.
- **Insights**: Provide a summary of insights derived from your analysis and visualizations that could be relevant to aircraft performance optimization.

---

This assignment is designed to reinforce the concepts learned in the lecture while providing a practical application relevant to your interests in aircraft data systems and analytics. Good luck!