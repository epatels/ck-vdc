<div align="center">

<img src="https://raw.githubusercontent.com/epatels/ck-vdc/main/vdc.png" width="96" alt="CK VDC icon">

# CK Video Downloader and Converter

Download videos and playlists with yt-dlp. Convert media with FFmpeg. One tidy queue.

<a href="https://apps.microsoft.com/detail/9NDXZ7087GLM">
  <img src="https://get.microsoft.com/images/en-us%20dark.svg" width="200" alt="Get it from Microsoft">
</a>

[![Latest release](https://img.shields.io/github/v/release/epatels/ck-vdc?label=release)](https://github.com/epatels/ck-vdc/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/epatels/ck-vdc/total)](https://github.com/epatels/ck-vdc/releases)
![Platform](https://img.shields.io/badge/Windows-10%20%7C%2011-0078D4)

</div>

---

## Install

Pick one. They all install the same app.

### Microsoft Store (recommended)

Click **Get it from Microsoft** above, open the [Store page](https://apps.microsoft.com/detail/9NDXZ7087GLM), or run:

```powershell
winget install 9NDXZ7087GLM --source msstore
```

Updates are automatic, through the Store.

### winget

```powershell
winget install epatels.CKVideoDownloaderConverter
```

Update later with:

```powershell
winget upgrade epatels.CKVideoDownloaderConverter
```

The app also shows an in-app update prompt.

### Installer (.exe)

Download `CKVDC-Setup-<version>.exe` from the [Releases](https://github.com/epatels/ck-vdc/releases/latest) page and run it. Updates come through the in-app prompt.

### Portable (.zip)

Download `CKVDC-<version>-portable.zip` from Releases, extract it and run `CKVDC.exe`. Updates are manual.

### MSIX (sideload)

Download `CKVDC-<version>-x64.msix` from Releases, if attached. It needs a trusted signing certificate, so the Store version is easier. Updates come through Windows / App Installer.

### Verify a download

Compare against the `.sha256` file or `SHA256SUMS-<version>.txt` on the Releases page:

```powershell
Get-FileHash .\CKVDC-Setup-4.0.0.exe -Algorithm SHA256
```

### Uninstall

```powershell
winget uninstall epatels.CKVideoDownloaderConverter
```

Store version: use Settings, then Apps, or the Store.

**Requirements:** Windows 10 version 1809 or later (x64) and an internet connection. yt-dlp and FFmpeg are included; there is nothing else to install.

## Features

**Download**
- Paste or drop links: single videos, playlists and channels (pick which videos to add)
- Playlist videos queued oldest first, with an upload-date column
- Files named with the video date (`2024-01-31 - Title`), optional
- Parallel downloads, pause, resume, cancel and drag-to-reorder queue
- Per-video options with a format and stream picker, plus presets (including audio-only M4A and FLAC)
- Live streams and upcoming premieres: wait for the start, record, then remux cleanly
- Optional thumbnail, metadata and source-URL saving, and a download history

**Automate**
- Queue persistence: unfinished items are offered back on the next launch
- Auto-retry for network, rate-limit and unknown failures (0 to 5 times)
- Subscriptions: follow a channel or playlist and new videos are queued automatically
- When finished: do nothing, sleep, shut down or close the app, with a cancellable countdown
- Auto-convert finished downloads with a chosen preset
- Schedule the queue to start at a set time, with an optional stop time

**Convert**
- Batch-convert audio and video with presets (MP4 H.264 / H.265, MKV and more)

**Other**
- Dark and light themes, resizable remembered columns, built-in dependency check and yt-dlp updater
- Optional anonymous telemetry, asked on first run and off until you agree

## Microsoft Store version

| | |
|---|---|
| Store listing | <https://apps.microsoft.com/detail/9NDXZ7087GLM> |
| Package identity | `epatels.CKVideoDownloaderandConverter` |
| Publisher | epatels |
| Package type | MSIX, x64, full-trust desktop app |
| Price | Free |
| Updates | Delivered by the Microsoft Store. The in-app update check is replaced by a notice. |

How the Store version differs from the installer:
- **Right-click menu:** instead of the registry "Open with" entry, the app registers for common video files (`.mp4`, `.mkv`, `.avi`, `.mov`, `.wmv`, `.flv`, `.webm`, `.m4v`, `.mpg`, `.mpeg`, `.m2ts`, `.ts`). Use right-click, then **Open with**.
- **Bundled tools:** `yt-dlp.exe`, `ffmpeg.exe` and `ffprobe.exe` ship inside the read-only package. On first run they are copied to `%LOCALAPPDATA%\CKVDC\bin`, so yt-dlp can update itself in place.
- **Command line:** the app can be started from a terminal or Win+R with `ckvdc`.
- **Uninstall:** use Settings, then Apps, or the Store. Windows normally removes the app's per-user settings with a Store (MSIX) install.

The app uses the *full trust* (`runFullTrust`) capability because it launches the bundled yt-dlp and FFmpeg programs and writes to the download folder you choose. It declares no other restricted capability beyond internet access.

## Settings and data

| Where | What |
|---|---|
| `%APPDATA%\CKVDC\config.json` | Settings |
| `%APPDATA%\CKVDC\history.json` | Download history |
| `%APPDATA%\CKVDC\queue.json` | Unfinished queue |
| `%APPDATA%\CKVDC\subscriptions.json` | Followed channels and playlists |

Everything stays on your computer. In the Store version Windows may redirect this folder into the app's private package storage; the contents and behaviour are the same.

## Privacy policy

*Last updated: 5 November 2026.*

CK Video Downloader and Converter runs on your PC. It needs no account and does not collect your name, email address or contacts.

**Stays on your device.** Settings, download history, the unfinished queue and subscriptions are stored locally. The developer never receives them.

**Network activity.** The app connects to the websites whose links you give it, in order to download the content you ask for, and to GitHub to check for updates to the app and to yt-dlp. Those services have their own privacy policies.

**Optional anonymous analytics.** The first time you run the app you are asked whether to share anonymous usage statistics through [PostHog](https://posthog.com/privacy). It is **off unless you agree**, and you can change your mind at any time in **Settings, then Privacy & Telemetry**.

If you agree, the app sends:
- App version, operating system version and a random install ID that is not linked to you
- Which features are used (download, convert, batch sizes), and formats and codecs chosen
- Whether a download or conversion succeeded, with a rough error category (never the error text)

It never sends:
- Video URLs, titles, file names or folder paths
- Cookies, proxy addresses or custom yt-dlp arguments

Like any internet service, PostHog receives the network request that carries these events.

**No sale or sharing.** Personal data is not sold or shared with anyone. The app contains no advertising.

**Children.** The app is a general-purpose utility and is not directed at children.

**Changes.** If this policy changes, the new version and date will appear here.

**Contact.** Open an [issue](https://github.com/epatels/ck-vdc/issues) on this repository.

Privacy policy link for store listings: <https://github.com/epatels/ck-vdc#privacy-policy>

## Responsible use

Download only content that you own, that is in the public domain or licensed for it, or that you otherwise have permission to save, and respect the terms of the websites you use. You are responsible for how you use this software.

## Support

- Bug or feature request: [GitHub Issues](https://github.com/epatels/ck-vdc/issues)
- Include the app version (see About), your Windows version, and whether you installed from the Store, winget or the installer.

## Third-party software and licences

CK Video Downloader and Converter is proprietary freeware; the application itself is not open source. It includes or uses these open-source components, each under its own licence:

| Component | Licence | Notes |
|---|---|---|
| [Qt for Python (PySide6)](https://doc.qt.io/qtforpython-6/) | LGPL v3 | Dynamically linked and unmodified. You may replace the libraries with your own build of the same version. Source: <https://www.qt.io/download-open-source> |
| [yt-dlp](https://github.com/yt-dlp/yt-dlp) | The Unlicense (public domain) | Bundled as `yt-dlp.exe`, unmodified |
| [FFmpeg](https://ffmpeg.org/) | GPL v3 (gyan.dev "essentials" build) | Bundled as `ffmpeg.exe` and `ffprobe.exe`, unmodified and run as separate programs. Source: <https://www.gyan.dev/ffmpeg/builds/> and <https://ffmpeg.org/download.html> |

Full licence texts are in the `licenses` folder of the installation.

This software is provided as is, without warranty.

## Credits

Built on yt-dlp, FFmpeg and Qt for Python (PySide6).

Copyright © 2026 CK Patel. All rights reserved.
