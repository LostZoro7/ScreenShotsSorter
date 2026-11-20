# ScreenShotsSorter

A small Windows app that gathers screenshots from all your game and app folders into one place, automatically, in the background.

Tools like AMD Software, NVIDIA App/GeForce Experience and others save screenshots into a separate subfolder for every game. ScreenShotsSorter watches those folders and moves every new screenshot into a single folder you choose, so you never have to dig through ten different directories.

<!-- Add a screenshot of the app at docs/screenshot.png -->

## Features

- **Pick a root folder, get all subfolders.** Add your capture tool's main screenshot folder once and every game folder inside it is watched, including folders created later. Add as many root folders as you like.
- **Runs quietly in the background.** Designed to stay light on resources: by default it reacts to new files as they appear instead of constantly scanning.
- **Check interval.** Prefer scheduled checks? Choose Instant, 5 sec, 10 sec, 30 sec, 1 min or 5 min.
- **Safe moving.** Waits until the capture tool has finished writing a file before moving it.
- **Duplicate handling.** If a file name already exists, rename it with a timestamp, skip it, or replace it.
- **File types.** Choose which extensions to move (default: png, jpg, jpeg, bmp, webp).
- **Start with Windows**, optionally **start hidden**.
- **Hide it your way.** Show or hide the tray icon, and keep the window out of the taskbar.
- **Choose what closing the window does.** Ask each time, keep running in the background, or quit.
- **Recent activity.** The window lists the latest sorted files, including ones moved while it was closed.
- **Pause** and **Sort now** controls.
- 
<p align="center">
  <img src="https://i.ibb.co.com/BKLyBrny/image.png">
</p>

## Requirements

- Windows 10 or 11 (64-bit)
- [.NET 8 Desktop Runtime](https://dotnet.microsoft.com/download/dotnet/8.0) (x64)

## Download and install
 
1. Download `ScreenShotsSorter.exe` from the [Releases](https://github.com/LostZoro7/ScreenShotsSorter/releases) page.
2. Put it anywhere you like and run it.
No installer is needed. If you enable **Start with Windows**, don't move the exe afterwards, or turn the switch off and on again.
 
**Windows may show "Windows protected your PC" the first time.** The app isn't code-signed. Click **More info**, then **Run anyway**.

## Getting started

1. Click **Add folders** and choose the main screenshot folder of your capture tool (for example the folder that contains all the per-game subfolders). Subfolders are included automatically.
2. Under **Move screenshots to**, click **Browse** and pick your destination folder.
3. That's it. New screenshots are moved as they appear.

> Screenshots are **moved**, not copied. They are removed from the source folders.

## Settings

| Setting | What it does |
| --- | --- |
| Folders to watch | Root folders to monitor, subfolders included |
| Move screenshots to | Destination folder |
| Check for new screenshots | Instant, or every 5 sec to 5 min |
| Start with Windows | Launches at sign-in |
| Start hidden | Skips opening the window when launched at sign-in |
| Show tray icon | Turn off to hide the app completely |
| Hide from taskbar | Keeps the window out of the taskbar |
| When I close the window | Ask me, keep running, or quit |
| If a file name already exists | Rename, skip or replace |
| File types | Extensions to move |

Settings are saved automatically.

### Running fully hidden
 
If you turn the tray icon off, nothing is visible while the app runs. To get the window back, just launch `ScreenShotsSorter.exe` again. It opens the window of the copy that is already running.
 
## Privacy and what it touches
 
- It only moves image files between folders you choose.
- It doesn't use the internet and doesn't collect or send any data.
- Settings are stored locally in `%AppData%\ScreenShotsSorter\settings.json`. Deleting that folder resets the app.
- If you turn on **Start with Windows**, it adds one entry named `ScreenShotsSorter` under `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run`. Turning the switch off removes it.

### Where things are stored

- Settings: `%AppData%\ScreenShotsSorter\settings.json`
- Start with Windows: one entry named `ScreenShotsSorter` under `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run`

Deleting the settings folder resets the app to its defaults.

## How it works

By default the app uses Windows file-system notifications, so it does nothing until a new image file actually appears. In interval mode it stops watching, sleeps, and scans your folders once every N seconds instead. Either way, each file is checked to make sure it is no longer being written before it is moved. Files that were saved while the app wasn't running are picked up by a scan when it starts.

If the destination folder is inside a watched folder, files already in the destination are ignored.

**Does it work with AMD, NVIDIA, Steam and other tools?**
It works with any tool that saves screenshots as image files in a folder. Point it at that tool's screenshot folder.

**Does it run before I sign in to Windows?**
No. It runs in your user session, from sign-in onward.

**How do I fully stop it?**
Choose Quit in the close prompt, set "When I close the window" to Quit, or right-click the tray icon and choose Quit. You can also end `ScreenShotsSorter.exe` in Task Manager.

## Disclaimer
 
Provided as is, without warranty. Screenshots are moved out of your source folders, so choose your folders carefully.
## License

This project is licensed under the [MIT License](LICENSE).
