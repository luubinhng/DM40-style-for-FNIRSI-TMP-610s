# Firmware Upgrade Guide

[English overview](../README.md) | [Hướng dẫn tiếng Việt](../README.vi.md)

## Scope and Source

These instructions follow the [bundled FNIRSI manual](TMP-610S_TMP-600_Manual_(EN).pdf), section **3.6**, printed page **22**, PDF page **25**. They describe the manufacturer's transfer procedure; they do not certify this mod's compatibility or successful operation.

Use the binary only for its intended **TMP-610S** target. A shared TMP-600/TMP-610S manual does not make the firmware interchangeable. Device or manual revisions may use different upgrade-entry sequences; if the documented sequence does not open the upgrade screen, consult the manual for your exact revision before copying firmware.

## Prepare

1. Disconnect measurement leads and other test connections. Ensure the device has enough charge to remain powered during the update.
2. Record the current firmware version and any settings you need to restore.
3. Obtain a suitable official firmware and the applicable recovery instructions from [FNIRSI](https://www.fnirsi.com/pages/manuals-firmwares) before replacing your current firmware. This repository does not contain a stock recovery image. Downgrading from a newer version has not been verified here.
4. Download `APP_TMP-610S_V1.9.9_260716_dm40-bar-allmodes.bin` from [binary/](../binary/). Use **Download raw file** on GitHub, or extract **Code > Download ZIP**. Do not save the GitHub HTML page as a `.bin`.
5. Verify the file's SHA-256 checksum before connecting the device.

## Verify the Download

From the repository root in Windows PowerShell:

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\binary\APP_TMP-610S_V1.9.9_260716_dm40-bar-allmodes.bin'
```

On Linux, from `binary/`:

```sh
sha256sum -c SHA256SUMS.txt
```

On macOS, from `binary/`:

```sh
shasum -a 256 -c SHA256SUMS.txt
```

Expected SHA-256, case-insensitive:

```text
5e40700dda8615a584b3a12f803e8b82cd378ff2a2e439bdde31950a18325619
```

Expected size: **946,176 bytes**. A matching hash confirms the file matches this repository's binary; it does not verify hardware compatibility. If it differs, stop and download the file again.

## Install

1. **Power off the TMP-610S.** Quickly press its **Power button three times**, as specified in the bundled manual.
2. Confirm that the **Firmware Upgrade** interface appears.
3. Connect the device to the computer using a USB Type-C cable that supports data transfer.
4. Wait for the computer to detect the device as a USB drive. Identify the device's drive before copying anything.
5. Copy **only** `APP_TMP-610S_V1.9.9_260716_dm40-bar-allmodes.bin` into the root of that drive. Keep the supplied filename. Do not copy the ZIP, images, PDF, or entire repository.
6. Wait for copying and any device update activity to finish. Do not disconnect the cable or interrupt power while the update is in progress. The manual gives no fixed timeout, so this guide does not prescribe one.
7. Restart the device after completion, following the manual.

## Check After Restart

For this update, also inspect the selected skin, menu, DMM, scope, and bar view. Check zero, signs, decimal placement, units, and HOLD where applicable. Preview images alone do not establish device behavior.


Check that the instrument boots, opens its menus, and renders digits, decimal points, signs, and units legibly. Check the reported firmware version, though this visual mod is not guaranteed to display a separate DM40 version string. Validate normal operation using suitable known references before relying on measurements.

## Troubleshooting

| Symptom | Next step |
| --- | --- |
| Upgrade screen does not appear | Start with the device off and repeat the manual's sequence. If it still fails, check the manual for your hardware revision. |
| No USB drive appears | Confirm upgrade mode; try a known data-capable cable and another direct USB port. |
| Download has the wrong hash or size | Delete the bad download and use GitHub's raw-file download again. Do not flash it. |
| Update fails or the device does not boot | Record the displayed error. Consult FNIRSI's recovery instructions for the exact model; do not assume another model's firmware or a forced reset will recover it. |

The supplied files do not establish a tested rollback or recovery procedure for this mod. If the bootloader remains accessible, use official guidance to determine whether an appropriate stock image can be restored.
