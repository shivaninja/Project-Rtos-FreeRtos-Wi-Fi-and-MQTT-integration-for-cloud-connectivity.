Use Case of the Extended FreeRTOS ESP32 Project
This updated project now includes:

A Producer Task: Simulates a sensor reading and places data into a queue.
A Consumer Task: Retrieves and processes data from the queue.
An LED Task: Responds to a semaphore signal to blink an LED when a sensor event occurs.
Real-World Applications
IoT Sensor Monitoring

The producer simulates a real sensor (e.g., motion detector, temperature sensor).
When an event is detected, data is sent to a consumer for logging or further processing. 
NOTE: Add the wifi library for ESP32 for wifi connection.
NOTE: In real world project the Producer Task can also be replaced with sensors like DHT11 or DHT22(Temperature & Humudity sensors). 
NOTE: If you are using real/physical DHT11 or DHT22 sensor then, you need to add DHT sensor library for ESP32 to your code, So that ESP32 can communicate with sensor.
NOTE: You might also use PubSubClient library so that your ESP32 understands MQTT communication. 
The LED task visually indicates an event.
Home Automation
A motion sensor triggers the LED, mimicking an automatic light system.
Data can be logged or sent to a cloud service via MQTT.
Interrupt-Driven Event Handling
The semaphore ensures an action (e.g., turning on an LED) happens only when required.

New Features Added
This updated FreeRTOS ESP32 project now includes Wi-Fi and MQTT integration for cloud connectivity.
Use Case Scenarios are such as IoT Sensor Data Streaming.
The ESP32 reads sensor data and publishes it to an MQTT broker (e.g., HiveMQ, Mosquitto, AWS IoT).
NOTE: An MQTT broker is a server that receives all messages from the clients and then routes the messages to the appropriate destination clients.
You can use HiveMQ, it is an temporary free MQTT-broker and a client based messaging platform which uses MQTT protocol for fast, reliable and efficient bi-directional data transfer to and from IoT devices.
You can use different types of HiveMQ MQTT brokers such as HiveMQ-cloud(Cloud based) or HiveMQ-Broker(self hosted).
Any subscribed client (e.g., a dashboard, cloud server) can receive and analyze this data.

Smart Home Automation
A motion sensor can trigger an MQTT message, notifying a home automation system.
The LED acts as an alert when motion is detected.
Remote Monitoring & Control
The ESP32 sends periodic status updates to the cloud.
A remote client can send commands via MQTT to control ESP32 operations.
