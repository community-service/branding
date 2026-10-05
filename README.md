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

Build `.moti`, `.motn` -> `m4v` (requires Apple Motion and Compressor)

```sh
COMPRESSOR="/Applications/Compressor.app/Contents/MacOS/Compressor"
ROOT="$(pwd)"
SETTING="$ROOT/Video/Apple Devices 4K.compressorsetting"
SOURCE="$ROOT/Video"
RENDERED="$ROOT/Rendered"
mkdir -p "$RENDERED"
find "$SOURCE" -type f \( -name '*.moti' -o -name '*.motn' \) ! -path "$RENDERED/*" -print0 |
while IFS= read -r -d '' FILE; do
  rel="${FILE#"$SOURCE"/}"
  out="$RENDERED/${rel%.*}.m4v"
  mkdir -p "$(dirname "$out")"
  "$COMPRESSOR" \
    -batchname "$(basename "${rel%.*}")" \
    -jobpath "$FILE" \
    -settingpath "$SETTING" \
    -locationpath "$out"
done
```

Build `.svg` -> `.png` (requires `brew install librsvg`)

```sh
find . -type f -name '*.svg' ! -path './Rendered/*' -print0 |
while IFS= read -r -d '' f; do
  rel="${f#./}"
  out="Rendered/${rel%.svg}.png"
  mkdir -p "$(dirname "$out")"
  rsvg-convert -w 1024 -o "$out" "$f"
done
```

