
# Ultrasonic Sensor–Controlled Relay (Arduino Project)

This project uses an **HC-SR04 ultrasonic sensor** to detect the presence of a hand (or any object) and control a **relay module** accordingly. Common applications include a **contactless water pump**, **automatic sanitizer dispenser**, or any **proximity-based switch**.

---

## Features
- Measures distance using HC-SR04 ultrasonic sensor  
- Controls a relay based on distance threshold  
- Serial Monitor output for real-time readings  
- Simple and customizable logic

---

## Project Files
- `main.ino` — Arduino source code  
- `README.md` — Documentation

---

## Hardware Requirements
- Arduino Uno (or compatible board)  
- HC-SR04 ultrasonic sensor  
- Relay module  
- Jumper wires  
- (Optional) Water pump or actuated device

---

## Wiring Diagram

| Component        | Arduino Pin |
|------------------|-------------|
| HC-SR04 Trigger  | 10          |
| HC-SR04 Echo     | 11          |
| Relay Signal     | 7           |
| VCC / GND        | 5V & GND    |

---

## How It Works
1. Arduino sends a pulse via the sensor's trigger pin.  
2. Echo time is measured and converted to distance (cm).  
3. If distance is **greater than 10 cm** or invalid (≤ 0), the relay turns **ON**.  
4. If an object is **10 cm or closer**, the relay turns **OFF**.

You can change the threshold here:

```cpp
const int distanceThreshold = 10;
```

----------

## **📜 Code Overview**

### Distance Measurement

```cpp
duration = pulseIn(echoPin, HIGH);
distance = duration * 0.034 / 2;

```

### Relay Control

```cpp
if (distance > distanceThreshold || distance <= 0) {
    digitalWrite(relayPin, HIGH);  // Pump ON
} else {
    digitalWrite(relayPin, LOW);   // Pump OFF
}

```

----------

## **▶️ Usage**

1.  Upload the  `.ino`  file to your Arduino board.
    
2.  Open  **Serial Monitor**  at  **9600 baud**.
    
3.  Move your hand or an object near the sensor.
    
4.  Watch the relay switch ON/OFF based on detected distance.
    

----------

## **🛠 Troubleshooting**

-   **Distance always reads 0**  → Check Echo/Trig wiring.
    
-   **Relay always ON**  → Sensor may not be receiving clean signals; verify power.
    
-   **Erratic readings**  → Add a small capacitor or increase delay.
    

----------

## **📄 License**

This project is open-source. You may modify and distribute it freely.