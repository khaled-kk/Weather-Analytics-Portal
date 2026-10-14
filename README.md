# OpenWeatherMap API Exercises (DMET1042)

A Jupyter/Colab notebook with four small interactive Python console programs that call the OpenWeatherMap REST API with `requests` and print the results. Written for the DMET1042 course.

## What the Notebook Contains

`DMET1042.ipynb` has four code cells, each a separate program driven by `input()` prompts:

1. **Current weather** – asks for a city, calls `/data/2.5/weather` (metric units) and prints temperature, description, humidity, pressure, wind speed/direction, cloudiness, visibility, and sunrise/sunset (UTC). Also prints the request URL, headers and raw response. Repeats every 10 seconds until the user answers "yes" to terminate.
2. **Forecast** – asks for a start date, end date and city, calls `/data/2.5/forecast` and prints each 3-hour forecast entry (timestamp, description, humidity, pressure, wind, cloudiness, visibility).
3. **Weather for agriculture** – asks for a city, crop name and units (metric/imperial), prints the current weather, then prints a fixed set of "ideal conditions" (25°, 60% humidity, 8 sunlight hours); these values are hard-coded and the same for every crop.
4. **Travel transport suggestion** – asks for origin city, destination city and date, fetches current weather for both, and prints a rule-based suggestion: car/train if either description contains "rain", air-conditioned transport if either temperature is above 30 °C, otherwise any mode.

## Known Limitations

- The forecast endpoint ignores the `start_date`/`end_date` parameters, so cell 2 always prints the standard 5-day/3-hour forecast; its temperature line reads a non-existent `day` key and prints `None`, and sunrise is always `None`.
- Cells 2–4 use `UPDATE_INTERVAL`, which is only defined in cell 1, so run cell 1 first.
- Cell 4 asks for a travel date but always uses *current* weather.

## Sample Output (saved in the notebook)

Cell 1, city "cairo":

```
Weather in Cairo, EG:
Temperature: 26.42°C
Description: clear sky
Humidity: 69%
Pressure: 1014 hPa
Wind Speed: 4.63 m/s
Wind Direction: 30°
Cloudiness: 0%
Visibility: 10.0 km
Sunrise: 03:32:23 UTC
Sunset: 16:17:47 UTC
```

Cell 4, Cairo → Berlin: `clear sky, 26.42°C` / `clear sky, 13.06°C` → "You can consider any mode of transportation based on your preference!"

## Tech Stack

- Python 3, Jupyter / Google Colab
- `requests`, `datetime`, `time`
- OpenWeatherMap Current Weather and 5-day Forecast APIs

## How to Run

1. Open `DMET1042.ipynb` in Jupyter or Google Colab.
2. Get a free API key from [OpenWeatherMap](https://openweathermap.org/api) and set it as `API_KEY` in each cell (cell 4 uses a local `api_key` variable).
3. Run cell 1 first, then any other cell, and answer the prompts.

---

*Developed by Khaled Walid*
