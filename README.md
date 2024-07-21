# Weather Analysis and Visualization with Python

The first part of this project generates visual representations of cities and their accommodations at random locations using the citipy Python library to identify city names and the OpenWeatherMap API to retrieve weather data, creating a model that shows the relationship between weather conditions and latitude. The second part uses the geoViews Python library, and the Geoapify API to generate a dataframe for the weather data to plan vacations and create a map visualizations.

## Table of Contents
2. [Prerequisites](#prerequisites)
3. [Part 1: WeatherPy](#part-1-weatherpy)
    - [Part 1: Create Plots to Showcase the Relationship Between Weather Variables and Latitude](#part-1-create-plots-to-showcase-the-relationship-between-weather-variables-and-latitude)
    - [Part 2: Compute Linear Regression for Each Relationship](#part-2-compute-linear-regression-for-each-relationship)
4. [Part 2: VacationPy](#part-2-vacationpy)
6. [Examples](#examples)


## Prerequisites
Before starting, ensure you have the following API keys:
- **OpenWeatherMap API Key**: You can obtain it by signing up on the [OpenWeatherMap website](https://home.openweathermap.org/users/sign_up).
- **Geoapify API Key**: You can obtain it by signing up on the [Geoapify website](https://www.geoapify.com/get-started-with-maps-api).

Install Dependencies:
Ensure you have Python and Jupyter Notebook installed. Then, install the required Python libraries:

bash
```
pip install matplotlib pandas numpy requests scipy citipy hvplot geoviews
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

## Part 1: WeatherPy

WeatherPy visualizes the weather of over 500 cities of varying distances from the equator. The `citipy` Python library, and the OpenWeatherMap API are used to create a representative model of weather across cities.

### Part 1: Create Plots to Showcase the Relationship Between Weather Variables and Latitude

To fulfill the first requirement, you'll use the OpenWeatherMap API to retrieve weather data from the cities list generated in the starter code. Next, you'll create a series of scatter plots to showcase the following relationships:

- Latitude vs. Temperature
- Latitude vs. Humidity
- Latitude vs. Cloudiness
- Latitude vs. Wind Speed

### Requirement 2: Compute Linear Regression for Each Relationship

To fulfill the second requirement, compute the linear regression for each relationship. Separate the plots into Northern Hemisphere (greater than or equal to 0 degrees latitude) and Southern Hemisphere (less than 0 degrees latitude). You may find it helpful to define a function in order to create the linear regression plots.

Next, create a series of scatter plots. Be sure to include the linear regression line, the model's formula, and the r^2 values as shown in the example below.

## Part 2: VacationPy
The `geoViews` Python library, and the Geoapify API are necessary for this section.

Steps:
    1. Create a map displaying a point for every city in the city_data_df DataFrame using the Geoviews library.
    2. Filter the city_data_df using preferred weather conditions such as temperature, wind speed, cloudiness and humiditiy.
    3. Create a new DataFrame called hotel_df. Using Geoapify's API, locate hotels within a 10,000 meter radius of each city’s coordinates.
    4. Using Geoviews library, create dymnamic maps to show locations with the hotels listed when hovering over the map.

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


