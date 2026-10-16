# Custom Shutter Sound · Sound Specifications

Applies to: Nikon Z6 C3.80 custom shutter sound resident v3. Updated: 2026-10-07.

## Required Format

| Item | Requirement |
|---|---|
| File container | RIFF/WAVE, little-endian |
| Encoding | Uncompressed signed 16-bit integer PCM, format tag = 1 |
| Sample rate | 8000 Hz |
| Channels | Mono |
| Byte rate / block alignment | 16000 bytes/s / 2 bytes |
| File header | Standard 44-byte header; fmt chunk length 16; data chunk immediately follows |
| PCM data length | Non-empty, even number of bytes; at most 17280 bytes, or 8640 samples |
| Maximum duration | 1.08 seconds, including fades and silence |
| Maximum file size | 17324 bytes |

The declared RIFF and data lengths must match the actual file. Do not include extra chunks such as LIST, JUNK, bext, or cover art. MP3, floating-point WAV, stereo, and 44.1/48 kHz files must be converted first; changing the file extension is not sufficient. The firmware does not automatically trim files that exceed the limit. If WAV loading fails, the previous usable sound is retained.

## File Names on the Card

| Menu selection | Path |
|---|---|
| Card default | /SHUTTER.WAV |
| 1 | /SHUTTER/1.WAV |
| 2 | /SHUTTER/2.WAV |
| 3 | /SHUTTER/3.WAV |
| 4 | /SHUTTER/4.WAV |

Use `1.WAV`, not `01.WAV`. The uppercase ASCII names shown above are recommended. The menu displays fixed numbers and does not read custom names. Adding `5.WAV` does not add a menu option. Older names such as `MEOW.WAV` are not read as numbered slots in this version.

`SHCORE.BIN` is the required matching core; keep it at the card root. `SHUTTER.SEL` is a camera-generated configuration file that stores the selected number and On/Off setting. After a successful save, these settings are restored on restart. Do not edit the configuration file manually.

## Sound Preparation Suggestions

- For continuous shooting: prioritize 0.10–0.20 seconds, with the recognizable part within the first 50 ms where possible.
- Short cues: 0.20–0.50 seconds; complete sound effects: 0.50–1.08 seconds.
- Remove leading silence, aiming for no more than 5 ms. Use a fade-in of about 1–3 ms and a fade-out of about 5–10 ms.
- Keep peaks at or below −0.5 dBFS to avoid clipping. As a starting point, adjust the RMS level of the active portion of each sound to about −8 dBFS, then refine based on peaks and playback on the camera. These are preparation suggestions; the firmware does not automatically normalize sounds.

Each photo restarts playback and cuts off the previous sound. Sounds are neither queued nor mixed. Hearing only the beginning of a long sound during continuous shooting is expected. The 1.08-second limit is a hard format limit.

## Quick Customization Workflow

1. Keep the original recording. Create a separate trimmed version and remove leading silence.
2. In an audio editor, convert it to mono, 8000 Hz, PCM16, and adjust fades and loudness.
3. Export a WAV with the standard 44-byte header and no additional metadata. Check its duration and file size.
4. Name the file for the target numbered slot and copy it to the card.
5. Select that number or **Reload** on the camera. Wait for card access to finish, confirm with **Play**, then test short-exposure single shots and continuous shooting.

All examples in the first release package are 0.20-second synthesized test sounds and can be replaced directly.
