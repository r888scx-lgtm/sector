# Sector 0.3.6 — Windows x64

Author: **by.mask21**. Experimental SSD cloning utility. Source code is private.

## Start

1. Download `Sector-0.3.6-Windows-x64.zip` from Releases and extract all files into one folder. Keep both AlphaVSS DLLs beside the EXE.
2. Windows x64, Windows PowerShell, .NET Framework and the Microsoft Visual C++ 2019/2022 x64 runtime are required. The app was developed for Windows 10/11 x64; other configurations have not been validated.
3. Run `Sector.exe` as administrator for cloning. `Sector-Preview.exe` shows simulated disks and cannot write to physical disks.
4. Choose **Русский**, **English** or **简体中文** in the top language selector. The choice takes effect immediately and is saved to `%LOCALAPPDATA%\Sector\settings.json`. Language switching is disabled while an operation is running.

## Copy Windows

1. Connect a destination SSD at least as large as the source, with the same logical sector size (512 or 4096 bytes).
2. Take **only the destination** Offline in Windows Disk Management. Keep the running Windows source Online. If the target is read only, its card contains a guarded **Remove write protection** button; this changes only that flag and never starts cloning.
3. Select the source on the left and destination on the right. Click **Check plan**. You can first run **Test VSS without writing** to check snapshot creation and reading; this does not test cloning itself.
4. Click **Clone SSD**. Before writing, enter the destination serial number reported by Windows and check the overwrite consent box. A USB bridge may report a different serial from the SSD label, including a number consisting entirely of zeros.
5. Wait for copying, full verification and any boot preparation to finish. Stopping or an error leaves an incomplete destination. The app cannot restore the target's old contents.
6. After successful completion, shut down and disconnect the source SSD before testing the first boot from the copy. Do not bring the destination Online during copying or verification.

## Modes and limits

- Running Windows on a basic GPT disk: Windows and its EFI must be on the same source disk. NTFS data volumes are copied through one coordinated VSS snapshot set. The copy reflects the snapshot time, excluding later changes. EFI and layout are checked separately.
- Dynamic GPT source: only one **simple** NTFS volume containing the current Windows, with EFI on that same SSD. Sector creates a new basic GPT layout, a 16 MB MSR, EFI boot files and system volume mapping on the destination. Spanned/mirrored volumes, extra user volumes and unknown GPT partitions are rejected.
- Two offline non-system disks: complete sector-by-sector copying and full byte comparison. Partition sizes stay unchanged; unused capacity on a larger target is not automatically added to partitions.
- Live MBR, BitLocker in live mode, RAID, virtual disks, smaller destinations, mixed logical sector sizes and automatic partition resizing are unsupported.

All copied data is read back. VSS copies are checked against SHA-256 block hashes captured before destination writes. Disk identity and state checks remain enabled in every language.

## Status and diagnostics

Version 0.3.6 is experimental. A full Windows volume copy and verification have been confirmed on one tested computer. Other hardware and boot configurations need further testing. Keep an independent backup of important files.

App messages and help are translated. Native Windows/driver errors and standard Windows dialog buttons may follow the operating system language. Technical log files retain original diagnostics in `%LOCALAPPDATA%\Sector\logs`; review them before sharing because they can contain device identifiers and paths.

## Author

**by.mask21** · [Telegram](https://t.me/+2A9pJfPMffU2Zjg6). Support is voluntary. The app can copy these public addresses; it never sends a payment:

- BTC, Bitcoin: `bc1qnltkdun0jnv8yj6rnz5cd46l9tfad3xzrqahlp`
- ETH, Ethereum: `0x8BD4C9B28A6341eCD0D5b66dbAaac1a16C5a1462`

Use the specified coin and network. First-party application source is not included. Third-party license notices are supplied with the release.
