# Privacy and verification

## Never recorded

- Screen contents: no screen recording, no screenshots.
- Window titles, browser URLs or tab names.
- Keystrokes or clipboard.
- File contents. Only file names and paths inside the folders you choose.

## Recorded

- The name and bundle id of the frontmost app, with times.
- File paths and the kind of change in your chosen folders. Paths can contain project or client names, so treat exports accordingly.
- Pause, resume and away markers.

## Verify: no network entitlement

Work Journal is App Sandboxed and ships without `com.apple.security.network.client` and `com.apple.security.network.server`. With the sandbox on, the kernel blocks outbound and inbound network connections for the process. Run this on the installed app:

```
codesign -d --entitlements :- /Applications/WorkJournal.app
```

Output for the 0.1.1 release:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "https://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>com.apple.security.app-sandbox</key>
    <true/>
    <key>com.apple.security.files.bookmarks.app-scope</key>
    <true/>
    <key>com.apple.security.files.user-selected.read-write</key>
    <true/>
  </dict>
</plist>
```

Three entitlements: the sandbox, access to folders you pick in the picker, and app-scoped bookmarks for them. No network, no camera, no microphone, no Apple Events, no screen recording.

## Verify: the download is the notarized build

```
shasum -a 256 -c WorkJournal-0.1.1.dmg.sha256
spctl -a -t open --context context:primary-signature -v WorkJournal-0.1.1.dmg
codesign --verify --deep --strict --verbose=2 /Applications/WorkJournal.app
```

## Encryption

Day files are AES-256-GCM sealed with a random 256-bit key held only in your Keychain. See [How it works](HOW-IT-WORKS.md#storage). This protects the day files if they are copied without your Keychain. It does not protect against someone who is logged in as you with your Keychain unlocked.

## Exports

Exports are plain text. They are written only where you choose in the save panel, and are then your responsibility.

## Not verified by us

VoiceOver labels are provided in the Journal window but have not been tested with VoiceOver in this release. The privacy claims above are about this app; Apple's on-device model is Apple's framework.
