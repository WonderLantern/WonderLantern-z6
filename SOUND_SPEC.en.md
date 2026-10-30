# Custom shutter sound requirements

[中文](声音要求.md) · [Back](README.en.md)

For Shuttersound.bin in this three-feature release.

| Field | Required value |
|---|---|
| Format | Little-endian RIFF/WAVE, uncompressed signed 16-bit integer PCM, format tag 1 |
| Sample rate / channels | 8000 Hz, mono |
| Byte rate / block alignment | 16000 bytes/s, 2 bytes |
| Header | Standard 44 bytes; fmt length 16, immediately followed by data |
| PCM data | Non-empty, even byte count, maximum 17280 bytes / 8640 samples |
| Duration / total size | Maximum 1.08 seconds / 17324 bytes |

RIFF and data lengths must match the file. No LIST, JUNK, bext or other extra chunks. Convert MP3, float WAV, stereo or 44.1/48 kHz files first; renaming the extension is insufficient. Oversized sounds are not truncated automatically.

Use `SHUTTER/1.WAV` through `15.WAV`, without leading zeros. The card-root SHUTTER.WAV is not read. Menu numbers are fixed; custom filenames or 16.WAV do not add slots. Put the matching `Shuttersound.bin` and the camera-generated `ShuttersoundMEM.SEL` at the card root.

Four unchanged examples are included: 1 cat (1.08 s), 2 film-camera shutter (0.20 s), 3 bird (0.896 s), and 4 leaf shutter (0.55475 s). Add other numbered slots as needed.

For bursts, prefer 0.10–0.20 s with the recognizable part at the start. Remove leading silence, use short fades and avoid clipping. Every shot cuts off the previous sound and restarts playback; hearing only the beginning of a long sound during a burst is expected. The 1.08 s limit is mandatory; the short-sound recommendation is not a frame-rate guarantee.

After replacing a WAV, select its number or Reload, wait for card activity to finish, and Play to verify. Use direction buttons/OK for the selection list and Play; other main-menu rows retain touch support. Failed loads retain the last usable sound; cold start without a usable sound uses the built-in fallback, so preview after changing a number.
