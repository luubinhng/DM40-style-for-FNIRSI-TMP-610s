# DM40 mod for FNIRSI TMP-610S

I made this mod to bring a DM40-style interface to the TMP-610S, with extra skins and a bar display. I've flashed and tested the new build on a real TMP-610S, and it runs normally.

[Download firmware](binary/APP_TMP-610S_V1.9.9_260716_dm40-bar-allmodes.bin) | [Tiếng Việt](README.vi.md) | [Changelog](CHANGELOG.md)

## What's new?

The main addition is the **bar display**, which shows the magnitude of the reading relative to the measurement range. The interface keeps the DM40-style digits and offers five skins:

| Skin | Colors |
| --- | --- |
| DM40 | Orange on a dark background |
| Matrix Green | Green on black |
| Cyber Neon | Cyan on a dark background |
| Phosphor Amber | Amber on black |
| Lab Gray | White and gray |

![Bar display across all five skins](images/skins/bar-skins.png)

## Interface gallery

These are interface previews from the development image set. Device photos follow below.

### Skin menu

![Skin menu comparison](images/skins/skin-menu.png)

### Digital multimeter

![DMM skin comparison](images/skins/skin-dmm.png)

### Scope

![Scope skin comparison](images/skins/skin-scope.png)

## Device photos

Photos taken during development on the TMP-610S:

![TMP-610S in analog-style meter view](images/device-meter.jpg)

![TMP-610S in graph view](images/device-graph.jpg)

## Download

New build: [APP_TMP-610S_V1.9.9_260716_dm40-bar-allmodes.bin](binary/APP_TMP-610S_V1.9.9_260716_dm40-bar-allmodes.bin).

Open the link on GitHub and choose **Download raw file**, or use **Code > Download ZIP** and extract the archive.

The [previous DM40 build](binary/APP_TMP-610S_V1.9.9_260716_dm40.bin) is also available in `binary/`. Checksums for both builds are in [SHA256SUMS.txt](binary/SHA256SUMS.txt).

## Upgrade

Charge the device, disconnect the test leads, and have a USB-C data cable ready.

1. Turn off the TMP-610S, then quickly press **Power three times** to enter **Firmware Upgrade**.
2. Connect it to your computer with the USB-C cable.
3. Wait for the TMP-610S to appear as a USB drive.
4. Copy `APP_TMP-610S_V1.9.9_260716_dm40-bar-allmodes.bin` to the root of that drive.
5. Wait for the transfer and update to finish, then restart the device. Keep it connected throughout the update.

Copy only the `.bin` file. If the USB drive doesn't appear, try another data cable.

These steps follow section 3.6 of the bundled manual. See the [full upgrade guide](docs/UPGRADE.md) for more detail.

To check your download in PowerShell:

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\binary\APP_TMP-610S_V1.9.9_260716_dm40-bar-allmodes.bin'
```

Compare the result with `binary/SHA256SUMS.txt`.

## Files

```text
binary/     Firmware and checksums
images/     Device photos and interface gallery
output/     Full preview set and development data
docs/       Manual, guides, and technical notes
```

This is a community mod for the FNIRSI TMP-610S. If you find a bug, open an issue with the skin, operating mode, steps to reproduce it, and a photo or video.
