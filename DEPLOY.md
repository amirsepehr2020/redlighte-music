# راه‌اندازی Redlighte Music

## 1) D1

Database موجود:

- Name: `prod-d1-tutorial`
- Worker binding: `MUSIC_DB`

Schema جدید را یک‌بار روی D1 اجرا کنید. توجه: این Schema داده‌های قدیمی جداول Music را حذف و ساختار جدید را از صفر می‌سازد.

```bash
npm install
npm run db:apply
```

یا محتوای `schema.sql` را در D1 Console اجرا کنید.

## 2) Deploy

```bash
npm run deploy
```

## 3) تست

```text
/api/health
/api/music
/api/music/search?q=شادمهر
```

صفحه:

```text
/music/
```

## 4) اتصال به redlighte.ir

Worker را به Route موردنظر Cloudflare متصل کنید؛ برای مثال:

`redlighte.ir/music/*`

## 5) پخش صوتی

این پروژه خودش فایل موسیقی را دانلود یا ذخیره نمی‌کند. برای پخش، رکورد باید `audio_url` معتبر و مجاز داشته باشد. MusicBrainz و TheAudioDB منبع عمومی Metadata هستند و نباید به‌عنوان منبع فایل صوتی فرض شوند.
