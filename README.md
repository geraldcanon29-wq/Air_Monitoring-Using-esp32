ESP32 Air Quality Monitor

An ESP32 air monitor that shows CO2, temperature, humidity and heat index on a 3.5" touchscreen and on a phone web page. Each reading is color coded green, yellow or red. Made as a school project at Laguna State Polytechnic University (LSPU), Siniloan.

Features
Live CO2, temperature, humidity and heat index (PAGASA style levels)
Green, yellow and red status on every card, plus an overall status
Tap a card to see a 5 hour graph (1 point per minute)
History is saved to flash, so it survives a power loss
Open Wi-Fi network (AirMonitor, no password) with a captive portal. Phones are redirected to the page when they connect
Phone page with live data, graphs and a printable PDF report
Hidden faculty settings (tap the title 7 times, then enter a code) to change the limits
Touch calibration saved in memory
Slide-out menu with a how to use guide and About the creators
Hardware
Part	Notes
ESP32 DOIT DevKit V1	Main board
3.5" SPI TFT with XPT2046 touch	Display and touch
SCD40 (generic module)	CO2, temperature, humidity
Pins
Device	Signal	GPIO
TFT	MOSI / SCK / CS / DC / RST / MISO	23 / 18 / 15 / 2 / 4 / 19
Touch (second SPI bus)	CLK / DO / DIN / CS	14 / 32 / 33 / 27
SCD40 (I2C)	SDA / SCL	25 / 26

The TFT backlight and VCC go to 3V3. IRQ on the touch controller is not connected.

Libraries
TFT_eSPI (Bodmer)
XPT2046_Touchscreen (Paul Stoffregen)
SparkFun SCD4x Arduino Library
ESP32 Arduino core 3.3.12 (WiFi, WebServer, DNSServer, LittleFS, Preferences, Wire, SPI)
Setup
Install the libraries above in the Arduino IDE.
Set up TFT_eSPI. It reads its pins from User_Setup.h in the library folder, not from the sketch. Use the pins in the table above.
Select ESP32 Dev Module (or DOIT ESP32 DEVKIT V1) as the board.
Open ESP32_Air_monitoring.ino, set your own faculty code, and upload. If the upload fails, hold the BOOT button while it connects and unplug wires from the boot pins.
On the first start, tap the three crosses to calibrate the touch.
Usage
Connect a phone to the AirMonitor Wi-Fi. The page should open by itself. If not, go to http://10.10.10.1.
Tap a card on the screen or the page to see its 5 hour graph.
Use Open report on the page, then Print / Save as PDF.
Default limits
Reading	Green	Yellow	Red
CO2	below 1000 ppm	1000 to 1499 ppm	1500 ppm and above
Humidity	30 to 65 %	near a limit	below 25 % or above 70 %
Heat index	below 33 C	33 to 41 C	42 C and above

The heat index levels follow PAGASA. The CO2 and humidity limits are our own defaults, not official standards.

Known limitations
The page uses http, so the faculty code is not encrypted. Do not reuse a password here.
No real time clock. Graphs show time ago, not clock time.
The SCD40 module is generic, so its accuracy may be worse than the data sheet.

Creators

Jeffrey B. Moises and Gerald C. Canon
