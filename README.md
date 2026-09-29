# Space Debris Predictor

Real-time space debris conjunction detection system. Monitors the ISS against 584 tracked debris objects from the Cosmos 2251 collision field, fetching live TLE data from Celestrak and sending Telegram alerts when debris approaches within 50 km.

## Result

Successfully detected a close approach of **81.73 km** between the ISS and COSMOS 2251 DEB over a 24-hour scan window.

## How It Works

1. Fetches TLE orbital elements from Celestrak (ISS + Cosmos 2251 debris)
2. Propagates orbits using Skyfield (SGP4)
3. Scans 24-hour windows at 1-minute resolution
4. Finds the closest approach distance across all 584 debris objects
5. Sends Telegram alert if any object approaches within 50 km
6. Runs continuously in a 10-minute loop

## Requirements

- skyfield
- requests
- Python 3.10+ or Google Colab

## How to Run

1. Open `orbital_engine.ipynb` in Google Colab
2. Set your Telegram bot token in Colab Secrets as `TELEGRAM_BOT_TOKEN`
3. Set your Telegram chat ID in Colab Secrets as `TELEGRAM_CHAT_ID`
4. Run all cells

## Limitations

- Uses SGP4 only (no J2 short-period terms, no atmospheric drag)
- Single-target monitoring (ISS only)
- 50 km alert threshold is hardcoded (configurable in code)

## Author

Shivaprabha
