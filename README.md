# AirSpot Bridge add-on for Home Assistant

AirSpot Bridge lets you play Spotify on AirPlay speakers from Home Assistant.

The add-on runs:

- OwnTone for AirPlay output and the web interface.
- go-librespot for the Spotify Connect device.

No Spotify username or password is stored in the add-on. go-librespot uses Zeroconf, so you select the advertised `AirSpot Bridge` device from the official Spotify app on the same network.

## Installation

1. In Home Assistant, go to `Settings` -> `Add-ons` -> `Add-on Store`.
2. Open the three-dot menu in the top right and choose `Repositories`.
3. Add this repository URL:

   ```text
   https://github.com/zamarawka/airspot-bridge
   ```

4. Reload the Add-on Store page.
5. Find `AirSpot Bridge`, open it, and click `Install`.
6. Start the add-on.
7. Open the OwnTone web UI from the add-on page, or visit:

   ```text
   http://[Home Assistant IP]:3689
   ```

## How to use

1. Open OwnTone and select or pair your AirPlay speaker.
2. Open Spotify on a phone, tablet, or desktop on the same network.
3. Choose the `AirSpot Bridge` Spotify Connect device.
4. Spotify audio should route through OwnTone to the selected AirPlay speaker.

## Configuration

Default configuration files are created automatically on first start:

- OwnTone: `/config/owntone/owntone.conf`
- go-librespot: `/config/owntone/go-librespot/config.yml`

After changing either file, restart the add-on.

Default OwnTone credentials:

- Username: `admin`
- Password: `owntoneadmin8765`

## Notes

- Home Assistant host networking is required so Spotify Connect, OwnTone, and AirPlay discovery work on the local network.
- Spotify Connect requires a Spotify client on the same network.
- The add-on keeps the audio FIFO path `/music/librespot-java` for compatibility with previous OwnTone setups.

## Support

If something does not work, open an issue on GitHub and include the add-on log from Home Assistant.
