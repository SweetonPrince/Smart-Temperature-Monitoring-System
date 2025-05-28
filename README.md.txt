SMART TEMPERATURE MONITORING SYSTEM USING ARDUINO

OVERVIEW:

This is a basic project for monitoring temperature using Arduino and a DHT11 sensor. The temperature is displayed on a 16x2 LCD and triggers an LED if the temperature exceeds a threshold.

COMPONENTS USED:

•Arduino Uno
•DHT11 Temperature and Humidity Sensor
•16x2 LCD Display
•10K Potentiometer
•Breadboard and Jumper wires
•LED

CIRCUIT DIAGRAM:
 

[DHT11 Sensor]
VCC -> 5V
GND -> GND
DATA -> Pin 2

[16x2 LCD Display]
VSS -> GND
VDD -> 5V
VO  -> Potentiometer center pin
RS  -> Pin 7
RW  -> GND
EN  -> Pin 8
D4  -> Pin 9
D5  -> Pin 10
D6  -> Pin 11
D7  -> Pin 12
A   -> 5V (Backlight +)
K   -> GND (Backlight -)

[LED - Optional for Alert]
+ve -> Pin 13
-ve -> GND (through 220-ohm resistor)

ARDUINO CODE:

#include <LiquidCrystal.h>
#include <DHT.h>

#define DHTPIN 2     // Sensor data pin
#define DHTTYPE DHT11
DHT dht(DHTPIN, DHTTYPE);

LiquidCrystal lcd(7, 8, 9, 10, 11, 12);

int ledPin = 13; // LED pin for alert

void setup() {
  lcd.begin(16, 2);
  dht.begin();
  pinMode(ledPin, OUTPUT);
  lcd.print("Temp Monitor");
  delay(2000);
}

void loop() {
  float temp = dht.readTemperature();
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Temp: ");
  lcd.print(temp);
  lcd.print(" C");

  if (temp > 30.0) {
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(ledPin, LOW);
  }
  delay(2000);
}


FUTURE SCOPE:

•Add Wi-Fi module to log data to a cloud platform
•Add humidity monitoring display
•Use OLED instead of LCD for compact display

Author 
Sweeton Prince S

