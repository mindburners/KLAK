# KLAK — Mindburner MIDI drum synth

Firmware installer, user manual and quick start for the Mindburner KLAK.

**Page:** https://mindburners.github.io/KLAK/

## Repo layout

```
index.html              installer page (ESP Web Tools)
manifest.json           tells the installer which files to flash
changelog.txt           newest version on the FIRST line - the page reads it
.nojekyll               stops GitHub Pages processing the site
KLAK_User_Manual.pdf    user manual (keep this exact name)
KLAK_Quick_Start.pdf    quick start (keep this exact name)
firmware/
  bootloader.bin        offset 0x1000
  partitions.bin        offset 0x8000
  boot_app0.bin         offset 0xE000
  KLAK.bin              offset 0x10000
```

## Releasing a new firmware version

1. Arduino IDE: **Sketch > Export Compiled Binary**.
2. From the sketch's `build` folder, rename and upload into `firmware/`:
   - `KLAK.ino.bin` -> `KLAK.bin`
   - `KLAK.ino.bootloader.bin` -> `bootloader.bin`
   - `KLAK.ino.partitions.bin` -> `partitions.bin`
3. Add the new version to the top of `changelog.txt`.

That's it - no `manifest.json` edit needed.

`boot_app0.bin` only needs uploading once. It comes with the ESP32 core, e.g.
`%LOCALAPPDATA%\Arduino15\packages\esp32\hardware\esp32\2.x.x\tools\partitions\boot_app0.bin`

## Guides

Replace `KLAK_User_Manual.pdf` / `KLAK_Quick_Start.pdf` with new files of the
same name - the links never change.

## GitHub Pages

Settings > Pages > Source: **Deploy from a branch**, branch `main`, folder `/ (root)`.
