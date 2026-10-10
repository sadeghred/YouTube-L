# YouTube-L

**Self-Hosted YouTube Download & Delivery Service for Telegram**

[فارسی](README.fa.md) · [Architecture](docs/en/ARCHITECTURE.md) · [Download Flow](docs/en/DOWNLOAD-FLOW.md) · [Session & Recovery](docs/en/SESSION-RECOVERY.md) · [Security](docs/en/SECURITY.md)

> **Public repository:** documentation and project presentation only. Production source code, binaries, credentials, cookies, browser profiles, sessions, deployable packages, and downloadable application files are not published here.

## Overview

YouTube-L is a Telegram-based YouTube download service built around a **self-hosted downloader core**. Its primary video-download path is designed to avoid dependence on third-party Telegram downloader bots and to keep extraction, authenticated YouTube access, download, media merge, metadata inspection, archive delivery, and recovery under project control.

The main video pipeline has been validated end-to-end.

## Core Capabilities

- Receive YouTube links through Telegram
- Detect the qualities actually available for each video
- Self-hosted downloader core
- Persistent authenticated Chrome profile for YouTube access
- Browser cookie/session reuse
- Event-driven session health checks tied to real requests
- Automatic recovery attempts
- Private administrator warning when manual login is required
- Manual recovery through SSH tunnel + noVNC
- Video/audio download and MP4 merge/remux
- Final media inspection with `ffprobe`
- Correct Telegram native-video metadata
- Streaming-friendly Telegram delivery
- Telegram archive-based delivery workflow
- Persian and English documentation

## End-to-End Flow

```text
Telegram User
     ↓
YouTube-L Bot
     ↓
YouTube Session Guard
     ↓
Self-Hosted Downloader Core
     ↓
YouTube
     ↓
Video + Audio Streams
     ↓
FFmpeg Merge / Remux
     ↓
ffprobe Metadata
     ↓
Telegram Archive
     ↓
User Delivery
```

If the authenticated YouTube session becomes unhealthy, the recovery layer attempts to restore it. When manual action is required, the administrator is notified and can access the persistent server-side Chrome session through a controlled recovery path.

## Why a Real Chrome Session?

YouTube may present login or automated-access challenges depending on network, account, and request conditions. YouTube-L maintains a persistent authenticated Chrome profile so the downloader core can reuse a real browser session when required.

No real cookies, Google credentials, browser profiles, or production session material are published in this repository.

## Native Telegram Video Delivery

The final MP4 is inspected before upload. Duration, width, and height are supplied explicitly to Telegram so the result is presented as a normal native video rather than a generic document.

This provides:

- Correct duration instead of `00:00`
- Correct aspect ratio and dimensions
- Standard Telegram video player
- Streaming/seek behavior
- Natural large video presentation

## Current Status

| Area | Status |
|---|---|
| Primary video download core | ✅ Operational |
| Real available-quality detection | ✅ Operational |
| Video + audio merge to MP4 | ✅ Operational |
| Native Telegram video presentation | ✅ Operational |
| Persistent Chrome login/session | ✅ Operational |
| Request-driven session health check | ✅ Operational |
| Automatic recovery | ✅ Operational |
| Manual admin recovery workflow | ✅ Operational |
| Periodic session polling | ✅ Intentionally disabled |
| Legacy auxiliary dependency cleanup | ⚠️ In progress |
| Legacy audio/metadata migration | ⚠️ Remaining cleanup |

**Public status:** the primary YouTube video-download path is operational and production-ready. Remaining work focuses mainly on migrating legacy auxiliary audio/metadata paths to the self-hosted core and continuing operational optimization.

## Contact

- Telegram: [@Sadeghred](https://t.me/Sadeghred)
- Email: [sadeghred@gmail.com](mailto:sadeghred@gmail.com)

---
© 2026 YouTube-L Project
