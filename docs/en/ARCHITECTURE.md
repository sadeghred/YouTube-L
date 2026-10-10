# Architecture

```text
Telegram User -> Bot -> YouTube Session Guard -> Self-Hosted Downloader Core
                                      |                |
                                      |                v
                                      |             YouTube
                                      v
                                  Recovery
                                      |
                          Persistent Chrome Profile
                                      |
                         Admin alert when required

Downloader Core -> Media Streams -> FFmpeg -> ffprobe -> Telegram Archive -> User
```

## Design Principles

1. **Self-hosted primary download path** — the main video path does not rely on a third-party Telegram downloader bot.
2. **Real browser session** — a persistent Chrome profile provides authenticated YouTube state when needed.
3. **Event-driven health checks** — session checks are tied to real requests rather than constant polling.
4. **Recovery before final failure** — automatic recovery is attempted before administrator intervention.
5. **Native Telegram media** — final video metadata is supplied explicitly for correct presentation.
