# Sector — Windows Migration and SSD Cloning

**Replacing your SSD and want to keep your Windows installation, apps, settings and files?** Sector is a Windows utility by **by.mask21** built for that task.

It copies a supported Windows installation to another SSD so you can test booting from the new drive without reinstalling the system and applications. Apps, settings and files move with the volumes that contain them; the volumes included depend on the copy mode below.

**[Download Sector 0.3.6 for Windows x64](https://github.com/r888scx-lgtm/sector/releases/download/v0.3.6/Sector-0.3.6-Windows-x64.zip)** · [Release page](https://github.com/r888scx-lgtm/sector/releases/tag/v0.3.6)

**You can also use the green `Code` button → `Download ZIP` on this page.** The repository archive includes the same ready-to-run 0.3.6 EXE and DLL files. Extract the whole archive, open the extracted folder and run **`Sector.exe` as administrator**. Keep both DLLs beside the EXE. `Sector-Preview.exe` is a separate interface demo with simulated disks and physical-device writes disabled.

**По-русски:** нажмите **Code → Download ZIP**, распакуйте весь архив и запустите **`Sector.exe` от имени администратора**. Оставьте обе DLL рядом с EXE. Через ссылку Download выше также доступен архив релиза. Контрольные суммы EXE и DLL указаны в `SHA256SUMS.txt`.

## What Sector Does

- **Copies running Windows to another SSD.** Supported GPT/UEFI installations use VSS: Windows keeps running, and the copy reflects the snapshot time.
- **Copies entire supported volumes**, including their installed apps, settings and user files.
- **Clones two offline non-system disks sector by sector**, including partitions, boot areas and unused sectors.
- **Migrates a simple dynamic Windows volume from LDM to basic GPT**, creating a new destination layout, EFI boot files and system volume mapping.
- **Verifies all copied data by reading it back.** VSS copies use SHA-256 block hashes saved before writing; standard sector copies use a byte-by-byte comparison.
- **Tests VSS without writing to an SSD** and can remove the software read-only flag from a separately identified eligible destination.
- **Checks the copy direction.** System disks cannot be selected as the destination. Overwriting requires the destination serial number and explicit consent.

## Supported Copy Modes

| Mode | What is copied | Main requirements |
| --- | --- | --- |
| Running Windows on basic GPT | Supported NTFS volumes, EFI and disk layout | Windows and its EFI on the same SSD; destination Offline |
| Dynamic GPT to basic GPT | One simple NTFS volume containing the current Windows; new EFI and MSR | EFI on the same SSD; no additional user volumes, spanned or mirrored volumes |
| Two offline non-system disks | Complete disk contents, sector by sector | Both disks Offline; standard GPT or MBR |

The destination's physical capacity must be at least as large as the source. Logical sector sizes must match: 512 or 4096 bytes. Partitions are not automatically expanded. RAID, virtual disks, smaller destinations, live MBR and BitLocker in live mode are unsupported.

## How to Use It

1. Connect the new SSD and take **only the destination** Offline in Windows Disk Management. Keep the running Windows source Online.
2. Select the source on the left and destination on the right, then click **Check plan**.
3. Click **Clone SSD**, check the direction and confirm overwriting with the destination serial number reported by Windows.
4. Wait for copying and full verification. After successful completion, shut down, disconnect the source SSD and test the first boot from the copy.

**All existing destination data will be overwritten.** Stopping or an error leaves an incomplete copy. Version 0.3.6 is experimental: a complete Windows volume copy and verification have been confirmed on one tested computer; compatibility and successful booting on every configuration are not guaranteed. Keep an independent backup of important files.

## Interface and Guides

Languages: **Russian, English and Simplified Chinese**. The language selector is at the top of the app, and your choice is saved after closing it.

[English guide](docs/README.en.md) · [Russian guide](docs/README.ru.md) · [Simplified Chinese guide](docs/README.zh-CN.md)

## Author

**by.mask21** · [Telegram channel](https://t.me/+2A9pJfPMffU2Zjg6). Voluntary author support is available inside the app.

This repository distributes compiled applications, documentation and third-party license notices. **First-party source code remains private.** See [third-party notices](THIRD-PARTY-NOTICES.txt).
