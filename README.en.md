# Wonder Lantern · Nikon Z6 Three-Feature Release v1

[中文](README.md)

2026-10-30. For the **original Nikon Z6, based on C3.80**. Includes custom shutter sounds, extended exposure and countdown, and custom framing guides with recoverable NEF crop metadata.

## Files and installation

```text
EG162080.BIN                 One main firmware for both languages
cn/                         Chinese cores; copy all three files to card root
  Shuttersound.bin
  Slowshutter.bin
  Grid.BIN
en/                         English cores, with the same filenames
SHUTTER/1.WAV through 4.WAV  Four unchanged sound examples from earlier releases
```

1. Turn the camera off. Back up your sounds, settings files and current matching firmware/core set.
2. Copy `EG162080.BIN` and the three files **inside** either `cn/` or `en/` to the card root. Do not copy the language directory as a substitute. This release updates both the main firmware and Grid core; use the matching files.
3. For the supplied examples, also copy `SHUTTER/` to the card root. Copy selectively if you already have custom sounds, to avoid replacing files with the same names.
4. With sufficient battery power, perform the update from the camera's **Firmware version** menu. Do not interrupt power. Turn the camera off and on after completion, then wait for loading and card activity to finish. The three features are then available in Setup.

To change language later, turn the camera off and replace the three cores. Both languages share the same main firmware. Custom menu language comes from the cores, independently of the factory language setting. A missing core omits its feature menu while the other cores can still load. Do not rename or mix older SHCORE/SLOWCORE or standalone-feature cores with this firmware.

## Features

- **Shutter sound:** 15 numbered slots, On/Off, selection, Reload and Play. Each shot restarts the sound and cuts off the previous one during a burst. Use direction buttons/OK for the selection list and Play; other main-menu rows retain touch support. Replacing a WAV does not require reflashing; select its number or Reload, then preview it.
- **Long Exposure & Countdown:** Enable or disable in Setup. Preserves the existing extended exposure and top LCD countdown behavior, restoring the shutter display after completion or cancellation. The switch is remembered on the card.
- **Custom framing guides:** Direct On/Off choices in the second-level menu, plus Select and Crop & Mask entries. Slot 1 is rule of thirds; slots 2–5 are 21:9, 65:25, 4:3 and 2.35:1; slots 6–10 are empty. Factory framing-grid switch linkage is retained. With Crop & Mask enabled, the area outside the frame is blacked out on supported LCD live view and recoverable crop metadata is written to NEF files. Lightroom Develop can adjust the crop or restore the full image. JPEG-only files do not receive this metadata; with JPEG+NEF, only the NEF receives it.

## Settings and sounds

The camera creates these files at the card root. No default settings files are included; do not overwrite your settings with someone else's records:

| File | Stored setting |
|---|---|
| ShuttersoundMEM.SEL (8B) | Sound number and switch |
| SlowshutterMEM.sel (8B) | Long-exposure switch |
| GridMEM.SEL (16B) | Guide switch, slot, Crop & Mask |

When upgrading from the preceding three-feature release, keep all three files. From the older standalone sound version, only if the new file is absent, back up and rename the 8-byte `ShutterMEM.SEL` to `ShuttersoundMEM.SEL`. The earlier `SHUTTER.SEL` can be treated the same way. Change only the settings filename, not its contents; this does not apply to core BIN files. Wait for card activity to finish before powering off. Single-file settings do not guarantee atomic saving during sudden power loss.

Sounds use `SHUTTER/1.WAV` through `15.WAV`; unused slots may be left empty. Examples 1–4 are the existing cat, film-camera shutter, bird and leaf-shutter sounds, unchanged. See [sound requirements](SOUND_SPEC.en.md).

## Known limits

**The existing USB/PixelCake tethering slowdown issue remains under investigation and is not fixed in this release.**
