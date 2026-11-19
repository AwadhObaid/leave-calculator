# حاسبة الإجازة — تطبيق الهاتف

## الطريقة 1: تثبيت كتطبيق (PWA) — الأسرع، بدون APK
1. ارفع محتويات مجلد `www/` كما هي إلى أي استضافة HTTPS (GitHub Pages أو Netlify أو Cloudflare Pages أو Vercel).
2. افتح الرابط على الهاتف:
   - أندرويد (Chrome): القائمة ⋮ ← «تثبيت التطبيق» أو «إضافة إلى الشاشة الرئيسية».
   - آيفون (Safari): زر المشاركة ← «إضافة إلى الشاشة الرئيسية».
3. يعمل بعد التثبيت بدون إنترنت، ويحفظ إعداداتك.

> لن يعمل التثبيت عند فتح الملف مباشرة من الجهاز (file://)؛ يلزم رابط https.

## الطريقة 2: ملف APK لأندرويد (Capacitor)
### بدون Android Studio (عبر GitHub)
1. أنشئ مستودعًا على GitHub وارفع كل محتويات هذا المجلد (بما فيها `.github`).
2. من تبويب Actions شغّل «Build APK».
3. حمّل ملف `leave-calculator-apk` من نتائج التشغيل، وفيه `app-debug.apk` لتثبيته على هاتفك (فعّل «التثبيت من مصادر غير معروفة»).

### على جهازك (يلزم Node 18+ و JDK 17 و Android Studio)
```
npm install
npx cap add android
npx cap sync android
cd android && ./gradlew assembleDebug
```
الناتج: `android/app/build/outputs/apk/debug/app-debug.apk`

لتغيير اسم الحزمة عدّل `appId` في `capacitor.config.json` قبل `cap add android`.
لنشر التطبيق على Google Play تحتاج نسخة موقّعة (release) بمفتاح توقيع خاص بك.
