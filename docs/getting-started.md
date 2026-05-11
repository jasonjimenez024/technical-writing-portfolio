# Getting Started with the OpenWeather API

The OpenWeather API gives you access to real-time weather data for any location in the world. You send a request with a city name or coordinates, and the API returns current conditions — temperature, humidity, wind speed, cloud cover, and more.

This guide walks you through making your first API call in under five minutes.

## What you need before you start

- An OpenWeather account (free at [openweathermap.org](https://openweathermap.org))
- An API key (generated automatically when you sign up)
- A way to make HTTP requests — this guide uses [Postman](https://postman.com), a free tool that requires no coding

## Step 1: Get your API key

After signing up, go to your profile and click **My API Keys**. You will see a key called Default. Copy it.

Note: new API keys take up to two hours to activate. If you receive a 401 Unauthorized error on your first call, wait and try again.

## Step 2: Make your first request

Open Postman and create a new HTTP request. Set the method to GET and paste the following URL into the address bar, replacing `YOUR_API_KEY` with your actual key:
https://api.openweathermap.org/data/2.5/weather?q=Calgary&appid=YOUR_API_KEY&units=metric
Click **Send**.

## Step 3: Read the response

A successful request returns a JSON object with current weather data for Calgary. It looks like this:

```json
{
  "coord": {
    "lon": -114.0853,
    "lat": 51.0501
  },
  "weather": [
    {
      "id": 803,
      "main": "Clouds",
      "description": "broken clouds",
      "icon": "04d"
    }
  ],
  "base": "stations",
  "main": {
    "temp": 8.95,
    "feels_like": 4.54,
    "temp_min": 6.94,
    "temp_max": 9.97,
    "pressure": 1016,
    "humidity": 73,
    "sea_level": 1016,
    "grnd_level": 890
  },
  "visibility": 10000,
  "wind": {
    "speed": 11.32,
    "deg": 360,
    "gust": 14.4
  },
  "clouds": {
    "all": 75
  },
  "dt": 1778511614,
  "sys": {
    "type": 2,
    "id": 2011327,
    "country": "CA",
    "sunrise": 1778500332,
    "sunset": 1778555599
  },
  "timezone": -21600,
  "id": 5913490,
  "name": "Calgary",
  "cod": 200
}
```

This is a simplified version. The full response contains additional fields covered in the [endpoint reference](./endpoints/current-weather.md).

## What the main fields mean

| Field | What it tells you |
|---|---|
| `name` | The city name the API matched to your query |
| `main.temp` | Current temperature in the unit you requested |
| `main.feels_like` | Perceived temperature accounting for wind and humidity |
| `main.humidity` | Relative humidity as a percentage |
| `weather.description` | Plain-language description of current conditions |
| `wind.speed` | Wind speed in metres per second (metric) |

## Next steps

- [Authentication](./authentication.md) — how API keys work and what happens when they fail
- [Current Weather Endpoint](./endpoints/current-weather.md) — full parameter and response reference
- [Error Codes](./reference/error-codes.md) — what errors mean and how to fix them
