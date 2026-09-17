<div dir="rtl" style="text-align: right; font-family: Tahoma, Arial, sans-serif; line-height: 1.8;">

# جلسه ۰۷ — I2C و راه‌اندازی OLED

## 🎯 هدف جلسه

در این جلسه با پروتکل ارتباطی **I2C** آشنا می‌شویم و یک نمایشگر **OLED** را به Arduino UNO متصل و راه‌اندازی می‌کنیم.

در این جلسه یاد می‌گیریم:

1. **I2C چیست و چگونه کار می‌کند؟**
2. **پایه‌های `SDA` و `SCL` چه کاری انجام می‌دهند؟**
3. **آدرس I2C چیست و چه کاربردی دارد؟**
4. **چگونه آدرس OLED را پیدا کنیم؟**
5. **چگونه OLED را به Arduino UNO متصل کنیم؟**
6. **چگونه اولین متن را روی OLED نمایش دهیم؟**

در پایان این جلسه می‌توانیم یک OLED را از طریق **I2C** به Arduino متصل کرده و اطلاعات ساده را روی آن نمایش دهیم.

</div>
---

## 🔗 I2C چیست و چگونه کار می‌کند؟

**I2C** (مخفف **Inter-Integrated Circuit**) یک پروتکل ارتباطی سریال است که برای ارتباط بین میکروکنترلر (مثل Arduino) و قطعات جانبی (سنسورها، نمایشگرها، حافظه‌ها و ...) استفاده می‌شود.

### ویژگی‌های مهم I2C:

- فقط به **دو سیم** نیاز دارد (به‌جز تغذیه و زمین).
- می‌تواند همزمان با **چندین دستگاه** ارتباط برقرار کند (Multi-Master / Multi-Slave).
- سرعت نسبتاً خوبی دارد (معمولاً ۱۰۰ کیلوهرتز یا ۴۰۰ کیلوهرتز).
- هر دستگاه یک **آدرس یکتا** دارد تا Arduino بداند با کدام قطعه صحبت می‌کند.

### نحوه کار I2C به زبان ساده:

در I2C دو خط اصلی وجود دارد:

| خط   | نام کامل              | وظیفه                          |
|------|-----------------------|--------------------------------|
| SDA  | Serial Data           | انتقال داده‌ها (دوطرفه)       |
| SCL  | Serial Clock          | سیگنال ساعت (زمان‌بندی)       |

**مراحل کلی ارتباط:**

1. Arduino (Master) خط SCL را کنترل می‌کند و ساعت را تولید می‌کند.
2. Arduino روی خط SDA آدرس دستگاه مورد نظر را می‌فرستد.
3. دستگاهی که آن آدرس را دارد پاسخ می‌دهد (ACK).
4. سپس داده‌ها بین Master و Slave رد و بدل می‌شوند.
5. در پایان ارتباط، Master سیگنال Stop می‌فرستد.

چون داده‌ها و ساعت روی دو خط جدا هستند، زمان‌بندی دقیق است و خطا کمتر رخ می‌دهد.

در **Arduino UNO** پایه‌های I2C از قبل مشخص هستند:

```text
A4 → SDA
A5 → SCL
```
📡 SDA و SCL
SDA (Serial Data)
خط انتقال داده است. هم Master و هم Slave می‌توانند از این خط داده بفرستند یا دریافت کنند.
SCL (Serial Clock)
خط کلاک است. Arduino این خط را کنترل می‌کند تا زمان ارسال و دریافت داده مشخص باشد.
اتصال کلی:
textArduino UNO          I2C Device
───────────────────────────────
A4 / SDA  ─────────── SDA
A5 / SCL  ─────────── SCL
GND       ─────────── GND
VCC       ─────────── VCC (معمولاً 3.3V یا 5V)


🏷️ آدرس I2C
هر دستگاه I2C دارای یک آدرس یکتا (Address) است تا Arduino بتواند آن را از بین چند دستگاه تشخیص دهد.
آدرس‌ها معمولاً به صورت هگزادسیمال نوشته می‌شوند.

بسیاری از OLEDهای رایج یکی از این دو آدرس را دارند:
text0x3C
0x3D
اگر آدرس نمایشگر را ندانیم، می‌توانیم با یک برنامه ساده به نام I2C Scanner آن را پیدا کنیم.

