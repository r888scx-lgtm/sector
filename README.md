# Sector / Сектор

Windows SSD cloning utility by **by.mask21**. **Русский · English · 简体中文**.

[Русский](docs/README.ru.md) · [English](docs/README.en.md) · [简体中文](docs/README.zh-CN.md)

**Download:** open [Releases](../../releases), download `Sector-0.3.6-Windows-x64.zip`, and extract the entire archive. Start `Sector.exe` as administrator to clone, or use `Sector-Preview.exe` for the interface demo with simulated disks and device writing disabled.

The language selector is at the top of the app. Your choice is saved and takes effect immediately.

Sector can copy a running GPT/UEFI Windows installation using VSS, migrate a supported simple dynamic Windows volume to a basic GPT disk, or copy two offline non-system disks sector by sector. All copied data is read back and verified. The destination's existing contents are overwritten after explicit confirmation.

**0.3.6 is an experimental release.** A completed Windows volume copy and verification have been confirmed on one computer; compatibility with other hardware and successful booting on every configuration are not guaranteed. Keep an independent backup of important data. See the language-specific instructions for supported layouts and limits.

This repository distributes **compiled applications and documentation only**. First-party source code remains private. AlphaVSS components retain their Apache 2.0 license; see [third-party notices](THIRD-PARTY-NOTICES.txt).

Author: **by.mask21** · [Telegram channel](https://t.me/+2A9pJfPMffU2Zjg6). Voluntary support is available inside the app.
