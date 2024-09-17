# Module Title: Introduction to Data Engineering in Aerospace

## Exercise Requirements

### 1. Problem Statement
As a data engineer in the aerospace industry, you are tasked with analyzing flight data to improve operational efficiency and safety. You have access to a database containing telemetry data from various drone flights, which includes the following tables:

- **Flights**: Contains information about each flight.
  - `flight_id`: Unique identifier for each flight
  - `drone_id`: Identifier for the drone used
  - `start_time`: Timestamp of when the flight started
  - `end_time`: Timestamp of when the flight ended
  - `distance_travelled`: Total distance travelled during the flight (in kilometers)

- **Telemetry**: Contains real-time data collected during flights.
  - `telemetry_id`: Unique identifier for each telemetry record
  - `flight_id`: Identifier for the associated flight
  - `altitude`: Altitude of the drone (in meters)
  - `speed`: Speed of the drone (in km/h)
  - `battery_level`: Battery percentage at the time of recording
  - `timestamp`: Timestamp of the telemetry data

Your goal is to write SQL queries that extract insights from this flight data, focusing on optimizing drone performance for aerial photography. Specifically, you need to answer the following questions:

1. What is the average speed of drones during flights?
2. Which flights had a battery level below 20% at any point during the flight?
3. Identify the drone that travelled the longest distance in a single flight.

### 2. Fill-in-the-Blank Starter Code
```sql
-- SQL query to calculate the average speed of drones during flights
SELECT AVG(speed) AS average_speed
FROM Telemetry
WHERE flight_id IN (SELECT flight_id FROM Flights WHERE start_time >= '2023-01-01' AND end_time <= '2023-12-31');

-- SQL query to find flights with battery levels below 20%
SELECT f.flight_id, f.drone_id, f.start_time, f.end_time
FROM Flights f
JOIN Telemetry t ON f.flight_id = t.flight_id
WHERE t.battery_level < 20;

-- SQL query to identify the drone that travelled the longest distance in a single flight
SELECT drone_id, MAX(distance_travelled) AS longest_distance
FROM Flights
GROUP BY drone_id
ORDER BY longest_distance DESC
LIMIT 1;
```

### 3. Hints
- For calculating average speed, consider using aggregate functions such as `AVG()` in SQL.
- When checking battery levels, remember to use a `JOIN` to combine data from both the Flights and Telemetry tables.
- To find the longest distance travelled, utilize `MAX()` and group by `drone_id` to get results for each drone.

### 4. Expected Outcome
By completing this exercise, you should be able to:
- Write SQL queries that effectively extract insights from flight data.
- Demonstrate an understanding of how telemetry data can inform decisions regarding drone performance and safety.
- Produce well-structured SQL code that adheres to best practices, including proper use of joins and aggregate functions.

The final solution should be well-commented to explain the reasoning behind each step, reinforcing your understanding of aircraft data systems and their applications in real-world scenarios within Aerospace and Defense.

---

### Integration
Ensure this exercise content is formatted with clear headings and sections for easy parsing and integration into your learning platform. Use markdown for formatting and include any necessary files or resources as links.