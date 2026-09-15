# 📘 جلسه 02 — <span dir="ltr">Arduino IDE</span>

<div dir="rtl" align="right">

## 🎯 هدف جلسه

در جلسه قبل با <span dir="ltr">Arduino</span> و اجزای اصلی آن آشنا شدیم.

در این جلسه یاد می‌گیریم:

<ul dir="rtl">
<li><span dir="ltr">Arduino IDE</span> چیست؟</li>
<li><span dir="ltr">Arduino IDE</span> را از کجا دانلود کنیم؟</li>
<li>چگونه <span dir="ltr">Arduino IDE</span> را نصب کنیم؟</li>
<li>محیط <span dir="ltr">Arduino IDE</span> از چه بخش‌هایی تشکیل شده است؟</li>
<li>چگونه برد <span dir="ltr">Arduino</span> را به کامپیوتر متصل کنیم؟</li>
<li>چگونه <span dir="ltr">Board</span> و <span dir="ltr">Port</span> را انتخاب کنیم؟</li>
<li>اولین برنامه <span dir="ltr">Arduino</span> را بنویسیم.</li>
<li>برنامه را روی <span dir="ltr">Arduino</span> آپلود کنیم.</li>
<li>خطاهای رایج هنگام آپلود را بشناسیم.</li>
</ul>

در پایان این جلسه باید بتوانیم **یک برنامه ساده را روی <span dir="ltr">Arduino</span> اجرا کنیم.**

</div>

---

## 🧰 تجهیزات موردنیاز

<div dir="rtl" align="right">

برای این جلسه به موارد زیر نیاز داریم:

<ul dir="rtl">
<li>یک برد <span dir="ltr">Arduino</span></li>
<li>کابل <span dir="ltr">USB</span> مناسب برد</li>
<li>کامپیوتر یا لپ‌تاپ</li>
<li><span dir="ltr">Arduino IDE</span></li>
</ul>

</div>

---

# 1. <span dir="ltr">Arduino IDE</span> چیست؟

<div dir="rtl" align="right">

<strong><span dir="ltr">Arduino IDE</span></strong> مخفف:

<p dir="ltr">Integrated Development Environment</p>

به معنی <strong>محیط توسعه یکپارچه</strong> است.

<span dir="ltr">Arduino IDE</span> نرم‌افزاری است که از آن برای موارد زیر استفاده می‌کنیم:

<ul dir="rtl">
<li>نوشتن برنامه</li>
<li>ویرایش کد</li>
<li>بررسی خطاهای برنامه</li>
<li>انتخاب برد</li>
<li>انتخاب پورت ارتباطی</li>
<li>کامپایل برنامه</li>
<li>آپلود برنامه روی <span dir="ltr">Arduino</span></li>
</ul>

به زبان ساده:

<blockquote>
<span dir="ltr">Arduino IDE</span> محیطی است که در آن برنامه <span dir="ltr">Arduino</span> را می‌نویسیم و آن را روی برد اجرا می‌کنیم.
</blockquote>

</div>

---

# 2. دانلود <span dir="ltr">Arduino IDE</span>

<div dir="rtl" align="right">

برای نصب <span dir="ltr">Arduino IDE</span> بهتر است همیشه از **وب‌سایت رسمی <span dir="ltr">Arduino</span>** استفاده کنید.

از صفحه دانلود رسمی <span dir="ltr">Arduino IDE</span>، نسخه مناسب سیستم‌عامل خود را دریافت کنید.

</div>

<div dir="rtl" align="right">

🔗 <a href="https://www.arduino.cc/en/software/">Arduino IDE — Download</a>

</div>

---

# 3. نصب <span dir="ltr">Arduino IDE</span>

<div dir="rtl" align="right">

بعد از دانلود فایل نصب، آن را اجرا کنید.

مراحل نصب معمولاً ساده است:

<ol dir="rtl">
<li>اجرای فایل نصب</li>
<li>قبول کردن <span dir="ltr">License</span></li>
<li>انتخاب محل نصب</li>
<li>نصب برنامه</li>
<li>اجرای <span dir="ltr">Arduino IDE</span></li>
</ol>

