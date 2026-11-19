# Install Work Journal

## Requirements

- macOS 27 or later (the app's minimum system version).
- A menu-bar app: it has no Dock icon. Look for the book symbol in the menu bar.

## 1. Download and verify

Download [WorkJournal-0.1.1.dmg](https://github.com/zyvorai/work-journal/releases/download/v0.1.1/WorkJournal-0.1.1.dmg) and its `.sha256` file from the [release page](https://github.com/zyvorai/work-journal/releases/tag/v0.1.1). The DMG is Developer ID signed and notarized by Apple.

```
shasum -a 256 -c WorkJournal-0.1.1.dmg.sha256
xcrun stapler validate WorkJournal-0.1.1.dmg
```

The SHA-256 of this release is `cc71cf0a9fcb1d184faec85e3d912e3d4a444675e35f1388909453c6b8488c69`.

## 2. Install

Open the DMG and drag **WorkJournal** to Applications, then open it.

## 3. First launch

A short Welcome window explains what is recorded, where it goes and the optional launch at login. It asks for no permissions. After that the book symbol sits in the menu bar; its menu shows whether Work Journal is recording, today's active time, Pause Recording, Open Journal, Settings, Licence, About and Quit.

## 4. Choose folders (optional)

Without folders Work Journal logs only which app is in front. To log file activity too, open **Settings > Watched folders > Add Folder…** and choose folders in the standard macOS picker. Only file names and paths are recorded, never contents.

## 5. Launch at login (optional)

Turn it on under **Settings > General**, or add Work Journal under System Settings > General > Login Items, so the day is covered from the first minute.

## 6. Trial key

You do not need a key to use Work Journal: with no key everything works and the status line says so. Free 30-day trial key: [sales@zyvor.dev](mailto:sales@zyvor.dev?subject=Work%20Journal%20trial%20key). Paid licences: contact [sales@zyvor.dev](mailto:sales@zyvor.dev?subject=Work%20Journal%20licence). Enter a key under **Licence…** in the menu. See [Trial and licence](LICENSING.md).

## Uninstall

- Quit Work Journal and delete it from Applications.
- To erase the journal first, use **Settings > Data > Delete All Journal Data…**. That removes the encrypted day files, not the Keychain key.
- The day files live inside the app's sandbox container (`~/Library/Containers/dev.zyvor.journal`). The encryption key is a Keychain item with the service name `dev.zyvor.journal.store`; delete it in Keychain Access if you want it gone.
