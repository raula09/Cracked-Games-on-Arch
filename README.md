Elden Ring (FitGirl Repack) – Proton + Lutris Installation Guide

Before you start make sure you downloaded torrent setup.exe files 

Arch Linux Setup Documentation

This document describes the full process used to install Elden Ring (FitGirl Repack) on Arch Linux using Proton-GE and Lutris.
All commands and steps are written as a neutral technical guide.

Required Packages

Wine, Proton, and Windows game installers depend on several runtime libraries.
The following packages should be installed:
```bash
sudo pacman -S wine winetricks icoutils rofi lutris steam \
alsa-lib alsa-plugins ffmpeg gnutls libpulse libva libxcomposite \
libxinerama opencl-icd-loader pcsclite samba sane sdl2 unixodbc \
v4l-utils vulkan-icd-loader ttf-liberation

```
Steam must be opened once afterward so that Proton directories get initialized.

Installing GE-Proton

Download the desired GE-Proton build (e.g., GE-Proton10-25) from:
https://github.com/GloriousEggroll/proton-ge-custom/releases
```bash
~/.local/share/Steam/compatibilitytools.d/

```
Example path after extraction:
```bash
~/.local/share/Steam/compatibilitytools.d/GE-Proton10-25/


```
The Proton binary used later will be:
```bash
~/.local/share/Steam/compatibilitytools.d/GE-Proton10-25/proton


```
Creating the Elden Ring Prefix

A dedicated Proton prefix directory is created to isolate all game data:
```bash
mkdir -p ~/Games/EldenRingPrefix

```
When Proton initializes, this folder will receive:
```bash
~/Games/EldenRingPrefix/pfx/
~/Games/EldenRingPrefix/drive_c/

```
Proton Environment Configuration

Before running the FitGirl installer, the required Proton environment variables are set:
```bash
export STEAM_COMPAT_CLIENT_INSTALL_PATH="$HOME/.local/share/Steam"
export STEAM_COMPAT_DATA_PATH="$HOME/Games/EldenRingPrefix"
export WINEPREFIX="$HOME/Games/EldenRingPrefix/pfx"
export PROTON="$HOME/.local/share/Steam/compatibilitytools.d/GE-Proton10-25/proton"

```
Running the FitGirl Installer

Inside the repack directory:
```bash
cd "/home/$USER/Downloads/ELDEN RING [FitGirl Repack]"
"$PROTON" run ./setup.exe

```
The Proton prefix initializes, and the FitGirl setup runs normally.
When installation completes, the game files are placed inside:
```bash
~/Games/EldenRingPrefix/pfx/drive_c/ELDEN RING/

```
Running the Game from Proton (Manual Test, although I wouldnt reccomend)

A direct launch test can be performed:
```bash
export STEAM_COMPAT_CLIENT_INSTALL_PATH="$HOME/.local/share/Steam"
export STEAM_COMPAT_DATA_PATH="$HOME/Games/EldenRingPrefix"
export WINEPREFIX="$HOME/Games/EldenRingPrefix/pfx"
export PROTON="$HOME/.local/share/Steam/compatibilitytools.d/GE-Proton10-25/proton"

"$PROTON" run "$WINEPREFIX/drive_c/ELDEN RING/Game/eldenring.exe"

```
Adding the Game to Lutris

Open Lutris.

Click Add Game → Add Locally Installed Game.

Set:

Runner: Wine (or Proton if installed as a Lutris runner)
Game executable:
```bash
~/Games/EldenRingPrefix/pfx/drive_c/ELDEN RING/Game/eldenring.exe

```
Wine prefix:
```bash
~/Games/EldenRingPrefix/pfx

```
Under Runner Options:

Enable Use system winetricks

Select Custom Proton-GE, or point to the Proton binary directly.
