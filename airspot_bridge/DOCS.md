# AirSpot Bridge

This add-on uses OwnTone to bridge audio to AirPlay speakers and go-librespot to expose a Spotify Connect device.

## Configuration

OwnTone is configurable at `/config/owntone/owntone.conf`.

go-librespot is configurable at `/config/owntone/go-librespot/config.yml`.

The default go-librespot configuration uses Zeroconf authentication and does not contain Spotify username/password fields.

After changing either configuration file, restart the add-on.

## AirPlay reconnects

If playback starts and then OwnTone logs that the AirPlay device closed the RTSP connection, edit `/config/owntone/owntone.conf` and make sure local audio output is disabled:

```text
audio {
	nickname = "None"
	type = "disabled"
}
```

For one speaker that repeatedly disconnects, add a per-device block with the exact OwnTone speaker name:

```text
airplay "Living Room" {
	reconnect = true
}
```

Restart the add-on after changing the file.

## Access OwnTone

OwnTone is available at:

```text
http://[Home Assistant IP]:3689
```

Default OwnTone credentials:

- Username: `admin`
- Password: `owntoneadmin8765`
