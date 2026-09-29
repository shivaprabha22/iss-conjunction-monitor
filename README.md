# ISS Conjunction Monitor

Real-time debris conjunction detection system for the International Space Station. Fetches live TLE data from Celestrak and monitors 584 tracked debris objects from the Cosmos 2251 collision field, sending Telegram alerts when any object approaches within 50 km of the ISS.

## Result

Successfully detected a close approach of **81.73 km** between the ISS and COSMOS 2251 DEB over a 24-hour scan window.

## Scope

- **Primary target:** ISS only
- **Debris catalog:** 584 objects from the Cosmos 2251 collision
- **This is not a full SDA system** — it is a focused demonstration of conjunction detection against a single target and debris field

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
- Single debris field (Cosmos 2251 only)
- 50 km alert threshold is hardcoded

## Future Work

- Extend to all ~35,000 tracked objects
- Add multiple primary targets (active satellites, other stations)
- Include additional debris fields (Fengyun, Iridium 33)
- Replace SGP4 with J2-accurate propagator

## Author

Shivaprabha
