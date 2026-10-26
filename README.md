# Page-Flow Agent

Page-Flow is a small program that runs on a workstation and lets the Lifetrenz web application scan
and print with the scanners and printers on that workstation's network, straight from the browser.
It replaces "scan to the desktop, then upload the file" with a **Scan and Upload** button inside the
application.

This repository publishes the **Windows installer** only. The browser-side client is the npm package
[`@lifetrenz/page-flow`](https://www.npmjs.com/package/@lifetrenz/page-flow).

## Download

**[Download the latest installer for Windows](https://github.com/lifetrenz/page-flow/releases/latest/download/PageFlow-Setup.exe)**

Every version, with its release notes and checksum, is on the
[Releases](https://github.com/lifetrenz/page-flow/releases) page.

| | |
|---|---|
| System | Windows 10 or 11, 64-bit |
| Admin rights | Not needed; it installs for the current user |
| Install folder | `%LOCALAPPDATA%\Programs\Page-Flow` |
| macOS, Linux | Not available yet |

## Install

1. Run `PageFlow-Setup.exe`.
2. The installer and the agent are signed by **DWISE Healthcare IT Solutions Private Limited**. While
   the certificate is still building its reputation with Microsoft, Windows SmartScreen may show
   "Windows protected your PC" with that publisher name. Choose **More info**, then **Run anyway**,
   after checking the file (see *Verify the download*).
3. During setup, set the **admin secret**. Your IT team uses it to open the agent's admin console. It
   is separate from the pairing token the web application uses.
4. Page-Flow starts and shows an icon in the system tray. It starts again when you sign in.

## Set up

- **Admin console:** open <http://127.0.0.1:52180/admin/> on the workstation and unlock it with the
  admin secret. From there you can find scanners and printers on the network, add one by its
  address, choose the default scanner and printer, test them, and see the pairing token.
- **Web application:** in the application's **Agent Settings**, enter the port and the pairing token
  shown in the admin console.
- **Ports:** 52180 (HTTP) and 52181 (HTTPS), on `127.0.0.1` only. The installer lets you change them.

## Verify the download

Each release includes a `.sha256` file. In PowerShell:

```powershell
Get-FileHash .\PageFlow-Setup.exe -Algorithm SHA256
```

The hash must match the one in `PageFlow-Setup.exe.sha256` on the release page. To check the
signature, open the file's **Properties → Digital Signatures**: the signer must be
DWISE HEALTHCARE ITSOLUTIONS PRIVATE LIMITED.

## Privacy

Page-Flow listens only on `127.0.0.1`, so other computers cannot reach it. Scanned pages go from the
scanner to the browser on the same workstation; Page-Flow does not send them anywhere else. Its log
records device names and outcomes, never document content, tokens or secrets.

## Uninstall

Windows **Settings → Apps → Installed apps → Page-Flow Agent → Uninstall**.

---

Lifetrenz Page-Flow Agent. © DWISE Healthcare IT Solutions Private Limited. All rights reserved.
