
<h1 align="center" dir="rtl">جلسه ۰۷ — I2C و راه‌اندازی OLED</h1>

<div dir="rtl" align="right">

## 🎯 هدف جلسه

در این جلسه با پروتکل ارتباطی **I2C** آشنا می‌شویم و یک نمایشگر **OLED** را به Arduino UNO متصل و راه‌اندازی می‌کنیم.

در این جلسه یاد می‌گیریم:

1. **I2C چیست؟**
2. **پایه‌های `SDA` و `SCL` چه کاری انجام می‌دهند؟**
3. **آدرس I2C چیست و چه کاربردی دارد؟**
4. **چگونه آدرس OLED را پیدا کنیم؟**
5. **چگونه OLED را به Arduino UNO متصل کنیم؟**
6. **چگونه اولین متن را روی OLED نمایش دهیم؟**

در پایان این جلسه می‌توانیم یک OLED را از طریق **I2C** به Arduino متصل کرده و اطلاعات ساده را روی آن نمایش دهیم.

</div>

---

<h2 dir="rtl" align="right">🔗 I2C چیست؟</h2>

<div dir="rtl" align="right">

**I2C** یک پروتکل ارتباطی برای ارتباط بین **Arduino** و قطعات مختلف است.

در **I2C** معمولاً از دو خط اصلی استفاده می‌شود:

</div>

```text
SDA → Data
SCL → Clock
```

<div dir="rtl" align="right">

بنابراین برخلاف بعضی روش‌های ارتباطی، برای انتقال اطلاعات فقط به دو خط ارتباطی اصلی نیاز داریم.

در Arduino UNO:

</div>

```text
A4 → SDA
A5 → SCL
```

---

<h2 dir="rtl" align="right">📡 SDA و SCL</h2>

<div dir="rtl" align="right">

### SDA
خط انتقال داده است.

### SCL
خط کلاک است و زمان‌بندی ارتباط را مشخص می‌کند.

اتصال کلی:

</div>

```text
Arduino UNO          I2C Device
A4 / SDA  ─────────── SDA
A5 / SCL  ─────────── SCL
GND       ─────────── GND
VCC       ─────────── VCC
```

<p align="center">
  <img src="./images/01-i2c-arduino.png" alt="Arduino UNO I2C SDA SCL" width="800">
</p>

---

<h2 dir="rtl" align="right">🏷️ آدرس I2C</h2>

<div dir="rtl" align="right">

هر دستگاه I2C دارای یک **Address** است تا Arduino بتواند آن را شناسایی کند.

برای مثال بسیاری از OLEDهای رایج دارای یکی از این آدرس‌ها هستند:

</div>

```text
0x3C
0x3D
```

<div dir="rtl" align="right">

اگر آدرس نمایشگر را ندانیم، می‌توانیم با یک برنامه ساده آن را پیدا کنیم.

</div>

---

<h2 dir="rtl" align="right">🔎 پیدا کردن آدرس با I2C Scanner</h2>

```cpp
#include <Wire.h>

void setup() {
  Wire.begin();
  Serial.begin(9600);
  Serial.println("I2C Scanner");
}

void loop() {
  byte error;
  int devices = 0;

  for (byte address = 1; address < 127; address++) {
    Wire.beginTransmission(address);
    error = Wire.endTransmission();

    if (error == 0) {
      Serial.print("I2C device found at 0x");
      if (address < 16)
        Serial.print("0");
      Serial.println(address, HEX);
      devices++;
    }
  }

  if (devices == 0)
    Serial.println("No I2C devices found.");

  delay(3000);
}
```

<div dir="rtl" align="right">

بعد از Upload، **Serial Monitor** را روی `9600` قرار دهید.

اگر OLED به درستی متصل باشد، مثلاً ممکن است ببینیم:

</div>

```text
I2C device found at 0x3C
```

<p align="center">
  <img src="./images/02-i2c-scanner.png" alt="I2C Scanner Serial Monitor" width="800">
</p>

---

<h2 dir="rtl" align="right">🖥️ OLED چیست؟</h2>

<div dir="rtl" align="right">

**OLED** یک نمایشگر کوچک است که می‌توانیم متن، عدد و شکل‌های ساده را روی آن نمایش دهیم.

