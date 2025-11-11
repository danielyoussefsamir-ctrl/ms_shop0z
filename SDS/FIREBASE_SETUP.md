# دليل إعداد Firebase للمصادقة

## خطوات التفعيل الكامل للمصادقة عبر Google و Facebook

### 1️⃣ إنشاء مشروع Firebase

1. **افتح Firebase Console:**
   - https://console.firebase.google.com/

2. **أنشئ مشروع جديد:**
   - اضغط "Add project"
   - اسم المشروع: `gaming-store` (أو أي اسم تريده)
   - اختر موقع: اختر الأقرب لك
   - اضغط "Create project"

---

### 2️⃣ تفعيل المصادقة (Authentication)

1. **من القائمة الجانبية:**
   - Build → Authentication → Get Started

2. **تفعيل Google:**
   - Sign-in method → Google → Enable
   - أدخل Support email (بريدك)
   - Save

3. **تفعيل Facebook:**
   - Sign-in method → Facebook → Enable
   - **ستحتاج App ID & App Secret من Facebook:**

#### إنشاء Facebook App:
1. افتح: https://developers.facebook.com/apps/
2. Create App → Consumer → Continue
3. App name: `Gaming Store` → Create App
4. Settings → Basic:
   - انسخ **App ID**
   - انسخ **App Secret** (اضغط Show)
5. ارجع لـ Firebase:
   - الصق App ID & App Secret
   - انسخ OAuth redirect URI من Firebase
6. ارجع لـ Facebook App:
   - Add Product → Facebook Login → Set up
   - Settings → Valid OAuth Redirect URIs:
     - الصق الرابط من Firebase
   - Save Changes
7. في Firebase اضغط Save

4. **تفعيل Anonymous (اختياري - للزوار):**
   - Sign-in method → Anonymous → Enable → Save

---

### 3️⃣ إضافة تطبيق Web

1. **من Project Overview:**
   - Project settings (⚙️) → Your apps
   - اضغط على أيقونة `</>` (Web)

2. **تسجيل التطبيق:**
   - App nickname: `Gaming Store Web`
   - ✅ Also set up Firebase Hosting (اختياري)
   - Register app

3. **نسخ بيانات الإعداد:**
   سيظهر لك كود مثل:
   ```javascript
   const firebaseConfig = {
     apiKey: "AIzaSyXXXXXXXXXXXXXXXXXX",
     authDomain: "gaming-store-xxxxx.firebaseapp.com",
     projectId: "gaming-store-xxxxx",
     storageBucket: "gaming-store-xxxxx.appspot.com",
     messagingSenderId: "123456789012",
     appId: "1:123456789012:web:xxxxxxxxxxxxx"
   };
   ```

4. **استبدل في `login.html`:**
   - ابحث عن `const firebaseConfig` في السطر 216
   - استبدل القيم بالقيم الخاصة بك

---

### 4️⃣ إعدادات الأمان (Security)

1. **Authorized domains:**
   - Authentication → Settings → Authorized domains
   - أضف النطاق الخاص بك (مثل: `dmsshop.netlify.app`)
   - `localhost` مضاف تلقائياً للتطوير

---

### 5️⃣ الاختبار

1. **اختبار محلي:**
   - افتح `login.html` في المتصفح
   - جرب تسجيل الدخول بـ Google
   - جرب تسجيل الدخول بـ Facebook

2. **التحقق من النجاح:**
   - Firebase Console → Authentication → Users
   - يجب أن ترى المستخدمين المسجلين

---

## 🔐 ملاحظات أمان مهمة

### ⚠️ لا تشارك المفاتيح السرية:
- **App Secret** من Facebook
- **Service Account Keys** من Firebase

### ✅ استخدم Environment Variables في الإنتاج:
في حالة رفع الكود على GitHub، استخدم Netlify Environment Variables:
1. Netlify Dashboard → Site settings → Environment variables
2. أضف:
   - `FIREBASE_API_KEY`
   - `FIREBASE_AUTH_DOMAIN`
   - إلخ...

---

## 🚀 النشر على Netlify

بعد إعداد Firebase:

1. **ارفع المشروع على GitHub:**
   ```bash
   git init
   git add .
   git commit -m "Add Firebase authentication"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/gaming-store.git
   git push -u origin main
   ```

2. **ربط مع Netlify:**
   - New site from Git
   - اختر repository
   - Deploy site

3. **إضافة Domain إلى Firebase:**
   - انسخ رابط Netlify (مثل: `dmsshop.netlify.app`)
   - Firebase Console → Authentication → Settings → Authorized domains
   - Add domain

---

## 📝 الوضع التجريبي (بدون Firebase)

حالياً، الموقع يعمل في **وضع تجريبي** بدون Firebase:
- يحفظ بيانات المستخدم في `localStorage`
- لا توجد مصادقة حقيقية
- مناسب للتجربة فقط

**لتفعيل المصادقة الكاملة:**
- اتبع الخطوات أعلاه
- استبدل `firebaseConfig` في `login.html`
- الكود سيعمل تلقائياً مع Firebase

---

## ❓ الدعم

إذا واجهت مشاكل:
1. تحقق من Console في المتصفح (F12)
2. تأكد من أن جميع القيم في `firebaseConfig` صحيحة
3. تأكد من تفعيل Google/Facebook في Firebase
4. تحقق من Authorized domains

---

## 📚 موارد إضافية

- [Firebase Authentication Docs](https://firebase.google.com/docs/auth)
- [Facebook Login Setup](https://firebase.google.com/docs/auth/web/facebook-login)
- [Google Sign-In Setup](https://firebase.google.com/docs/auth/web/google-signin)
