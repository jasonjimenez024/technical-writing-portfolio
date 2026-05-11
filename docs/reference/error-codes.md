# Error Codes

The OpenWeather API returns standard HTTP status codes. When a request 
fails, the response body includes a `cod` field with the error code 
and a `message` field explaining what went wrong.

## 200 — Success

The request was successful. Weather data is returned in the response body.

```json
{
  "cod": 200,
  "name": "Calgary"
}
```

## 401 — Unauthorized

Your API key is missing, incorrect, or not yet active.

```json
{
  "cod": 401,
  "message": "Invalid API key. Please see https://openweathermap.org/faq#error401 for more info."
}
```

**Common causes:**

| Cause | Fix |
|---|---|
| Key not yet active | Wait up to two hours after signup |
| Key missing from request | Add `appid=YOUR_KEY` to the URL |
| Key copied incorrectly | Return to My API Keys and copy again |

## 404 — Not Found

The city name in your request did not match any location in the 
OpenWeather database.

```json
{
  "cod": "404",
  "message": "city not found"
}
```

**Common causes:**

| Cause | Fix |
|---|---|
| Typo in city name | Check spelling and try again |
| City name too vague | Add a country code: `q=Paris,FR` |
| City not in database | Try searching by coordinates instead: `lat=48.85&lon=2.35` |

## 429 — Too Many Requests

You have exceeded the rate limit for your API plan. The free tier 
allows 60 calls per minute and 1,000,000 calls per month.

```json
{
  "cod": 429,
  "message": "Your account is temporary blocked due to exceeding of requests limitation of your subscription type."
}
```

Reduce your request frequency or upgrade your plan.

## 500 — Internal Server Error

An unexpected error occurred on OpenWeather's servers. This is not 
caused by your request.

```json
{
  "cod": 500,
  "message": "Internal error"
}
```

Wait a few minutes and try the request again. If the error persists, 
check the [OpenWeather status page](https://openweathermap.org).

## Related

- [Authentication](../authentication.md) — API key setup and security
- [Getting Started](../getting-started.md) — making your first request
- [Current Weather Endpoint](../endpoints/current-weather.md) — full 
parameter reference
