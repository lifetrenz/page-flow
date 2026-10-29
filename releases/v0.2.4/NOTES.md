## What's new in 0.2.4

- **Failure reasons are shown.** The console and the WAPP now say why a device is unavailable: no answer,
  an error, a reply that was not understood, or a changed certificate.
- **Scanners can be added by `https://` address**, as `https://address[:port]`.
- **HTTPS-only scanners are discovered.** Scanners that advertise eSCL over HTTPS are found automatically, and
  HTTPS is preferred when a scanner offers both.
- **Scanner certificates are pinned on first use.** A changed certificate is refused until an admin clicks
  **Trust new certificate** in the console, and a pinned scanner is never contacted over plain HTTP. If a
  scanner's HTTPS is turned off on purpose, an admin can use **Reset secure connection** in the console.

**For integrators:** `device_unavailable` is HTTP 503 even when `retryable` is `false` (for example, a changed
certificate). Decide whether to retry from `retryable`, not from the status code.

Install over the previous version; your settings and devices are kept.