در طول نصب ممکن است سیستم‌عامل از شما اجازه نصب <span dir="ltr">Driver</span> یا ایجاد تغییرات در سیستم را درخواست کند.

در صورت نمایش چنین پیامی، مراحل نصب را ادامه دهید.

</div>

---

## 📷 تصویر محیط نصب

<p align="center">
<img src="./images/02-install-arduino-ide.png" alt="Arduino IDE Installation" width="700">
</p>

---

# 4. آشنایی با محیط <span dir="ltr">Arduino IDE</span>

<div dir="rtl" align="right">

بعد از اجرای <span dir="ltr">Arduino IDE</span> با محیطی مشابه تصویر زیر روبه‌رو می‌شوید.

</div>

<p align="center">
<img src="./images/03-arduino-ide-interface.png" alt="Arduino IDE Interface" width="800">
</p>

<div dir="rtl" align="right">

بخش‌های مهم محیط <span dir="ltr">Arduino IDE</span> عبارت‌اند از:

</div>

<table dir="rtl" style="margin-left: auto; margin-right: 0;">
<thead>
<tr>
<th>بخش</th>
<th>کاربرد</th>
</tr>
</thead>
<tbody>
<tr>
<td><code dir="ltr">Editor</code></td>
<td>نوشتن و ویرایش کد</td>
</tr>
<tr>
<td><code dir="ltr">Verify</code></td>
<td>بررسی و <span dir="ltr">Compile</span> کردن برنامه</td>
</tr>
<tr>
<td><code dir="ltr">Upload</code></td>
<td>ارسال برنامه به <span dir="ltr">Arduino</span></td>
</tr>
<tr>
<td><code dir="ltr">Serial Monitor</code></td>
<td>مشاهده اطلاعات سریال</td>
</tr>
<tr>
<td><code dir="ltr">Board</code></td>
<td>انتخاب نوع برد</td>
</tr>
<tr>
<td><code dir="ltr">Port</code></td>
<td>انتخاب پورت ارتباطی</td>
</tr>
</tbody>
</table>

<div dir="rtl" align="right">
<br><br>
</div>

---

# 5. اتصال <span dir="ltr">Arduino</span> به کامپیوتر

<div dir="rtl" align="right">

ابتدا <span dir="ltr">Arduino</span> را با استفاده از کابل <span dir="ltr">USB</span> به کامپیوتر متصل کنید.

پس از اتصال، <span dir="ltr">Arduino</span> از طریق <span dir="ltr">USB</span> با کامپیوتر ارتباط برقرار می‌کند.

این ارتباط برای موارد زیر استفاده می‌شود:

<ul dir="rtl">
<li>انتقال برنامه</li>
<li>دریافت اطلاعات</li>
<li><span dir="ltr">Serial Communication</span></li>
<li>تأمین توان در بسیاری از حالت‌ها</li>
</ul>

</div>

---

# 6. انتخاب <span dir="ltr">Board</span>

<div dir="rtl" align="right">

قبل از <span dir="ltr">Upload</span> کردن برنامه باید مشخص کنیم که از چه بردی استفاده می‌کنیم.

برای مثال اگر از **<span dir="ltr">Arduino UNO</span>** استفاده می‌کنید، باید برد مناسب را در <span dir="ltr">Arduino IDE</span> انتخاب کنید.

از قسمت <span dir="ltr">Board</span>، برد موردنظر را انتخاب کنید.

</div>

<p align="center">
<img src="./images/04-select-board-port.png" alt="Select Arduino Board and Port" width="800">
</p>

---

# 7. انتخاب <span dir="ltr">Port</span>

<div dir="rtl" align="right">

بعد از اتصال <span dir="ltr">Arduino</span> به کامپیوتر، باید <span dir="ltr">Port</span> مربوط به برد را انتخاب کنیم.

<span dir="ltr">Port</span> همان مسیر ارتباطی است که کامپیوتر از طریق آن با <span dir="ltr">Arduino</span> ارتباط برقرار می‌کند.

