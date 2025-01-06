# Name: Prajapati Uday Mukesh
# Company: CODTECH IT SOLUTIONS 
# Id: CT6WDS2794
# Domain: Java Programming
# Duration: DECEMBER 12th, 2024 to JANUARY 27th, 2025.
# Mentor: Muzammil Ahmed

# Overview:
The RestApiConsumer program is a Java-based application that interacts with the OpenWeatherMap API to fetch real-time weather data for a specified location. The program takes user input for the city name and desired temperature unit (Celsius or Fahrenheit), retrieves weather data from the API, parses the JSON response, and displays the data in a structured format. Additionally, it saves the weather report to a text file for future reference.

# Key Activities:
# 1. Fetching Data from the OpenWeatherMap API:
The program constructs an API URL based on the user's input (city name and temperature unit).
It makes an HTTP GET request using HttpURLConnection to fetch weather data in JSON format.

# 2. Parsing and Displaying Weather Data:
The JSON response is parsed using the org.json library to extract key details such as temperature, humidity, wind speed, visibility, and a description of the weather conditions.
The parsed data is displayed in a user-friendly format on the console.

# 3. Saving Weather Data to a File:
The program writes the fetched weather details to a file named weather_report.txt.
It appends the data with a timestamp to allow users to maintain a log of past weather reports.

# Technology Used:
# 1. REST API Integration:
The program uses the OpenWeatherMap API to fetch weather data.
HTTP GET requests are sent via HttpURLConnection, and the JSON response is processed using the org.json library.

# 2. File Handling:
Weather reports are stored in a text file using FileWriter to allow persistent storage of data.

# 3. JSON Parsing:
The org.json library is used to parse the API response and extract specific weather attributes.

# 4. Dynamic URL Construction:
The program dynamically constructs the API endpoint URL based on user inputs (city name, temperature unit) and appends the API key.

# Key Insights:
# 1. Real-time API Consumption:
Demonstrates how to consume a public REST API to retrieve and process data dynamically.

# 2. Error Handling and Resilience:
Handles potential errors like network issues, invalid city names, or incorrect API responses gracefully.

# Final Output:
![image](https://github.com/user-attachments/assets/5e2d162e-a63f-4d6b-893a-83df0a113dff)
![image](https://github.com/user-attachments/assets/0d9aebbe-cbb1-47e5-a370-bf20e4e9f793)


