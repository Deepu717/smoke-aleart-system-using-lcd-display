//#smoke-aleart-system-using-lcd-display
//SMART INNOVATIONS
#include <LiquidCrystal.h> // include liquidcrystal library
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);//pins used for 16x2 lcd display

int redLed = 10; // danger signal led
int buzzer = 8; //buzzer for sound when danger signal comes
int smokeA0 = A0; //pin to read sensor data
int sensorThres = 200;//value by the sensor for danger signal

void setup() {
  pinMode(redLed, OUTPUT);//output pins from arduino
  pinMode(buzzer, OUTPUT);
  pinMode(smokeA0, INPUT);//input pin to arduino to read the sensor data
  Serial.begin(9600);//boardrate
  lcd.begin(16,2);
}

void loop() {
  int analogSensor = analogRead(smokeA0);

  Serial.print("Pin A0: ");
  Serial.println(analogSensor);// print sensor data in serial moniter
  lcd.print("Smoke Level:"); //print sensor data in lcd display
  lcd.print(analogSensor-50);
  if (analogSensor-50 > sensorThres)//if sensor data is greater than sensor thres then it gives danger signal
  {
    digitalWrite(redLed, HIGH);
    lcd.setCursor(0, 2);
    lcd.print("Alert....!!!");//print aleart in lcd display
    tone(buzzer, 1000, 200);
  }
  else
  {
    digitalWrite(redLed, LOW);
    lcd.setCursor(0, 2);
    lcd.print(".....Normal.....");//if no danger then print normal in lcd display
    noTone(buzzer);
  }
  delay(500);
  lcd.clear();
}
