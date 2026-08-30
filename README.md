# Redlighte Music

نسخه‌ی جدید و فارسی‌محور Redlighte Music.

## هدف

یک کاتالوگ موسیقی سریع و RTL برای کشف **آهنگ، خواننده و آلبوم**. Metadata از منابع عمومی موسیقی جمع می‌شود و در Cloudflare D1 نگهداری می‌شود. فایل صوتی داخل GitHub یا D1 ذخیره نمی‌شود.

## معماری

- Cloudflare Workers: API و routing
- Cloudflare D1: Catalog پایدار
- MusicBrainz: metadata و شناسه‌های موسیقی
- TheAudioDB Free API: metadata و artwork تکمیلی
- Cover Art Archive: artwork آلبوم‌های MusicBrainz
- Static Assets: رابط فارسی RTL

## API

- `GET /api/health`
- `GET /api/music`
- `GET /api/music/search?q=...`
- `GET /api/music/song/:id`
- `GET /api/music/artist/:id`
- `GET /api/music/album/:id`
- `GET /api/music/cover?url=...`

## Cloudflare

Binding دیتابیس باید دقیقاً این باشد:

`MUSIC_DB`

Database name:

`prod-d1-tutorial`

بعد از تغییر Schema، آن را روی D1 ریموت اجرا کنید:

```bash
npm install
npm run db:apply
npm run deploy
```

## پخش صوتی

این پروژه فایل‌های صوتی را دانلود یا میزبانی نمی‌کند. Player فقط وقتی فعال می‌شود که برای یک رکورد، یک `audio_url` از یک منبع مجاز در Catalog ثبت شده باشد. Metadata API به‌تنهایی منبع پخش نیست.

## زبان

رابط کاربری پیش‌فرض فارسی و RTL است؛ نام‌های اصلی هنرمند/آهنگ دست‌نخورده نگه داشته می‌شوند تا Search بین فارسی و لاتین بهتر عمل کند.
