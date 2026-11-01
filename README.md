# C2K Demo Viewer

A Windows app for watching CS2 demos with a custom input overlay and player HUD. Built by **cs2kitchen**.

Open a demo, pick a player and see their recorded movement, attacks, velocity and weapon information. Step through ticks and rounds, change the overlay layout, or launch the demo in CS2 and record it with OBS.

![C2K Demo Viewer](docs/screenshots/overview.png)

## Download

Get these two files from the **Releases** section:

- `C2K-Demo-Viewer-Setup-0.20.2.exe`
- `SHA256-0.20.2.txt`

Run the setup file and open C2K Demo Viewer. The desktop runtime and helper tools are included. You don't need to install them separately.

You need Windows 10 version 2004 or later, or Windows 11, on a 64-bit PC. Steam and CS2 must already be installed for playback in the game. You can inspect a demo and work on overlays without launching CS2.

The installer is unsigned. The publisher name in its file details is `cs2kitchen`, but Windows may still display **Unknown publisher**.

### Check the download

Open PowerShell in the folder containing the installer and run:

```powershell
Get-FileHash .\C2K-Demo-Viewer-Setup-0.20.2.exe -Algorithm SHA256
```

Compare the result with `SHA256-0.20.2.txt`. The letters can be upper- or lowercase; the hash should otherwise match exactly.

## Using it

1. Click **Open demo…** and choose a `.dem` file. Wait for parsing to finish.
2. Select a player. Use the timeline, tick buttons and round controls to review their inputs.
3. Open **Appearance** to change fonts, colours, scale and opacity. **Overlay studio** lets you move and resize individual elements.
4. Save a preset if you want to reuse the layout.
5. For playback in CS2, click **Play demo**, choose your rounds or highlights and start the local session.

### Recording with OBS

Set CS2 to **Fullscreen Windowed** and use **Display Capture** in OBS to capture both the game and the overlay. Select the display running CS2 and check the OBS preview before recording.

C2K starts the game with `-insecure` and sets `sv_lan 1` for local demo playback.

The overlay can show movement and attack inputs, velocity, a player card, health, armour, weapons, ammo, a team strip, chat and voice activity when that information exists in the demo. Player names and portraits can be changed. A vertical layout is available for a 9:16 crop.

You can also export the input overlay, or combine it with existing gameplay footage. Imported footage needs timing calibration so the overlay lines up with the video.

## Appearance

![Overlay settings](docs/screenshots/appearance.png)

## Overlay studio

![Overlay layout editor](docs/screenshots/overlay-studio.png)

These are interface previews from version 0.20.2. The layout editor uses sample player data; it isn't a screenshot of a live match.

## A few things to know

- Inputs come from the demo. They describe game actions, not necessarily the physical key or mouse-wheel direction used.
- Local playback starts CS2 with `-insecure` and `sv_lan 1`. This app is for demo playback, not matchmaking.
- CS2 updates can affect local playback. If playback stops working after an update, check for a new app release.
- Optional captions are processed locally. They need recorded voice data and may contain transcription mistakes.
- Optional TTD, preaim and match estimates are experimental. They aren't official HLTV statistics.

Settings, presets and demo caches are stored in `%LOCALAPPDATA%\C2KDemoViewer`. Open **About / uninstall** to open the installation folder or remove the app. Keep your local data for a later installation, or select **Remove all local data too** to permanently delete settings, presets, imported portraits, demo caches and logs. Original demos and exported recordings are kept. Unchanged C2K spectator configs are removed or restored from their backups. The same choice is available when uninstalling through Windows Settings.

## Problems or feedback

Open an issue with the app version, your Windows version and the steps that caused the problem. Add a screenshot if it helps. Check logs and screenshots for personal information before posting them; don't attach private demos or voice recordings.