برای بسیاری از OLEDهای رایج، ارتباط با **Arduino** از طریق **I2C** انجام می‌شود.

اتصال OLED به **Arduino UNO**:

</div>

```text
OLED          Arduino UNO
VCC   ───────  5V
GND   ───────  GND
SDA   ───────  A4
SCL   ───────  A5
```

<p align="center">
  <img src="./images/03-oled-arduino-i2c.png" alt="OLED connected to Arduino UNO using I2C" width="800">
</p>

---

<h2 dir="rtl" align="right">📚 نصب کتابخانه OLED</h2>

<div dir="rtl" align="right">

برای OLEDهای رایج **SSD1306** می‌توانیم از کتابخانه‌های زیر استفاده کنیم:

* `Adafruit SSD1306`
* `Adafruit GFX`

در Arduino IDE:

</div>

```text
Library Manager
      ↓
Adafruit SSD1306
      ↓
Install
Adafruit GFX
      ↓
Install
```

---

<h2 dir="rtl" align="right">🚀 اولین برنامه OLED</h2>

<div dir="rtl" align="right">

بعد از نصب کتابخانه‌ها، می‌توانیم OLED را راه‌اندازی کنیم.

در این مثال فرض می‌کنیم آدرس OLED برابر `0x3C` و اندازه آن `128×64` است.

</div>

```cpp
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define SCREEN_WIDTH 128
#define SCREEN_HEIGHT 64

Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, -1);

void setup() {
  if (!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) {
    while (true);
  }

  display.clearDisplay();
  display.setTextSize(2);
  display.setTextColor(SSD1306_WHITE);
  display.setCursor(0, 20);
  display.println("Hello!");
  display.display();
}

void loop() {
}
```

<div dir="rtl" align="right">

### نکته مهم

دستور:

</div>

```cpp
display.clearDisplay();
```

<div dir="rtl" align="right">

صفحه را پاک می‌کند.

دستور:

</div>

```cpp
display.display();
```

<div dir="rtl" align="right">

محتویات آماده‌شده را روی OLED نمایش می‌دهد.

</div>

---

<h2 dir="rtl" align="right">🧪 پروژه عملی</h2>

<div dir="rtl" align="right">

برنامه را تغییر دهید تا روی OLED متن زیر نمایش داده شود:

</div>

```text
Arduino
I2C
OLED
```

<div dir="rtl" align="right">

سپس اندازه متن و محل نمایش آن را تغییر دهید.

</div>

---

<h2 dir="rtl" align="right">📝 سوالات</h2>

<div dir="rtl" align="right">

1. **I2C** چیست؟
2. دو خط اصلی **I2C** چه نام دارند؟
3. پایه‌های **SDA** و **SCL** در **Arduino UNO** کدام‌اند؟
4. آدرس **I2C** چه کاربردی دارد؟
5. چگونه آدرس یک دستگاه **I2C** را پیدا می‌کنیم؟
6. **OLED** چگونه از طریق **I2C** به **Arduino** متصل می‌شود؟

</div>

---

<h2 dir="rtl" align="right">📌 جمع‌بندی</h2>

<div dir="rtl" align="right">

در این جلسه:

- با مفهوم **I2C** آشنا شدیم.
- **SDA** و **SCL** را شناختیم.
- پایه‌های **I2C** در **Arduino UNO** را پیدا کردیم.
- با مفهوم **I2C Address** آشنا شدیم.
- با **I2C Scanner** آدرس دستگاه را پیدا کردیم.
- یک **OLED** را به **Arduino** متصل کردیم.
- کتابخانه **OLED** را نصب کردیم.
- اولین متن را روی **OLED** نمایش دادیم.

در جلسه بعد سراغ پروتکل ارتباطی **SPI** می‌رویم.

</div>

---

<div dir="rtl" align="right">

## 🔜 جلسه بعد

در جلسه هشتم با پروتکل ارتباطی **SPI** آشنا می‌شویم و یاد می‌گیریم چگونه از این پروتکل برای ارتباط **Arduino** با قطعات مختلف استفاده کنیم.

<p dir="rtl">
⬅️ <a href="../08-SPI/">جلسه ۰۸ — پروتکل SPI</a>
</p>

</div>

<p align="center">
  <strong>Arduino From Zero to Projects</strong><br>
  <strong>Mohammad Esteghamat</strong>
</p>
