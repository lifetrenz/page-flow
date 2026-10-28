## What's new in 0.2.3

- **Scanners that redirect to HTTPS now work.** Some scanners, such as HP Enterprise (FutureSmart) MFPs,
  redirect scanning to HTTPS by default. Page-Flow now follows that redirect and scans over HTTPS. A scanner
  added on port 443 is also reached over HTTPS.
- **Scanning works on HP FutureSmart scanners** that previously refused the scan request.
- **Cut-off pages are reported as errors.** If a scanner drops the connection mid-page, Page-Flow now
  reports an error instead of returning an incomplete page.

Install over the previous version; your settings and devices are kept.
