# Good Morning: Smart Wake-Up System

A smart IoT system designed to improve wake-up routines by integrating sound and light sensors with real-time data analysis.

## Project Overview

The "Good Morning" system leverages IoT technology with an ESP32 microcontroller to monitor environmental conditions and enhance the wake-up experience. The system listens for alarm clock sounds, adjusts lighting accordingly, and logs data for further analysis.

Key functionalities include:
- **Alarm Sound Detection**: Activates the system upon detecting an alarm clock sound.
- **Adaptive Lighting Control**: Illuminates an LED strip when an alarm is detected in a dark room, and turns off the lights when the room becomes bright.
- **Real-Time Data Logging**: Sends environmental data to Adafruit IO for monitoring and analysis, with email notifications based on specific triggers.

## Components Used

- **ESP32 Microcontroller**: Central unit for processing sensor data and controlling outputs.
- **Microphone Sensor**: Detects alarm clock sounds.
- **Light Sensor**: Measures ambient light levels.
- **LED Strip**: Provides visual cues by lighting up in response to sensor inputs.
- **Adafruit IO**: Platform for data logging, visualization, and email notifications.

These components work together seamlessly to detect environmental changes and execute responsive actions in real time.

## Features

1. **Smart Alarm Detection**: Enhances the waking experience by automatically turning on lights when an alarm sound is detected in a dark room.
2. **Automatic Light Adjustment**: Saves energy by turning off the lights when natural daylight is sufficient.
3. **Data Monitoring and Alerts**: This feature enables users to track their environment through real-time data and receive alerts for significant changes.

## Contribution

I designed, developed, and tested the system as part of my coursework. This included integrating the hardware components, writing the code for the ESP32, and configuring data transmission and visualization using Adafruit IO. Contributions are welcome; please fork the repository and submit a pull request with your improvements.

## Acknowledgements

Special thanks to the "Internet of Things" course instructors for their guidance and support throughout this project.

---

For more details, refer to the original project documentation on Instructables: [Good Morning Project](https://www.instructables.com/Good-Morning/)
