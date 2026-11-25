# Fan-Task-Tick for Android

Fan-Task-Tick is a shared checklist application that keeps working offline. **This Android app is a client of a
Fan-Task-Tick server: it shows that server's checklists and syncs with it. On its own it does nothing.** Today no
Fan-Task-Tick server can be reached from the Internet (they are on a private network), and an account is created
only from an invitation. You can download, check and install this app, but **you cannot use it yet** unless the
person who runs a server has invited you and given you its address.

This repository holds only the signed installation files (APKs) and the information to check them. There is no
source code here.

## Requirements

- Android 9 or later.
- An up-to-date **Android System WebView**, version 120 or later (WebView 120 is the oldest that runs the site's
  pages, measured on them). If yours is older, the app says so and tells you where to update it. It never shows a
  blank screen.
- The address of a Fan-Task-Tick server (`https://…`) and an account on it, from an invitation.

## Install, step by step

1. On your phone, open this repository's **[Releases page](https://github.com/romain-nicod/fan-task-tick-android/releases/latest)**.
   Download only from there, and only from the **latest** release.
2. Download the file named `fan-task-tick-YYYY.MM.DD.NN.apk` (the version is the date of the release).
3. Allow your browser to install apps:
   - The simplest way is to open the downloaded file. Android says your phone isn't allowed to install unknown apps
     from this source. Tap **Settings**, switch on **Allow from this source**, then go back.
   - Or set it in advance: **Settings → Apps → Special app access → Install unknown apps → (your browser) → Allow
     from this source**. On Android 9 the first step is **Apps & notifications**. Other brands use other words:
     search your Settings for "unknown apps".
4. Open the downloaded file and tap **Install**.
5. **Switch "Install unknown apps" off again** for your browser, in the same menu.
6. Open Fan-Task-Tick and type the address of your server. The field is empty: the app suggests no server.

**Never turn off Google Play Protect.** The app isn't on the Play Store, so Play Protect may warn you or offer to
scan it. Let it scan. If it still warns, first check the file as described below; if the check fails, don't install
it.

## Verify the file (recommended)

Each release has a `SHA256SUMS` file. Put the APK and `SHA256SUMS` in the same folder on a computer and run one of
these:

- Linux: `sha256sum -c SHA256SUMS --ignore-missing`
- macOS: `shasum -a 256 -c SHA256SUMS --ignore-missing`
- Windows (PowerShell): `Get-FileHash .\fan-task-tick-YYYY.MM.DD.NN.apk -Algorithm SHA256`, then compare the result
  with the line in `SHA256SUMS`.

If the values don't match, don't install the file.

**Signing certificate:** run `apksigner verify --print-certs fan-task-tick-YYYY.MM.DD.NN.apk`. The `certificate
SHA-256 digest` must be the one below, which each release also carries as `release-cert.sha256`:

```
F9:48:C2:92:1A:62:95:21:BE:CF:B1:06:37:B6:7C:61:E6:47:39:2E:5D:D8:2C:79:60:C7:7A:20:4C:24:2B:49
f948c2921a629521becfb10637b67c61e647392e5dd82c7960c77a204c242b49   (same value, as apksigner prints it)
```

## Updates

- **From the server, in one tap.** Once installed and signed in, the app asks its server for a newer version, at most
  every six hours and once a day in the background on Wi-Fi. It downloads it, checks its size, its SHA-256 and its
  signing certificate, then offers **Mettre à jour**: Android asks you to confirm, and the app restarts in the new
  version with your checklists and your changes not yet sent. The first time, Android asks you to allow
  Fan-Task-Tick to install its own updates.
- **Or from this page:** download the newer APK and install it over the app you have.

**Never uninstall to update.** Uninstalling deletes the app's local data, including the changes it has not sent to
the server yet. Android refuses an older version and refuses a file signed with another certificate; the app does
too, and says so. If that happens, stop and report it.

## Your data

- Your checklists live on your server; the app keeps a local copy so that you can work offline, and sends your
  changes when the network comes back.
- Nothing is copied to a cloud backup. **Uninstalling the app, or clearing its storage, deletes its local copy and
  the changes not yet sent.**

## Privacy

The app talks to the one server whose address you typed, and to nothing else: no analytics, no ads, no Google
service. It asks for three permissions: **internet** (to reach your server), **install packages** (to install its
own updates, each time with your confirmation) and **network state** (so that the daily check waits for Wi-Fi).

## Licence and credits

See [LICENSE](LICENSE) and [NOTICE](NOTICE).

## Support

Ask the person who runs your Fan-Task-Tick server. Please never attach a file exported from the app to a public
issue: it contains your checklists.
