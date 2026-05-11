# Current Weather Endpoint

Returns current weather conditions for a specified location.

## Endpoint
GET https://api.openweathermap.org/data/2.5/weather

## Parameters

| Parameter | Required | Description |
|---|---|---|
| `q` | Yes* | City name. Example: `q=Calgary` |
| `lat` | Yes* | Latitude coordinate. Use with `lon`. |
| `lon` | Yes* | Longitude coordinate. Use with `lat`. |
| `appid` | Yes | Your API key |
| `units` | No | `metric` (Celsius), `imperial` (Fahrenheit), or `standard` (Kelvin). Defaults to `standard`. |
| `lang` | No | Language for the `description` field. Example: `lang=fr` for French. |

*Use either `q` or `lat`/`lon`. Not both.

## Example request

By city name:

https://api.openweathermap.org/data/2.5/weather?q=Calgary&appid=YOUR_API_KEY&units=metric

By coordinates:

## Response fields

| Field | Type | Description |
|---|---|---|
| `name` | string | City name matched to your query |
| `main.temp` | float | Current temperature |
| `main.feels_like` | float | Perceived temperature |
| `main.temp_min` | float | Minimum temperature at the location |
| `main.temp_max` | float | Maximum temperature at the location |
| `main.pressure` | integer | Atmospheric pressure in hPa |
| `main.humidity` | integer | Relative humidity as a percentage |
| `weather[0].id` | integer | Weather condition code |
| `weather[0].main` | string | Weather group. Example: `Rain`, `Snow`, `Clear` |
| `weather[0].description` | string | Plain-language description of conditions |
| `weather[0].icon` | string | Icon code for the current conditions |
| `wind.speed` | float | Wind speed |
| `wind.deg` | integer | Wind direction in degrees |
| `clouds.all` | integer | Cloud coverage as a percentage |
| `dt` | integer | Time of data calculation as a Unix timestamp |
| `sys.country` | string | Country code. Example: `CA` |
| `sys.sunrise` | integer | Sunrise time as a Unix timestamp |
| `sys.sunset` | integer | Sunset time as a Unix timestamp |
| `timezone` | integer | Timezone offset from UTC in seconds |
| `cod` | integer | Response status code. `200` means success. |

## Example response

```json
{
  "name": "Calgary",
  "main": {
    "temp": 12.4,
    "feels_like": 11.1,
    "temp_min": 10.2,
    "temp_max": 14.1,
    "pressure": 1013,
    "humidity": 45
  },
  "weather": [
    {
      "id": 800,
      "main": "Clear",
      "description": "clear sky",
      "icon": "01d"
    }
  ],
  "wind": {
    "speed": 5.2,
    "deg": 270
  },
  "clouds": {
    "all": 0
  },
  "sys": {
    "country": "CA",
    "sunrise": 1715856000,
    "sunset": 1715910000
  },
  "timezone": -21600,
  "dt": 1715880000,
  "cod": 200
}
```

## Notes

- All timestamps are Unix time. To convert: divide by 1 and format 
with a date library, or use an online converter.
- Wind speed is in metres per second when `units=metric`.
- The `weather` field is an array. Most responses contain one item. 
Access it with `weather[0]`.

## Related

- [Getting Started](../getting-started.md)
- [Authentication](../authentication.md)
- [Error Codes](../reference/error-codes.md)
