
## Board config
- TFT (ST7789)
    - TFT_RST=
    - TFT_SCLK=
    - TFT_DC=
    - TFT_CS=
    - TFT_MOSI=
    - TFT_MISO=
    - TFT_BCKL=
- Touch	(CST820)
    - TOUCH_SDA=
    - TOUCH_SCL=
    - I2C_TOUCH_ADDRESS=0x38

## Touch and Draw sample (without LVGL)
Replace the content of main.cpp with the following to test quickly  
For `Ardiuno IDE`, install LovyanGFX library then copy & paste the below code into your .ino file and flash!
``` C++

/*
    Simple Touch Drawing sample for WT32-SC01
*/
#define LGFX_AUTODETECT     // Autodetect board
#define LGFX_USE_V1         // set to use new version of library

#include <LovyanGFX.hpp>    // main library

static LGFX lcd;            // declare display variable

// Variables for touch x,y
static int32_t x,y;

void setup(void)
{
  lcd.init();

  // Setting display to landscape
  if (lcd.width() < lcd.height()) lcd.setRotation(lcd.getRotation() ^ 1);

  lcd.setCursor(0,0);
  lcd.printf("Ready to touch & draw!");
}

void loop()
{
  if (lcd.getTouch(&x, &y)) {
    lcd.fillRect(x-2, y-2, 5, 5, TFT_RED);
    lcd.setCursor(380,0);
    lcd.printf("Touch:(%03d,%03d)", x,y);
  }
}

```

## 3D Printable enclosure (STL)  

