# CK Video Downloader and Converter

A Windows desktop app for downloading videos and audio from the web (powered by [yt-dlp](https://github.com/yt-dlp/yt-dlp)) and converting media files (powered by [FFmpeg](https://ffmpeg.org/)), with a clean dark/light interface.

**Download:** grab the latest `CKVDC-Setup-<version>.exe` from the [Releases page](https://github.com/epatels/ck-vdc/releases/latest).

---

## Features

**Downloads**
- Download from the sites yt-dlp supports, one link at a time or in batches
- Drag and drop `.url` shortcut files, or load a whole folder of them at once
- Playlist and channel links are listed so you can pick the videos you want
- Optional thumbnail saving and subtitle download (choose the language)
- Sign-in support for restricted content: use cookies from your browser or a `cookies.txt` file
- Optional proxy (HTTP or SOCKS5)
- Unicode filenames (Gujarati, Hindi, Tamil and other languages)

**Converter**
- Convert video files between common formats (MP4, MKV, WebM, AVI, MOV, FLV)
- Choose the video codec (copy, H.264, H.265, AV1, VP9, VP8, MPEG-4) or use a ready-made preset
- Queue several files and convert them in one go

**Convenience**
- Windows Explorer right-click entry: **Open with CK Video Downloader and Converter** for `.url` files and video files (select several at once)
- The **Check & Update All** button keeps the bundled yt-dlp current, which matters because sites change often
- Built-in app updates: the app tells you when a new version is out and installs it for you
- Dark and light themes

Everything the app needs (yt-dlp, FFmpeg, FFprobe) is bundled with the installer. You do **not** need Python or any other software installed.

---

## Install

1. Download `CKVDC-Setup-<version>.exe` from the [latest release](https://github.com/epatels/ck-vdc/releases/latest).
2. Run it. By default it installs for your user only, so no administrator rights are needed.
3. Launch **CK Video Downloader and Converter** from the Start Menu.

**Requirements:** Windows 10 or 11, 64-bit.

> The installer is not code-signed, so Windows SmartScreen may show a warning. Choose **More info → Run anyway** if you trust the download. You can verify the file against the `.sha256` file published with each release.

### Updating

The app checks for new versions shortly after it starts. When one is available, choose **Update Now** and it downloads, verifies and installs the new version, then reopens. Your settings and history are kept.

### Uninstalling

Use **Settings → Apps → Installed apps**. You'll be asked whether to also delete your settings and download history (stored in `%APPDATA%\CKVDC`).

---

## Privacy

Anonymous usage analytics are **off by default**. On first launch the app asks for your permission, and you can change your mind any time from **Help → Privacy & Telemetry**. If enabled, only coarse, non-identifying signals are sent (app version, which features are used, whether a download or conversion succeeded). Video URLs, titles, filenames, folder paths, cookies, proxy settings and custom yt-dlp arguments are never read or sent.

---

## Building from source

You need Windows, [Python 3.13](https://www.python.org/downloads/) and an internet connection (for the first build).

```powershell
winget install Python.Python.3.13
build_installer.bat -Python "py -3.13"
```

The build script:
1. Creates a private virtual environment in `build\venv` and installs `requirements-build.txt`
2. Uses `yt-dlp.exe`, `ffmpeg.exe` and `ffprobe.exe` from the project folder if they are there, otherwise downloads them into `build\cache`
3. Compiles the app with [Nuitka](https://nuitka.net/)
4. Builds the installer with [Inno Setup 6](https://jrsoftware.org/isinfo.php) (installed automatically with winget if missing)

Output: `installer_out\CKVDC-Setup-<version>.exe` and a matching `.sha256` file.

Useful options: `-SkipCompile` (reuse the last compile, rebuild only the installer), `-Refresh` (re-download yt-dlp and FFmpeg), `-NoInstaller` (stop after compiling).

To run directly from source without building: `pip install yt-dlp tkinterdnd2 requests packaging sv-ttk mutagen posthog`, put FFmpeg on your `PATH`, then run `python vdc.pyw`.

### Releasing a new version

1. Raise `__version__` in `vdc.pyw`.
2. Run `build_installer.bat -Python "py -3.13"`.
3. Create a GitHub release tagged `v<version>` (for example `v3.0.1`) and attach **both** `installer_out\CKVDC-Setup-<version>.exe` and its `.sha256` file. The in-app updater looks for these two files.

---

## Responsible use

Only download or convert content you have the right to use. You are responsible for following the terms of the sites you download from and the copyright laws that apply to you.

## Credits

Built on [yt-dlp](https://github.com/yt-dlp/yt-dlp), [FFmpeg](https://ffmpeg.org/), [Nuitka](https://nuitka.net/), [Inno Setup](https://jrsoftware.org/isinfo.php), [sv-ttk](https://github.com/rdbende/Sun-Valley-ttk-theme) and [tkinterdnd2](https://github.com/Eliav2/tkinterdnd2).

## License

*Add your license here (for example MIT), and a `LICENSE` file to the repository.*
