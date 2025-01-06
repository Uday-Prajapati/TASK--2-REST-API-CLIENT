/**
 * A Java program to consume a public REST API and display the data in a structured format.
 * This program fetches weather data from the OpenWeatherMap API.
 * Ensure you replace "YOUR_API_KEY" with a valid API key from OpenWeatherMap.
 */

 import java.io.*;
 import java.net.HttpURLConnection;
 import java.net.URL;
 import java.net.URI;
 import java.util.Scanner;
 import org.json.JSONObject;
 
 public class RestApiConsumer {
 
     // Method to fetch data from a given URL
     public static String fetchData(String apiUrl) {
         StringBuilder response = new StringBuilder();
         try {
             URL url = new URI(apiUrl).toURL(); // Fixed deprecation warning
             HttpURLConnection connection = (HttpURLConnection) url.openConnection();
             connection.setRequestMethod("GET");
             connection.setRequestProperty("Accept", "application/json");
 
             int responseCode = connection.getResponseCode();
             if (responseCode == 200) { // HTTP OK
                 try (BufferedReader reader = new BufferedReader(new InputStreamReader(connection.getInputStream()))) {
                     String line;
                     while ((line = reader.readLine()) != null) {
                         response.append(line);
                     }
                 }
             } else {
                 System.err.println("Error: Unable to fetch data. HTTP Response Code: " + responseCode);
             }
         } catch (Exception e) {
             System.err.println("Error fetching data: " + e.getMessage());
         }
         return response.toString();
     }
 
     // Method to parse and display weather data
     public static void displayWeatherData(String jsonData) {
         try {
             JSONObject jsonObject = new JSONObject(jsonData);
             String cityName = jsonObject.getString("name");
             JSONObject main = jsonObject.getJSONObject("main");
             double temperature = main.getDouble("temp");
             double humidity = main.getDouble("humidity");
 
             JSONObject wind = jsonObject.getJSONObject("wind");
             double windSpeed = wind.getDouble("speed");
 
             String weatherDescription = jsonObject.getJSONArray("weather").getJSONObject(0).getString("description");
             int visibility = jsonObject.optInt("visibility", 0);
 
             System.out.println("Weather Data for: " + cityName);
             System.out.println("Temperature: " + String.format("%.2f", temperature) + " °C");
             System.out.println("Humidity: " + humidity + "%");
             System.out.println("Weather: " + weatherDescription);
             System.out.println("Wind Speed: " + windSpeed + " m/s");
             System.out.println("Visibility: " + (visibility / 1000.0) + " km");
 
             // Save weather data to a file
             saveWeatherReport(cityName, temperature, humidity, weatherDescription, windSpeed, visibility);
         } catch (Exception e) {
             System.err.println("Error parsing JSON data: " + e.getMessage());
         }
     }
 
     // Method to save weather data to a file
     public static void saveWeatherReport(String cityName, double temperature, double humidity, String weatherDescription, double windSpeed, int visibility) {
         try (FileWriter writer = new FileWriter("weather_report.txt", true)) {
             writer.write("City: " + cityName + "\n");
             writer.write("Temperature: " + String.format("%.2f", temperature) + " °C\n");
             writer.write("Humidity: " + humidity + "%\n");
             writer.write("Weather: " + weatherDescription + "\n");
             writer.write("Wind Speed: " + windSpeed + " m/s\n");
             writer.write("Visibility: " + (visibility / 1000.0) + " km\n");
             writer.write("Date: " + java.time.LocalDateTime.now() + "\n\n");
         } catch (IOException e) {
             System.err.println("Error saving weather report: " + e.getMessage());
         }
     }
 
     public static void main(String[] args) {
         Scanner scanner = new Scanner(System.in);
 
         System.out.println("Enter the city, state, taluka, Suburban District name to fetch weather data:");
         String cityName = scanner.nextLine();
 
         System.out.println("Choose temperature unit (1 for Celsius, 2 for Fahrenheit):");
         int choice = scanner.nextInt();
         String units = (choice == 2) ? "imperial" : "metric";
 
         // Replace with your OpenWeatherMap API key
         String apiKey = "02bfe91c358f9d7a3d6736208b58456d";
         String apiUrl = "http://api.openweathermap.org/data/2.5/weather?q=" + cityName + "&appid=" + apiKey + "&units=" + units;
 
         System.out.println("Fetching weather data...");
         String jsonData = fetchData(apiUrl);
 
         if (!jsonData.isEmpty()) {
             displayWeatherData(jsonData);
         } else {
             System.out.println("No data fetched.");
         }
 
         scanner.close();
     }
 }

 // javac -cp ".;lib/json-20241224.jar;src" RestApiConsumer.java
// java -cp ".;lib/json-20241224.jar;src" RestApiConsumer
 
