# نظام تسجيل الحضور للطلبة (Flask + SQLite)

## المتطلبات
- Python 3.10+
- تثبيت الحزم:

```bash
pip install -r requirements.txt
```

## التشغيل (بيئة تطوير)

```bash
python run.py
```

سيفتح الموقع على `http://127.0.0.1:5000`.

الصفحات:
- الرئيسية: إحصائيات اليوم وعدد الطلبة
- تسجيل الطلبة: إضافة طالب (الاسم، الرقم الامتحاني، المرحلة، الشعبة)
- البحث: حسب الاسم أو الرقم الامتحاني + سجل الحضور للطالب
- تسجيل الحضور: اختيار المرحلة/الشعبة والتاريخ وتحديد حاضر/غائب
- التصدير: Excel و PDF مع فلاتر الفترة والمرحلة والشعبة

يتم حفظ قاعدة البيانات في ملف `attendance.db` داخل نفس المجلد.

## النشر على الإنترنت

### Railway (موصى به)
1. سجل على [railway.app](https://railway.app)
2. أنشئ مشروع جديد
3. اضغط "Deploy from GitHub repo" وربط المستودع
4. اضبط BUILD COMMAND: `pip install -r requirements.txt`
5. اضبط START COMMAND: `gunicorn run:app`
6. رايلوي ينشر تلقائياً مع HTTPS وقرص دائم للـ SQLite

### Render
1. سجل على [render.com](https://render.com)
2. أنشئ Web Service جديد
3. اربط مستودع GitHub
4. Build: `pip install -r requirements.txt`
5. Start: `gunicorn run:app --bind 0.0.0.0:$PORT`
6. Render يعطيك URL تلقائياً

### إرشادات عامة
- تأكد وجود `Procfile` في الجذر
- أضف `gunicorn` إلى requirements.txt
- يمكنك رفع attendance.db إلى VPS بنفسك إذا احتجت استيراد بيانات سابقة
