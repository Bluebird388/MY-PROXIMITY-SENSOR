 MY PROXIMITY SENSOR 

This project simulates a simple proximity sensor system using Arduino.  
It reads distance values (via a potentiometer mapped to meters) and triggers an LED alert when the distance is below a threshold.

---
 Components Used
- Arduino board (Uno/Nano/ESP32 in Wokwi)
- Potentiometer (simulates distance input)
- Ultrasonic sensor pins (trig/echo defined but not used in current code)
- Red LED (alerts when object is close)
- Serial Monitor (displays distance readings)

---

 How It Works
1. The potentiometer value (0–1023) is read as input.  
2. This value is mapped to a distance range (0–100 meters).  
3. The distance is printed to the Serial Monitor.  
4. If the distance is ≤ 50 meters, the red LED turns ON.  
5. If the distance is  50 meters, the red LED turns OFF.  

---
 Code Overview
```cpp
int redled = 6;
int trigpin = 9;
int echopin = 10;
int potpin = A0;
int potvalue;
int distance;

void setup() {
  pinMode(redled, OUTPUT);
  pinMode(trigpin, OUTPUT);
  pinMode(echopin, INPUT);
  Serial.begin(9600);
}

void loop() {
  potvalue = analogRead(A0);
  distance = map(potvalue, 0, 1023, 0, 100);

  Serial.print("Distance ");
  Serial.print(distance);
  Serial.println(" m");

  if(distance <= 50) {
    digitalWrite(redled, HIGH);
  } else {
    digitalWrite(redled, LOW);
  }
  delay(5000);
}
