<h1 align="center"> ESP32 Wroom NodeMcu WiFi CP2102 </h1>

# Content

1. [Chapter 1: Introduction to Basic Electronics](#chapter1)
    - [Chapter 1 - Part 1: Basic Components](#chapter1part1)
    - [Chapter 1 - Part 2: Basic Circuits](#chapter1part2)
    - [Chapter 1 - Part 3: Basic Tools](#chapter1part3)
2. [Chapter 2: Introduction to the ESP32 Wroom](#chapter2)
    - [Chapter 2 - Part 1: ESP32 Features](#chapter2part1)
    - [Chapter 2 - Part 2: ESP32 Pinout](#chapter2part2)
3. [Chapter 3: Setting Up the Development Environment](#chapter3)
    - [Chapter 3 - Part 1: Necessary Software](#chapter3part1)
    - [Chapter 3 - Part 2: Setup Steps](#chapter3part2)
4. [Chapter 4: First Projects with the ESP32](#chapter4)
    - [Chapter 4 - Part 1: Blink an LED](#chapter4part1)
    - [Chapter 4 - Part 2: Temperature Sensor with DHT11](#chapter4part2)


## <a name="chapter1"></a>Chapter 1: Introduction to Basic Electronics

#### <a name="chapter1part1"></a>Chapter 1 - Part 1: Basic Components

- **Resistors**: Limit the amount of current that flows through a circuit.

- **Capacitors**: Store and release electrical energy.

- **LEDs**: Light-emitting diodes that light up when a current passes through them.

- **Buttons/Switches**: Used to manually open or close circuits.

- **Transistors**: Used for amplification and switching of electrical signals.

- **Diodes**: Allow current to flow in only one direction.

- **Sensors**: Devices that detect changes in the environment, such as temperature, light, humidity, etc.

#### <a name="chapter1part2"></a>Chapter 1 - Part 2: Basic Circuits

- **Series and Parallel**: Learn how components behave when connected in series or parallel.

- **Ohm’s and Kirchhoff’s Laws**: Fundamentals to understand voltage, current, and resistance.

#### <a name="chapter1part3"></a>Chapter 1 - Part 3: Basic Tools

- **Multimeter**: To measure voltage, current, and resistance.

- **Breadboard**: To temporarily assemble circuits.

- **Jumpers**: Wires used to make connections on the breadboard.

- **Power Supply**: To provide power to your circuits.

## <a name="chapter2"></a>Chapter 2: Introduction to the ESP32 Wroom

#### <a name="chapter2part1"></a>Chapter 2 - Part 1: ESP32 Features

- **CPU**: Dual-core with up to 240MHz.

- **Memory**: 520KB RAM.

- **Connectivity**: WiFi 802.11 b/g/n and Bluetooth 4.2.

- **GPIOs**: Many input/output pins to connect sensors, LEDs, buttons, etc.

- **Protocols**: Supports SPI, I2C, UART, PWM, ADC, DAC, etc.

#### <a name="chapter2part2"></a>Chapter 2 - Part 2: ESP32 Pinout

[ESP-32_NodeMCU Developmentboard Pinout](https://github.com/vitorstabile/esp32wroomnodemcuwifico2102/blob/main/img/ESP-32_NodeMCU_Developmentboard_Pinout.pdf)

## <a name="chapter3"></a>Chapter 3: Setting Up the Development Environment

#### <a name="chapter3part1"></a>Chapter 3 - Part 1: Necessary Software

- **Arduino IDE**: A popular development environment for microcontrollers.

- **CP210x Driver**: So that your computer recognizes the ESP32.

#### <a name="chapter3part2"></a>Chapter 3 - Part 2: Setup Steps

- **1: Install the Arduino IDE**: Download and install the Arduino IDE from the official Arduino website.

- **2: Install the CP210x Driver**: Download the driver from the official Silicon Labs website and install it.

- **3: Configure the ESP32 in the Arduino IDE**:

  - Open the Arduino IDE.

  - Go to File > Preferences.

  - In Additional Board Manager URLs, add: https://dl.espressif.com/dl/package_esp32_index.json.

  - Go to Tools > Board > Boards Manager, search for esp32 and install the package.

## <a name="chapter4"></a>Chapter 4: First Projects with the ESP32

#### <a name="chapter4part1"></a>Chapter 4 - Part 1: Blink an LED

- **Necessary Components**
  - 220Ω resistor
  - LED
  - ESP32
  - jumpers

- **Circuit Assembly**
  - Connect an LED to the GPIO 2 pin of the ESP32 (positive side of the LED) and the other side to GND with a 220Ω resistor in series.
 
- **Code**:

 ```cpp
void setup() {
  pinMode(2, OUTPUT); // Set GPIO 2 as output
}

void loop() {
  digitalWrite(2, HIGH); // Turn the LED on
  delay(1000);           // Wait for 1 second
  digitalWrite(2, LOW);  // Turn the LED off
  delay(1000);           // Wait for 1 second
}
```

- **Upload the Code:**:
  - Connect the ESP32 to the computer via USB.
  - Select the correct board and port in Tools > Board and Tools > Port.
  - Click the upload button (right arrow).

#### <a name="chapter4part2"></a>Chapter 4 - Part 2: Temperature Sensor with DHT11

- **Necessary Components**
  - 220Ω resistor
  - LED
  - ESP32
  - jumpers
  - DHT11 sensor

- **Circuit Assembly**
  - Connect the data pin of the DHT11 to GPIO 4 of the ESP32, power to 3.3V, and GND.
 
- **Code**:

 ```cpp
#include "DHT.h"

#define DHTPIN 4     // DHT11 sensor pin
#define DHTTYPE DHT11 // Sensor type

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(115200);
  dht.begin();
}

void loop() {
  float h = dht.readHumidity();
  float t = dht.readTemperature();
  Serial.print("Humidity: ");
  Serial.print(h);
  Serial.print(" %\t");
  Serial.print("Temperature: ");
  Serial.print(t);
  Serial.println(" *C ");
  delay(2000);
}
```

- **Upload the Code:**:
  - Connect the ESP32 to the computer via USB.
  - Select the correct board and port in Tools > Board and Tools > Port.
  - Click the upload button (right arrow).
