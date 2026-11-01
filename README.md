# AutoPayuz — GitHub Pages versiyasi (Mini App + Tariflar + Statistika + Docs)

Bu papkadagi 4 ta fayl — server TALAB QILMAYDI, GitHub Pages'da to'g'ridan-to'g'ri ishlaydi.
Sahifalar ma'lumotni **API serverdan** (AutoPayuz boti) oladi.

| Fayl | GitHub'dagi manzil | Nima qiladi |
|---|---|---|
| `index.html` | `https://USER.github.io/REPO/` | Telegram **Mini App** (balans, to'lovlar, yechish) |
| `tariflar.html` | `.../tariflar.html` | Tariflar sahifasi (cloud animatsiya) |
| `stats.html` | `.../stats.html` | Statistika dashboard |
| `docs.html` | `.../docs.html` | API hujjatlari |

## 1) E'LON QILISH (2 daqiqa, brauzer orqali)

1. https://github.com/new — repository nomi: `autopayuz` (Public), **Create repository**
2. **Add file → Upload files** — shu papkadagi 4 ta `.html` va `.nojekyll` ni tanlab **Commit changes**
3. **Settings → Pages** → Source: `Deploy from a branch` → Branch: `main` / `/ (root)` → **Save**
4. 1–2 daqiqadan so'ng sayt ishga tushadi: `https://mentalego123-bit.github.io/autopayuz/`

## 2) API MANZILINI BOGLASH (bir marta, majburiy)

Sahifalar qayerdan ma'lumot olishini bir marta aytish kerak:

```
https://mentalego123-bit.github.io/autopayuz/tariflar.html?api=https://BACKEND-MANZILI
```

`BACKEND-MANZILI` — AutoPayuz botining https manzili (hozir: `public_url.txt` dagi trycloudflare
yoki kelajakdagi doimiy domen). Bir marta shunday ochilsa, manzil brauzerda **saqlanib qoladi**
(localStorage) — keyin oddiy havola bilan ham ishlaydi.

## 3) TELEGRAM MINI APP MANZILI

BotFather → `/mybots` → **AutoPayuz** → Bot Settings → **Menu Button** →
**Change Menu Button URL** → yuqoridagi GitHub manzilini kiriting.
Shundan so'ng bot ichida «Open Mini App» tugmasi shu sahifani ochadi.

## MUHIM CHEKLOVLAR

- **GitHub Pages faqat statik fayl ushlaydi.** Bot, to'lov API'si, SQLite baza va webhook'lar
  GitHub'da ISHLAMAYDI — ular doim 24/7 ishlaydigan serverda (VPS) turishi shart.
- **`/pay/ID` to'lov sahifasi GitHub'da bo'la olmaydi** — u dinamik (har to'lov uchun server
  yasaydi) va doim backend manzilida ochiladi.
- Hozir backend `trycloudflare` tunnel'da: kompyuteringiz o'chsa yoki tunnel qayta boshlansa
  URL o'zgaradi va GitHub sahifasi ma'lumot ola olmaydi (yana `?api=` bilan bog'lash kerak).
  Shuning uchun GitHub Pages'dan foyda bo'lishi uchun **avval doimiy domen + 24/7 server** kerak.
- `.env`, `data/autopayuz.db`, `bot.py` — bu papkada YO'Q va GitHub'ga HECH QACHON yuklanmasligi
  kerak (ichida BOT_TOKEN va barcha foydalanuvchi ma'lumotlari bor).
