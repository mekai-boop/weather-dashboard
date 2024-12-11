{\rtf1\ansi\ansicpg1252\cocoartf2820
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;}
{\colortbl;\red255\green255\blue255;}
{\*\expandedcolortbl;;}
\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\pard\tx720\tx1440\tx2160\tx2880\tx3600\tx4320\tx5040\tx5760\tx6480\tx7200\tx7920\tx8640\pardirnatural\partightenfactor0

\f0\fs24 \cf0 import streamlit as st\
import pandas as pd\
import numpy as np\
import requests\
import matplotlib.pyplot as plt\
\
# API Configuration\
WEATHER_API_KEYS = \{\
    "OpenWeatherMap": "3e05a90825df15adcc4ea7d28d48e144",\
    "WeatherStack": "30d14e69899d4562a95e01b4ca2e7790",\
    "TomorrowIO": "rbdBVL09Uu1bZrW2nPdiQTu7Oe7BxY78",\
    "VisualCrossing": "5CFJLHV2NAGBBF87WGD7CK5QD",\
    "AccuWeather": "yn0bx3fIEwRSHDVrJKKtqAUhdsURmVjY"\
\}\
\
API_URLS = \{\
    "OpenWeatherMap": "https://api.openweathermap.org/data/2.5/forecast",\
    "WeatherStack": "http://api.weatherstack.com/forecast"\
\},\
    "TomorrowIO": "https://api.tomorrow.io/v4/timelines"\
\},\
    "VisualCrossing": "https://weather.visualcrossing.com/VisualCrossingWebServices/rest/services/timeline"\
\},\
    "AccuWeather": "https://dataservice.accuweather.com/forecasts/v1/daily/1day"\
\}\
\
# Fetch Data from APIs\
def fetch_weather_data(location, date):\
    predictions = \{\}\
\
    # OpenWeatherMap API\
    params_owm = \{\
        "q": location,\
        "appid": WEATHER_API_KEYS["OpenWeatherMap"],\
        "units": "metric"\
    \}\
    response_owm = requests.get(API_URLS["OpenWeatherMap"], params=params_owm)\
    if response_owm.status_code == 200:\
        data = response_owm.json()\
        predictions["OpenWeatherMap"] = data['list'][0]['main']['temp']\
\
    # WeatherStack API\
    params_ws = \{\
        "access_key": WEATHER_API_KEYS["WeatherStack"],\
        "query": location\
    \}\
    response_ws = requests.get(API_URLS["WeatherStack"], params=params_ws)\
    if response_ws.status_code == 200:\
        data = response_ws.json()\
        predictions["WeatherStack"] = data['current']['temperature']\
\
    # Tomorrow.io Integration\
    params_tomorrow = \{\
        "location": location,  # Use "latitude,longitude" format if required\
        "apikey": WEATHER_API_KEYS["TomorrowIO"],\
        "fields": ["temperature"],\
        "timesteps": "1d",  # Daily forecast\
        "units": "metric"\
    \}\
    response_tomorrow = requests.get(API_URLS["TomorrowIO"], params=params_tomorrow)\
    if response_tomorrow.status_code == 200:\
        data = response_tomorrow.json()\
        forecast = data['data']['timelines'][0]['intervals']\
        for entry in forecast:\
            if entry['startTime'].startswith(str(date)):\
                predictions["TomorrowIO"] = entry['values']['temperature']\
                break\
\
    # VisualCrossing API Integration\
    params_visualcrossing = \{\
        "key": WEATHER_API_KEYS["VisualCrossing"],\
        "unitGroup": "metric",\
        "include": "days",\
    \}\
    response_visualcrossing = requests.get(f"\{API_URLS['VisualCrossing']\}/\{location\}/\{date\}", params=params_visualcrossing)\
    if response_visualcrossing.status_code == 200:\
        data = response_visualcrossing.json()\
        predictions["VisualCrossing"] = data['days'][0]['temp']\
\
    # AccuWeather API Integration\
    params_accuweather = \{\
        "apikey": WEATHER_API_KEYS["AccuWeather"],\
        "q": location,\
        "metric": True\
    \}\
    response_accuweather = requests.get(API_URLS["AccuWeather"], params=params_accuweather)\
    if response_accuweather.status_code == 200:\
        data = response_accuweather.json()\
        predictions["AccuWeather"] = data['DailyForecasts'][0]['Temperature']['Maximum']['Value']\
\
    # Add more API integrations as needed...\
\
    return predictions\
\
# Calculate Weighted Average\
def calculate_weighted_average(predictions, weights):\
    weighted_sum = sum(predictions[model] * weights.get(model, 1) for model in predictions)\
    total_weight = sum(weights.get(model, 1) for model in predictions)\
    return weighted_sum / total_weight\
\
# Mock Historical Accuracy Weights (Replace with actual weights)\
HISTORICAL_WEIGHTS = \{\
    "OpenWeatherMap": 1.1,\
    "WeatherStack": 1.0\
\}\
\
# Streamlit App\
st.title("Weather Model Dashboard")\
st.subheader("Combine Multiple Weather Models for Precise Predictions")\
\
# Input Section\
location = st.text_input("Enter Location:", "Buffalo, NY")\
date = st.date_input("Select Date:")\
\
if location and date:\
    predictions = fetch_weather_data(location, str(date))\
    \
    # Calculate Prediction\
    weighted_avg = calculate_weighted_average(predictions, HISTORICAL_WEIGHTS)\
    \
    # Display Combined Prediction\
    st.markdown(f"### Combined Predicted Temperature: \{weighted_avg:.2f\} \'b0C")\
    \
    # Model Comparison Table\
    df = pd.DataFrame(\
        \{\
            "Model": predictions.keys(),\
            "Prediction (\'b0C)": predictions.values(),\
            "Weight": [HISTORICAL_WEIGHTS.get(model, 1) for model in predictions]\
        \}\
    )\
    st.dataframe(df)\
\
    # Visualization\
    st.markdown("### Temperature Predictions by Model")\
    plt.figure(figsize=(10, 5))\
    plt.bar(df["Model"], df["Prediction (\'b0C)"], color="skyblue")\
    plt.axhline(weighted_avg, color="red", linestyle="--", label=f"Weighted Avg: \{weighted_avg:.2f\} \'b0C")\
    plt.xlabel("Weather Model")\
    plt.ylabel("Predicted Temperature (\'b0C)")\
    plt.title("Model Predictions")\
    plt.legend()\
    st.pyplot(plt)\
\
    st.markdown("### Historical Weight Analysis")\
    plt.figure(figsize=(10, 5))\
    plt.bar(df["Model"], df["Weight"], color="orange")\
    plt.xlabel("Weather Model")\
    plt.ylabel("Weight")\
    plt.title("Historical Accuracy Weights")\
    st.pyplot(plt)\
\
st.markdown("---")\
st.markdown("*Note: Replace API keys and ensure correct API data extraction for real-world use.")\
}