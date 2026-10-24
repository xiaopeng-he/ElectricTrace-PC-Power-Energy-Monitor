# ElectricTrace · PC Power & Energy Monitor · PC Power & Energy Monitor

A Windows desktop monitor for CPU/GPU power, temperatures and energy trends, with a floating widget and a full statistics window. Data stays on the local machine.

[中文](README.md) · [Compatibility](docs/COMPATIBILITY.md) · [Changelog](CHANGELOG.md)

This repository distributes documentation and packaged binaries. The application's proprietary source code remains private. **0.5.0 is a preview**, with ongoing compatibility, long-term performance and release validation.

- [Windows installer](https://github.com/xiaopeng-he/ElectricTrace-PC-Power-Energy-Monitor/releases/download/v0.5.0/ElectricTrace-0.5.0-Windows-Setup.exe): automatically selects x64 or x86.
- [Windows portable ZIP](https://github.com/xiaopeng-he/ElectricTrace-PC-Power-Energy-Monitor/releases/download/v0.5.0/ElectricTrace-0.5.0-Windows-Portable.zip): extract the complete archive into a writable folder and run `电迹.exe`.
- [SHA256 checksums](https://github.com/xiaopeng-he/ElectricTrace-PC-Power-Energy-Monitor/releases/download/v0.5.0/SHA256SUMS.txt).

Requires .NET Framework 4.8+; the full UI requires WebView2 Runtime 120+. A basic native UI is available without WebView2. The current host validation is Windows 11 x64 and WOW64; Windows 10 and ARM devices need further validation. Windows 7/8/XP are unsupported. No macOS or Linux package is currently available.

The package is not yet signed with a trusted code-signing certificate. Download from this repository's Releases and keep Windows protection enabled.

View power, temperatures, load, clocks, memory, available battery/fan metrics, historical energy, estimated cost and CSV exports. Search the 24-metric inventory by device, metric or source; unavailable and measured-zero values remain distinct. CPU sensor collection requires user-approved elevation and an existing compatible PawnIO driver. Availability depends on the hardware and driver.

CPU + GPU power represents those components, rather than wall-outlet power. Energy only covers valid recorded intervals; missing, sleep and exit periods are not filled in. Set your actual electricity price in the app.

Backups contain saved history and settings; restoring requires validation and explicit confirmation, and retains the previous files in a recovery point. Databases, CSV files and backups are not encrypted. The application has no account or cloud history-upload workflow.

![Example UI with synthetic readings](assets/overview.png)

Screenshots use synthetic example readings. UI browser tests, protected-assembly checks and the earlier real-hardware collection baseline are separate validation layers. Full cross-device, installation, power-loss and long-running certification are still pending.

Report issues with the app version, Windows version, architecture, CPU/GPU model and reproduction steps. Do not attach private history, backups, full logs or `session.dat`. Third-party notices and source links are in [THIRD-PARTY.md](THIRD-PARTY.md) and the package's `licenses` folder.