در <span dir="ltr">Arduino IDE</span> معمولاً می‌توانید <span dir="ltr">Port</span> را از منوی مربوط به <strong><span dir="ltr">Board / Port</span></strong> انتخاب کنید.

<blockquote>
نام <span dir="ltr">Port</span> در سیستم‌های مختلف می‌تواند متفاوت باشد.
</blockquote>

</div>

---

# 8. اولین برنامه <span dir="ltr">Arduino</span>

<div dir="rtl" align="right">

حالا می‌خواهیم اولین برنامه خودمان را روی <span dir="ltr">Arduino</span> اجرا کنیم.

در <span dir="ltr">Arduino</span> معمولاً دو تابع اصلی داریم:

</div>

```cpp
void setup() {
}

void loop() {
}
```

<div dir="rtl" align="right">

### <code dir="ltr">setup()</code>

تابع <code dir="ltr">setup()</code> فقط یک بار در هنگام شروع یا <span dir="ltr">Reset</span> شدن <span dir="ltr">Arduino</span> اجرا می‌شود.

معمولاً تنظیمات اولیه را در این بخش قرار می‌دهیم.

### <code dir="ltr">loop()</code>

تابع <code dir="ltr">loop()</code> بعد از اجرای <code dir="ltr">setup()</code> به‌صورت پیوسته و تکرارشونده اجرا می‌شود.

معمولاً دستورات اصلی برنامه را در این بخش قرار می‌دهیم.

</div>

---

# 9. اولین برنامه عملی — چشمک زدن <span dir="ltr">LED</span>

<div dir="rtl" align="right">

حالا یک برنامه ساده می‌نویسیم که <span dir="ltr">LED</span> داخلی <span dir="ltr">Arduino</span> را روشن و خاموش کند.

</div>

```cpp
void setup() {
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop() {
  digitalWrite(LED_BUILTIN, HIGH);
  delay(1000);

  digitalWrite(LED_BUILTIN, LOW);
  delay(1000);
}
```

<div dir="rtl" align="right">

در این برنامه:

<ul dir="rtl">
<li><code dir="ltr">pinMode()</code> نوع استفاده از پایه را مشخص می‌کند.</li>
<li><code dir="ltr">OUTPUT</code> یعنی پایه به‌عنوان خروجی استفاده می‌شود.</li>
<li><code dir="ltr">digitalWrite()</code> مقدار خروجی را تغییر می‌دهد.</li>
<li><code dir="ltr">HIGH</code> خروجی را فعال می‌کند.</li>
<li><code dir="ltr">LOW</code> خروجی را غیرفعال می‌کند.</li>
<li><code dir="ltr">delay(1000)</code> برنامه را به مدت ۱۰۰۰ میلی‌ثانیه متوقف می‌کند.</li>
</ul>

بنابراین <span dir="ltr">LED</span> تقریباً هر یک ثانیه روشن و هر یک ثانیه خاموش می‌شود.

</div>

---

# 10. بررسی برنامه

<div dir="rtl" align="right">

قبل از ارسال برنامه به <span dir="ltr">Arduino</span> بهتر است ابتدا آن را بررسی کنیم.

روی دکمه <span dir="ltr">Verify</span> کلیک کنید.

<span dir="ltr">Arduino IDE</span> کد را بررسی و <span dir="ltr">Compile</span> می‌کند.

اگر خطایی وجود نداشته باشد، برنامه برای <span dir="ltr">Upload</span> آماده است.

</div>

---

# 11. <span dir="ltr">Upload</span> کردن برنامه

<div dir="rtl" align="right">

بعد از انتخاب <span dir="ltr">Board</span> و <span dir="ltr">Port</span>، روی دکمه <span dir="ltr">Upload</span> کلیک کنید.

<span dir="ltr">Arduino IDE</span> مراحل زیر را انجام می‌دهد:

</div>

```text
Source Code
     ↓
   Compile
     ↓
Machine Code
     ↓
     USB
     ↓
   Arduino
     ↓
Program Execution
```

<div dir="rtl" align="right">

بعد از پایان موفقیت‌آمیز <span dir="ltr">Upload</span>، برنامه روی <span dir="ltr">Arduino</span> اجرا می‌شود.

