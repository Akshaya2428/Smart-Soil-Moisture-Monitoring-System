🌱 Smart Soil Moisture Monitoring & Auto Irrigation System

An Arduino-based smart irrigation system that monitors soil moisture levels and automatically controls a water pump with LED alerts — designed to help farmers optimize water usage.


📌 Project Overview

This project reads soil moisture levels using a capacitive soil moisture sensor and takes automated action:


🟢 Green LED ON → Soil is wet (sufficient moisture)
🔴 Red LED ON + Pump ON → Soil is dry (auto irrigation triggered)


Simulated on Tinkercad with full circuit and working code.


🛠️ Components Used

Component                         Quantity
Arduino UNO                           1
Soil Moisture Sensor                  1
Green LED                             1
Red LED                               1
Water Pump (DC Motor)                 1
Resistors                             2
Breadboard                            1
Jumper Wires                      As required


⚙️ How It Works


Arduino powers the soil moisture sensor briefly (to reduce corrosion)
Reads analog value from sensor via pin A0
Compares reading against threshold value (600)
If moisture is above threshold → Green LED ON, Pump OFF (soil is wet)
If moisture is below threshold → Red LED ON, Pump ON (soil is dry, irrigation starts)
Reading is printed to Serial Monitor for real-time tracking



📊 Threshold Logic

Sensor Value > 600  →  WET  → Green LED ON  | Pump OFF
Sensor Value < 600  →  DRY  → Red LED ON    | Pump ON


Note: Threshold value (600) can be calibrated based on soil type

💻 Code

cppconst int sensorpin = A0;
const int sensorpower = 2;
const int LED1 = 2;   // Red LED
const int LED2 = 3;   // Green LED
const int pumppin = 11;

int sensor;
const int delayTime = 1;
int thresh = 600;

void setup(){
  pinMode(LED1, OUTPUT);
  pinMode(LED2, OUTPUT);
  pinMode(sensorpower, OUTPUT);
  pinMode(pumppin, OUTPUT);
  Serial.begin(9600);
}

void loop(){
  digitalWrite(sensorpower, HIGH);
  delay(10);
  sensor = analogRead(sensorpin);
  digitalWrite(sensorpower, LOW);
  Serial.println(sensor);

  if(sensor > thresh){
    digitalWrite(LED1, LOW);
    digitalWrite(LED2, HIGH);
    digitalWrite(pumppin, LOW);
  } else {
    digitalWrite(LED1, HIGH);
    digitalWrite(LED2, LOW);
    digitalWrite(pumppin, HIGH);
  }
  delay(delayTime);
}


🔗 Simulation Link

👉 View on Tinkercad


🌾 Real World Application


Helps farmers avoid overwatering and underwatering
Saves water through automated irrigation
Low cost and easy to deploy in fields
Can be extended with IoT (ESP32/NodeMCU) for remote monitoring



🚀 Future Improvements


 Add LCD display to show moisture percentage
 Integrate ESP32 for IoT based remote monitoring
 Add multiple sensors for different zones
 Mobile app notification when pump activates
 Solar powered for field deployment



🧰 Tools & Platform


Simulation: Tinkercad
Microcontroller: Arduino UNO
Language: Embedded C (Arduino)



👤 Author

Your Name : Sajja Akshaya

📄 License

This project is open source and available under the MIT License
