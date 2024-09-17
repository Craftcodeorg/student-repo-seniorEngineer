### Assignment: Enhancing Flight Safety through Data-Driven Insights

#### Problem Statement:
As a data engineer in the aerospace industry, your task is to develop a predictive maintenance model that enhances flight safety by analyzing flight data. You will create a function that evaluates engine temperature data from various flights to determine which flights require maintenance before potential failures occur. This task will help you apply the concepts of predictive analytics and anomaly detection discussed in the lecture.

#### Starter Code:
Below is the starter code that sets up the environment for your analysis. You will need to expand upon this code to complete the assignment.

```python
import pandas as pd

# Sample DataFrame of flight data
data = {
    'Flight_ID': [1, 2, 3, 4, 5],
    'Engine_Temperature': [200, 210, 220, 230, 240],
    'Maintenance_Needed': [0, 0, 0, 0, 0]  # 0 means no maintenance needed
}
df = pd.DataFrame(data)

# Predictive maintenance function
def predict_maintenance(df):
    # Step 1: Identify flights needing maintenance based on engine temperature
    # Define a threshold for maintenance
    temperature_threshold = 215
    
    # Step 2: Create a new column indicating if maintenance is needed
    df['Maintenance_Needed'] = df['Engine_Temperature'] > temperature_threshold
    
    # Step 3: Return the DataFrame with flights needing maintenance
    return df[df['Maintenance_Needed']]

# Test the function with the sample data
flights_to_check = predict_maintenance(df)
print(flights_to_check)
```

#### Detailed Instructions:
1. **Modify the Function**: 
   - Enhance the `predict_maintenance` function to return not only the DataFrame of flights needing maintenance but also include a count of how many flights exceed the temperature threshold.
   - Create a new column called `Temperature_Excess` that calculates how much each flight's engine temperature exceeds the threshold.

2. **Add Detailed Feedback**: 
   - Modify the print statement at the end of your function to include a summary message that states how many flights need maintenance and lists their IDs along with their excess temperatures.

3. **Implement Anomaly Detection**: 
   - Add functionality to identify any unusual patterns in engine temperature data. For example, if a flight's engine temperature is significantly higher than the average temperature of all flights, flag it as an anomaly.

4. **Enhance Data Visualization** (Optional):
   - If time permits, consider using libraries such as Matplotlib or Seaborn to visualize the engine temperatures and highlight those exceeding the threshold.

#### Criteria for Success and Evaluation:
- **Correctness**: The function must accurately identify and return flights needing maintenance based on engine temperature.
- **Code Quality**: The code should be clean, well-structured, and include comments explaining each step.
- **Functionality**: The final output should clearly indicate how many flights need maintenance and provide detailed feedback on each flight.
- **Anomaly Detection**: Successfully implement and report any detected anomalies in engine temperatures.
- **Documentation**: Ensure that your code is documented adequately for others to understand your logic and methodology.

#### Submission:
Submit your completed Python script with all modifications made according to the instructions above. Ensure it runs without errors and meets all criteria for success as outlined.