# Air-pollution-monitoring-system-using-IoT
To analysis the Air Quality in thr form of ppm by displaying in LCD and Buzzer alarm when Air Quality exceed the limit.


#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);



#define LED 2

#define Buzzer 3

#define Sensor A1



void setup() {

  Serial.begin(9600);

  lcd.init();

  lcd.backlight();

  pinMode(LED, OUTPUT);

  pinMode(Buzzer, OUTPUT);

}



void loop() {

  int value = analogRead(Sensor);

  lcd.setCursor(0, 0);

  lcd.print("Value :");

  lcd.print(value);

  lcd.print("  ");



  if (value > 100) {

    digitalWrite(LED, HIGH);

    digitalWrite(Buzzer, HIGH);

    lcd.setCursor(0, 1);

    lcd.print("GAS Detected!");

  } else {

    digitalWrite(LED, LOW);

    digitalWrite(Buzzer, LOW);

    lcd.setCursor(0, 1);

    lcd.print("No Gass Detected");

  }

}
