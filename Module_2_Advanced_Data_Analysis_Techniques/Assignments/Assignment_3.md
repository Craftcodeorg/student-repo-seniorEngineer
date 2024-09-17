### Assignment: Develop a Dashboard to Visualize Aircraft Performance Metrics

#### Problem Statement
In the aerospace industry, data visualization is crucial for analyzing aircraft performance metrics. Your task is to create a dashboard that visualizes key performance indicators (KPIs) of aircraft, such as fuel efficiency, flight altitude, and speed. This dashboard will help stakeholders make informed decisions based on real-time data, aligning with the concepts of machine learning and data analysis discussed in the lecture.

#### Starter Code
Below is a basic framework for your dashboard using Python with the Dash library. This code sets up the environment and includes comments to guide you on where to implement your solutions.

```python
# Import necessary libraries
import dash
from dash import dcc, html
import plotly.express as px
import pandas as pd

# Sample data: Replace this with your actual aircraft performance data
data = {
    'Flight Number': ['FL001', 'FL002', 'FL003', 'FL004'],
    'Altitude (ft)': [30000, 32000, 29000, 31000],
    'Speed (knots)': [500, 520, 480, 510],
    'Fuel Efficiency (mpg)': [25, 27, 24, 26]
}

# Create a DataFrame
df = pd.DataFrame(data)

# Initialize the Dash app
app = dash.Dash(__name__)

# Layout of the dashboard
app.layout = html.Div(children=[
    html.H1(children='Aircraft Performance Dashboard'),

    dcc.Graph(
        id='altitude-speed',
        figure=px.scatter(df, x='Altitude (ft)', y='Speed (knots)', 
                          title='Altitude vs Speed', 
                          labels={'Altitude (ft)': 'Altitude (ft)', 'Speed (knots)': 'Speed (knots)'})
    ),

    dcc.Graph(
        id='fuel-efficiency',
        figure=px.bar(df, x='Flight Number', y='Fuel Efficiency (mpg)', 
                       title='Fuel Efficiency by Flight',
                       labels={'Fuel Efficiency (mpg)': 'Fuel Efficiency (mpg)', 'Flight Number': 'Flight Number'})
    )
])

# Run the app
if __name__ == '__main__':
    app.run_server(debug=True)
```

#### Detailed Instructions
1. **Data Integration**: Replace the sample data in the `data` dictionary with actual aircraft performance metrics. Ensure that the data structure matches the DataFrame format used in the starter code.

2. **Enhance Visualizations**:
   - **Step 1**: Add a new graph that visualizes the relationship between fuel efficiency and speed using a line chart. Use Plotly Express to create this visualization.
   - **Step 2**: Modify the existing graphs to include additional features such as hover data that provides more context about each flight.

3. **User Interaction**:
   - **Step 3**: Implement dropdowns or sliders that allow users to filter data based on specific criteria such as altitude range or speed range.
   - **Step 4**: Ensure that the dashboard updates dynamically based on user input.

4. **Documentation**: Comment on your code thoroughly to explain what each section does. This will help others understand your thought process and make it easier for you to revisit your work later.

5. **Testing**: Test your dashboard to ensure all visualizations work as expected and that user interactions are functioning correctly.

#### Criteria for Success and Evaluation
- **Functionality**: The dashboard should correctly visualize aircraft performance metrics and respond to user interactions.
- **Code Quality**: The code should be clean, well-documented, and follow best practices in coding standards.
- **User Experience**: The dashboard should provide a user-friendly interface that effectively communicates the data insights.
- **Creativity**: Additional visualizations or features that enhance the dashboard beyond the basic requirements will be considered positively.

By completing this assignment, you will reinforce your understanding of machine learning applications in aerospace while gaining practical experience in data visualization and dashboard development. This task aligns perfectly with your career goals of becoming a lead data engineer specializing in aircraft data systems and analytics.