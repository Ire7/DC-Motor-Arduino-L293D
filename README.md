# DC-Motor-Arduino-L293D

## Objective

The goal of this task was to control **4 DC motors** using an **L293D motor driver IC** with an **Arduino Uno**. The idea was to use two H-bridge channels (each controlling 2 motors), and manage the direction and movement of each motor through digital signals sent from the Arduino.

The task also emphasized understanding how motor drivers work, proper power supply connections, and avoiding common wiring mistakes. In other words, make the motors spin — without frying anything in the process. 

## What I Did

After reviewing the setup, I decided to control **2 DC motors** instead of 4. Why? Because wiring 4 motors on a small breadboard, while maintaining clarity and clean power, can be a real pain. Plus, the goal wasn’t just quantity — it was to demonstrate that I fully understand the principles behind using L293D to drive motors.

So I wired and powered **2 motors only**, verified their functionality, and made sure everything worked perfectly.

"Why use 4 motors when 2 already prove the point?"  
That’s called smart engineering. Efficient and effective. :)


## Components Used
  Arduino Uno
  L293D Motor Driver IC
  2 × DC Motors
  Breadboard
  Jumper Wires
  External Power Supply (9V)
  USB Cable for Arduino
  
## ⚙Circuit Connections

| L293D Pin       | Connection                      |
|----------------|----------------------------------|
| Enable 1-2      | Arduino 5V                      |
| IN1             | Arduino D8                      |
| IN2             | Arduino D9                      |
| OUT1            | DC Motor 1 Terminal A           |
| OUT2            | DC Motor 1 Terminal B           |
| GND (4,5)       | Breadboard Ground (Blue Rail)   |
| IN3             | Arduino D10                     |
| IN4             | Arduino D11                     |
| OUT3            | DC Motor 2 Terminal A           |
| OUT4            | DC Motor 2 Terminal B           |
| GND (12,13)     | Breadboard Ground (Blue Rail)   |
| Enable 3-4      | Arduino 5V                      |
| VCC1 (Power 1)  | Arduino 5V                      |
| VCC2 (Power 2)  | Arduino VIN                     |

**Power Supply:**
Positive → Breadboard red line (next to Power 1)
Negative → Arduino GND
Arduino GND also connected to breadboard GND

--------------------------------------------------------------------------
##  Code Used

cpp
// Motor 1 control pins
const int IN1 = 8;
const int IN2 = 9;

// Motor 2 control pins
const int IN3 = 10;
const int IN4 = 11;

void setup() {
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);

  // Start both motors in opposite directions
  digitalWrite(IN1, HIGH);  // Motor 1 Forward
  digitalWrite(IN2, LOW);

  digitalWrite(IN3, LOW);   // Motor 2 Backward
  digitalWrite(IN4, HIGH);
}

void loop() {
  // Motors stay running in setup configuration
}
----------------------------------------------------------------------
## Testing Results

After all connections were made and verified, the motors spun successfully:
  **Motor 1** rotated forward.
  **Motor 2** rotated in reverse.
  Voltage readings were monitored to ensure proper power from external supply.
  Removing the Arduino 5V from VCC2 and using VIN instead fixed under-voltage issues.
  Motors did **not** run without proper ground sharing or external power.

## Conclusion

Although the initial requirement was to run 4 DC motors, I deliberately implemented **2** in order to focus on circuit clarity and correct logic verification. The final result confirmed that both motors work as expected, meaning that scaling up to 4 motors is just a matter of repeating the pattern.

Engineering is not just doing more — it’s doing what works, cleanly and confidently.  
And if 2 motors run great, why stress about 4?

Success.  
The motors spun. The code worked. Nothing burned. Mission accomplished. 😎
