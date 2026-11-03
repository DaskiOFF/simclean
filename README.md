# SimClean

A native macOS app to manage Xcode simulators, reclaim disk space, and inspect app data.

Simulators accumulate as you work across projects and iOS versions. SimClean shows which devices take up space, lets you protect the ones you need, and helps you remove the rest.

## Download and install

Once a release is published, open this repository's **Releases** section and download `Simclean.dmg` from **Assets**.

1. Open the DMG.
2. Drag **Simclean** into **Applications**.
3. Launch the app with Xcode and Simulator installed.

Updates are installed manually by downloading a newer release.

## Requirements

- Apple Silicon Mac.
- macOS 14 Sonoma or later.
- Xcode with Simulator installed.

The current app interface is in Russian.

## What you can do

- **Find large simulators.** Sort devices by size and search by name, operating system, or UDID.
- **Protect devices from deletion.** Keep frequently used simulators while reviewing the others.
- **Delete or reset selected devices.** Select multiple devices and review the list before confirming an operation.
- **Inspect app files.** Browse app containers, App Groups, or a simulator's data directory. Filter by file name or modification time.
- **Compare file snapshots.** See which files were added, changed, or removed. Save named snapshots for later comparisons.
- **Open folders directly.** Jump to Finder or Terminal from a simulator or file.
- **Choose your environment.** Select an Xcode installation or a different CoreSimulator device set.

## How cleanup works

SimClean uses Apple's `simctl` commands to delete devices or reset their content and settings.

| Action | Result |
| --- | --- |
| Delete a device | Removes the simulator device, its installed apps, and its data. |
| Reset a device | Keeps the device and erases its apps, data, and settings. |
| Protect a device | Prevents deletion. A reset is still possible after confirmation. |

Running devices cannot be deleted or reset. The app rechecks device state and protection before each operation. Shared operating system runtimes are not removed.

**Deletion and reset cannot be undone.** Review the selection before confirming.

Displayed sizes estimate the space used by device folders, excluding shared runtimes. APFS can share storage blocks, so the actual increase in free disk space may differ.

## File snapshots

Snapshots store file metadata, not file contents. They help compare changes but are not backups and cannot restore deleted files. Incomplete scans cannot be used for comparisons.

## Privacy

Simulator scanning, cleanup, and file inspection run locally on your Mac. The current app does not send usage analytics or simulator data to a server. Downloading the app takes place through GitHub.

## Feedback

If you report a problem, include your macOS, Xcode, and SimClean versions, the steps to reproduce it, and the error message. Remove private project names, paths, and file contents from screenshots or logs before sharing them.
