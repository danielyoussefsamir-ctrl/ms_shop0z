# 📤 دليل رفع المشروع على GitHub

## 🚀 الطريقة الأولى: GitHub Desktop (موصى بها للمبتدئين)

### الخطوة 1: تحميل GitHub Desktop
1. اذهب إلى: https://desktop.github.com/
2. اضغط **Download for Windows**
3. ثبت البرنامج (Next → Next → Install)
4. افتح GitHub Desktop

### الخطوة 2: تسجيل الدخول
1. من البرنامج، اضغط **Sign in to GitHub.com**
2. سجل دخول بحسابك (أو أنشئ حساب جديد)
3. اضغط **Authorize desktop**

### الخطوة 3: إضافة المشروع
1. في GitHub Desktop، اضغط **File** → **Add local repository**
2. أو اضغط **Ctrl + O**
3. اختر المجلد: `C:\Users\Daniel\Desktop\متجر\SDS`
4. إذا ظهر "This directory does not appear to be a Git repository":
   - اضغط **create a repository**
   - اسم Repository: `MS-Gaming-Store`
   - Description: `متجر ألعاب احترافي مع تسجيل دخول Google`
   - ✅ اترك **Git ignore:** None
   - ✅ اترك **License:** None
   - اضغط **Create Repository**

### الخطوة 4: عمل Commit
1. في GitHub Desktop ستجد قائمة بجميع الملفات
2. في الأسفل، اكتب رسالة Commit:
   - **Summary:** `Initial commit: MS Gaming Store`
   - **Description:** `متجر ألعاب مع Firebase Authentication`
3. اضغط **Commit to main**

### الخطوة 5: النشر على GitHub
1. اضغط **Publish repository** (في الأعلى)
2. اختر:
   - **Name:** `MS-Gaming-Store`
   - **Description:** `متجر ألعاب احترافي`
   - ⬜ **Keep this code private** (اتركها فارغة = public)
   - أو ✅ ضعها = private
3. اضغط **Publish Repository**
4. انتظر التحميل (قد يستغرق دقيقة)

### ✅ تم النشر!
افتح: `https://github.com/YOUR_USERNAME/MS-Gaming-Store`

---

## 💻 الطريقة الثانية: Git Command Line

### الخطوة 1: تثبيت Git
1. اذهب إلى: https://git-scm.com/download/win
2. حمل **64-bit Git for Windows Setup**
3. ثبته بالإعدادات الافتراضية
4. أعد تشغيل VS Code أو PowerShell

### الخطوة 2: تهيئة Git (مرة واحدة فقط)
افتح PowerShell واكتب:
```powershell
git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"
```

### الخطوة 3: إنشاء Repository محلي
```powershell
cd "C:\Users\Daniel\Desktop\متجر\SDS"
git init
```

### الخطوة 4: إضافة الملفات
```powershell
git add .
git commit -m "Initial commit: MS Gaming Store"
```

### الخطوة 5: إنشاء Repository على GitHub
1. اذهب إلى: https://github.com/new
2. **Repository name:** `MS-Gaming-Store`
3. **Description:** `متجر ألعاب احترافي`
4. اختر **Public** أو **Private**
5. ⬜ **لا تضع** ✅ في Initialize
6. اضغط **Create repository**

### الخطوة 6: ربط ورفع المشروع
انسخ الأوامر من GitHub (ستظهر بعد الإنشاء):
```powershell
git remote add origin https://github.com/YOUR_USERNAME/MS-Gaming-Store.git
git branch -M main
git push -u origin main
```

### ✅ تم الرفع!

---

## 🔄 كيفية تحديث المشروع لاحقاً

### باستخدام GitHub Desktop:
1. افتح GitHub Desktop
2. عدل الملفات في VS Code
3. ارجع لـ GitHub Desktop → سترى التغييرات
4. اكتب Commit message
5. اضغط **Commit to main**
6. اضغط **Push origin** (في الأعلى)

### باستخدام Git Command Line:
```powershell
cd "C:\Users\Daniel\Desktop\متجر\SDS"
git add .
git commit -m "وصف التعديلات"
git push
```

---

## 🌐 ربط GitHub مع Netlify (اختياري)

بعد رفع المشروع على GitHub:

1. اذهب إلى: https://app.netlify.com/
2. اضغط **Add new site** → **Import an existing project**
3. اختر **GitHub**
4. اختر Repository: `MS-Gaming-Store`
5. **Branch:** `main`
6. **Build command:** (اتركه فارغ)
7. **Publish directory:** `/` أو `.`
8. اضغط **Deploy site**

### مميزات الربط:
- ✅ أي تعديل على GitHub = تحديث تلقائي للموقع
- ✅ Continuous Deployment
- ✅ رابط مباشر دائم

---

## 📁 ملفات سيتم رفعها

سيتم رفع:
- ✅ index.html
- ✅ store.html
- ✅ login.html
- ✅ admin.html
- ✅ create_admin.html
- ✅ view_accounts.html
- ✅ README.md
- ✅ FIREBASE_SETUP.md
- ✅ GOOGLE_LOGIN_GUIDE.md
- ✅ GITHUB_UPLOAD_GUIDE.md

---

## 🔒 ملاحظات أمان مهمة

### ⚠️ قبل الرفع على GitHub Public:

إذا كنت ستجعل المشروع **Public** (عام):

1. **تأكد من عدم وجود مفاتيح حقيقية في login.html**
   - حالياً الملف يحتوي على `YOUR_API_KEY` فقط = آمن ✅
   - إذا أضفت مفاتيح Firebase الحقيقية، اجعل Repository **Private**

2. **أو استخدم Environment Variables:**
   - ضع المفاتيح في Netlify Environment Variables
   - لا ترفعها في الكود

### للمشاريع الخاصة:
- اجعل Repository **Private** ✅
- أو استخدم `.gitignore` لاستبعاد ملفات الإعدادات

---

## ✅ خلاصة سريعة

| الطريقة | المميزات | العيوب |
|---------|----------|--------|
| **GitHub Desktop** | سهل، واجهة مرئية، للمبتدئين | برنامج إضافي |
| **Git Command Line** | قوي، احترافي، مرن | يحتاج تعلم أوامر |
| **Netlify Drop** | فوري، بدون Git | لا توجد إدارة إصدارات |

---

## 🆘 استكشاف الأخطاء

### "repository not found"
- تأكد من URL صحيح
- تأكد من تسجيل الدخول

### "permission denied"
- استخدم GitHub Desktop
- أو أضف SSH key لحسابك

### "failed to push"
- تأكد من الاتصال بالإنترنت
- جرب `git pull` أولاً

---

## 📞 الدعم

- GitHub Desktop Guide: https://docs.github.com/en/desktop
- Git Documentation: https://git-scm.com/doc
- Netlify Docs: https://docs.netlify.com/

---

**التوصية:** استخدم **GitHub Desktop** للسهولة والسرعة! 🚀
