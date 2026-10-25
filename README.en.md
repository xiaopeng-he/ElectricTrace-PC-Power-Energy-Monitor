<p align="center"><img src="assets/icon.png" width="80" alt="ElectricTrace icon"></p>

# ElectricTrace · PC Power & Energy Monitor

See how much power your PC is using, how warm your CPU and GPU are, and how much energy you have consumed today. ElectricTrace brings live charts, a floating desktop widget and historical statistics to Windows. Readings and history stay on your computer.

[中文](README.md) · [Download](#download) · [Features](#features) · [Getting started](#getting-started) · [Compatibility](docs/COMPATIBILITY.md) · [Changelog](CHANGELOG.md)

## Download

**Choose the Windows installer for everyday use.** One download automatically selects x64 or x86. The current public release is **0.5.6 preview**.

| Package | Download | How to use it |
| --- | --- | --- |
| **Windows installer · Recommended** | [Download Setup.exe](https://github.com/xiaopeng-he/ElectricTrace-PC-Power-Energy-Monitor/releases/download/v0.5.6/ElectricTrace-0.5.6-Windows-Setup.exe) | Install for your Windows account and launch from the shortcut |
| Windows portable | [Download Portable.zip](https://github.com/xiaopeng-he/ElectricTrace-PC-Power-Energy-Monitor/releases/download/v0.5.6/ElectricTrace-0.5.6-Windows-Portable.zip) | Extract the complete archive into a writable folder, then run `电迹.exe` |
| Checksums | [SHA256SUMS.txt](https://github.com/xiaopeng-he/ElectricTrace-PC-Power-Energy-Monitor/releases/download/v0.5.6/SHA256SUMS.txt) | Check download integrity |

[Release page and notes](https://github.com/xiaopeng-he/ElectricTrace-PC-Power-Energy-Monitor/releases/tag/v0.5.6)

Targets Windows 10 version 1709 or later and Windows 11. Requires [.NET Framework 4.8+](https://dotnet.microsoft.com/download/dotnet-framework/net48); the full interface requires [WebView2 Runtime 120+](https://developer.microsoft.com/microsoft-edge/webview2/#download-section). A basic native interface is available without WebView2. See [compatibility](docs/COMPATIBILITY.md) for architecture and hardware coverage.

![Live monitoring with example readings](assets/overview.png)

*Screenshots use synthetic example readings. Available sensors depend on your computer.*

## Features

| Feature | What you can see or do |
| --- | --- |
| Live monitoring | CPU/GPU power, temperature, load and clocks; physical memory, commit usage and VRAM |
| Charts | Switch between power, temperature and load; inspect values at a specific time |
| Energy history | Daily, weekly, monthly or custom date ranges; energy, average power and recorded duration |
| Cost estimates | Set your electricity price and choose the measurement scope |
| Hardware details | Search 24 common metrics, filter by device or availability, inspect sources and raw CPU sensors |
| Floating widget | Keep key readings visible, drag the widget, pin it and return to the main window |
| Task measurements | Start and finish a named interval; retain energy, cost, elapsed/valid duration, average/peak power and maximum CPU/GPU temperatures |
| High-temperature events | Review CPU/GPU event times, peak temperature and valid duration; events end 3°C below the configured threshold |
| Local backup | Save history and settings while recording; validate and restore a backup with a recovery point |
| Preferences | Graphite, Clear and Mist themes, sampling interval and temperature alerts |

Battery capacity, charging/discharging power, fan speed and additional hardware sensors appear when the device supplies them. An unavailable value displays as “—”; a measured zero stays zero.

![Searchable hardware metrics](assets/metrics.png)

The main window closes to the tray while sampling continues. Hidden main pages are released, and the widget uses a separate page to reduce retained interface resources. Choose **Exit** from the tray to stop recording.

## Start in the background at sign-in

Version 0.5.6 can start directly in the tray, loading the full interface when you open statistics. Double-click the tray icon or launch the ordinary shortcut to open the existing recording session.

To start at Windows sign-in, copy the app shortcut and append ` --background` to its **Target**. Press `Win + R`, enter `shell:startup`, and put the shortcut in that folder. Add ` --cpu` to request enhanced CPU collection. Installed copies offer **CPU 登录自动采集 → 启用（首次授权）** in the tray menu: approve administrator setup once, then collection starts and reconnects through the authorized task without repeated prompts. Remove this shortcut to disable automatic startup.

Measurements use the selected CPU, GPU or combined hardware scope and capture the electricity price at the start. Both record lists live under History, follow its date filters and show up to 100 recent records each. Records share the existing sampling stream and local backups. Interrupted measurements keep their saved results.

## Getting started

1. Install and launch the app, or extract the portable ZIP and run `电迹.exe`.
2. Enable enhanced CPU collection to read package power and temperature. Installed copies can authorize the tray option **CPU 登录自动采集** once; the regular prompt-based mode remains available. It uses an existing compatible PawnIO driver; see [sensor compatibility](docs/COMPATIBILITY.md).
3. Open the live monitor, enable the widget, or use hardware details to find a particular metric.
4. Set your electricity price. The default sampling interval is two seconds, adjustable from 1 to 30 seconds.
5. Open history to select a date range and measurement scope, or export readings as CSV.

## Understanding the readings

**Power in watts (W)** describes the current rate of energy use. **Energy in watt-hours (Wh)** accumulates over time: a constant 150 W for two hours consumes 300 Wh, or 0.3 kWh. At 0.60 per kWh, the estimated cost is 0.18 in the same currency.

Choose a scope that matches your question:

- **CPU + GPU components:** the sum of valid, non-overlapping component readings. Displays, other parts and adapter losses are additional.
- **CPU / GPU:** power and accumulated energy for one component.
- **Battery discharge:** whole-system DC power while a laptop is actually discharging.
- **Estimated system:** component readings plus your configured allowance for other parts, labelled as an estimate.

Energy is integrated between valid recorded samples. Sleep, exit and missing-sensor periods remain gaps. Use a corresponding power meter when you need wall-outlet energy readings.

## Data and backups

The installer stores data in `%LOCALAPPDATA%\ElectricTrace\data`. Portable copies use the `data` folder alongside the app. The actual location is shown in the application. No account is required.

Create an `.etbackup` under **Settings → Data and operation** to save recorded history and settings while sampling continues. Restoring validates the backup and asks for confirmation before restarting; previous files are kept in `restore-points`.

Create a backup before upgrading. Keep the complete folder, including `data`, when moving a portable copy. Uninstalling an installed copy retains its data. Databases, exports and backups are ordinary local files; handle them as personal records. See [privacy](docs/PRIVACY.md).

## Common questions

**Which download fits my PC?** The same installer or portable ZIP selects x64 or 32-bit x86 automatically. Windows ARM coverage is described in [compatibility](docs/COMPATIBILITY.md). Packages are currently available for Windows.

**Why is a metric unavailable?** Hardware, drivers and permissions determine which sensors are exposed. Enable enhanced collection for CPU power and temperature; other available metrics continue recording.

**Why is there a gap in a chart?** No valid reading was recorded for that interval. Check the collection status, reconnect enhanced CPU collection if needed, or resume paused recording. New samples continue the history while the earlier gap remains visible.

**Why does Windows show an unknown publisher?** The preview package is not yet signed with a trusted code-signing certificate. Download from this project's [Releases](https://github.com/xiaopeng-he/ElectricTrace-PC-Power-Energy-Monitor/releases), use the checksums to check integrity, and keep Windows protection enabled.

## Feedback and distribution

[Report a problem or suggest an improvement](https://github.com/xiaopeng-he/ElectricTrace-PC-Power-Energy-Monitor/issues/new/choose) with the app version, Windows version, architecture, CPU/GPU model and reproduction steps. Remove personal information from screenshots and error text before sharing.

This repository distributes documentation and packaged binaries. The application's proprietary source code remains private; see [NOTICE.md](NOTICE.md) for distribution information. Third-party licenses and source links are listed in [THIRD-PARTY.md](THIRD-PARTY.md), with license texts in the package's `licenses` folder.
