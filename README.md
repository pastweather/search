# Weather Archive

A single-page tool for looking up **historical hourly weather** for any location — including yesterday and earlier today, the cases most weather apps make oddly difficult.

🔗 **Live:** https://zebraavatar.github.io/weather-archive/

## What it does

- Search any city or place by name (no need to know coordinates), or use your browser's location.
- Pick a date range (up to 31 days) and get a detailed **hourly breakdown**: temperature, feels-like, humidity, precipitation, rain chance, wind speed and direction, cloud cover, visibility, and a plain-language conditions description.
- A temperature sparkline shows the shape of the whole period at a glance.
- Toggle between metric (°C, km/h, mm) and imperial (°F, mph, in).

## How it works

All data comes from the [Open-Meteo](https://open-meteo.com/) API, which is free and requires no API key.

- **Recent dates** (within ~90 days, including today) are served by Open-Meteo's forecast endpoint, which is continuously updated.
- **Older dates** are served by the ERA5 historical archive, which reaches back to 1940.

Because the archive lags real time by roughly 5 days, requests near that boundary fall back to the other endpoint automatically. Note that a few fields — such as rain *probability* — only exist for forecast-era dates and will show `—` for older historical queries; this is expected, not an error.

## Running it

It's a single static `index.html` with no build step and no dependencies beyond the Open-Meteo and geocoding endpoints. Open the file locally in a browser, or host it anywhere that serves static files (GitHub Pages, Netlify, etc.).

## Privacy

Location lookups and weather requests go directly from your browser to Open-Meteo. Nothing is stored or sent anywhere else.

## License

MIT
