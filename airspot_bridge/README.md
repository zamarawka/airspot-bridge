# AirSpot Bridge

Play Spotify on AirPlay speakers from Home Assistant.

AirSpot Bridge combines OwnTone and go-librespot:

- OwnTone sends audio to AirPlay speakers and provides the web interface.
- go-librespot exposes a Spotify Connect device named `AirSpot Bridge`.

No Spotify username or password is configured in the add-on. Select `AirSpot Bridge` from an official Spotify app on the same network.

## Getting started

1. Start the add-on.
2. Open the OwnTone web UI from the add-on page.
3. Select or pair your AirPlay speaker in OwnTone.
4. Open Spotify and choose the `AirSpot Bridge` Spotify Connect device.

OwnTone is also available at:

```text
http://[Home Assistant IP]:3689
```

## Configuration

Default configuration files are created on first start:

- OwnTone: `/config/owntone/owntone.conf`
- go-librespot: `/config/owntone/go-librespot/config.yml`

After changing either file, restart the add-on.

Default OwnTone credentials:

- Username: `admin`
- Password: `owntoneadmin8765`

## Notes

- The add-on uses host networking for local discovery.
- Spotify Connect and AirPlay devices must be reachable from the Home Assistant network.
- The Spotify audio FIFO is `/music/librespot-java` for compatibility with earlier setups.
- If an AirPlay speaker disconnects after playback starts, check `/config/owntone/owntone.conf` and make sure `audio` uses `type = "disabled"`.
