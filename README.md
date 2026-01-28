# 16x2-LCD-display-and-distance-Measurement-System-using-Raspberry-Pi
This project uses a Raspberry Pi, an ultrasonic sensor, and a 16x2 LCD display to measure and show the distance of an object in real time.

The ultrasonic sensor calculates the distance by sending sound waves and measuring the time taken for the echo to return. The measured distance is then displayed on an LCD screen and printed in the terminal.

🚀 Features:
- 📡 Measures distance using an HC-SR04 Ultrasonic Sensor
- 🖥️ Displays real-time distance on a 16x2 LCD
- 🧠 Uses Raspberry Pi GPIO pins for hardware control
- ⏱️ Continuously updates distance every 0.5 seconds
- 💻 Also prints the distance in the terminal for monitoring

🧰 Hardware Required:

- Raspberry Pi (any model with GPIO)
- HC-SR04 Ultrasonic Sensor
- 16x2 LCD Display (without I2C)
- Jumper wires
- Breadboard
- 220Ω resistor (recommended for LCD backlight)

🔌 GPIO Pin Connections

Ultrasonic Sensor (HC-SR04)

Sensor Pin	Raspberry Pi GPIO

- VCC ---	5V
- GND ---	GND
- TRIG ---	GPIO 21
- ECHO ---	GPIO 20 (use voltage divider to reduce 5V to 3.3V)

16x2 LCD Pins
- LCD Pin ---	GPIO Pin
- RS ---	GPIO 2
- E ---	GPIO 3
- D4 ---	GPIO 4
- D5 ---	GPIO 17
- D6 ---	GPIO 27
- D7 ---	GPIO 22

🧠 How It Works
1️⃣ Distance Measurement
- The Raspberry Pi sends a short pulse from the TRIG pin.
- The ultrasonic sensor emits a sound wave.
- The ECHO pin goes HIGH until the sound wave returns.
- The time difference between sending and receiving is calculated.
- Distance is computed using:

      𝐷𝑖𝑠𝑡𝑎𝑛𝑐𝑒 = (𝑇𝑖𝑚𝑒 × 𝑆𝑝𝑒e𝑑 𝑜𝑓 𝑆𝑜𝑢𝑛𝑑 (34300 𝑐𝑚/𝑠)) / 2
Division by 2 accounts for the sound traveling to the object and back.

2️⃣ LCD Display

- The LCD operates in 4-bit mode using GPIO pins.
- The first line shows: Measured Dist:
- The second line shows the live distance value in centimeters.

💻 Software Requirements

Install required libraries on Raspberry Pi:

    pip install RPi.GPIO spidev
(spidev is imported but not heavily used here — included for SPI compatibility if extended later)

▶️ How to Run

1. Connect all components correctly.
2. Enable GPIO access on Raspberry Pi.
3. Run the script:

       python3 Main.py
4. The LCD will start displaying the measured distance continuously.

🧪 Sample Output
Terminal:

    Measured Distance = 24.6 cm
    Measured Distance = 25.1 cm

LCD Display:

    Measured Dist:
    24.60 cm

⚠️ Important Notes

- The ECHO pin outputs 5V, but Raspberry Pi GPIO accepts only 3.3V.
  -👉 Use a voltage divider (two resistors) to safely step down the voltage.
- Make sure the sensor is placed in front of a stable object for accurate readings.
- Avoid running without proper wiring — it may damage the Pi.
