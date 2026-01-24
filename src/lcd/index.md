# LCD Display

In this section, we will be using Hitachi HD44780 compatible LCD (Liquid Crystal Display) displays. You might have seen them in devices like printers, digital clocks, microwaves, washing machines, air conditioners, and other home appliances. They're also used in equipment like copiers, fax machines, and routers.

You can display ASCII character and up to 8 custom characters.


## Variants
It comes in various variants, such as 16x2 (16 columns, 2 rows) and 20x4 (20 columns, 4 rows), and also based on backlight color (blue, yellow, or green). The one I have displays white characters with a blue backlight. However, you can choose any variant as it won't significantly affect the code.  Most of these variants will have 16 pins.

### I2C variants
Some variants come with an I2C interface adapter, so you can use I2C for communication. The main advantage of I2C variant is that it reduces the number of pin connections. We will be using an LCD display with an I2C interface adapter. 

If you're interested in using Parallel Interface LCDs, refer to the [LCD section](https://pico.implrust.com/lcd-display) in the Pico version of this book. However, keep in mind that the parallel interface requires more GPIO pins(but cheaper).
 
<img style="display: block; margin: auto;width:400px;" alt="lcd1602 I2C" src="./images/lcd1602-i2c.jpg"/>

So, when you are purchasing an LCD module, make sure it has only four pins and includes an I2C interface adapter, as shown in the image.

## Hardware Requirements

We will need an LCD1602 display. A 16x2 module with an I2C adapter is recommended so you can follow along without adjustments, although other sizes behave the same way.

### Level Shifter

<img style="display: block; margin: auto;width:400px;" alt="lcd1602 I2C" src="./images/4 Channel (I2C or SPI) 3.3V-5V Bi-Directional Logic Level Converter.jpg"/>

ESP32 GPIO pins are 3.6 V tolerant, which means they are not safe to use with 5 V signals. Applying a higher voltage, such as 5 V, to these pins can damage the board. Many LCD1602 displays with an I2C adapter are designed to operate at 5 V, which creates a voltage mismatch when connecting them directly to the Pico.

To connect the ESP32 and the LCD safely, we need to handle this voltage difference. This is where a level shifter is used. A bidirectional I2C logic level shifter allows 3.3 V and 5 V devices to communicate safely and protects the ESP32 GPIO pins. These modules are inexpensive and are commonly sold as "4 Channel (I2C) 3.3V-5V Bi-Directional Logic Level Converter".

Alternatively, you can power the LCD with 3.3 V. This avoids the voltage issue, but the display backlight and contrast will be noticeably dimmer.

## Datasheet
- You can access the datasheet for the HD44780 from [Sparkfun](https://www.sparkfun.com/datasheets/LCD/HD44780.pdf) or [MIT site](https://academy.cba.mit.edu/classes/output_devices/44780.pdf)
- [LCD Driver Data Book](https://www.crystalfontz.com/controllers/datasheet-viewer.php?id=433)
- [LCD Module 1602A Datasheet](https://www.openhacks.com/uploadsproductos/eone-1602a1.pdf)
