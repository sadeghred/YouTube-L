# YouTube-L

**سرویس Self-Hosted دانلود و تحویل ویدئوی YouTube در Telegram**

[English](README.md) · [معماری](docs/fa/ARCHITECTURE.md) · [جریان دانلود](docs/fa/DOWNLOAD-FLOW.md) · [Session و Recovery](docs/fa/SESSION-RECOVERY.md) · [امنیت](docs/fa/SECURITY.md)

> **Repository عمومی:** فقط برای معرفی پروژه و مستندات است. سورس Production، Binary، Credential، Cookie، Browser Profile، Session، بسته قابل Deploy و فایل دانلود برنامه منتشر نمی‌شوند.

## معرفی

YouTube-L یک سرویس دانلود از YouTube بر بستر Telegram است که هسته اصلی آن یک **Downloader Core مستقل و Self-Hosted** است. مسیر اصلی دانلود ویدئو به ربات‌های دانلودر شخص ثالث وابسته نیست و کنترل استخراج، دسترسی احراز هویت‌شده به YouTube، دانلود، Merge، بررسی Metadata، تحویل Archive و Recovery در اختیار خود پروژه است.

مسیر اصلی Video Download به‌صورت End-to-End تست و عملیاتی شده است.

## قابلیت‌های اصلی

- دریافت لینک YouTube در Telegram
- تشخیص واقعی کیفیت‌های موجود هر ویدئو
- Downloader Core مستقل روی سرور
- Chrome Profile واقعی، احراز هویت‌شده و ماندگار
- استفاده مجدد از Cookie/Session مرورگر
- Health Check فقط هنگام درخواست واقعی
- Recovery خودکار
- هشدار خصوصی ادمین در صورت نیاز به Login دستی
- Recovery دستی با SSH Tunnel و noVNC
- دانلود Video/Audio و Merge/Remux به MP4
- بررسی فایل نهایی با `ffprobe`
- ارسال Native Video با Metadata صحیح
- پشتیبانی Streaming در Telegram
- تحویل مبتنی بر Telegram Archive
- مستندات فارسی و انگلیسی

## جریان End-to-End

```text
کاربر Telegram
     ↓
ربات YouTube-L
     ↓
YouTube Session Guard
     ↓
Downloader Core محلی
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
تحویل به کاربر
```

اگر Session احراز هویت‌شده YouTube ناسالم شود، Recovery ابتدا تلاش می‌کند آن را بازیابی کند. اگر اقدام دستی لازم باشد، ادمین مطلع می‌شود و می‌تواند از مسیر کنترل‌شده به Chrome ماندگار سرور دسترسی پیدا کند.

## چرا Chrome واقعی؟

YouTube بسته به شبکه، حساب و نوع درخواست ممکن است Login/Bot Challenge نمایش دهد. پروژه یک Chrome Profile ماندگار و احراز هویت‌شده نگه می‌دارد تا Downloader Core در صورت نیاز از Session واقعی Browser استفاده کند.

هیچ Cookie، Google Credential، Chrome Profile یا Session واقعی در Repository عمومی منتشر نمی‌شود.

## نمایش صحیح Video در Telegram

MP4 نهایی قبل از Upload بررسی می‌شود و Duration، Width و Height به Telegram داده می‌شود تا فایل به‌صورت Native Video نمایش داده شود، نه Document عمومی.

نتیجه:

- Duration صحیح به‌جای `00:00`
- Aspect Ratio صحیح
- Player استاندارد Telegram
- Streaming و Seek
- نمایش طبیعی و بزرگ Video

## وضعیت فعلی

| بخش | وضعیت |
|---|---|
| Core اصلی دانلود ویدئو | ✅ عملیاتی |
| تشخیص واقعی کیفیت‌های موجود | ✅ عملیاتی |
| Merge ویدئو + صدا به MP4 | ✅ عملیاتی |
| نمایش Native Video در Telegram | ✅ عملیاتی |
| Login/Session ماندگار Chrome | ✅ عملیاتی |
| Health Check هنگام درخواست | ✅ عملیاتی |
| Recovery خودکار | ✅ عملیاتی |
| Recovery دستی ادمین | ✅ عملیاتی |
| Polling دوره‌ای Session | ✅ عمداً خاموش |
| حذف وابستگی‌های جانبی Legacy | ⚠️ در حال تکمیل |
| مهاجرت Audio/Metadata قدیمی | ⚠️ باقی‌مانده |

**وضعیت عمومی:** مسیر اصلی دانلود ویدئو از YouTube عملیاتی و Production-ready است. کارهای باقی‌مانده عمدتاً مهاجرت مسیرهای جانبی Legacy صوت/Metadata به Core محلی و بهینه‌سازی عملیاتی هستند.

## تماس

- تلگرام: [@Sadeghred](https://t.me/Sadeghred)
- ایمیل: [sadeghred@gmail.com](mailto:sadeghred@gmail.com)

---
© 2026 YouTube-L Project
