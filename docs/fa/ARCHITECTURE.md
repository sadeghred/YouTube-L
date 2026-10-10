# معماری

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

## اصول طراحی

1. **مسیر اصلی Self-Hosted** — دانلود اصلی ویدئو به ربات دانلودر Telegram شخص ثالث وابسته نیست.
2. **Session واقعی Browser** — Chrome Profile ماندگار در صورت نیاز وضعیت احراز هویت‌شده YouTube را فراهم می‌کند.
3. **Health Check مبتنی بر رویداد** — بررسی Session به درخواست واقعی متصل است و Polling دائمی انجام نمی‌شود.
4. **Recovery قبل از Failure نهایی** — قبل از دخالت ادمین Recovery خودکار امتحان می‌شود.
5. **Native Telegram Media** — Metadata نهایی Video صریحاً برای نمایش صحیح به Telegram داده می‌شود.