🔎 پیدا کردن آدرس با I2C Scanner
کد زیر را روی Arduino آپلود کنید:
```cpp
include <Wire.h>

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
      if (address < 16) Serial.print("0");
      Serial.println(address, HEX);
      devices++;
    }
  }

  if (devices == 0) {
    Serial.println("No I2C devices found.");
  }

  delay(3000);
}
```
بعد از آپلود:

Serial Monitor را باز کنید.
Baud Rate را روی 9600 قرار دهید.
اگر OLED درست متصل باشد، چیزی شبیه این می‌بینید:

textI2C device found at 0x3C


🖥️ OLED چیست؟
OLED (Organic Light-Emitting Diode) یک نمایشگر کوچک و کم‌مصرف است که می‌توانیم روی آن متن، عدد و شکل‌های ساده نمایش دهیم.
بیشتر OLEDهای رایج (مثل SSD1306) از طریق I2C با Arduino ارتباط برقرار می‌کنند.
اتصال OLED به Arduino UNO:
textOLED          Arduino UNO
─────────────────────────
VCC   ───────  5V (یا 3.3V)
GND   ───────  GND
SDA   ───────  A4
SCL   ───────  A5


📚 نصب کتابخانه OLED
برای OLEDهای رایج SSD1306 این دو کتابخانه را نصب کنید:

Adafruit SSD1306
Adafruit GFX

مراحل نصب در Arduino IDE:
textSketch → Include Library → Manage Libraries
      ↓
جستجو: Adafruit SSD1306
      ↓
Install
      ↓
جستجو: Adafruit GFX
      ↓
Install

🚀 اولین برنامه OLED
در این مثال فرض می‌کنیم:

آدرس OLED = 0x3C
اندازه صفحه = 128×64
```cpp
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define SCREEN_WIDTH 128
#define SCREEN_HEIGHT 64

Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, -1);

void setup() {
  if (!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) {
    // اگر OLED پیدا نشد، برنامه متوقف می‌شود
    while (true);
  }

  display.clearDisplay();           // پاک کردن صفحه
  display.setTextSize(2);           // اندازه متن
  display.setTextColor(SSD1306_WHITE);
  display.setCursor(0, 20);         // موقعیت شروع نوشتن
  display.println("Hello!");
  display.display();                // نمایش محتوا روی صفحه
}

void loop() {
  // خالی می‌ماند
}
```
نکته‌های مهم:

display.clearDisplay(); → صفحه را پاک می‌کند.
display.display(); → محتوایی که آماده کرده‌ایم را روی OLED نشان می‌دهد.
بدون display.display() هیچ چیزی روی صفحه ظاهر نمی‌شود.


🧪 پروژه عملی
برنامه را تغییر دهید تا روی OLED این سه خط نمایش داده شود:
textArduino
I2C
OLED
سپس:

اندازه متن را تغییر دهید.
موقعیت (setCursor) را جابه‌جا کنید.
سعی کنید متن را وسط صفحه قرار دهید.


📝 سوالات

I2C چیست و چه مزیتی نسبت به روش‌های دیگر دارد؟
دو خط اصلی I2C چه نام دارند و هر کدام چه کاری انجام می‌دهند؟
پایه‌های SDA و SCL در Arduino UNO کدام‌اند؟
آدرس I2C چه کاربردی دارد؟
چگونه آدرس یک دستگاه I2C را پیدا می‌کنیم؟
OLED چگونه از طریق I2C به Arduino متصل می‌شود؟


📌 جمع‌بندی
در این جلسه:

با مفهوم I2C و نحوه کار آن آشنا شدیم.
خطوط SDA و SCL را شناختیم.
پایه‌های I2C در Arduino UNO را یاد گرفتیم.
با مفهوم I2C Address آشنا شدیم.
با I2C Scanner آدرس دستگاه را پیدا کردیم.
یک OLED را به Arduino متصل کردیم.
کتابخانه‌های لازم را نصب کردیم.
اولین متن را روی OLED نمایش دادیم.

در جلسه بعد سراغ پروتکل ارتباطی SPI می‌رویم.

🔜 جلسه بعد
در جلسه هشتم با پروتکل ارتباطی SPI آشنا می‌شویم و یاد می‌گیریم چگونه از این پروتکل برای ارتباط Arduino با قطعات مختلف استفاده کنیم.
⬅️ جلسه ۰۸ — پروتکل SPI

Arduino From Zero to Projects

Mohammad Esteghamat
