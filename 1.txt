const byte buzzer_gpio = 18; // the PWM pin the LED is attached to
// how many points to fade the LED by
#define POTENTIOMETER_PIN  15


// the setup routine runs once when you press reset:
void setup() {
  Serial.begin(9600);

  pinMode(POTENTIOMETER_PIN, INPUT);
  pinMode(buzzer_gpio, OUTPUT);
}

// the loop routine runs over and over again forever:
void loop() {
  int analogValue = analogRead(POTENTIOMETER_PIN);
  int brightness = map(analogValue, 0, 4095, 0, 255);
  if (brightness > 200) {
    Serial.println("decrease the volume ");
    digitalWrite(buzzer_gpio, HIGH);
    delay(100);
  }
  digitalWrite(buzzer_gpio, LOW);
  Serial.println(brightness);
  delay(30);
}
