# Authentication

The OpenWeather API uses API keys to control access. Every request you 
send must include a valid key. Without one, the API rejects the request 
and returns an error.

## What is an API key

An API key is a unique string of characters tied to your account. It 
tells OpenWeather who is making the request and whether that account 
has permission to access the data.

Think of it like a building key card. The door doesn't know your name. It just checks whether your card is valid.

## How to get your key

1. Create a free account at [openweathermap.org](https://openweathermap.org)
2. Click your profile icon in the top right
3. Select **My API Keys**
4. Copy the key listed under **Default**

New keys take up to two hours to activate. During that window, requests 
return a `401 Unauthorized` error. This is expected — wait and try again.

## How to include your key in a request

Add your API key as a query parameter called `appid` at the end of 
the request URL:

https://api.openweathermap.org/data/2.5/weather?q=Calgary&appid=YOUR_API_KEY

Replace `YOUR_API_KEY` with your actual key. The key goes in the URL 
itself — no headers or special configuration required.

## What happens when authentication fails

If your key is missing, incorrect, or not yet active, the API returns 
a `401 Unauthorized` response:

```json
{
  "cod": 401,
  "message": "Invalid API key. Please see https://openweathermap.org/faq#error401 for more info."
}
```

Common causes:

| Problem | Fix |
|---|---|
| Key not yet active | Wait up to two hours after signup |
| Key copied incorrectly | Return to My API Keys and copy again |
| Key missing from URL | Ensure `appid=YOUR_KEY` is included |
| Key deleted or expired | Generate a new key in your account |

## Keeping your key secure

Your API key is private. Anyone who has it can make requests counted against your account's rate limits. Do not paste it directly into code you share publicly 
or commit it to a public repository.

For the purposes of this guide, the key is included directly in the 
URL for simplicity. In a production application, store it as an 
environment variable.

## Next steps

- [Getting Started](../getting-started.md) — make your first API call
- [Current Weather Endpoint](../endpoints/current-weather.md) — full parameter and response reference
