# Session و Recovery یوتیوب

YouTube بسته به شبکه، Account و نوع Request ممکن است Login یا Bot Challenge نمایش دهد.

پروژه از این اجزا استفاده می‌کند:

- Google Chrome واقعی
- Chrome Profile ماندگار
- Session احراز هویت‌شده Google/YouTube
- استفاده مجدد از Browser Session/Cookie در Downloader Core
- Recovery هنگام Failure سلامت Session

## چرخه Session

1. درخواست واقعی مرتبط با YouTube می‌رسد.
2. سلامت Session بررسی می‌شود.
3. اگر سالم باشد پردازش ادامه پیدا می‌کند.
4. اگر ناسالم باشد Recovery خودکار انجام می‌شود.
5. اگر کافی نباشد وضعیت Browser Diagnose می‌شود.
6. ادمین هشدار خصوصی دریافت می‌کند.
7. Login/Recovery دستی با SSH Tunnel + noVNC انجام می‌شود.
8. سلامت Session دوباره بررسی می‌شود.

Polling دوره‌ای Session عمداً خاموش است و Validation مبتنی بر Event است.
