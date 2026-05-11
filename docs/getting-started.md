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
  "name": "Calgary",
  "main": {
    "temp": 12.4,
    "feels_like": 11.1,
    "humidity": 45
  },
  "weather": [
    {
      "description": "clear sky"
    }
  ],
  "wind": {
    "speed": 5.2
  }
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