</div>

<p align="center">
<img src="./images/06-upload-success.png" alt="Arduino Upload Success" width="800">
</p>

---

# 12. تفاوت <span dir="ltr">Verify</span> و <span dir="ltr">Upload</span>

<div dir="rtl" align="right">

این دو گزینه را با یکدیگر اشتباه نگیرید.

</div>

<table dir="rtl" style="width: 100%; border-collapse: collapse; margin: 20px 0;">

<thead>

<tr>

<th style="text-align: right; padding: 12px; border-bottom: 1px solid #888;">
گزینه
</th>

<th style="text-align: right; padding: 12px; border-bottom: 1px solid #888;">
کاربرد
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="padding: 12px; border-bottom: 1px solid #555;">
<code dir="ltr">Verify</code>
</td>

<td style="padding: 12px; border-bottom: 1px solid #555;">
بررسی و <span dir="ltr">Compile</span> برنامه
</td>

</tr>

<tr>

<td style="padding: 12px; border-bottom: 1px solid #555;">
<code dir="ltr">Upload</code>
</td>

<td style="padding: 12px; border-bottom: 1px solid #555;">
<span dir="ltr">Compile</span> و ارسال برنامه به <span dir="ltr">Arduino</span>
</td>

</tr>

</tbody>

</table>

<div style="clear: both;"></div>

<div dir="rtl" align="right">
<br><br>

به‌صورت ساده:

<strong><span dir="ltr">← Verify </span> فقط بررسی و <span dir="ltr">Compile</span> برنامه</strong>

<br>

<strong><span dir="ltr">← Upload </span> بررسی، <span dir="ltr">Compile</span> و ارسال برنامه به برد</strong>

</div>

---

# 13. ساختار پایه برنامه <span dir="ltr">Arduino</span>

<div dir="rtl" align="right">

یک برنامه ساده <span dir="ltr">Arduino</span> معمولاً ساختاری شبیه این دارد:

</div>

```cpp
void setup() {
  // Initial configuration
}

void loop() {
  // Main program
}
```

<div dir="rtl" align="right">

می‌توانیم این ساختار را به شکل زیر تصور کنیم:

</div>

```text
Arduino Start
      ↓
   setup()
      ↓
   loop()
      ↓
   loop()
      ↓
   loop()
      ↓
    ...
```

<div dir="rtl" align="right">

<code dir="ltr">setup()</code> یک بار اجرا می‌شود و <code dir="ltr">loop()</code> به‌صورت مداوم تکرار می‌شود.

</div>

---

# 14. خطاهای رایج

<div dir="rtl" align="right">

هنگام کار با <span dir="ltr">Arduino IDE</span> ممکن است با خطاهای مختلفی مواجه شوید.

### 🔴 <span dir="ltr">Board</span> اشتباه

اگر <span dir="ltr">Board</span> صحیح انتخاب نشده باشد، ممکن است برنامه به‌درستی روی برد اجرا نشود.

### 🔴 <span dir="ltr">Port</span> اشتباه

اگر <span dir="ltr">Port</span> صحیح انتخاب نشده باشد، <span dir="ltr">Arduino IDE</span> نمی‌تواند با برد ارتباط برقرار کند.

### 🔴 کابل <span dir="ltr">USB</span> نامناسب

برخی کابل‌های <span dir="ltr">USB</span> فقط برای شارژ هستند و قابلیت انتقال داده ندارند.

### 🔴 <span dir="ltr">Arduino</span> شناسایی نمی‌شود

در این حالت موارد زیر را بررسی کنید:

<ul dir="rtl">
<li>اتصال <span dir="ltr">USB</span></li>
<li>کابل <span dir="ltr">USB</span></li>
<li>انتخاب <span dir="ltr">Port</span></li>
<li><span dir="ltr">Driver</span></li>
<li>اتصال صحیح برد</li>
</ul>

### 🔴 خطای <span dir="ltr">Compile</span>

اگر در کد برنامه خطای <span dir="ltr">Syntax</span> وجود داشته باشد، <span dir="ltr">Arduino IDE</span> نمی‌تواند برنامه را <span dir="ltr">Compile</span> کند.

