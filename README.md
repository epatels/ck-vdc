# CK Video Downloader and Converter

A Windows desktop app for downloading videos and audio with [yt-dlp](https://github.com/yt-dlp/yt-dlp) and converting media files with [FFmpeg](https://ffmpeg.org/). Modern Qt interface with dark and light themes.

```
winget install epatels.CKVideoDownloaderConverter
```

Or download the latest `CKVDC-Setup-<version>.exe` from the [Releases](https://github.com/epatels/ck-vdc/releases) page and run it. The app checks for updates and offers new versions.

## Features

**Downloading**
- Paste or drop links; single videos, playlists and channels (pick which videos to add)
- Playlist videos are queued oldest first, with an upload-date column
- Output files are prefixed with the video date (`2024-01-31 - Title`), optional in Settings
- Parallel downloads, pause / resume / cancel, drag to reorder the queue
- Per-video options with a format / stream picker, plus presets (including audio-only M4A and FLAC)
- Live streams and upcoming premieres: wait for the start, record, and stop to finish with a clean remux
- Optional thumbnail, metadata and source-URL saving; download history

**Automation**
- **Queue persistence:** unfinished items are saved and offered back on next launch (resume and start, restore only, or discard)
- **Auto-retry:** network, rate-limit and unknown failures retry automatically (0–5 times, set in Settings)
- **Subscriptions:** follow a channel or playlist; new videos are checked periodically and queued oldest first, in a subfolder named after the source
- **When finished:** do nothing, sleep, shut down or close the app, with a cancellable countdown
- **Auto-convert:** run finished downloads through a chosen converter preset
- **Schedule:** start the queue at a set time, with an optional stop time

**Converter**
- Batch-convert audio and video with presets (MP4 H.264 / H.265, MKV, and more)

**Other**
- Dependency check for yt-dlp and FFmpeg, in-app update check, optional context-menu entry, optional anonymous telemetry (asked on first run)
- Resizable table columns with remembered widths

## Requirements

- Windows 10 or later
- yt-dlp and FFmpeg are included with the installer; the app can check for and update yt-dlp

## Settings and data

Stored in `%APPDATA%\CKVDC\`:

| File | Contents |
|---|---|
| `config.json` | Settings |
| `history.json` | Download history |
| `queue.json` | Unfinished queue |
| `subscriptions.json` | Followed channels and playlists |

## Third-party software and licences

CK Video Downloader and Converter is proprietary freeware; the application itself is not open source. It includes or uses the following open-source components, each under its own licence:

| Component | Licence | Notes |
|---|---|---|
| [Qt for Python (PySide6)](https://doc.qt.io/qtforpython-6/) | LGPL v3 | Used as dynamically linked libraries, unmodified. You may replace them with your own build of the same version. Licence text and Qt source: <https://www.qt.io/download-open-source> |
| [yt-dlp](https://github.com/yt-dlp/yt-dlp) | The Unlicense (public domain) | Bundled as `yt-dlp.exe`, unmodified |
| [FFmpeg](https://ffmpeg.org/) | GPL v3 (gyan.dev "essentials" build) | Bundled as `ffmpeg.exe` and `ffprobe.exe`, unmodified and run as separate programs. Source code: <https://www.gyan.dev/ffmpeg/builds/> and <https://ffmpeg.org/download.html> |

The full licence texts and notices are in the `licenses` folder of the installation directory.

This software is provided as is, without warranty. Download only content you have the right to download, and respect the terms of the sites you use.

## Credits

Built on yt-dlp, FFmpeg and Qt for Python (PySide6).
