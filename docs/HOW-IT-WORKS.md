# How Work Journal works

## What it records

- **Which app is in front, and when.** Work Journal listens for the system's frontmost-application notifications (`NSWorkspace`). It stores the app's name and bundle id and the time. It does not read window titles, URLs, documents or the screen.
- **File activity in folders you choose.** It watches those folders with `FSEvents` and stores the path and the kind of change (created, modified, removed, renamed). It never opens or reads the files.
- **Pause, sleep and lock markers**, so that time away is not counted as work.

## Time away

An app session ends when the Mac sleeps, the screen sleeps or locks, the screen saver starts, you switch user, you pause recording, or you have been idle for 5 minutes. For idle, the session is closed at the moment you stopped, not five minutes later. It resumes when you return.

## Files

- Folders are chosen with the macOS folder picker. The sandbox keeps a security-scoped bookmark so access survives relaunch.
- Noise is ignored: `.git`, `node_modules`, `.build`, `DerivedData`, `.swiftpm`, `__pycache__`, `.Trash`, `.DS_Store`, editor swap and temp files.
- A file touched many times in a day counts once in the day's list; the summary shows how many distinct files changed in each folder.

## Storage

- One file per day, named `YYYY-MM-DD.wjday`, in the app's sandbox container. Folder mode 0700, file mode 0600.
- Each file is a short magic header followed by an AES-256-GCM sealed JSON list of that day's events. The date is bound in as authenticated data, so a day file cannot be swapped for another day's.
- The 256-bit key is generated on your Mac and kept only in the Keychain (generic password, this device only, when unlocked). There is no key file anywhere. If the Keychain refuses, Work Journal keeps today in memory only, writes nothing to disk and says so in the window and the menu.
- Events are written about every 30 seconds and when you quit.
- Days older than your retention setting (30 days, 90 days (default), 1 year or forever) are deleted when the app starts.

## From events to a day

The Journal window turns the events into sessions per app (adjacent sessions of the same app are merged), time per app, a timeline (sessions shorter than a minute are left out of the timeline, not out of the totals), and the files touched per folder.

## Summaries

- By default the summary is a **template** computed on your Mac from those numbers. The window labels it as such.
- If your Mac has Apple's on-device model (the Foundation Models framework) and the setting is on, **Summarize on-device** (Shift-Command-S) asks it to rewrite the same facts in plain sentences. The prompt tells it to use only the facts given. The window then says the text was written by Apple's on-device model. If the model is unavailable or fails, you keep the template.
- Nothing is sent to a server in either case; Work Journal has no network entitlement.

## Keyboard shortcuts

| Shortcut | Action |
|---|---|
| Command-[ and Command-] | Previous and next day |
| Command-T | Jump to today |
| Command-E | Export this day as Markdown |
| Shift-Command-E | Export the last 7 days as Markdown |
| Shift-Command-S | Summarize on-device (when available) |
| Command-comma | Settings |
