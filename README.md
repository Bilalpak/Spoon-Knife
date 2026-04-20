# چالش ۴۰ روزه (Web App + Mobile Packaging)

این پروژه یک نسخه تک‌فایلی از برنامه «چالش ۴۰ روزه» است که:

- روی مرورگر موبایل اجرا می‌شود.
- به صورت **PWA** قابل نصب روی گوشی است.
- می‌تواند با **Capacitor** تبدیل به پروژه‌های **Android (APK/AAB)** و **iOS (Xcode project)** شود.

## اجرای محلی

```bash
python3 -m http.server 8080
```

سپس باز کنید:

- `http://localhost:8080`

> برای Service Worker بهتر است از HTTP server استفاده کنید (باز کردن مستقیم فایل با `file://` مناسب نیست).

---

## گزینه ۱: نصب مستقیم روی گوشی به‌عنوان PWA

### Android (Chrome)
1. سایت را باز کنید.
2. از منو گزینه **Install app / Add to Home screen** را بزنید.
3. برنامه مثل اپ مستقل اجرا می‌شود.

### iPhone (Safari)
1. سایت را در Safari باز کنید.
2. Share را بزنید.
3. گزینه **Add to Home Screen** را انتخاب کنید.

---

## گزینه ۲: ساخت APK و iOS app با Capacitor

### پیش‌نیازها
- Node.js 20+
- Android Studio (برای Android)
- Xcode + CocoaPods (برای iOS، فقط روی macOS)

### مراحل

1. مقداردهی اولیه npm:

```bash
npm init -y
npm i @capacitor/core @capacitor/cli
npx cap init challenge40 com.example.challenge40 --web-dir=.
```

2. افزودن پلتفرم‌ها:

```bash
npm i @capacitor/android @capacitor/ios
npx cap add android
npx cap add ios
```

3. همگام‌سازی فایل‌های وب با پروژه موبایل:

```bash
npx cap sync
```

4. باز کردن IDE:

```bash
npx cap open android
npx cap open ios
```

5. خروجی گرفتن:
- Android Studio → Build APK یا AAB
- Xcode → Archive → TestFlight / App Store

---

## نکته مهم

در نسخه فعلی، داده‌ها فقط در حافظهٔ موقت (session) هستند و با بستن اپ از بین می‌روند. برای نگه‌داری دائمی داده‌ها می‌توانید در نسخه بعدی از `localStorage` یا `Capacitor Preferences` استفاده کنید.
