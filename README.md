# TvLauncher

A lightweight, modern home screen launcher for old Android TVs (Android 4.4+, 512 MB RAM) with a remote-friendly app grid and an option to open a chosen app automatically at startup.

Built for TVs that are stuck with a slow or limited stock launcher and have no setting to choose a start-up app or input.

## Features

- **Remote-friendly app grid**: move with the arrow keys, open with OK. The selected app zooms slightly so it is easy to see from the couch.
- **Modern look**: dark gradient background, clock and date, rounded cards.
- **Startup app**: pick one app that opens automatically after the TV starts. A short countdown (3, 5, 10 or 15 seconds) lets you cancel by pressing any button.
- **Once per power-on**: auto-start runs only once per boot, so pressing Home inside an app never throws you back into the startup app.
- **Shows hidden apps**: lists apps that do not appear in normal launchers, and lets you add any installed app by hand.
- **Default home helper**: a menu item that helps you make TvLauncher the default home screen on Android 4.4, which has no setting for it.
- **Tiny and fast**: no third-party libraries, a few hundred KB of code, suitable for 512 MB of RAM.
- **Export tool**: saves a report about the TV's original software to a file, for troubleshooting.

## Requirements

- Android 4.4 (API 19) or newer
- To build: Android Studio, or the Android SDK with JDK 17

## Build

1. Open the project folder in **Android Studio** and let Gradle sync.
2. Choose **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
3. The APK is at `app/build/outputs/apk/debug/app-debug.apk`.

Command line: `./gradlew assembleDebug`

## Install on the TV

1. Copy the APK to a USB drive and plug it into the TV.
2. On the TV, turn on **Settings > Security > Unknown sources**.
3. Open a file manager on the TV and install the APK. Installing over an older version keeps your settings.

## Make it the default home screen

Android 4.4 has no menu for this. It is chosen with the Home button:

1. Open TvLauncher.
2. Press **Home** on the remote. If Android shows "Complete action using", choose **TvLauncher** and then **Always**.

If the list does not appear, another launcher was saved as "Always" earlier. In TvLauncher, select the button at the top right and choose **Make this the default home screen**. It will either show the list, or open the old launcher's App info page where you select **Clear defaults**. Then press Home and choose TvLauncher > Always.

A yellow hint under the clock is shown while TvLauncher is not yet the default.

To go back to the old launcher: **Settings > Apps > TvLauncher > Clear defaults**.

## Usage

| Action | How |
| --- | --- |
| Open an app | Select it and press **OK** |
| App options | Hold **OK** or press **MENU** on an app |
| Settings | Select the button at the top right |
| Set the startup app | App options > *Open this automatically when the TV starts* |
| Cancel the startup countdown | Press any button |

**Settings menu**

- Make this the default home screen
- Auto-start on or off
- Delay before starting (3 / 5 / 10 / 15 seconds)
- Choose the startup app
- Add a missing app to the home screen
- Find a TV / HDMI input screen (advanced)
- Show or hide hidden/system apps
- Export info for the developer
- Test auto-start now
- Remove the startup app

### An app is missing from the grid

Open the top-right button > **Add a missing app to the home screen**, pick it from the alphabetical list, then choose **Add to the home screen**. To remove a tile you added: hold OK on it > *Remove from the home screen*.

## Known limitations

- **Live HDMI / set-top-box tile.** Many TVs' stock launchers show the live picture from an HDMI input as a tile and open it full screen when clicked. That picture is drawn by the TV's own hardware, not by an app, and is controlled through the manufacturer's private system software. TvLauncher cannot show that tile, and may not be able to switch to the HDMI input at startup on every TV. The *Find a TV / HDMI input screen* tool and the export file are there to investigate this for a specific model.
- **Standby.** If the TV goes into standby instead of fully restarting, Android may keep the launcher in memory and the startup app will not open when the TV wakes up.
- **Some firmwares block changing the home app.** On those TVs, TvLauncher cannot become the default.

## Export info

*Settings > Export info for the developer* saves `TvLauncherExport/tv_export.zip` on the TV's storage. It contains the stock launcher and TV-related system apps, and a text report listing the device and installed packages. Nothing is uploaded: the app has no network access, and the file only leaves the TV if you copy it yourself.

## Contributing

Issues and pull requests are welcome, especially:

- reports of which TV models work, and how to open their HDMI input
- fixes for other Android versions or screen sizes

## License

Licensed under the [GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html). See the `LICENSE` file.

You are free to use, study, change and share this software. If you distribute a modified version, you must release its source code under the same license.
