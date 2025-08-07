# Send DHT22 data with ESP32 using MQTT to Node-Red Dashboard

 
NOTE: Add the wifi library for ESP32 for wifi connection.

NOTE: In real world project the Producer Task can also be replaced with sensors like DHT11 or DHT22(Temperature & Humudity sensors). 

NOTE: If you are using real/physical DHT11 or DHT22 sensor then, you need to add DHT sensor library for ESP32 to your code, So that ESP32 can communicate with sensor.

NOTE: You might also use PubSubClient library so that your ESP32 understands MQTT communication.

NOTE : Node-RED is an open-source, visual programming tool/flow-based programming tool that uses nodes and edges to program & is primarily used for wiring together hardware devices, APIs, and online services, especially within the context of the Internet of Things (IoT). It provides a visual, low-code development environment that allows users to create applications by dragging and dropping "nodes" and connecting them to form "flows"/edges

NOTE: Install Node-Red and Node-Red dashboard. Then after installing node-red, it will output the IP of server that you can use. Check that IP in browser.

NOTE: The Node-red dashboard is different from just Node-red. Once you program the system using Node-Red, You need to also install the node red dashboard which outputs the IP address, If you check the IP address it would display all the telemetry data on dashboard.

" NOTE: USING NODE-RED YOU WILL ESENTIALLY CREATE THE SERVER & PROGRAM THE SERVER BEHAVIOUR, WORKFLOW , SYSTEM. YOU WILL GIVE SERVER MULTIPLE PARAMETERS SUCH AS TO WHAT CLIENTS AND SENSERS THE SERVER NEEDS TO CONNECT AND HOW TO CONNECT,  SUCH AS WHAT PROTOCOL SHOULD BE USED, WHAT TO DISPLAY. THEN YOU NEED TO CONNECT THE NODE-RED TO THE NODE-RED DASHBOARD AND DEPLOY NODE-RED DASHBOARD. THEN YOU IF YOU COPY THE IP AND CHECK YOU CAN GRAPHICALLY MONITER THE TELEMETRY DATA FROM MICROCONTROLLER SENSORS. "

Home Automation
Data can be logged or sent to a cloud service via MQTT.
Interrupt-Driven Event Handling

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

## Flow diagram of the Project


### Step 1: Install the Required Libraries
- Open an Arduino IDE --> Tools --> Manage Libraries
- Search and install the following libraries
    
    1. pubsubclient
    
    2. WiFi
    
    3. DHT sensor library for ESPx
    

### Step 2: Hardware Schematic
- Four pin DHT22

### Step 3: Running the program
- Copy the code to the Arduino IDE
- Setup the Board and Port
- Connect the ESP32 to the USB port of the computer
- Upload the code
- Monitor the values in the Serial monitor

### Step 4: Setup the Node-RED flow

- Open Node-RED URL in the browser
- Click on Menu --> Manage Palette
- Search for "node-red-dashboard" and install it. 
- Import the flow using the following code

```
[{"id":"5e04b9dd.81c658","type":"tab","label":"MQTT Dashboard","disabled":false,"info":""},{"id":"235eb13c.0e6e6e","type":"mqtt in","z":"5e04b9dd.81c658","name":"","topic":"iotfrontier/temperature","qos":"2","datatype":"auto-detect","broker":"6ec4dcef.913b24","nl":false,"rap":false,"inputs":0,"x":144,"y":347,"wires":[["7e75f56e.a3ef1c","125d1072.694a2"]]},{"id":"7e75f56e.a3ef1c","type":"debug","z":"5e04b9dd.81c658","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"payload","targetType":"msg","statusVal":"","statusType":"auto","x":341,"y":314,"wires":[]},{"id":"98d00e19.a6762","type":"mqtt in","z":"5e04b9dd.81c658","name":"","topic":"iotfrontier/humidity","qos":"2","datatype":"auto-detect","broker":"6ec4dcef.913b24","nl":false,"rap":false,"inputs":0,"x":130,"y":120,"wires":[["07048bb50e4963b7","89bc352.e41bac8"]]},{"id":"89bc352.e41bac8","type":"ui_gauge","z":"5e04b9dd.81c658","name":"Humidity","group":"92a9cd27.99b9d","order":0,"width":0,"height":0,"gtype":"gage","title":"Humidity","label":"%","format":"{{value}}","min":0,"max":"100","colors":["#00b3d9","#0073e6","#001bd7"],"seg1":"33","seg2":"66","diff":false,"className":"","x":340,"y":180,"wires":[]},{"id":"125d1072.694a2","type":"ui_chart","z":"5e04b9dd.81c658","name":"Temperature","group":"92a9cd27.99b9d","order":1,"width":0,"height":0,"label":"Temperature","chartType":"line","legend":"false","xformat":"HH:mm","interpolate":"linear","nodata":"","dot":false,"ymin":"","ymax":"","removeOlder":1,"removeOlderPoints":"","removeOlderUnit":"3600","cutout":0,"useOneColor":false,"useUTC":false,"colors":["#1f77b4","#aec7e8","#ff7f0e","#2ca02c","#98df8a","#d62728","#ff9896","#9467bd","#c5b0d5"],"outputs":1,"useDifferentColor":false,"className":"","x":341,"y":374,"wires":[[]]},{"id":"07048bb50e4963b7","type":"debug","z":"5e04b9dd.81c658","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"payload","targetType":"msg","statusVal":"","statusType":"auto","x":350,"y":100,"wires":[]},{"id":"6ec4dcef.913b24","type":"mqtt-broker","name":"","broker":"broker.hivemq.com","port":"1883","clientid":"","autoConnect":true,"usetls":false,"protocolVersion":"4","keepalive":"15","cleansession":true,"birthTopic":"","birthQos":"0","birthPayload":"","birthMsg":{},"closeTopic":"","closePayload":"","closeMsg":{},"willTopic":"","willQos":"0","willPayload":"","willMsg":{},"userProps":"","sessionExpiry":""},{"id":"92a9cd27.99b9d","type":"ui_group","name":"Temperature and Humidity","tab":"6f670e80.d2e0f","order":1,"disp":true,"width":"6","collapse":false,"className":""},{"id":"6f670e80.d2e0f","type":"ui_tab","z":"5e04b9dd.81c658","name":"Dashboard","icon":"dashboard"}]
```
- Deploy the flow
- Navigate to the following URL and modify the <your IP address>. For example http://localhost:1880/ui
```
http://<your IP address>:1880/ui
```
  

