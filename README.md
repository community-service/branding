# Community Service Hour branding

This repository has the on-brand media and visuals we use on the hour.gg website, our livestream and shows.

## Style guide

todo: take existing style decisions from existing media, document it here nicely, and then update things to be more consistent/on-brand as appropriate.

### Font

* Logo font is Rockwell (only available on macOS?) // should we be exporting to traced paths on graphics svgs?
* Alternate font is Courier New

### Colors

<div style="width: 20px; height: 20px; background-color: #341334; display:inline-block; vertical-align: middle"></div> Purple #341334

<div style="width: 20px; height: 20px; background-color: #f22f54; display:inline-block; vertical-align: middle"></div> Pink #f22f54




## Music

[Verified Picasso - Scary Island](Verified Picasso - Scary Island) licensed freely "You're free to use this song in any of your videos"

## Build

Requires Apple Motion and Compressor.

```sh
COMPRESSOR="/Applications/Compressor.app/Contents/MacOS/Compressor"
ROOT="$(pwd)"
SETTING="$ROOT/Video/Apple Devices 4K.compressorsetting"

mkdir -p "$ROOT/Rendered"

"$COMPRESSOR" \
  -batchname "2023-06 CSH starting soon" \
  -jobpath "$ROOT/Video/2023-06 CSH starting soon.moti" \
  -settingpath "$SETTING" \
  -locationpath "$ROOT/Rendered/2023-06 CSH starting soon.m4v"

"$COMPRESSOR" \
  -batchname "2026-09-25 CSH episode intro" \
  -jobpath "$ROOT/Video/2026-09-25 CSH episode intro.moti" \
  -settingpath "$SETTING" \
  -locationpath "$ROOT/Rendered/2026-09-25 CSH episode intro.m4v"
```

