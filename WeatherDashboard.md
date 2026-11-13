# Python Weather Dashboard

## Presetup

### Step 1: Create Project Directory
Open your terminal and create a folder for your project:
```python
mkdir weather-app
cd weather-app
```
```python

```

### Step 2: Create a Virtual Environment
On macOS/Linux:
```python
python3 -m venv venv
source venv/bin/activate
```
On Windows:
```python
python -m venv venv
venv\Scripts\activate
```
You’ll see `(venv)` at the start of your terminal prompt, confirming it's active.

### Step 3: Install Required Packages
We’ll use the `requests` library to fetch weather data from a free API.
```python
pip install requests matplotlib
```
Save dependencies:
```python
pip freeze > requirements.txt
```

## Level 1 — Get Weather for a Fixed City
We begin with the simplest possible version: one city, one number. We hard-code the coordinates of Abu Dhabi, ask the API for the current temperature, and print it.

Create a file called `weather.py`:
```python
# Start with a fixed location
import requests

latitude = 24.4539
longitude = 54.3773

url = "https://api.open-meteo.com/v1/forecast"

params = {
    "latitude": latitude,
    "longitude": longitude,
    "current": "temperature_2m"
}

response = requests.get(url, params=params)
data = response.json()
temperature = data["current"]["temperature_2m"]
print("Temperature:", temperature, "°C")
```
Expected output:
```python
Temperature: 34.2 °C 
```
Three things are happening here. We send a request to the API with our coordinates, the API replies with JSON (a nested structure of dictionaries and lists), and we dig into that dictionary to pull out the value we want.

Try it yourself: change the coordinates to another city.




## Level 2 — Display More Weather Information
Temperature alone isn’t much of a dashboard. The API can return several values in one request, so we ask for humidity and wind speed too, separating the names with commas.
