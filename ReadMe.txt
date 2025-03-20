Use Case of the Extended FreeRTOS ESP32 Project
This updated project now includes:

A Producer Task: Simulates a sensor reading and places data into a queue.
A Consumer Task: Retrieves and processes data from the queue.
An LED Task: Responds to a semaphore signal to blink an LED when a sensor event occurs.
Real-World Applications
IoT Sensor Monitoring

The producer simulates a real sensor (e.g., motion detector, temperature sensor).
When an event is detected, data is sent to a consumer for logging or further processing.
The LED task visually indicates an event.
Home Automation

A motion sensor triggers the LED, mimicking an automatic light system.
Data can be logged or sent to a cloud service via MQTT.
Interrupt-Driven Event Handling

The semaphore ensures an action (e.g., turning on an LED) happens only when required.
This structure can be expanded for other real-time applications.