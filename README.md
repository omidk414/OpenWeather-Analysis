# Weather Analysis and Visualization with Python

# Weather Analysis and Visualization with Python

## Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Part 1: WeatherPy](#part-1-weatherpy)
    - [Requirement 1: Create Plots to Showcase the Relationship Between Weather Variables and Latitude](#requirement-1-create-plots-to-showcase-the-relationship-between-weather-variables-and-latitude)
    - [Requirement 2: Compute Linear Regression for Each Relationship](#requirement-2-compute-linear-regression-for-each-relationship)
4. [Part 2: VacationPy](#part-2-vacationpy)
5. [How to Use the Project and Replicate It](#how-to-use-the-project-and-replicate-it)
6. [Examples](#examples)

## Introduction
Data's true power is its ability to definitively answer questions. So, let's take what you've learned about Python requests, APIs, and JSON traversals to answer a fundamental question: "What is the weather like as we approach the equator?"

Now, we know what you may be thinking: “That’s obvious. It gets hotter.” But, if pressed for more information, how would you prove that?

## Prerequisites
Before starting, ensure you have the following API keys:
- **OpenWeatherMap API Key**: You can obtain it by signing up on the [OpenWeatherMap website](https://home.openweathermap.org/users/sign_up).
- **Geoapify API Key**: You can obtain it by signing up on the [Geoapify website](https://www.geoapify.com/get-started-with-maps-api).

## Part 1: WeatherPy

In this deliverable, you'll create a Python script to visualize the weather of over 500 cities of varying distances from the equator. You'll use the `citipy` Python library, the OpenWeatherMap API, and your problem-solving skills to create a representative model of weather across cities.

For this part, you'll use the `WeatherPy.ipynb` Jupyter notebook provided in the starter code ZIP file. The starter code will guide you through the process of using your Python coding skills to develop a solution to address the required functionalities.

To get started, the code required to generate random geographic coordinates and the nearest city to each latitude and longitude combination is provided.

### Requirement 1: Create Plots to Showcase the Relationship Between Weather Variables and Latitude

To fulfill the first requirement, you'll use the OpenWeatherMap API to retrieve weather data from the cities list generated in the starter code. Next, you'll create a series of scatter plots to showcase the following relationships:

- Latitude vs. Temperature
- Latitude vs. Humidity
- Latitude vs. Cloudiness
- Latitude vs. Wind Speed

### Requirement 2: Compute Linear Regression for Each Relationship

To fulfill the second requirement, compute the linear regression for each relationship. Separate the plots into Northern Hemisphere (greater than or equal to 0 degrees latitude) and Southern Hemisphere (less than 0 degrees latitude). You may find it helpful to define a function in order to create the linear regression plots.

Next, create a series of scatter plots. Be sure to include the linear regression line, the model's formula, and the r^2 values as shown in the example below.

## Part 2: VacationPy

In this deliverable, you'll use your weather data skills to plan future vacations. Additionally, you'll use Jupyter notebooks, the `geoViews` Python library, and the Geoapify API.

The code needed to import the required libraries and load the CSV file with the weather and coordinates data for each city created in Part 1 is provided to help you get started.

Your main tasks will be to use the Geoapify API and the `geoViews` Python library and employ your Python skills to create map visualizations.

## How to Use the Project and Replicate It
Install Dependencies:
Ensure you have Python and Jupyter Notebook installed. Then, install the required Python libraries:

bash
```
pip install matplotlib pandas numpy requests scipy citipy hvplot
```


1. **Clone the Repository**:

Add API Keys:
Create a config.py file in the project directory and add your API keys:

python
```
weather_api_key = "YOUR_OPENWEATHERMAP_API_KEY"
geoapify_api_key = "YOUR_GEOAPIFY_API_KEY"
```

Run ipynb files:
Start preferred ide and open the WeatherPy.ipynb and VacationPy.ipynb notebooks to run the code cells:

## Examples: 
1. Scatter Plot for Latitude vs Wind Speed

python
```
# Build the scatter plots for latitude vs. wind speed
plt.scatter(city_data_df["Lat"], city_data_df["Wind Speed"], edgecolors = "black", alpha = 0.8)

# Incorporate the other graph properties
plt.title("City Latitude vs. Wind Speed (2024-7-17)")
plt.xlabel("Latitude")
plt.ylabel("Wind Speed (m/s)")
plt.grid()

# Save the figure
plt.savefig("output_data/Fig4.png")

# Show plot
plt.show()
```


2. Create a map that displays a point for every city in the `city_data_df` DataFrame. The size of the point should be the humidity in each city.

python
```
%%capture --no-display

# Configure the map plot
humidity_map = city_data_df.hvplot.points(
    'Lng',
    'Lat',
    geo = True,
    tiles = 'EsriNatGeo',
    size = 'Humidity',
    scale = 1,
    color = 'City',
    hover_cols = 'City'
)

# Display the map
humidity_map
```


