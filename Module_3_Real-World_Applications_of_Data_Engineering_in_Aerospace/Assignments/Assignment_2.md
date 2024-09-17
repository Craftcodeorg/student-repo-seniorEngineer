# Assignment: Create a Simulation Model for an Autonomous Drone Delivery System

## Problem Statement
In this assignment, you will create a simulation model for an autonomous drone delivery system. The goal is to analyze flight data generated from a simulated environment to optimize delivery routes, ensure safety, and enhance operational efficiency. You will utilize concepts learned from the lecture on flight simulation gaming as a data source, focusing on data generation, performance metrics, and data integration.

## Starter Code
Below is the starter code that sets up a basic structure for your simulation model. You will expand upon this code to implement the required functionalities.

```python
import pandas as pd
import numpy as np

# Function to simulate drone delivery data
def simulate_drone_delivery(num_deliveries):
    # Generate random data for drone deliveries
    delivery_data = {
        'delivery_id': range(1, num_deliveries + 1),
        'altitude': np.random.uniform(100, 500, num_deliveries),  # in meters
        'speed': np.random.uniform(30, 80, num_deliveries),  # in knots
        'distance': np.random.uniform(5, 20, num_deliveries),  # in kilometers
        'g_force': np.random.uniform(1, 9, num_deliveries)  # g-force experienced
    }
    
    return pd.DataFrame(delivery_data)

# Step 1: Simulate delivery data for 100 deliveries
delivery_df = simulate_drone_delivery(100)

# Step 2: Analyze the average speed and identify critical maneuvers
def analyze_delivery_data(data):
    # Calculate average speed
    average_speed = data['speed'].mean()
    
    # Identify critical maneuvers where g-force exceeds 5
    critical_maneuvers = data[data['g_force'] > 5]
    
    return average_speed, len(critical_maneuvers)

# Test the function with the simulated data
average_speed, critical_count = analyze_delivery_data(delivery_df)
print(f'Average Speed: {average_speed:.2f} knots')
print(f'Critical Maneuvers Count: {critical_count}')
```

## Detailed Instructions
1. **Simulate Drone Delivery Data**: 
   - Modify the `simulate_drone_delivery` function to include additional parameters such as `battery_level` (percentage) and `weather_conditions` (e.g., clear, cloudy, rainy). Generate random values for these parameters.
   
2. **Enhance Data Analysis**:
   - Update the `analyze_delivery_data` function to also calculate the average battery level across all deliveries.
   - Implement a mechanism to categorize deliveries based on weather conditions and analyze their impact on speed and critical maneuvers.

3. **Output Enhancement**:
   - Modify the output of your analysis to include detailed feedback. For example, provide insights into how many deliveries were affected by adverse weather conditions and their average speeds compared to clear weather conditions.

4. **Visualization**:
   - Create a simple visualization (e.g., using matplotlib or seaborn) that shows the distribution of speeds across different weather conditions.

## Criteria for Success and Evaluation
Your submission will be evaluated based on the following criteria:

- **Functionality**: The simulation should accurately generate and analyze drone delivery data.
- **Code Quality**: Code should be clean, well-documented, and follow best practices.
- **Output Clarity**: The output should be informative and easy to understand, providing meaningful insights into the delivery data.
- **Visualization**: Include a visualization that effectively communicates the results of your analysis.
- **Creativity**: Consider additional metrics or enhancements that could improve the simulation or analysis.

### Evaluation Rubric
- **Functionality (40%)**: Does the code run without errors? Are all required functionalities implemented?
- **Code Quality (30%)**: Is the code well-organized and documented? Are variable names meaningful?
- **Output Clarity (20%)**: Is the output informative? Does it provide clear insights into the data?
- **Visualization (10%)**: Is the visualization effective in conveying information? 

This assignment will help you apply key concepts from the lecture while contributing to your project goals of developing a comprehensive data model for predictive maintenance in military aircraft. Good luck!