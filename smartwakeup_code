#include "WiFi.h"
#include "AdafruitIO_WiFi.h"
#include <Adafruit_NeoPixel.h>

// Adafruit IO credentials
#define IO_USERNAME "your_io_username"
#define IO_KEY "your_io_key"

// Wi-Fi credentials
#define WIFI_SSID "your_wifi_ssid"
#define WIFI_PASS "your_wifi_password"

// Initialize Adafruit IO connection
AdafruitIO_WiFi io(IO_USERNAME, IO_KEY, WIFI_SSID, WIFI_PASS);
AdafruitIO_Feed *light = io.feed("light");
AdafruitIO_Feed *sound = io.feed("sound");

// Pin definitions
#define MIC_PIN 34             // Microphone sensor pin
#define LIGHT_SENSOR_PIN 32    // Light sensor pin
#define LED_PIN 23             // LED strip pin
#define NUM_LEDS 12            // Number of LEDs in the strip

// Threshold values
int soundThreshold = 3000;     // Threshold for detecting sound
int lightThreshold = 1200;     // Threshold for detecting light
bool ledsTurnedOn = false;     // Flag to check if LEDs are on

// Initialize LED strip
Adafruit_NeoPixel strip = Adafruit_NeoPixel(NUM_LEDS, LED_PIN, NEO_GRB + NEO_KHZ800);

void setup() {
  Serial.begin(115200);

  // Connect to Adafruit IO
  io.connect();
  while (io.status() < AIO_CONNECTED) {
    Serial.print(".");
    delay(500);
  }
  Serial.println("\nConnected to Adafruit IO!");

  // Initialize sensors and LEDs
  pinMode(MIC_PIN, INPUT);
  pinMode(LIGHT_SENSOR_PIN, INPUT);
  strip.begin();
  turnOffLEDs();

  Serial.println("System initialized: Microphone and Light Sensor ready.");
}

void loop() {
  io.run();

  // Read values from sensors
  int soundLevel = analogRead(MIC_PIN);
  int lightLevel = analogRead(LIGHT_SENSOR_PIN);

  // Send data to Adafruit IO feeds
  light->save(lightLevel);
  sound->save(soundLevel);

  // Debug output to Serial Monitor
  Serial.print("Sound Level: ");
  Serial.print(soundLevel);
  Serial.print(" | Light Level: ");
  Serial.println(lightLevel);

  // Check conditions to turn on LEDs
  if (lightLevel > lightThreshold && soundLevel > soundThreshold && !ledsTurnedOn) {
    Serial.println("Sound detected in a dark room. Turning on LEDs...");
    turnOnLEDs();
    ledsTurnedOn = true;
  }

  // Check conditions to turn off LEDs
  if (ledsTurnedOn && lightLevel < lightThreshold) {
    Serial.println("Room is bright. Turning off LEDs...");
    turnOffLEDs();
    ledsTurnedOn = false;
  }

  delay(2000);
}

// Function to turn on LEDs
void turnOnLEDs() {
  for (int i = 0; i < strip.numPixels(); i++) {
    strip.setPixelColor(i, strip.Color(0, 0, 255));  // Blue color
  }
  strip.show();
}

// Function to turn off LEDs
void turnOffLEDs() {
  for (int i = 0; i < strip.numPixels(); i++) {
    strip.setPixelColor(i, strip.Color(0, 0, 0));  // Turn off LEDs
  }
  strip.show();
}
