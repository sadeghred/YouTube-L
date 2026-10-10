# جریان دانلود و تحویل

## Pipeline

1. دریافت درخواست YouTube
2. بررسی Session احراز هویت‌شده در صورت نیاز
3. دریافت Metadata و تشخیص کیفیت‌های واقعاً موجود
4. اعتبارسنجی کیفیت انتخاب‌شده
5. دانلود Video Stream
6. دانلود Audio Stream سازگار در صورت نیاز
7. Merge/Remux با FFmpeg به MP4
8. بررسی MP4 نهایی با ffprobe
9. استخراج Duration، Width و Height
10. Upload به Telegram Archive به‌عنوان Native Video
11. تحویل Media آرشیوشده به کاربر

## اهمیت Metadata

MP4 بودن فایل به‌تنهایی نمایش صحیح Telegram را تضمین نمی‌کند. ارسال صریح Duration و Dimensions مشکل نمایش فایل‌مانند/قاب کوچک و Duration اشتباه `00:00` را برطرف می‌کند و رفتار Native Video را فراهم می‌کند.
