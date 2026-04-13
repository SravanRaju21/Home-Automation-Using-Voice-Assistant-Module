# Home-Automation-Using-Voice-Assistant-Module
The Home Automation Using Voice Assistant Module enables users to control household appliances using voice commands. A voice recognition module processes commands and sends signals to an Arduino, which controls devices via relays. It offers a simple, low-cost, and hands-free automation solution.

## 📌 Project Overview
This project demonstrates a simple **home automation system** controlled using a voice recognition module. The system allows users to control electrical appliances like lights or fans using voice commands.

The voice module processes spoken commands and sends signals to the Arduino, which then controls appliances through a relay module.

---

## 🎯 Objectives
- To design a voice-controlled home automation system  
- To control appliances using voice commands  
- To reduce manual switching effort  
- To understand interfacing of voice modules with Arduino  
- To implement relay-based device control  

---

## 🧰 Components Used
- Arduino Uno  
- Voice Recognition Module (DFRobot / Elechouse type)  
- Relay Module (2-Channel)  
- Speaker  
- Jumper Wires  
- Power Supply  

---

## 🔌 Circuit Connections

### 🎤 Voice Recognition Module
- VCC → 5V  
- GND → GND  
- TX → Arduino RX (Pin 0)  
- RX → Arduino TX (Pin 1)  

### ⚡ Relay Module
- VCC → 5V  
- GND → GND  
- IN1 → Arduino Pin 7  
- IN2 → Arduino Pin 8  

### 🔊 Speaker
- Connected to voice module audio output  

---

## ⚙️ Working Principle
- The voice recognition module is trained with specific commands (e.g., "Light ON", "Light OFF")  
- When the user speaks a command, the module processes and matches it  
- The recognized command is sent to the Arduino via serial communication  
- Arduino interprets the command and activates the corresponding relay  
- The relay switches ON/OFF the connected appliance  
- The speaker provides audio feedback for confirmation  

---

## 💻 Arduino Code

```cpp
int relay1 = 7;
int relay2 = 8;
char command;

void setup() {
  Serial.begin(9600);
  pinMode(relay1, OUTPUT);
  pinMode(relay2, OUTPUT);
}

void loop() {
  if (Serial.available()) {
    command = Serial.read();

    if (command == 'A') {        // Command for ON
      digitalWrite(relay1, HIGH);
    } 
    else if (command == 'B') {   // Command for OFF
      digitalWrite(relay1, LOW);
    } 
    else if (command == 'C') {
      digitalWrite(relay2, HIGH);
    } 
    else if (command == 'D') {
      digitalWrite(relay2, LOW);
    }
  }
}
