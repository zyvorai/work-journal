# Frequently asked questions

## Does Work Journal send anything over the network?

No. It is sandboxed and ships without the network entitlement, so it cannot connect. Check it yourself: see [Privacy](PRIVACY.md).

## Does it record my screen or what I type?

No. It records which app is in front and when, plus file names and paths in folders you choose. No screen recording, no window titles, no keystrokes, no file contents.

## Where is my data, and can I delete it?

In encrypted day files inside the app's sandbox container, with the key in your Keychain. **Settings > Data > Delete All Journal Data…** removes every day. You can also choose how long days are kept.

## Does the summary use AI?

Only if you click **Summarize on-device** and your Mac has Apple's on-device Foundation Models available. Otherwise you get a template summary computed from your numbers. The window always says which one you are reading.

## Why is the time lower than I expected?

Time away is not counted: sleep, lock, screen saver and 5 idle minutes end the session. Work Journal's own window is not counted either.

## Does it work with several displays, Spaces or full-screen apps?

It follows the frontmost application, so yes in principle. We have not tested those setups in this release.

## Is there a trial?

Free 30-day trial key: [sales@zyvor.dev](mailto:sales@zyvor.dev?subject=Work%20Journal%20trial%20key). Price: ₹2,999 per Mac per year including GST (about US$30). Teams of 5 or more Macs: ₹2,549 per Mac per year, by invoice. Paid licences: contact [sales@zyvor.dev](mailto:sales@zyvor.dev?subject=Work%20Journal%20licence). Without a key everything still works.

## What happens when the trial ends?

The status line says the licence has expired. Nothing is disabled.

## Which macOS?

macOS 27 or later.

## Are the screenshots real?

They are the real app windows rendered with invented sample data, not captures of anyone's journal. Every caption says so.

## Can I see the source?

No. The Work Journal source code is private; this repository holds the documentation, website and downloads.