</div>

---

# 🧪 تمرین‌های جلسه

<div dir="rtl" align="right">

## تمرین 01

برنامه‌ای بنویسید که <span dir="ltr">LED</span> را:

<ul dir="rtl">
<li>۱ ثانیه روشن</li>
<li>۱ ثانیه خاموش</li>
</ul>

کند.

---

## تمرین 02

زمان روشن و خاموش شدن <span dir="ltr">LED</span> را به <code dir="ltr">500ms</code> تغییر دهید.

---

## تمرین 03

برنامه را طوری تغییر دهید که <span dir="ltr">LED</span>:

<ul dir="rtl">
<li>۲ ثانیه روشن</li>
<li>۵۰۰ میلی‌ثانیه خاموش</li>
</ul>

باشد.

---

## تمرین 04

تفاوت <code dir="ltr">setup()</code> و <code dir="ltr">loop()</code> را با زبان خودتان توضیح دهید.

</div>

---

# 📝 سوالات

<div dir="rtl" align="right">

<ol dir="rtl">
<li><span dir="ltr">Arduino IDE</span> چیست؟</li>
<li><span dir="ltr">Verify</span> چه کاری انجام می‌دهد؟</li>
<li><span dir="ltr">Upload</span> چه کاری انجام می‌دهد؟</li>
<li><span dir="ltr">Board</span> چیست؟</li>
<li><span dir="ltr">Port</span> چیست؟</li>
<li>تابع <code dir="ltr">setup()</code> چند بار اجرا می‌شود؟</li>
<li>تابع <code dir="ltr">loop()</code> چند بار اجرا می‌شود؟</li>
<li><code dir="ltr">pinMode()</code> چه کاری انجام می‌دهد؟</li>
<li><code dir="ltr">digitalWrite()</code> چه کاری انجام می‌دهد؟</li>
<li><code dir="ltr">delay(1000)</code> چه معنایی دارد؟</li>
</ol>

</div>

---

# 📌 جمع‌بندی

<div dir="rtl" align="right">

در این جلسه یاد گرفتیم:

<ul dir="rtl">
<li><span dir="ltr">Arduino IDE</span> چیست.</li>
<li>چگونه <span dir="ltr">Arduino IDE</span> را نصب کنیم.</li>
<li>با محیط <span dir="ltr">Arduino IDE</span> آشنا شدیم.</li>
<li><span dir="ltr">Arduino</span> را به کامپیوتر متصل کردیم.</li>
<li><span dir="ltr">Board</span> و <span dir="ltr">Port</span> را انتخاب کردیم.</li>
<li>ساختار پایه برنامه <span dir="ltr">Arduino</span> را یاد گرفتیم.</li>
<li>اولین برنامه خودمان را نوشتیم.</li>
<li>برنامه را <span dir="ltr">Compile</span> و <span dir="ltr">Upload</span> کردیم.</li>
<li>با <code dir="ltr">setup()</code> و <code dir="ltr">loop()</code> آشنا شدیم.</li>
<li><span dir="ltr">LED</span> داخلی <span dir="ltr">Arduino</span> را کنترل کردیم.</li>
<li>خطاهای رایج را بررسی کردیم.</li>
</ul>

در جلسه بعد وارد یکی از مهم‌ترین مباحث <span dir="ltr">Arduino</span> می‌شویم:

## 🔌 <span dir="ltr">Digital Input / Output</span>

یعنی یاد می‌گیریم چگونه با پایه‌های دیجیتال <span dir="ltr">Arduino</span> کار کنیم و قطعاتی مانند **<span dir="ltr">LED</span>** و **<span dir="ltr">Push Button</span>** را کنترل کنیم.

</div>

---

# 🔗 جلسه بعد

<div dir="rtl" align="right">

**➡️ جلسه 03 — <span dir="ltr">Digital Input / Output</span>**

</div>

<br>

<div align="center">

### <span dir="ltr">Arduino From Zero to Projects 🚀</span>

**<span dir="ltr">Learn → Build → Experiment → Create</span>**

</div>
