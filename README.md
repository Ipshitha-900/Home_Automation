# Home_Automation
It is the project based on IOT Arduino
#define BLYNK_TEMPLATE_ID "TMPL33ELh4Asm"
#define BLYNK_TEMPLATE_NAME "home automation1"
#define BLYNK_AUTH_TOKEN "VYAu-Q-XVEnB84f2CtcvqjhqqWnLstpZ"


#include <ESP8266wifi.h>
#include <BlynkSimpleEsp8266.h>

// Your WiFi credentials
char auth[] = BLYNK_AUTH_TOKEN;
char ssid[] = "realme C55";
char pass[] = "Suhana44";

// Pin configurations for controlling lights
int light1Pin = D1;  // GPIO pin for light 1
int light2Pin = D2;  // GPIO pin for light 2

void setup() {
  Serial.begin(115200);
  Blynk.begin(auth, ssid, pass);

  // Set the pin modes for lights
  pinMode(light1Pin, OUTPUT);
  pinMode(light2Pin, OUTPUT);

  // Initial state of lights (OFF)
  digitalWrite(light1Pin, LOW);
  digitalWrite(light2Pin, LOW);
}

void loop() {
  Blynk.run();
}

// Blynk Virtual Pins configuration
BLYNK_WRITE(V1) {  // Virtual Pin for Light 1
  int state = param.asInt();
  digitalWrite(light1Pin, state);
}

BLYNK_WRITE(V2) {  // Virtual Pin for Light 2
  int state = param.asInt();
  digitalWrite(light2Pin, state);
}
