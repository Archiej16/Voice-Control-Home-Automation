# Voice-Control-Home-Automation
This project lets you control your home appliances using voice commands via a smartphone! Built using an Arduino UNO and HC-05 Bluetooth module, it processes voice inputs through a mobile app, which sends commands to the Arduino to switch devices on or off. A simple step toward a smarter, hands-free lifestyle powered by hardware and code.

# Arduino Bluetooth Home Automation

Control your AC, lights, fan, and TV wirelessly using simple text commands sent via Bluetooth to an Arduino! This project uses the `SoftwareSerial` library to read data from a Bluetooth module (like HC-05) and activates relays connected to appliances.

## Features

- Turn ON/OFF individual appliances via Bluetooth
- Supports commands for:
  - AC
  - Light
  - Fan
  - TV
- "Turn ON/OFF all" functionality
- Simple command format using asterisks (`*`) and hashtags (`#`) as delimiters
- Serial monitoring for debugging

## Components Required

- Arduino Uno (or similar)
- HC-05 Bluetooth Module
- 4 x 5V Relay Modules
- Jumper Wires
- Power Supply
- Appliances (AC, fan, light, TV – for demonstration)
- Breadboard (optional)

## 🔌 Wiring Setup

| Device       | Arduino Pin |
|--------------|-------------|
| AC Relay     | D4          |
| Light Relay  | D5          |
| Fan Relay    | D6          |
| TV Relay     | D7          |
| HC-05 TX     | D0 (rxPin)  |
| HC-05 RX     | D1 (txPin)  |

>  **Note:** Do NOT connect the Bluetooth module while uploading the sketch to the Arduino, as pins 0 and 1 are used by the serial monitor during upload.

## Command Format

Each command must:
- Begin with `*`
- End with `#`
- Be typed exactly (case-sensitive)

| Command             | Function           |
|---------------------|--------------------|
| `*turn on AC#`      | Turns on AC        |
| `*turn off AC#`     | Turns off AC       |
| `*turn on light#`   | Turns on light     |
| `*turn off light#`  | Turns off light    |
| `*turn on fan#`     | Turns on fan       |
| `*turn off fan#`    | Turns off fan      |
| `*turn on TV#`      | Turns on TV        |
| `*turn off TV#`     | Turns off TV       |
| `*turn on all#`     | Turns on all       |
| `*turn off all#`    | Turns off all      |

## How It Works

- The Bluetooth module sends a command string to the Arduino via `SoftwareSerial`.
- The sketch reads characters until it detects a `#`.
- It matches the full command and performs the corresponding action.
- All appliances are controlled using digital output pins connected to relay modules.

##  Testing

1. Upload the code to your Arduino.
2. Open the Serial Monitor (9600 baud).
3. Connect your phone to the HC-05 module using a Bluetooth terminal app.
4. Send a command like `*turn on fan#` and see it take effect.

## Notes

- Make sure your relays are active-LOW (LOW signal turns them ON).
- You can modify the pin numbers or command strings in the code as needed.
- If relays behave oppositely (ON when OFF), swap `HIGH`/`LOW` in `digitalWrite()`.

## License
You are free to use, modify, and share it—just give credit where it's due!
